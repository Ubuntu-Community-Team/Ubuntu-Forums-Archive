---
title: "Cannot start automatically eth0 on boot"
date: 2004-12-28
forum: Networking &amp; Wireless
---

### Post by giorgosc61 on 2004-12-28
Hello.
I have installed ubuntu and i am with an adsl router in ppoa.
I don't use dhcp but used in gnome the system setting->networking to activate my eth0 card and passed the dns settings for my provider. 
Everything worked fine until I installed new 686 kernel.
Now at every boot it seems that eth0 is deactivated and by entering in gnome at system setting->networking i see my eth0 being unchecked. After reactivating i connect to internet but at reboot it deactivates again.
Please help. Is there a config file to see if it deactivates the eth0 at boot?

Thank you in advance.

---

### Post by Ruediger on 2005-01-05
I am having a similar problem, but I can't get my eht0 work. It stopped working after rebooting the computer, I searched the forums but none of the suggestions worked. Can anyone help?

---

### Post by wallijonn on 2005-01-05
Start a root terminal
```
gnome-nettool
```
[COLOR=Blue]Network device[/COLOR]: [COLOR=Red]eth0[/COLOR]
[COLOR=Red]Configure[/COLOR]
[COLOR=Red]Check[/COLOR] (on) Activate when the computer starts.

<ok>
<ok>
<exit root terminal>
<reboot>

Notice that there is a Connection settings configuration: "[COLOR=Green]manua[/COLOR]l" setting you can adjust if necessary.

---

### Post by Ruediger on 2005-01-05
[QUOTE=wallijonn]Start a root terminal
```
gnome-nettool
```
[COLOR=Blue]Network device[/COLOR]: [COLOR=Red]eth0[/COLOR]
[COLOR=Red]Configure[/COLOR]
[COLOR=Red]Check[/COLOR] (on) Activate when the computer starts.

<ok>
<ok>
<exit root terminal>
<reboot>

Notice that there is a Connection settings configuration: "[COLOR=Green]manua[/COLOR]l" setting you can adjust if necessary.[/QUOTE]

The only network device listed is Loopback Interface (lo)  :confused:

---

### Post by rolando on 2005-01-06
why dont you try and bind an IP address via the command line, at least then you will be told of any errors rather than the Gnome GUI program failing quietly.

Open a root command shell and try this line by line

```
ifconfig eth0 192.168.0.11 netmask 255.255.255.0 broadcast 192.168.0.255

ifconfig eth0 up

route add default gw 192.168.0.1
```

Obviously change the ethernet and IP addresses to reflect your system

Rolando

---

### Post by Ruediger on 2005-01-06
[QUOTE=rolando]why dont you try and bind an IP address via the command line, at least then you will be told of any errors rather than the Gnome GUI program failing quietly.

Open a root command shell and try this line by line

```
ifconfig eth0 192.168.0.11 netmask 255.255.255.0 broadcast 192.168.0.255

ifconfig eth0 up

route add default gw 192.168.0.1
```

Obviously change the ethernet and IP addresses to reflect your system

Rolando[/QUOTE]

The first command fails, it says that couldn't find the network device.

It looks like the NIC is not installed. I've tested the NIC on a Windows machine and it is working, I've also try to reboot and do cold boots several times. Everything was working fine until yesterday.  :confused:  :sad:

---

### Post by rolando on 2005-01-06
what does ifconfig report? 

Post the results here.

Make sure you bring up any interfaces you have before you use the ifconfig command

i.e. 
ifconfig eth0 up
and 
ifconfig eth1 up

Also how many network interfaces do you have?

For instance I have eth0 which is my wireless
and eth1 which is my ethernet

---

### Post by fng on 2005-01-06
Is the right module loaded?
Post the output of 'lsmod' please.

Did you also install the linux-restricted-modules-686 and the linux-restricted-modules-2.6.8.1-3-686 packages when you installed your new kernel?

---

### Post by wallijonn on 2005-01-06
[QUOTE=Ruediger]The only network device listed is Loopback Interface (lo)  :confused:[/QUOTE]

See that down pointing triangle? next to the listed loopback device. push (depress) it. is there a device listed? if so, highlight it, hit the "configure" button. Otherwise, push the "Add" button and follow the wizard.

---

### Post by Ruediger on 2005-01-06
[QUOTE=rolando]what does ifconfig report? 

Post the results here.

Make sure you bring up any interfaces you have before you use the ifconfig command

i.e. 
ifconfig eth0 up
and 
ifconfig eth1 up

Also how many network interfaces do you have?

For instance I have eth0 which is my wireless
and eth1 which is my ethernet[/QUOTE]

both commands result in the same message:

```

ETH0: ERROR while getting interface flags: Dispositivo Inexistente
ETH1: ERROR while getting interface flags: Dispositivo Inexistente

```

I only have one NIC.

---

### Post by Ruediger on 2005-01-06
[QUOTE=fng]Is the right module loaded?
Post the output of 'lsmod' please.
[/QUOTE]

lsmod output:
```

md
ipv6
af_packet
dm_mod
capability
commoncap
parport_pc
lp
parport
evdev
ide_cd
cdrom
mousedev
psmouse
ext3
jbd
ide_generic
sis5513
ide_disk
ide_core
unix
font
vesafb
cfbcopyarea
cfbimgbet
cfbfillrect

```

[QUOTE=fng]
Did you also install the linux-restricted-modules-686 and the linux-restricted-modules-2.6.8.1-3-686 packages when you installed your new kernel?[/QUOTE]

Yes, those packages are installed (but not the -686 version, since the computer is a K6-2)

---

### Post by Ruediger on 2005-01-06
[QUOTE=wallijonn]See that down pointing triangle? next to the listed loopback device. push (depress) it. is there a device listed? if so, highlight it, hit the "configure" button. Otherwise, push the "Add" button and follow the wizard.[/QUOTE]

I already tried that but the only device list is loopback interface, and there is no add button :(

---

### Post by rolando on 2005-01-07
Another Guy had this problem when he upgraded his Kernel and it was Debian as well. 

Check out this posting

[http://www.nvnews.net/vbulletin/archive/index.php/t-9949.html](http://www.nvnews.net/vbulletin/archive/index.php/t-9949.html)

May help, may not

---

### Post by Ruediger on 2005-01-07
[QUOTE=rolando]Another Guy had this problem when he upgraded his Kernel and it was Debian as well.

Check out this posting

[http://www.nvnews.net/vbulletin/archive/index.php/t-9949.html](http://www.nvnews.net/vbulletin/archive/index.php/t-9949.html)

May help, may not[/QUOTE]

I added the alias ne2k-pci eth0 to my /etc/modules.conf and rebooted, but still doesn't work.

I want to stay with Ubuntu but this problem is frustrating.

---

### Post by rolando on 2005-01-07
what about running a bootlocal.sh when you start Gnome, its worth a try eh?

---

### Post by wallijonn on 2005-01-07
[QUOTE=giorgosc61]Everything worked fine until I installed new 686 kernel.[/QUOTE]

Which 686 kernel did you install?, there are at least 6 (if you include all the repositories). 

Did you install the corresponding linux-kernel-headers? Did you install the corresponding kernel-image? They should all be the same "number" and version.

Maybe you installed one version of the kernel and a different version of the headers.

---

### Post by Ruediger on 2005-01-07
[QUOTE=rolando]what about running a bootlocal.sh when you start Gnome, its worth a try eh?[/QUOTE]

All I have to do is to start xterm and type sudo ./bootlocal.sh?

---

### Post by fng on 2005-01-07
[QUOTE=Ruediger]Yes, those packages are installed (but not the -686 version, since the computer is a K6-2)[/QUOTE]

There are no k6 kernel/module packages.  A 686 is the closest thing to a k6-2.  You are even running a 686-kernel.  I would install those module packages for the 686 or revert back to a 386 kernel.

---

### Post by Ruediger on 2005-01-08
[QUOTE=fng]There are no k6 kernel/module packages.  A 686 is the closest thing to a k6-2.  You are even running a 686-kernel.  I would install those module packages for the 686 or revert back to a 386 kernel.[/QUOTE]

I didn't know that  :oops: 

I'll try it.

---

