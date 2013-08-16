relaynode
=========

Configuration, script and instructions for relay nodes

tunnelbroker should be installed in /opt/tunnelbroker




TODO:

Add dependency package list and create install/setup script.

Add l2tp connections from relay to exit node.

There are some issues with MTU when using l2tp. When client connects
to sudomesh ap, then e.g. "wget amazon.com" results in lots of TCP
retransmissions.
If, on the client, we do "ifconfig wlan0 mtu 1000" and repeat
the "wget amazon.com" then everything works fine.


We had some problems with ICMP Redirects resulting from 10.42.0.1 (node)
and 10.42.0.10 (relay's bat0 interface) being on the same ethernet
due to the layer 2 tunnel. E.g. "ping google.com" would result in a long
wait followed by an ICMP Redirect (from 10.42.0.1 to 10.42.0.10) and
then pinging would proceed as normal. This behaviour seems to have
stopped, but I'm not sure why. 

To disable icmp redirects:

  echo 0 > /proc/sys/net/ipv4/conf/<ifname>/send_redirects

