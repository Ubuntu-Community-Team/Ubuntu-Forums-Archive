---
title: "Ubuntu won't finish installing?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by kelsad on 2011-02-02
Hello everyone! I'm trying to install Ubuntu 10.10 on my mac, and my friend told me the best way to install it was installing it through a VM... 

I'm using VirtualBox on Mac OS X 10.5.8 to install it,  i gave it 10MB of space, and i filled out everything correctly.

When i start the machine everything runs fine and it begins to install, i start filling everything out and get to where you go to enter you name (who are you? page) and everything is done, then i wait for it to finish installing and then it gets to the (Waiting on you...) part, then nothing happens... for a while... The finish button isn't highlighted so i can click on it. Can anyone help me????

---

### Post by taseedorf on 2011-02-02
Virtualbox is NOT The best way to install....perhaps maybe to try it, it's okay.  try wubi, perhaps. google it.

you need quite a bit more than 10mb of space.  Did you mean GB?

Also, make sure the settings in VB are correct.  Make sure that you have certain options enabled/disabled depending on your computer's capability.

---

### Post by lotus@terminal on 2011-02-02
Try allocating the Linux partition more space. If i'm understanding you correctly 10MB for a Linux partition is not near enough.

---

### Post by Sealbhach on 2011-02-02
10MB of space, did you mean 10GB?

Apart from disk space, maybe you need to allocate more memory to the virtual machine, maybe you just need to give it more RAM, at least 512MB, preferably more.

Another possibility is that perhaps the download was bad somehow so if you can't get it working any other way, try a new download and run md5sum on it.

.

---

### Post by kelsad on 2011-02-02
Yea sorry, it would be 10MB, I'm a bit tired! but that could be the problem, more space... And i will try the other VM software

---

### Post by Sealbhach on 2011-02-02
> **kelsad said:**
> Yea sorry, it would be 10MB, I'm a bit tired! but that could be the problem, more space... And i will try the other VM software

Wubi is **NOT** VM software, it will mess with your MBR, it's not the same as using Virtualbox. 

Virtualbox is fine for virtualization.

.

---

### Post by robgraves on 2011-02-02
i had a similar problem on a regular install, it wont let you get past the "Who Are You?" screen if your username has any uppercase letters.

---

### Post by Dutch70 on 2011-02-02
Edit: Sorry, missed the Mac OS X thing.

---

### Post by xoomer.ap on 2011-02-02
**kelsad**, 1 CPU, no io-apic, 768 Mb RAM, turned on VT-x/AMD-V, 10 Gb HDD, 32 Mb Video RAM, default audio and ethernet settings - this is fine settings for running Ubuntu on VirtualBox.

---

### Post by 3rdalbum on 2011-02-02
> **Dutch70 said:**
> +1 on using Wubi to try Ubuntu. you just install it directly into windows like any other windows application. 
 If you don't like it, just uninstall it the same way. It will be slow in a virtual machine.
[**_[COLOR="Red"]Click here for Wubi[/COLOR]_**]("https://wiki.ubuntu.com/WubiGuide")

Please, everyone, stop telling **kelsad** to try Wubi. He/she has clearly stated in their first post that they are _using Mac OS X_.

**Kelsad**: A common cause of this particular problem is putting capital letters or spaces into your "username"; it should be all lowercase and contain no spaces. There are also reserved words that can't be used, such as "root", "admin", "audio", "daemon".

---

### Post by synicalx on 2011-02-02
> **xoomer.ap said:**
> **kelsad**, 1 CPU, no io-apic, 768 Mb RAM, turned on VT-x/AMD-V, 10 Gb HDD, 32 Mb Video RAM, default audio and ethernet settings - this is fine settings for running Ubuntu on VirtualBox.

This 

Although, it is possible that OP's Mac doesn't support virtualization - my first gen Intel iMac used a laptop CPU (on a $2k desktop mind you...) that refused to behave with any sort of virtualization. Ended up having to use Bootcamp to run anything other than OSX...

---

### Post by 3rdalbum on 2011-02-02
> **synicalx said:**
> This 

Although, it is possible that OP's Mac doesn't support virtualization - my first gen Intel iMac used a laptop CPU (on a $2k desktop mind you...) that refused to behave with any sort of virtualization. Ended up having to use Bootcamp to run anything other than OSX...

If so, then they would turn off VT-x and AMD-V.

---

### Post by xoomer.ap on 2011-02-02
**synicalx**, you mean that CPU in your 1st Mac doesn't support hardware-virtualisation?
And, by the way, agree with **3rdalbum**. :)

---

