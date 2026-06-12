---
title: "i can absolutely not connect to the net (wired)"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Demonice on 2007-10-28
hi!
i have a dell d630 latitude and i run the latest version of ubuntu.
it used to connect wired to the net with no problem at all, but after i removed the network cable and tried to access some wireless networks, the wired network stopped working when i plugged the cable back in. 
rebooting doesnt help.
i'd paste the syslog, but i'm writing from my other pc (windows). we're on the same router and everything, and it works fine here.
i'm a complete noob to linux - i don't know which part of the log is important. here are the last lines (written by hand ;_;):

dhcdbd: unrequested down ?:3
NetworkManager: <info> dhcp daemon state is now 14 (normal exit) for interface eth0
ntpdate[6087]: can't find host ntp.ubuntu.com
ntpdate[6087]: no server can be used, exiting
kernel: [75.312000]: eth0 no IPv6 routers present
kernel: [1063.000000]: tg3: eth0: link is down.
NetworkManager: <info> SWITCH: terminating current connection 'eth0' because it's no longer valid
NetworkManager: <info> Deactivating device eth0
avahi-daemon[5488]: withdrawing address record for 169.254.4.126 on eth0
avahi-daemon[5488]: leaving mDNS multicast group on interface eth0. IPv4 with address 169.254.4.126.
avahi-daemon[5488]: interface eth0. IPv4 no longer relevant for mDNS
avahi-daemon[5488]: withdrawing address record for fe80::21c:23ff:fe14:cc23 on eth0.


please help ;_;

---

### Post by Demonice on 2007-10-28
edit:
i completely removed the NetworkManagerprogram and then reinstalled it (using an usb-drive to copy the files o.O ).  it now works! however, i really want to avoid having to do this every time i disconnect, so i'm pasting the errorlog in hopes that someone has a better idea of what to do next time:

> Oct 28 22:44:41 Krataia kernel: [   19.216000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 28 22:44:41 Krataia kernel: [   19.216000] tg3: eth0: Flow control is on for TX and on for RX.
Oct 28 22:44:41 Krataia NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 28 22:44:41 Krataia NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 28 22:44:43 Krataia dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 28 22:44:43 Krataia NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 28 22:44:43 Krataia NetworkManager: <debug> [1193607883.298223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_7_10_i386'). 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) started... 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 28 22:44:43 Krataia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 28 22:44:43 Krataia anacron[5614]: Anacron 2.3 started on 2007-10-28
Oct 28 22:44:43 Krataia anacron[5614]: Normal exit (0 jobs run)
Oct 28 22:44:43 Krataia /usr/sbin/cron[5641]: (CRON) INFO (pidfile fd = 3)
Oct 28 22:44:43 Krataia /usr/sbin/cron[5642]: (CRON) STARTUP (fork ok)
Oct 28 22:44:43 Krataia /usr/sbin/cron[5642]: (CRON) INFO (Running @reboot jobs)
Oct 28 22:44:44 Krataia NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 28 22:44:44 Krataia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 28 22:44:44 Krataia NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 28 22:44:45 Krataia NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct 28 22:44:45 Krataia kernel: [   23.484000] NET: Registered protocol family 17
Oct 28 22:44:49 Krataia dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 28 22:44:49 Krataia NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Oct 28 22:44:49 Krataia gdmgreeter[5749]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Oct 28 22:44:49 Krataia gdmgreeter[5749]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Oct 28 22:44:49 Krataia gdmgreeter[5749]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Oct 28 22:44:49 Krataia gdmgreeter[5749]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Oct 28 22:44:52 Krataia dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Oct 28 22:44:58 Krataia dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct 28 22:45:10 Krataia kernel: [   48.660000] UDF-fs: No VRS found
Oct 28 22:45:10 Krataia kernel: [   48.728000] ISO 9660 Extensions: Microsoft Joliet Level 3
Oct 28 22:45:10 Krataia kernel: [   48.836000] ISO 9660 Extensions: RRIP_1991A
Oct 28 22:45:14 Krataia hcid[5523]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Oct 28 22:45:14 Krataia hcid[5523]: Default authorization agent (:1.20, /org/bluez/auth) registered
Oct 28 22:45:16 Krataia dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 28 22:45:19 Krataia NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 28 22:45:19 Krataia NetworkManager: <info>  Updating VPN Connections... 
Oct 28 22:45:19 Krataia NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Oct 28 22:45:19 Krataia NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Oct 28 22:45:20 Krataia dhclient: No DHCPOFFERS received.
Oct 28 22:45:20 Krataia avahi-autoipd(eth0)[5990]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 28 22:45:20 Krataia avahi-autoipd(eth0)[5990]: Successfully called chroot().
Oct 28 22:45:20 Krataia avahi-autoipd(eth0)[5990]: Successfully dropped root privileges.
Oct 28 22:45:20 Krataia avahi-autoipd(eth0)[5990]: Starting with address 169.254.4.126
Oct 28 22:45:26 Krataia avahi-autoipd(eth0)[5990]: Callout BIND, address 169.254.4.126 on interface eth0
Oct 28 22:45:26 Krataia kernel: [   64.876000] NET: Registered protocol family 10
Oct 28 22:45:26 Krataia kernel: [   64.876000] lo: Disabled Privacy Extensions
Oct 28 22:45:26 Krataia kernel: [   64.876000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 28 22:45:27 Krataia avahi-daemon[5488]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.4.126.
Oct 28 22:45:27 Krataia avahi-daemon[5488]: New relevant interface eth0.IPv4 for mDNS.
Oct 28 22:45:27 Krataia avahi-daemon[5488]: Registering new address record for 169.254.4.126 on eth0.IPv4.
Oct 28 22:45:28 Krataia avahi-daemon[5488]: Registering new address record for fe80::21c:23ff:fe14:cc23 on eth0.*.
Oct 28 22:45:30 Krataia avahi-autoipd(eth0)[5990]: Successfully claimed IP address 169.254.4.126
Oct 28 22:45:30 Krataia NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Oct 28 22:45:30 Krataia NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Oct 28 22:45:30 Krataia NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 28 22:45:30 Krataia NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct 28 22:45:30 Krataia NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 28 22:45:30 Krataia dhcdbd: Unrequested down ?:3
Oct 28 22:45:30 Krataia NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Oct 28 22:45:31 Krataia ntpdate[6087]: can't find host ntp.ubuntu.com 
Oct 28 22:45:31 Krataia ntpdate[6087]: no servers can be used, exiting
Oct 28 22:45:37 Krataia kernel: [   75.312000] eth0: no IPv6 routers present
Oct 28 23:02:05 Krataia kernel: [ 1063.000000] tg3: eth0: Link is down.
Oct 28 23:02:05 Krataia NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 28 23:02:05 Krataia NetworkManager: <info>  Deactivating device eth0. 
Oct 28 23:02:05 Krataia avahi-daemon[5488]: Withdrawing address record for 169.254.4.126 on eth0.
Oct 28 23:02:05 Krataia avahi-daemon[5488]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.4.126.
Oct 28 23:02:05 Krataia avahi-daemon[5488]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 28 23:02:05 Krataia avahi-daemon[5488]: Withdrawing address record for fe80::21c:23ff:fe14:cc23 on eth0.

---

### Post by elctb on 2007-10-30
I have the same laptop (Dell Latitude D630) and have had absolutely no problems with the wired interface. I installed GutsyGibbon amd64 and eth0 always worked.

Next time you have the same problem verify the driver detects the cable has been plugged in. 
You should see the message:
Oct 28 22:44:41 Krataia kernel: [ 19.216000] tg3: eth0: Link is up at 100 Mbps, full duplex.
every time the cable is plugged in and the message:
Oct 28 23:02:05 Krataia kernel: [ 1063.000000] tg3: eth0: Link is down.
every time the cable is unplugged.

If you see the link up message, but you still can't connect capture the output of "ifconfig eth0", and "netstat -rn".

---

### Post by Demonice on 2007-10-31
hum, i had the link down message (as you saw), but i'm 100% certain that the cable was plugged in!

...now my current problem is that networkmanager can't seem to register that i also have a wireless card...! i swear, every time i unplug the laptop from the wired net, something weird happnes with the networkmanager. i tried the same procedure that worked the first time - completely removing and reisntalling, but it had no effect. so now it can't find the wireless card.. i'll see if i can find something in the syslog.. it's prolly eth1, right?


edit: i can't find anything about eth1 in the syslog :/

---

### Post by elctb on 2007-10-31
Yes, the wireless interface should be eth1.

First make sure you have the wireless driver loaded:
lsmod |grep 3945

I get something like:
ipw3945               195360  0 
ieee80211              34504  1 ipw3945

Then run iwconfig. I get something like:
eth1      IEEE 802.11g  ESSID:"Linksys"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:95:06:AF:21   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-34 dBm  Noise level=-35 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21312   Missed beacon:0

The wireless interface doesn't always come up for me though. I noticed when that happens, there is more than one interface with the eth1 name. Something like eth1 and eth1.avay. Most times unloading the driver and reloading it fixes the problem. 
To unload driver I do:
sudo modprobe -r ipw3945
To load driver I do:
sudo modprobe ipw3945

If that doesn't work I reconfigure the wireless interface:
sudo network-admin
Select the wireless interface, click on properties and reconfigure. Then it always works.... for me at least.

---

### Post by Demonice on 2007-10-31
i found out what it was.. and i'm embarrased haha. it turns out there's a button on the left side of the laptop that turns the wireless card (and bluetooth) on and off. i didn't even know it existed until a friend noticed it o.O  so, it had prolly been switched off in my bag or something... it works now. *blush* ;_;

thanks for your reply tho;) i'll post here again if my original problem ever returns.

---

