---
title: "IP notification script for br0? or ssh connect to eth0"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by muso on 2008-02-19
On my pc I've got an account set-up for a colleague to connect via ssh to update bzr files.

He can't connect to eth0, which is on a static IP, as he gets something like:

```

[~]$ ssh 192.168.1.6
ssh: connect to host 192.168.1.53 port 22: No route to host
```

However, I found out he can access it via "br0"s address (from ifconfig):

```
br0       Link encap:Ethernet  HWaddr 00:1D:09:0F:BD:1D
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
```

However the ".10" keeps changing.  I'd like some way of getting the system to notify me as and when the IP changes and what it's changed to.

Does anyone know what a good solution to this problem is?  I think you can get a cron to check every 15 mins or so, and send messages which might do the trick... or perhaps there is something else that we're doing wrong... (I know br0 is something to do with bridging between wireless and wired networks)

Any help would be gratefully appreciated :)

---

### Post by jhetrick62 on 2008-02-19
If accessing on br0 you are access over a bridge network connection.  Can you colleague ping 192.168.1.6?  If so, then either you have your firewall blocking port 22 or you have sshd set up to answer on a non-standard port other than port 22.

That is the message you get back to a linux box when you ssh and don't get a valid answer back.

Jeff

---

### Post by muso on 2008-02-19
I can't remember whether he can ping that address, but ssh does work when he uses the br0 address, which indicates to me that it isn't an external firewall, or an ssh configuration problem.

The only issue with using br0, as I said, is that the IP keeps changing (probably when our router gets rebooted).

---

### Post by bernied on 2008-02-19
Do you know how the bridge interface was setup? One possible contender is VirtualBox - do you have this or any other VM software installed? Or maybe VPN? Or any other non-standard networking? Are you using the machine as a router?

(Before you change any of these files, make a backup copy of the file first, so you can easily revert when your networking doesn't)

Is the br0 interface defined in /etc/network/interfaces? If so, it will probably be configured to get it's address through dhcp. You could change this to static, and change eth0 to manual, to tidy things up. Post the contents of the interfaces file for more info:
```
$ cat /etc/network/interfaces
```

If the br0 interface is not defined in that file, then some other software (other than standard networking scripts) has created it, and if it is persistent after a reboot, then it is being created at every startup. To find out what startup scripts are active, try this:
```
$ ls /etc/rc2.d/
```and```
$ ls /etc/rcS.d/
```
Again, post the results here for more help.

---

### Post by jhetrick62 on 2008-02-19
Muso,

I believe that you are incorrect in assuming that it may not be the firewall.  Iptables assigns firewall rules by interface individually so eth0, eth1 and any other interface CAN ( the operative word as they may all be blocked also) have separate firewall rules.

Are you running any firewall tools such a Firestarter?  If so check those.  Have you looked at /etc/sshd/sshd_config file to see what port is being listened to.  Is your colleagues machine ip'd on the same first (3) octets (192.168.1 x)?

Jeff

---

### Post by muso on 2008-02-19
> **jhetrick62 said:**
> I believe that you are incorrect in assuming that it may not be the firewall.

I wasn't making that assumption, which was why I was careful to specify "external firewall."

> **jhetrick62 said:**
> Iptables assigns firewall rules by interface individually so eth0, eth1 and any other interface CAN ( the operative word as they may all be blocked also) have separate firewall rules.

Are you running any firewall tools such a Firestarter?  If so check those.  Have you looked at /etc/sshd/sshd_config file to see what port is being listened to.  Is your colleagues machine ip'd on the same first (3) octets (192.168.1 x)?

Jeff

No, I haven't installed any firewall, just what is standard on Ubuntu (although I probably should be using Firestarter or something similar).

---

### Post by muso on 2008-02-19
> **bernied said:**
> Do you know how the bridge interface was setup? One possible contender is VirtualBox - do you have this or any other VM software installed? Or maybe VPN? Or any other non-standard networking? Are you using the machine as a router?

(Before you change any of these files, make a backup copy of the file first, so you can easily revert when your networking doesn't)

Is the br0 interface defined in /etc/network/interfaces? If so, it will probably be configured to get it's address through dhcp. You could change this to static, and change eth0 to manual, to tidy things up. Post the contents of the interfaces file for more info:
```
$ cat /etc/network/interfaces
```

If the br0 interface is not defined in that file, then some other software (other than standard networking scripts) has created it, and if it is persistent after a reboot, then it is being created at every startup. To find out what startup scripts are active, try this:
```
$ ls /etc/rc2.d/
```and```
$ ls /etc/rcS.d/
```
Again, post the results here for more help.

I didn't even think of VirtualBox, but yes, I do use that... and that's picked up by your first suggestion:

```
[~]$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.53
netmask 255.255.255.0
gateway 192.168.1.1

# VirtualBox amendment
auto br0
iface br0 inet dhcp
        bridge_ports eth0

```

Note: the IP of .6 before was a typo.  This shows the correct IP, but the error message he got with ssh to the 53 address (via eth0) was the same.

---

### Post by bernied on 2008-02-19
I suggest you do something like this -
1 - make a backup copy of the interfaces file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.old
```
2 - Edit the interfaces file:
```
gksu gedit /etc/network/interfaces
```
and change this:
> ```
# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.53
netmask 255.255.255.0
gateway 192.168.1.1

# VirtualBox amendment
auto br0
iface br0 inet dhcp
        bridge_ports eth0
```to this:
```
# The primary network interface
# ...does not need to be configured as it is bridged by br0

# Previous configuration for eth0:
#auto eth0
#iface eth0 inet static
#address 192.168.1.53
#netmask 255.255.255.0
#gateway 192.168.1.1

iface eth0 inet manual

# VirtualBox amendment
auto br0
iface br0 inet static
    address 192.168.1.53
    netmask 255.255.255.0
    gateway 192.168.1.1
    bridge_ports eth0
```(Note that lines with # are just comments, so not actually necessary.)

3 - Reboot, and check network connectivity. It might be a good idea to check your VMs connectivity as well.

4 - If it worked, then you should have a static IP the same as before you installed the bridged network device - 192.168.1.53. And you're done.

If it didn't work, you can revert to the original interfaces:
```
sudo cp /etc/network/interfaces.old /etc/network/interfaces
```

---

### Post by muso on 2008-02-19
Thanks bernied.  It worked perfectly.

Not sure about VirtualBox, as I had it working a while back but it isn't working now (it wasn't working before the changes I made today though).  VirtualBox isn't a high priority at the moment, so I'll worry about that another day.

---

