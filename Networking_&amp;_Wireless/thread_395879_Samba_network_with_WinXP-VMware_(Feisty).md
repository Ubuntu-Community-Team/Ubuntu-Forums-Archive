---
title: "Samba network with WinXP-VMware (Feisty)"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by baldercm on 2007-03-28
Hi!

I had my Samba network between my Ubuntu Edgy and VMWare-Winxp, but when I upgraded to Feisty I found some problems:
 - I can't navigate my workgroup in WinXp, nor access my Linux host using the Samba name (writing \\MyName in my WinXp address bar), but I'm able to see my shared folders if I use my Linux IP instead of the name (using \\192.168.9.2).

- twhen trying to acces my WinXp shares in Konqueror, I can use the name and IP's, but I can't see the WinXp virtual machine when exploring my workgroup.

- my smbtree or findsmb output shows my Linux laptop and my Linux desktop PC, but I can't see my WinXp virtual machine.

- I've all these problems if I boot the dual boot desktop PC with WinXp

I need this working to plug a network drive in WinXp (which cant' be done with IP's).

Any ideas? Something related to my virtual ethernet card maybe? Samba permissions?

Thank you!

---

### Post by rickyjones on 2007-03-28
> **baldercm said:**
> 
I need this working to plug a network drive in WinXp (which cant' be done with IP's).


I'm not sure where the problem stems from, but you can connect to network drives using just the IP in Windows XP. I know this because that is what happens at my job.

net use z: \\xxx.xxx.xxx.xxx\share

You don't /need/ to use a name all the time. The IP should work just fine.

-Richard

---

### Post by baldercm on 2007-03-28
I tried, but I get an error message:
```
Error 53
Can't find path to the device
```

or something like that, because I have Windows in spanish.

I ping my IP and it worked, but I couldn't create the network drive!

I don't know what's happening...

---

### Post by baldercm on 2007-03-30
I still don't know why the upgrade to Feisty broke my network, but I've fixed it!!

I edited my smb.conf file and I saw a lot of options in my shares. I think they're automatic options, so I deleted them and left all like that:
```
[web]
path = /home/balder/web
guest ok = yes
```

It all worked again, both with my VMware WinXp and with my flat mate's desktop WinXp!!

---

### Post by reagle on 2007-04-03
This sounds a lot like the bug I filed here: [Problems in networking between 7.04 host and win2k guest OS in vmware]("https://launchpad.net/ubuntu/+bug/96445")

---

