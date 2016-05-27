# dhclient-script-multiwan
Fork of dhclient-script with modifications to better support multi-homed hosts

# Features
* Inserts routes with proto dhcp
* Does not touch DNS resolver config
* Adds explicit routes to DHCP servers (many ISPs use DHCP relays to servers on other subnets, this ensures requests to renew your lease go out the correct interface)
* If `ipset` is installed, your the IP will be added to a list named <interface>-ip. This makes writing NAT hairpinning in iptables easier.
* Default routes are added to routing tables named after the interface, and appropriate policy routing rules are set up (see [`routing-rules.sh.example`](routing-rules.sh.example) and [`rt_tables.example`](rt_tables.example))

# Limitations
* Hostname won't be set from DHCP server
* DHCPv6 support removed
* You didn't need your ISP's DNS servers, did you?
* Policy routing rule priorities are not guaranteed not to collide, but there's a spot to fixup collisions
