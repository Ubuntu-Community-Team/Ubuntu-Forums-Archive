---
title: "Problems With Linux Server"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2008-02-20
I'm having a few problems with my Linux server. 

It doesn't serve anything advanced, I just have some mapped drives on my Vista laptop that connect to it.

On my Ubuntu server (which is just the desktop amd64 version of Ubuntu 7.10) I have music and video shares that my laptop accesses. My server is rarely ever turned off, it stays on almost all the time.

Most of the time my laptop accesses the shares just fine. Sometimes, it cannot access the shares. When this happens the server cannot be pinged. Trying to reconnect the shared drives in Windows does nothing.

A reboot fixes this problem for me every single time. After rebooting the server, I'm able to access all the shares again.

Another strange thing, is that another computer on the network, also Ubuntu, never fails with a computer accessing its shares. It uses the same configuration file for Samba and the same version of Ubuntu.

Here is the configuration files I use for Samba. I need to know why my Ubuntu server sometimes stops sharing. It's almost as if the Samba process dies for some reason.

[/etc/samba/smb.conf]
```

[global]
workgroup = SERVICE
security = share
include = /etc/samba/smbshared.conf

wins support = no

```

[/etc/samba/smbshared.conf]```
[Jeremy's Laptop - Shared] ; user="jeremy"
	force user = jeremy
	path = /home/jeremy/Shared
	writable = yes
	public = yes

[Jeremy's Laptop - Shared Music] ; user="jeremy"
	force user = jeremy
	path = /home/jeremy/Music
	writable = no
	public = yes

```

---

### Post by jhetrick62 on 2008-02-20
Sounds like it could be an acpi problem that is powering down the network connection.  I've had issues like this on my FC5 server and turning of acpi seemed to do the trick.

Try that and see if you still have the issue.

Jeff

---

### Post by jlacroix on 2008-02-20
Would that be something I would turn off in my computer BIOS or in Ubuntu's settings somewhere?

---

### Post by Iowan on 2008-02-20
It's been awhile since I played around with GRUB settings, but the file is **/boot/grub/menu.lst**.  Probably a **noacpi** option on the **kernel** line
 - but it's been awhile since I played around with GRUB settings.
There's also an **acpi=off** option... see if [this]("http://ubuntuforums.org/showthread.php?t=144448&") helps.

---

### Post by The Cog on 2008-02-21
Certainly you can forget problems with samba. If you cannot ping the server when this happens then the problem is a low-level networking problem and you should concentrate on why the ping isn't working,

---

### Post by jhetrick62 on 2008-02-21
You can turn this off in the system > administrations > services option. Just uncheck it and then restart your machine.

It will work in Grub, but now necessary to go to that extent.

Jeff

---

### Post by jlacroix on 2008-02-25
Thanks, I turned off "acpid", is that it? I will test and see if there are any problems and I will let you guys know if there are. Thanks for the support!

---

