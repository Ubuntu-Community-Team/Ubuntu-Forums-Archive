---
title: "Network question."
date: 2010-03-27
forum: New to Ubuntu
---

### Post by I Tj on 2010-03-27
I'm trying not to be risky at this, so I wanted to know if having a Linux computer will mess with windows computers on the network.

---

### Post by Mike'sHardLinux on 2010-03-27
Mixing Windows and Linux workstations on the same network will not be a problem. Go for it! :D

---

### Post by I Tj on 2010-03-27
Thank you!

---

### Post by joshwaaa on 2010-03-27
Short answer no. Linux wont mess with your windows devices.
 
It can be a pain connecting to windows vista/7 file shares from ubuntu though. Just have to make sure you have the right settings turned on.
 
Cheers,
 
Joshwaaa

---

### Post by I Tj on 2010-03-27
I don't plan on sharing files or anything, just checking to make sure it won't completely mess things up or anything or make blips come up saying, Warning a Linux is on your network, or anything.

---

### Post by new_tolinux on 2010-03-27
The only way you can "mess up" your network is when you're going to install a DHCP-server on your linux-machine.
That's not done by default, and you _will_ notice the both "words" DHCP and "server" in the package-description in synaptics or add/remove-programs.

And even then you will _not_ completely mess-up your network. Only thing then is that some computers may get an IP-adres from the linux machine instead of the normal router.
_If_ that is the case just unplug the network-cable from the linux-machine and reboot those PC's and everything will be running fine again. After that uninstall the DHCP-server the same way you installed it and plug the network-cable back in and there should be no more problems again.

---

### Post by a.walker on 2010-03-27
> **I Tj said:**
> I'm trying not to be risky at this, so I wanted to know if having a Linux computer will mess with windows computers on the network.

It depends, do you want it to? :D

Seriously though, it depends on the type of network you're talking about. What are you wanting to do? A little more information would be helpful.

I've never had a problem with a Linux computer messing with Windows computers. If it's a home network, I wouldn't worry about it.

I wouldn't install Linux on a work computer without written permission from the sysadmin or at the very least some manager, especially if you are going to try to access network resources with it (ie network shares). Although Linux computers are pretty secure, it might make you an easy target if something goes wrong with the network even if you aren't the cause of it.

---

### Post by I Tj on 2010-03-27
The connection is just a simple WEP network, and I use comcast ISP, I was already told nothing would happen with my ISP tho. Don't know the type tho, how would I find this out?

---

### Post by new_tolinux on 2010-03-27
I think a.walker means "home network", "office network", "school network" etc.
Should not be to hard to find out ;)

---

### Post by Mike'sHardLinux on 2010-03-27
> **I Tj said:**
> The connection is just a simple WEP network, and I use comcast ISP, I was already told nothing would happen with my ISP tho. Don't know the type tho, how would I find this out?

I TJ, people are over-complicating things. You will not have ANY problems as a result of mixing Linux and Windows on the same network. Trust me. I am a networking professional. I mix them at home and my company uses Linux, Unix, and Windows all on the same network as well.

---

### Post by a.walker on 2010-03-27
> **new_tolinux said:**
> I think a.walker means "home network", "office network", "school network" etc.
Should not be to hard to find out ;)

Yeah, that.:p

---

### Post by I Tj on 2010-03-27
Well, it's just a home network, we have a Vista an XP and a 7, 7 is the one I'm switching, I'm sure it'll work, but I'm just being more specific.

---

