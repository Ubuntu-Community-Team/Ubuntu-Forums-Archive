---
title: "help with netstat noob"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by therealstig on 2010-12-18
Hi, when i type in netstat, netstat -n, netstat -a or netstat -na, i get the this crap, i dont understand what it is, i get the proper stuff for about 5 seconds and then this crap comes up.
Could anyone help me with what im doing wrong or what is wrong, thanks :D

---

### Post by Eiji Takanaka on 2010-12-18
I'm guessing you want to see just what 'external' network traffic is going down and not the whole list of procedures in internal network traffic as well? If so type netstat --help or 'man netstat' and it should give you an extensive list of filters you can apply via the switch - parameter. I can't remember them off the top of my head but isn't -t tcp filter? -u udp filter.

---

### Post by Eiji Takanaka on 2010-12-18
If its monitoring network traffic you intend to do. Try wireshark it's a very powerful network analzyer. IMHO anyways.

---

### Post by therealstig on 2010-12-18
thanks, want it for connections "in" and connections "out". 
I done netstat -l "-l, --listening          display listening server sockets"
Does this cover both? im learning.
will have a read up mate "wireshark"
Thanks Mark

---

### Post by Eiji Takanaka on 2010-12-18
I think that lists 'listening' sockets dude, or potential channels of communication between computers. 

I'm just checking out a few on my own computer, to find out what the deal is! ;)

---

### Post by therealstig on 2010-12-18
thanks buddy, just installed wireshark, looks good just trying to get the hang of it and dumping packets into my file so there not live- just trying to sound teche lol:D, any hints or tips, for wireshark.

---

### Post by Eiji Takanaka on 2010-12-18
Yeah you don't want to run it as root bud.

Theres a procedure for not running it as root, that the developer disclosed....

Here it is.... Or if you would prefer the source, i reckon googling wireshark non-root, will ping the page i found it on.

Enabling Non-root Capture
Step 1: Install setcap

First, we'll need to install the setcap executable if it hasn't been already. We'll use this to set granular capabilities on Wireshark's dumpcap executable. setcap is part of the libcap2-bin package.

stretch@Sandbox:~$ sudo apt-get install libcap2-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libcap-dev
The following NEW packages will be installed:
  libcap2-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.7kB of archives.
After this operation, 135kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libcap2-bin 1:2.16-5ubuntu1 [17.7kB]
Fetched 17.7kB in 0s (36.7kB/s)    
Selecting previously deselected package libcap2-bin.
(Reading database ... 146486 files and directories currently installed.)
Unpacking libcap2-bin (from .../libcap2-bin_1%3a2.16-5ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libcap2-bin (1:2.16-5ubuntu1) ...

Step 2: Create a Wireshark Group (Optional)

Since the application we'll be granting heightened capabilities can by default be executed by all users, you may wish to add a designated group for the Wireshark family of utilities (and similar applications) and restrict their execution to users within that group. However, this step isn't strictly necessary.

root@Sandbox# groupadd wireshark
root@Sandbox# usermod -a -G wireshark stretch

After adding yourself to the group, your normal user may have to log out and back in. Or, you can run newgrp to force the effect of the new group (you'll have to launch Wireshark from this same terminal environment in step 3):

stretch@Sandbox$ newgrp wireshark

We assign the dumpcap executable to this group instead of Wireshark itself, as dumpcap is responsible for all the low-level capture work. Changing its mode to 750 ensures only users belonging to its group can execute the file.

root@Sandbox# chgrp wireshark /usr/bin/dumpcap
root@Sandbox# chmod 750 /usr/bin/dumpcap

Step 3: Grant Capabilities

Granting capabilities with setcap is a simple matter:

root@Sandbox# setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap

In case you're wondering, that =eip bit after the capabilities list grants them in the effective, inheritable, and permitted bitmaps, respectively. A more thorough explanation is provided in section 2 of this FAQ.

To verify our change, we can use getcap:

root@Sandbox# getcap /usr/bin/dumpcap
/usr/bin/dumpcap = cap_net_admin,cap_net_raw+eip

---

### Post by Eiji Takanaka on 2010-12-18
I'm just trying to understand why port 33087 is listening on my computer, from what i can see thats a channel that can be used by ssh2. I might want to try and shut that down or at the very least fully comprehend it haha....Cheers for the heads up on listening sockets! ;)

---

### Post by Eiji Takanaka on 2010-12-18
P.s the non-root fix might of allready been applied in subsequent versions of wireshark, i'm not fully up-to-date on that news front ;)

---

### Post by therealstig on 2010-12-18
cheers dude,
I dont get this bit.
Get:1 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe libcap2-bin 1:2.16-5ubuntu1 [17.7kB]
Fetched 17.7kB in 0s (36.7kB/s)    
Selecting previously deselected package libcap2-bin.
(Reading database ... 146486 files and directories currently installed.)
Unpacking libcap2-bin (from .../libcap2-bin_1%3a2.16-5ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libcap2-bin (1:2.16-5ubuntu1) ...

---

### Post by therealstig on 2010-12-18
hi, think ive worked it out,  Im on wireshark and just wanted to know what "pseudo-device that captures on all devices" is or does? Thanks mark

---

### Post by Eiji Takanaka on 2010-12-18
Thats what the computer should be saying if all is going to plan ;) I forgot to quote is all. Just copied and pasted direct fro9m the website. 

Pseudo device is one that catches on all interfaces. i.e if you have an ethernet hookup and a wireless card it will capture all data being sent across those networks. 

Very useful tool for monitoring both hardwired traffic on a network, but also on wireless channels.

---

### Post by Eiji Takanaka on 2010-12-18
also substitute the 'stretch' group with your username ;)

---

### Post by therealstig on 2010-12-18
hi dude,
I done this bit, 

We assign the dumpcap executable to this group instead of Wireshark  itself, as dumpcap is responsible for all the low-level capture work.  Changing its mode to 750 ensures only users belonging to its group can  execute the file.

root@Sandbox# chgrp wireshark /usr/bin/dumpcap
root@Sandbox# chmod 750 /usr/bin/dumpcap

Step 3: Grant Capabilities

Granting capabilities with setcap is a simple matter:

root@Sandbox# setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap

In case you're wondering, that =eip bit after the capabilities list  grants them in the effective, inheritable, and permitted bitmaps,  respectively. A more thorough explanation is provided in section 2 of  this FAQ.

To verify our change, we can use getcap:

root@Sandbox# getcap /usr/bin/dumpcap
/usr/bin/dumpcap = cap_net_admin,cap_net_raw+eip 	


is this right.

---

### Post by Eiji Takanaka on 2010-12-19
Yo dude, just sifted through threads and managed to find this one again, i really should start following threads it would make my life a whole lot easier, haha ah well...

It looks o.k to me from what its outputting it would appear you've changed the capabilities alright, did you do the whole group thing before yeh? creating the group adding yourself?

but yeah it seems you've successfully changed the privileges.

if you can now see your devices when running wireshark in non-root mode (i.e from command line or gui without sudo). I would say theres a good chance all is good chief. 

- dan

---

