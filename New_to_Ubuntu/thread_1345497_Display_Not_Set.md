---
title: "Display Not Set"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by kevinhobson2000 on 2009-12-04
Hi,

I installed open ssh server on my ubuntu box and i am trying to launch two programs remotely from an SSH session. The two programs are VMWare and GNS.

I am getting the following messages when i try to launch:

kev@ubuntu:~$ sudo gns3
[sudo] password for kev:
gns3: cannot connect to X server


kev@ubuntu:~$ vmware
DISPLAY is not set, unable to open the VMware Workstation user interface.


Any help would be greatly appreciated.

Thanks

Kev

---

### Post by nothingspecial on 2009-12-04
Are you forwarding X?

---

### Post by kevinhobson2000 on 2009-12-04
How would i verify that?

Thanks

Kev

---

### Post by nothingspecial on 2009-12-04
When you ssh into your remote machine use the -X argument

```
ssh -X kev@192.168.1.2
```

or whatever username and ip you have.

---

### Post by ukripper on 2009-12-04
Also check in your ```
sudo vi /etc/ssh/sshd_config
``` you have set X11Forwarding to yes

---

### Post by kevinhobson2000 on 2009-12-04
There is no x forward set can it be set using that line anywhere in the config.

Cheers

Kev

---

### Post by nothingspecial on 2009-12-04
Post the file please

---

### Post by kevinhobson2000 on 2009-12-04
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

"/etc/ssh/sshd_config" 77 lines, 1874 characters

---

### Post by ukripper on 2009-12-04
where is the rest?

---

### Post by kevinhobson2000 on 2009-12-04
lol appologies i didnt scroll down must be cus its friday.

X11 forwarding is set to yes in the file.

Thansk

Kev

---

### Post by ukripper on 2009-12-04
read this how to X forward - [http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29)

---

### Post by kevinhobson2000 on 2009-12-04
Hi,

I set the putty client to XForward and tried to launch VMware and GNS remotely and now get this:

kev@ubuntu:~$ vmware
xprop:  unable to open display 'localhost:10.0'
xprop:  unable to open display 'localhost:10.0'

(vmware-modconfig:10267): Gtk-WARNING **: cannot open display: localhost:10.0
kev@ubuntu:~$ echo $DISPLAY
localhost:10.0
kev@ubuntu:~$ vmware
xprop:  unable to open display 'localhost:10.0'
xprop:  unable to open display 'localhost:10.0'

(vmware-modconfig:10276): Gtk-WARNING **: cannot open display: localhost:10.0
kev@ubuntu:~$ gns3
gns3: cannot connect to X server localhost:10.0
kev@ubuntu:~$ sudo gns3
gns3: cannot connect to X server localhost:10.0




Does this mean these apps are incompatible with this?


Thanks

Kev

---

### Post by kevinhobson2000 on 2009-12-04
Ok,

Figured this out i needed an xserver on my windows machine it works great now.

Issue i have now is i dont see all my partitions on GNS3 when i try to load my topologies anyone know how to get around this.

Cheers

Kev

---

### Post by ukripper on 2009-12-04
In my opinion you are better of using FreeNX [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) instead of xforwarding for running advanced apps on cross-platform (like windows). it runs on SSH as well. i have no issue with it so far and it is very fast, even works on low bandwidth and high latency networks.

---

### Post by kevinhobson2000 on 2009-12-04
Thanks for the info i will check it out.

---

### Post by kevinhobson2000 on 2009-12-21
Hi,

Nxserver is very good.

I have an issue with it though i dont see anything in the console windows in VMware Workstation 7.

I have disabled all optimizations in the display customisations in the  NXclient to no avail.

Does anyone know how to fix this?

Thanks

Kev

---

### Post by ukripper on 2009-12-21
Can you explain you network setup?

---

### Post by kevinhobson2000 on 2009-12-21
Basically this is a PC setup remotely to run a lab utilising VMWARE and GNS3.

So i use an NX Client to connect to the PC which is running NX server but in the VMware workstation console i just get a blank desktop.

Cheers

Kev

---

### Post by ukripper on 2009-12-21
How much RAM you have on the machine you running vmware workstation?

---

### Post by kevinhobson2000 on 2009-12-21
10 gig

---

