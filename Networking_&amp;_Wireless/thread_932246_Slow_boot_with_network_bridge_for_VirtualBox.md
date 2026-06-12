---
title: "Slow boot with network bridge for VirtualBox"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by fbn on 2008-09-28
Hi,

I have configured a network bridge for VirtualBox Host Interface Network as described in the manual:

```

1. sudo apt-get install bridge-utils

2. /etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# VirtualBox
auto eth0
iface eth0 inet manual
auto br0
iface br0 inet dhcp
    bridge_ports eth0
    bridge_fd 5

3. sudo /etc/init.d/networking restart

4. sudo VBoxAddIF vbox0 fbn br0

5. Virtual Box Interface auf vbox0

```

Unfortunately this leads to extreme long boot times (Configuring network interfaces ...) if there is no eth0 connected. At home I'm using wireless lan configured by Networkmanager, so this is a real problem for me.

Is there anything that I can change to improve this situation? I can't be the only one using VirtualBox Host Interface Networking and having slow boot times ...

Thanks,
  Frank

---

### Post by fbn on 2008-09-29
No idea anybody?

---

### Post by freegeek on 2008-10-07
I have a similar problem but did not take the time to figure it out. I have a faulty ethernet card (eth0, on motherboard) so I used a second card (eth1, pci). Since then, network config at boot time is extremely slow.

my /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual
        up ifconfig $IFACE 0.0.0.0 up promisc
        down ifconfig $IFACE down

auto tap0
iface tap0 inet manual
        up ifconfig $IFACE 0.0.0.0 up promisc
        down ifconfig $IFACE down
        tunctl_user freegeek

auto br0 
iface br0 inet dhcp
        bridge_ports tap0 eth1

```

Sorry to be of no help for now but I'll let you know if I find anything.

---

### Post by fbn on 2008-10-07
Hi,

I don't have a solution yet.

I disable the network interface after I have used the VM and I enable it if I have to use the VM. Which is very annoying but better than waiting minutes while booting and resuming ...

Frank

---

### Post by JSGolf on 2008-10-07
I'm in the same boat as you folks.  If I comment out the bridge, the system boots normal and fast.  I'm running XP as my guest OS under Virtualbox. Obviously then I don't have windows networking without the bridge.  

If I find anything out I'll let you know.

UPDATE:

I'm a computer teacher and I'm using VirtualBox on my laptop.  My classroom monitoring software (Genevalogic Vision Dashboard) only runs on Windows.  I have VirtualBox running Windows XP so that I can use Vision.  It works like a charm...with the network bridge, I'm able to do live supervision, remote control machines, even the full lab demo works on 30 computers at once all running through the virtual machine.  Obviously I need to have Host Interface Networking enabled to be able to do this. 

When I'm at work, I'm hooked up via ethernet cable and the system starts up fast because the connection the bridge looks for exists.  When I'm at home, however, I'm on wireless so the bridge causes the computer to take about 3 min more than normal to start up.  I came up with a workaround...it works for me, so I hope it will work for you too.

What I did is create 2 shortcuts to make my life easier and placed both in my panel.  The first one for Type I put Application in Terminal.  For name I put Network Config.  For command I put sudo gedit /etc/network/interfaces.  The second shortcut I made was for restarting networking.   For Type put Application in Terminal. Name it whatever you want.  I called mine Network Restart.    For command I just put sudo /etc/init.d/networking restart.  

Here is an excerpt from my /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#auto br0
#iface br0 inet dhcp
    #bridge_ports eth0


By default, I leave the bridge commented out like in the example above, so my computer starts fast no matter where I'm at.  If I'm at work, I just click the network config shortcut and remove the comment marks from the 3 lines above this text that relate to the bridge.  Then click restart networking to use the bridge.  

I hope I helped!

---

### Post by robert114 on 2008-11-17
maybe this works for you folks:
[https://wiki.ubuntu.com/VirtualBoxNetworking?highlight=(bridge)|(network](https://wiki.ubuntu.com/VirtualBoxNetworking?highlight=(bridge)|(network))

---

### Post by arnem_ on 2008-11-20
It does work but than my windows guest system is not able to connect with the internet anymore.

---

### Post by robert114 on 2008-11-21
Same here, but i couldn't find a workaround.

Robert

---

