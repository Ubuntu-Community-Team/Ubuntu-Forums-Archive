---
title: "GRUB update and BURG"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by 29732 on 2010-07-23
well...
i installed the grub update and now burg isn't working 
is there any way to reset it back to burg??

---

### Post by 29732 on 2010-07-23
bump :/

---

### Post by 29732 on 2010-07-23
bump  :cry:

---

### Post by 29732 on 2010-07-24
bump again

---

### Post by themusicalduck on 2010-07-24
So has it reverted back to using grub? Strange, that didn't happen to me even though I updated grub too.

If that's the case, then I would probably go through the steps you went through to install burg in the first place. Basically just reinstall burg over grub.

Assuming you haven't removed burg completely using apt-get, then I think this would work:

Copied and pasted from OMGUbuntu..

> Install BURG to your Master Boot Record

Install burg to your MBR using the command below. Substitute ‘hd0’ with an alternative drive if needed.

sudo burg-install "(hd0)"

Update BURG entries

You MUST run this step or you may be left scratching your head upon reboot when nothing shows up

sudo update-burg

---

### Post by Elmer Fudd on 2010-07-24
Happened to me as well.

All I did to repair was:

sudo burg-install --alt /dev/sda  
&& change sda to appropriate device.

then

sudo update-burg

That returned my system to normal.
(which I then tweak to get what I want)

I use the "--alt" install cuz it works on all the systems that I support.
It may not be ness for you, but I got tired of having to repair windows dual-boot systems that I converted to Burg with the standard install

---

### Post by 29732 on 2010-07-24
ummmm... simple english?
step-by-step?
thx

---

### Post by k3lt01 on 2010-07-24
> **29732 said:**
> ummmm... simple english?
step-by-step?
thxSimple English would be to re-install Burg. Simple as that.

---

### Post by 29732 on 2010-07-24
awww...
there is no other way???

---

### Post by k3lt01 on 2010-07-24
Re-install BURG and remove GRUB that way GRUB wont update and bork your BURG on you ;). I have this on my flash drives but NOT on my PCs so only do this if you want to risk it.

---

### Post by 29732 on 2010-07-24
can't i just remove the grub repositories so it won update it??

---

### Post by hackerseraph on 2010-07-24
normally a grub update wont damage burg. I too suffered from the last update but all i did was a simple

```
sudo apt-get autoremove burg
sudo apt-get install burg
sudo update-burg
```

restarted and everything was fine.

as far as removing grub, i really dont recommend doing that.

---

### Post by k3lt01 on 2010-07-24
GRUB doesn't have its own repository so to speak. You can, if you want to Remove GRUB from your system in Synaptic but you should install BURG and I would do that before removing GRUB.

Remember BURG is not the default at the moment on your system so you need to re-install it to make it the default again. When you have done that remove grub if you want to or you can "Pin" Grub so it will never update again. I just think why have 2 things on your system that do essentially the same thing?

You could always make GRUB use BURG's settings etc.

---

### Post by hackerseraph on 2010-07-24
> **k3lt01 said:**
>  When you have done that remove grub if you want to or you can "Pin" Grub so it will never update again. I just think why have 2 things on your system that do essentially the same thing?

You could always make GRUB use BURG's settings etc.


off the top of your head, how could we go about "pinning" grub in its current state?

---

### Post by 29732 on 2010-07-24
pinning would be nice
the reason i dont want to uninstall grub is because that i want to keep grub as a "backup" in case burg goes wrong 
and 
when i install burg, it asks for a command line so grub has the original command so i want to keep it just in case

all of this sounds pointless, but im sorta more of a "better safe than sorry" kind of guy when it comes to pcs so how do you "pin" grub??

---

### Post by k3lt01 on 2010-07-24
> **hackerseraph said:**
> off the top of your head, how could we go about "pinning" grub in its current state?In Synaptic locate the GRUB files that are installed. Up the top of Synaptic go to the Package menu and select Lock Version. That will stop anything you Locked "Pinned" from ever updating again.

---

### Post by 29732 on 2010-07-24
Thanks,
i now locked the grub , now no more problems ^.^

---

### Post by yoramdavid on 2010-09-29
Today the system did an update (I am using ubuntu Lucid) and in the update grup-pc was included probably to solve a bug (every time I would install or uninstall an application there was an [error]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/628859").
Anyway, I was using BURG, had uninstalled GRUB and now grub has taken over again. I reinstalled BURG with Burg-manager, did the burg-update but it is still the grub showing up on reboot.
If I uninstall grub, I fear to get this errors again, I was wondering if I could just disable GRUB and use BURG.
Any ideas?

---

