---
title: "entries added to interface file are deleted after a reboot - using  15.10"
date: 2016-01-12
forum: Networking &amp; Wireless
---

### Post by dan_tiernan on 2016-01-12
Hi, when  I vi the interfaces file and add dummy interfaces write/save  all is good. As well, I can see my dummy interfaces when i do ifconfig.  But, when I reboot the system, the dummy interfaces are no longer listed  when i do ifconfig and have been removed from the interfaces file.

Any insight to why and how to work arounf it?

thanks,
dan

---

### Post by yancek on 2016-01-12
That would be the expected behavior on a Live CD/DVD or an install to a flash drive using unetbootin, pendrivelinux or similar software to put the Live CD on a flash drive.  That would be a read-only filesystem and no changes will be saved on reboot.

Is this an actual install to a hard drive?  Are you using Ubuntu?  Which release?.

---

### Post by Bucky Ball on 2016-01-12
*Thread moved to **Networking & Wireless**.*

Generally, changes are not made to the interfaces file directly anymore if you are using Network Manager. Your interfaces file should look something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Create your dummy connections directly in Network Manager, if that's what you're using.

---

### Post by dan_tiernan on 2016-01-13
thanks for the reply,

I am running on a HP ELITEDESK running 15.10. As i said, I modify the interface file, restart the process and my new interfaces that I added (dummy) are see-able in the ifconfig command. So, when I reboot, I loose the dummy interface entries. also, I am using vi to add the dummy interfaces.


with that said, any ideas why this is a problem?

---

### Post by ian-weisser on 2016-01-13
Bucky Ball concisely and correctly answered your questions for most use cases in Post #3.
Are you not using Network Manager?

---

### Post by dan_tiernan on 2016-01-18
i purchased a new system, i have the same results, so i have taken your advise and using network manager, my problem now is I do not have a connection option in the manager. i only have as options, general, dns,host. how do i add the connection option, so i can add my interfaces?

---

### Post by dan_tiernan on 2016-01-18
I purchased a new system, i have the same results, so i have taken your  advise and using network manager, my problem now is I do not have a  connection option in the manager. i only have as options, general,  dns, host. how do i add the connection option, so i can add my  interfaces?

---

### Post by bab1 on 2016-01-18
> **dan_tiernan said:**
> I purchased a new system, i have the same results, so i have taken your  advise and using network manager, my problem now is I do not have a  connection option in the manager. i only have as options, general,  dns, host. how do i add the connection option, so i can add my  interfaces?
What kind of interface do you need to add?  Ethernet, Wi-Fi, Bridged, etc?  You mentioned dummy interfaces, do you mean a dummy0 or dummy1  interface?  There is a dummy module (driver) you need to install, if that's what you mean.

Network Manager has provisions for you to add an interface as well as editing existing interfaces.

---

### Post by dan_tiernan on 2016-01-18
i been told, i should not add interfaces to the interface file (etc/network/interfaces) via vi, use network manager. I am trying to use the network manager, but there is no connections tabs, only general, host, dns. 

this is what my ifconfig needs to look like, when i display it (just the interfaces that i am trying to configure)

so, how do i get the connection tab to display when i run network manager?

auto lo
iface lo inet loopback
 
# Internet side in
auto eth0
iface eth0 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br0
iface br0 inet manual
                bridge_ports eth0
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# Subscriber side in
auto eth1
iface eth1 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br1
iface br1 inet manual
                bridge_ports eth1
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# Control network (OFC)
auto eth2
iface eth2 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br2
iface br2 inet manual
                bridge_ports eth2
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# PTS Internet in
 
auto dummy3
iface dummy3 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br3
iface br3 inet manual
                bridge_ports dummy3
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# PTS Subscriber in
 
auto dummy4
iface dummy4 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br4
iface br4 inet manual
                bridge_ports dummy4
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off

---

### Post by bab1 on 2016-01-18
> **dan_tiernan said:**
> i been told, i should not add interfaces to the interface file (etc/network/interfaces) via vi, use network manager. I am trying to use the network manager, but there is no connections tabs, only general, host, dns. 

this is what my ifconfig needs to look like, when i display it (just the interfaces that i am trying to configure)

so, how do i get the connection tab to display when i run network manager?

Please use the[noparse]```
code goes here
```[/noparse] code brackets when posting the output of fixed width font from terminal commands.  This is easily done using the [SIZE=5]**```

```**[/SIZE] icon at the top of the advanced reply editor that you use to respond with.  See below.

The direct answer to your question is for you to NOT select edit after starting Network Manager (NM).  Instead, select ADD instead to see all of your options.  I can't say whether NM will be able to handle all complex interface configurations.  After all it was designed for typical desktop user interface needs; not at all like what you want to do.  If this is some day going to be a dedicated server appliance I would look towards using Ubuntu Server edition which has no GUI at all.  Then you can use VI to edit the /etc/network/interfaces file.  If this is just experimenting then try the NM options after you select ADD (an interface).  I believe you will need to add each interface separately.  I assume you already know how to add the dummy module so you can create the dummy interfaces. 
> 

```
auto lo
iface lo inet loopback
 
# Internet side in
auto eth0
iface eth0 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br0
iface br0 inet manual
                bridge_ports eth0
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# Subscriber side in
auto eth1
iface eth1 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br1
iface br1 inet manual
                bridge_ports eth1
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# Control network (OFC)
auto eth2
iface eth2 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br2
iface br2 inet manual
                bridge_ports eth2
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# PTS Internet in
 
auto dummy3
iface dummy3 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br3
iface br3 inet manual
                bridge_ports dummy3
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
 
# PTS Subscriber in
 
auto dummy4
iface dummy4 inet manual
                up ip link set dev $IFACE up
                down ip link set dev $IFACE down
 
auto br4
iface br4 inet manual
                bridge_ports dummy4
                bridge_maxwait 5
                bridge_fd 1
                bridge_stp off
```

---

### Post by dan_tiernan on 2016-01-18
can you advise how to load a dummy module or direct me to where?

thanks

---

### Post by bab1 on 2016-01-18
> **dan_tiernan said:**
> can you advise how to load a dummy module or direct me to where?

thanksThe complete walk through is this:

First you need to see if the dummy module is loaded into the kernel with this command
```
sudo lsmod | grep dummy
```

If it works you will see something like this
```
dummy                  14752  0 

```
*I assume you are here:*
If you don't see the above you need to load the module manually with this
```
sudo modprobe dummy
```
If you need to load more than one (1) dummy interface use the following (Using 6 in this example)
```
sudo modprobe dummy numdummies=6
```
NOTE: If this all works for you you will need to permanently add the module at boot up time.  The can be done by adding the ***dummy*** module to the /etc/modules file.

---

### Post by dan_tiernan on 2016-01-19
thank you for your support...i am a rookie on Linux....can you advise what reading / training material can ramp me up, with the internals of linux? I will probably have more questions. thanks again

---

### Post by bab1 on 2016-01-19
> **dan_tiernan said:**
> thank you for your support...i am a rookie on Linux....can you advise what reading / training material can ramp me up, with the internals of linux? I will probably have more questions. thanks again
The results you got are just as important as the answers to your questions.  The forum works best if there is more than just a terse "thanks" and a request for more info.

If you were successful then tell us here and mark the thread solved.

---

