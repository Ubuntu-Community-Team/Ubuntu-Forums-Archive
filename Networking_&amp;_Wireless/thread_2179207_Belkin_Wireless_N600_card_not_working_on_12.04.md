---
title: "Belkin Wireless N600 card not working on 12.04"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by chkneater on 2013-10-07
I'm using a Belkin N600 card with Ubuntu 12.04 and the computer is not recognizing the adapter.  

lshw -C network on shows only the ethernet card 

lsusb shows no USB or Belkin card

I'm pretty sure it is a problem with the drivers, I'm not sure which ones to install/remove.   rtlwifi shows rt18723fw.bin

The card does not even show the power on light connected to my computer, but on a windows laptop it was able to connect and run fine.

---

### Post by chili555 on 2013-10-07
Please show us:```
lspci -nn | grep 0280
lsusb
```Thanks.

---

### Post by chkneater on 2013-10-11
lspci -nn | grep 0280 yielded nothing and lsusb yielded this: 

```
dethkiller@dethkiller-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 006 Device 002: ID 05b8:3155 Agiler, Inc.
```

---

### Post by chili555 on 2013-10-11
Please remove the device from the USB port. Open a terminal and run:```
tail -f /var/log/syslog
```Insert the device and capture and post any messages that appear as the device is inserted.

Get out of 'tail' with Ctrl+c.

---

### Post by chkneater on 2013-10-12
This was the output of 'sudo tail -f /var/log/syslog':

Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Oct 12 00:58:51 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483648 seconds.
Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: reading /var/run/dnsmasq/resolv.conf
Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: using nameserver 192.168.2.1#53
Oct 12 00:59:01 dethkiller-desktop kernel: [105207.874025] eth0: no IPv6 routers present
Oct 12 00:59:10 dethkiller-desktop kernel: [105216.641048] usb 2-3: new high-speed USB device number 4 using ehci_hcd
Oct 12 00:59:10 dethkiller-desktop kernel: [105216.728056] hub 2-0:1.0: unable to enumerate USB device on port 3

Once I plugged in the device the terminal stalled there and I was still unable to access the device.  Where should I look from here?

I should note that the above was done with Network Manager turned off and using WicD.  I have a problem with the network dropping while using Network Manager.  I turned Network Manager on and ran the command again and this is the result using Network Manager: 

CPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483648 seconds.
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: reading /var/run/dnsmasq/resolv.conf
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: using nameserver 192.168.2.1#53
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:59:01 dethkiller-desktop kernel: [105207.874025] eth0: no IPv6 routers present
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.641048] usb 2-3: new high-speed USB device number 4 using ehci_hcd
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.728056] hub 2-0:1.0: unable to enumerate USB device on port 3
No command 'Oct' found, did you mean:
 Command 'vct' from package 'spark' (universe)
 Command 'qct' from package 'qct' (universe)
Oct: command not found
dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$ 

Again when I plugged in the wireless device nothing happened.

Now when I use Wicd with Network Manager turned off I get a different result than the first time:

.B device on port 3
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ CPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
CPDISCOVER: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483648 seconds.
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: reading /var/run/dnsmasq/resolv.conf
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: using nameserver 192.168.2.1#53
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:01 dethkiller-desktop kernel: [105207.874025] eth0: no IPv6 routers present
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.641048] usb 2-3: new high-speed USB device number 4 using ehci_hcd
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.728056] hub 2-0:1.0: unable to enumerate USB device on port 3
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ CPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
CPDISCOVER: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:51 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483648 seconds.
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: reading /var/run/dnsmasq/resolv.conf
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:58:58 dethkiller-desktop dnsmasq[1008]: using nameserver 192.168.2.1#53
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:01 dethkiller-desktop kernel: [105207.874025] eth0: no IPv6 routers present
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.641048] usb 2-3: new high-speed USB device number 4 using ehci_hcd
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ Oct 12 00:59:10 dethkiller-desktop kernel: [105216.728056] hub 2-0:1.0: unable to enumerate USB device on port 3
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$  Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$  Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Oct: command not found
Oct:: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ dethkiller@dethkiller-desktop:~$ 
dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ tail -f /var/log/syslog
Oct 12 02:27:12 dethkiller-desktop dhclient: Listening on LPF/eth0/bc:5f:f4:79:65:5e
Oct 12 02:27:12 dethkiller-desktop dhclient: Sending on   LPF/eth0/bc:5f:f4:79:65:5e
Oct 12 02:27:12 dethkiller-desktop dhclient: Sending on   Socket/fallback
Oct 12 02:27:12 dethkiller-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 12 02:27:12 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Oct 12 02:27:12 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Oct 12 02:27:12 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Oct 12 02:27:13 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483647 seconds.
Oct 12 02:27:14 dethkiller-desktop dnsmasq[1008]: reading /var/run/dnsmasq/resolv.conf
Oct 12 02:27:14 dethkiller-desktop dnsmasq[1008]: using nameserver 192.168.2.1#53

I have found two packages in synaptic called Oct and SPARK but not qct or vct.  I don't understand what the packages are for but maybe they have something to do with it?

bump

---

### Post by chili555 on 2013-10-13
> hub 2-0:1.0: unable to enumerate USB device on port 3I suspect either the device or the USB port is defective. Moreover:> Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Oct 12 00:58:51 dethkiller-desktop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Oct 12 00:58:51 dethkiller-desktop dhclient: bound to 192.168.2.3 -- renewal in 2147483648 seconds.You have a perfectly valid ethernet connection. It's a bit tricky to troubleshoot wireless if wired ethernet is plugged in and working. 

Next, it is even *MORE *tricky to try to juggle Network Manager and Wicd. I'd pick one and remove the other. Neither will work if either the device or the USB port is defective.

Before you proceed further, try a different USB port. Also try the device in another computer. Until the system sees the device properly in lsusb and dmesg, we are spinning our wheels. 

I have no idea what this is; I have never seen it:> dethkiller@dethkiller-desktop:~$: command not found
dethkiller@dethkiller-desktop:~$ No command 'Oct' found, did you mean:
No: command not found
dethkiller@dethkiller-desktop:~$ Command 'vct' from package 'spark' (universe)
bash: syntax error near unexpected token `('
dethkiller@dethkiller-desktop:~$ Command 'qct' from package 'qct' (universe)
bash: syntax error near unexpected token `('In any case, we need to get the device recognized first.

---

### Post by varunendra on 2013-10-13
> **chili555 said:**
> I have no idea what this is; I have never seen it

Yes you have, and very often, like this -
> **dethkiller@dethkiller-desktop:~$ [COLOR="#696969"]*dethkiller@dethkiller-desktop:~$*[/COLOR]** [COLOR="#FF0000"]Oct 12 00:59:10 dethkiller-desktop kernel: [105216.728056] hub 2-0:1.0: unable to enumerate USB device on port 3[/COLOR]

Looks like the OP copy-pasted the syslog output as a command, then the same output from their post here, including the shell prompt. :)

---

### Post by chkneater on 2013-10-14
Allright, now this is confusing but I have reinstalled ndiswrapper and its components and 'lsusb' yields this:

```
dethkiller@dethkiller-desktop:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 003 Device 002: ID 05b8:3155 Agiler, Inc. 
Bus 002 Device 007: ID 050d:110a Belkin Components 


Right at the bottom, lusb recognizes the Belkin wireless BUuuuT, 'dmesg' still yields this mess:


[   22.529457] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.592065] udevd[379]: starting version 175
[   22.804711] lp: driver loaded but no devices found
[   22.925051] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.087597] wmi: Mapper loaded
[   23.271164] parport_pc 00:09: reported by Plug and Play ACPI
[   23.271244] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   23.306735] MCE: In-kernel MCE decoding enabled.
[   23.321744] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   23.342048] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   23.342052] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   23.358276] lp0: using parport0 (interrupt-driven).
[   23.364392] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   23.364539] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   23.390065] EDAC MC: Ver: 2.1.0
[   23.395871] AMD64 EDAC driver v3.4.0
[   23.395908] EDAC amd64: DRAM ECC disabled.
[   23.395912] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   23.395914]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   23.395915]  (Note that use of the override may cause unknown side effects.)
[   23.491127] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   23.491132] Disabling lock debugging due to kernel taint
[   23.555246] type=1400 audit(1381797022.932:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=651 comm="apparmor_parser"
[   23.555750] type=1400 audit(1381797022.932:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=651 comm="apparmor_parser"
[   23.556060] type=1400 audit(1381797022.933:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=651 comm="apparmor_parser"
[   23.988459] ppdev: user-space parallel port driver
[   23.991084] Bluetooth: Core ver 2.16
[   23.991135] NET: Registered protocol family 31
[   23.991137] Bluetooth: HCI device and connection manager initialized
[   23.991141] Bluetooth: HCI socket layer initialized
[   23.991143] Bluetooth: L2CAP socket layer initialized
[   23.991150] Bluetooth: SCO socket layer initialized
[   24.047823] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.047827] Bluetooth: BNEP filters: protocol multicast
[   24.145135] type=1400 audit(1381797023.522:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=782 comm="apparmor_parser"
[   24.145730] type=1400 audit(1381797023.522:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=782 comm="apparmor_parser"
[   24.204745] Bluetooth: RFCOMM TTY layer initialized
[   24.204754] Bluetooth: RFCOMM socket layer initialized
[   24.204756] Bluetooth: RFCOMM ver 1.11
[   24.313421] init: failsafe main process (774) killed by TERM signal
[   24.649772] type=1400 audit(1381797024.026:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=890 comm="apparmor_parser"
[   24.652831] type=1400 audit(1381797024.029:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=890 comm="apparmor_parser"
[   24.667235] type=1400 audit(1381797024.044:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=893 comm="apparmor_parser"
[   24.673262] type=1400 audit(1381797024.050:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=893 comm="apparmor_parser"
[   24.673556] type=1400 audit(1381797024.050:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=893 comm="apparmor_parser"
[   24.872587] snd_cmipci 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.917349] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   24.917420] snd_hda_intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   24.921029] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   25.053939] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   25.054057] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input4
[   25.480460] init: plymouth-upstart-bridge main process (733) killed by TERM signal
[   25.986949] [fglrx] Maximum main memory to use for locked dma buffers: 2865 MBytes.
[   25.988669] [fglrx]   vendor: 1002 device: 68f9 count: 1
[   25.990323] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   25.990341] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.990347] pci 0000:01:00.0: setting latency timer to 64
[   25.990666] [fglrx] Kernel PAT support is enabled
[   25.990691] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   26.051925] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   26.051929] vesafb: scrolling: redraw
[   26.051933] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   26.054397] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011d00000, using 5824k, total 5824k
[   26.054683] Console: switching to colour frame buffer device 175x65
[   26.054690] fb0: VESA VGA frame buffer device
[   26.088728] init: plymouth-splash main process (1149) terminated with status 1
[   26.256908] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
[   26.261056] [fglrx] Firegl kernel thread PID: 1153
[   26.263058] [fglrx] Firegl kernel thread PID: 1154
[   26.265060] [fglrx] Firegl kernel thread PID: 1155
[   26.266250] [fglrx] IRQ 44 Enabled
[   26.501562] [fglrx] Gart USWC size:940 M.
[   26.501566] [fglrx] Gart cacheable size:372 M.
[   26.501571] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   26.501574] [fglrx] Reserved FB block: Unshared offset:fa0d000, size:2f3000 
[   26.501576] [fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
[   28.282661] init: plymouth-stop pre-start process (1536) terminated with status 1
[   33.116802] r8169 0000:02:00.0: eth0: link down
[   33.117802] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   98.531810] ISO 9660 Extensions: Microsoft Joliet Level 3
[   98.580728] ISOFS: changing to secondary root
[  607.147267] r8169 0000:02:00.0: eth0: link up
[  607.147863] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  617.314020] eth0: no IPv6 routers present
[  714.732646] r8169 0000:02:00.0: eth0: link down
[  714.732663] r8169 0000:02:00.0: eth0: link down
[  714.733719] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  714.982365] r8169 0000:02:00.0: eth0: link down
[  714.983313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  716.963413] r8169 0000:02:00.0: eth0: link up
[  716.964054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  727.874041] eth0: no IPv6 routers present
[  954.253072] usb 2-3: new high-speed USB device number 5 using ehci_hcd
[  954.340049] hub 2-0:1.0: unable to enumerate USB device on port 3
[  954.551229] usb 6-1: USB disconnect, device number 2
[  954.886061] usb 2-3: new high-speed USB device number 6 using ehci_hcd
[  954.973054] hub 2-0:1.0: unable to enumerate USB device on port 3
[  970.817058] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[  970.985531] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input5
[  970.986340] generic-usb 0003:05B8:3155.0003: input,hidraw0: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:12.0-3/input0
[  970.993789] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input6
[  970.994448] generic-usb 0003:05B8:3155.0004: input,hiddev0,hidraw1: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:12.0-3/input1
[  977.410050] usb 2-4: new high-speed USB device number 7 using ehci_hcd
[  977.606117] ndiswrapper version 1.57 loaded (smp=yes, preempt=yes)
[  977.763050] usb 2-4: reset high-speed USB device number 7 using ehci_hcd
[  977.925807] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[  977.925815] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[  977.925838] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  977.925844] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  977.925850] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  977.925856] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  977.925864] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  977.925869] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  977.925875] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  977.925881] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  977.925887] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  977.925892] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  977.925898] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  977.925923] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  977.925929] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  977.925937] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  977.925950] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  977.925956] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  977.925971] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  977.925977] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  977.925982] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  977.925988] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  977.925998] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  977.926593] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  977.926599] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  977.926604] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  977.926609] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  977.926612] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netrtwlanu'
[  977.926682] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netrtwlanu'
[  977.927119] usbcore: registered new interface driver ndiswrapper

```

Sorry for the lengthy file but I wanted to make sure you could see everything that is going on, I have installed 'netrlwanlu' with 'Windows Wireless Drivers' package I found in synaptic and it is installed according to the 'windows wireless driver' but not loading at all.  I'm considering looking for another driver??

---

### Post by chili555 on 2013-10-14
A mess, indeed. I suggest you do:```
sudo apt-get remove --purge wicd
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/rtl8192du.git
cd rtl8192du
make
sudo make install
sudo modprobe 8192du
```If there are any errors, stop and post them. If there are no errors, your wireless device should be working. Warnings are probably OK.

---

### Post by chkneater on 2013-10-16
Well, lsusb is showing Belkin components on Bus 2, which would be the wireless adapter, however dmesg is not showing any wireless devices.  This was done with the etho unplugged to avoid any confusions.

Also, I edited /etc/modprobe.d/ndiswrapper.conf and commented out the three lines in the file referring to usb, they were:

#alias usb:v050Dp1105d*dc*dsc*dp*ic*isc*ip* ndiswrapper
#alias usb:v050Dp110Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
#alias usb:v050Dp120Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper

After restarting, 'dmesg' doesn't have any conflict with ndiswrapper in it, but still no wireless.  And 'dmesg' appears to load the 'netrwlanu' driver.  Also, the program "Windows Wireless Drivers' recognizes that hardware is present, which it hadn't shown prior, so editing ndiswrapper had some effect.

I have plugged the adapter into a windows laptop and it worked on that comp, and I have used other usb devices in the same port the device is in, so I can safely say that the port and adapter aren't part of the problem... that leaves software, I think I'll take chili555's advice and try it out.  I'll post what happens afterward.  

And I found this link that seems related, but is different hardware, but same line of devices from Belkin, tell me what you think of this: [https://bbs.archlinux.org/viewtopic.php?id=149329](https://bbs.archlinux.org/viewtopic.php?id=149329)

And yes, you were correct chili555, I did accidentally double copy the output and run it as a command ;-)  Good eye!

---

### Post by chili555 on 2013-10-17
So, did you undertake my proposed solution above? What does this tell us?```
sudo modprobe 8192du
dmesg | grep -e 8192 -e ndis
iwconfig
```

---

### Post by chkneater on 2013-10-17
Yes Chili555, your commands worked perfectly!!  Right after I rebooted after running your commands I notice the wireless light flicker and Network Manager was picking up signals from everywhere!  This thing is MUCH faster than even the ethernet was when I was using it.  I didn't remove Wicd tho, I had some trouble with NM a few weeks ago and I just want to keep it as a backup.  Interestingly, Wicd does not detect the wireless network for some reason, but I'm not concerned since NM is running good and hasn't dropped the signal once.  That's the only variation I made, I followed the rest of the commands and they worked just like they should have.  Here are the outputs since the wireless has been working:

```
dethkiller@dethkiller-desktop:~$ sudo modprobe 8192du
[sudo] password for dethkiller: 
dethkiller@dethkiller-desktop:~$ dmesg | grep -e 8192 -e ndis
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bfc00000 s83328 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s83328 r8192 d23168 u262144 alloc=1*2097152
[   22.955212] usbcore: registered new interface driver rtl8192du
dethkiller@dethkiller-desktop:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"belkin.70a"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:2C:07:0A   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```


I'm guessing that 8192du is the correct third party driver and that's why I don't need ndiswrapper anymore?  And why not 'apt-get install' instead of 'git' 'make' and 'make install'?  Is it because of the file type?

Again, thank you so much Chili555, like I said your advice worked perfectly.  Any body having issues with Belkin N600 Wireless Adapters should try that out, thanks again!

Please mark as solved!!

---

### Post by chili555 on 2013-10-17
> I'm guessing that 8192du is the correct third party driver and that's why I don't need ndiswrapper anymore? Exactly!>  And why not 'apt-get install' instead of 'git' 'make' and 'make install'? Is it because of the file type?To use apt, the package would need to be in the official Ubuntu repositories. This is not quite yet. It is in the git repository. 

When Update Manage installs a newer kernel version, also known as linux-image, you will be asked to reboot to complete the update. Then you'll need to compile the driver for the newer kernel:```
cd rtl8192du
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo make install
sudo modprobe 8192du
```Please retain the files and these instructions for that time. Also, please mark the thread Solved: [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

Glad it's working. Have fun!

---

### Post by chkneater on 2013-10-18
When Update Manage installs a newer kernel version, also known as linux-image, you will be asked to reboot to complete the update. Then you'll need to compile the driver for the newer kernel:

When I compile it I'll need an internet connection, so if updating the kernel messes up the driver this would create a conundrum right?  Thanx again, I saved those instructions to my desktop.

---

### Post by chili555 on 2013-10-18
> When I compile it I'll need an internet connectionNope. If you've kept the 8192du files that you downloaded to compile the driver just now, then the same files needn't be downloaded again. That's why I said:> **Please retain the files** and these instructions for that time.

---

### Post by AmyR on 2013-10-19
chili555 - just wanted to let you know that I was having the same problem and with your instructions I was able to establish wireless on my belkin adapter. Thank you so much! I had been trying for hours with ndiswrapper with no success!

---

