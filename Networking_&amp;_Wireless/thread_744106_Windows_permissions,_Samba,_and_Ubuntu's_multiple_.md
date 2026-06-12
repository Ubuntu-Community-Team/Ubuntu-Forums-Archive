---
title: "Windows permissions, Samba, and Ubuntu's multiple personalities"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by EntityAbacus on 2008-04-03
I'm extremely new to Linux - like, 5 days new. I've broken 3 installs (purposely) learning the package manager, the terminal, etc. Now that I have a stable install, I have one problem that keeps haunting me and I can't seem to find a decent answer to it.

And mind you, this after reading and following multiple samba share tutorials on the wiki and in the forum.

I have two computers - an XP Pro workstation and an Ubuntu 7.10 laptop. I'm on a college network, and I share out a good deal of my media on my workstation to the rest of the school. I have one folder, however, that contains all my research and schoolwork that needs to remain private but still accessable to my laptop which I use elsewhere for research and word processing.

What I used to do, when my laptop was XP, was share the sensitive folder on the network after unchecking the "read" option under "Everyone" in the access permissions. Then, on my laptop, I would map the folder (which didn't even broadcast on the windows network) "//Workstation/Sensitive" as Me@Workstation. It would appear on my laptop and I would have full write and edit access. No one else (on windows) could even see it, let alone access it.

Now, with Ubuntu, I tried that same scheme. I did the 

smbmount //Workstation/Sensitive mnt/sensitive user=Me password=password;uid=laptopMe etc etc.

But when I mount it - and it does mount - /mnt/sensitive disappears. I can only see it, as root, with a dir command in /mnt. But anything sudo -whatever I try to do to it fails thereafter.

My theory is that after I mount it with the smbmount command using my windows username and password, it literally turns into that share with the same permissions mounted to /mnt/Sensitive. That means that, the same way that no one else can see it on the network, my Ubuntu user account can't see it or access it because it's not Me@Workstation.

The only thing I haven't tried is
smbmount //Workstation/Sensitive mnt/sensitive **user=Me@Workstation** password=password;uid=laptopMe etc etc.
But that only just occurred to me, and my laptop is on the other side of campus at the moment. I'll have to try it later.

Any suggestions?

---

### Post by Eiríkr on 2008-04-03
Hey there --

The smbmount command has been deprecated for some time, and is now officially abandoned.  From the man page:
> WARNING: smbmount is deprecated and not maintained any longer.  mount.cifs (mount -t cifs) should be used instead of smbmount.

I've had some very weird results when testing smbmount recently that strongly suggest the tool is no longer useful.  I'm not surprised you're getting weirdness on your end.  

You'll want to try something like the following instead:
```
sudo mount -t cifs -o username=USERNAME,password=PASSWORD,rw,uid=UID,gid=GID //workstation/sensitive /mnt/sensitive
```

Replace the caps with the appropriate values.  UID and GID values define who will own the share after it's mounted; if you leave these out, it defaults to root, which can be bothersome.  :)  Use either your username's and group's numeric values, or just your username and primary group names (definitely easier to remember).  And have a look at [font=courier]man mount[/font] and [font=courier]man mount.cifs[/font] for details on other options you might want or need.

HTH,

Eiríkr

PS -- The @ notation used on Windows machines for share access won't work for access via the Samba tools.

---

