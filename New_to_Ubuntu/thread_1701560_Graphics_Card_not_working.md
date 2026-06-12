---
title: "Graphics Card not working"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-03-06
Hello all

Had to build / replace my motherboard, so along with a "Asrock K10N78D, Socket AM2" I fitted a NVIDIA GeForce 8400 GS Graphics Card, which is supposed to be, and I quote

(Operating Systems Supported-WHQL Certified &#149; Windows 2000/XP/Vista &#149; Linux)

Note the last one Linux, as I know nothing about Linux and took about 5 attempts to duel boot, (XP  "needed") and Ubuntu, I am left with Display settings of 600X800 I would need it about 1920 X 1080 (16:9) it also has failed to detect my hp monitor

Step by step help is needed,:confused: :confused:

Thanks in advance

Dave [B]
[/B]

---

### Post by TeoBigusGeekus on 2011-03-06
Have you installed the restricted drivers for your card?

---

### Post by stephanvaningen on 2011-03-06
That is, in Gnome desktop use System -> Administration -> Additional drivers. There let the program do it's work and respond accordingly to buttons / questions...
> **TeoBigusGeekus said:**
> Have you installed the restricted drivers for your card?

---

### Post by TenSpeed on 2011-03-06
If you go to the 'System' menu and choose 'Preferences' and then 'Monitors' does the dropdown there give you any resolution options other than 640x480?

---

### Post by DaveMcC on 2011-03-06
> **stephanvaningen said:**
> That is, in Gnome desktop use System -> Administration -> Additional drivers. There let the program do it's work and respond accordingly to buttons / questions...

Don't have Additional Drivers, but do have Hardware Drivers, which tell me
No proprietary drivers are in use on this system

> **TenSpeed said:**
> If you go to the 'System' menu and choose 'Preferences' and then 'Monitors' does the dropdown there give you any resolution options other than 640x480?

Thats strange, as I don't have monitors either in the System , Preference, 

Dave

---

### Post by TeoBigusGeekus on 2011-03-06
> **DaveMcC said:**
> Don't have Additional Drivers, but do have Hardware Drivers, which tell me
No proprietary drivers are in use on this system

Aren't there any available?

---

### Post by DaveMcC on 2011-03-06
None that I can see?

This is a worry

Dave

---

### Post by TeoBigusGeekus on 2011-03-06
Strange, I thought all nvidia cards (especially oldish ones) have excellent support in linux.
Is your card recognised by your system?
```
lshw -c display
```

---

### Post by DaveMcC on 2011-03-06
> **TeoBigusGeekus said:**
> 
```
lshw -c display
```

Dont know what the above means, ????
Have just updated to ver 10.04

Dave

---

### Post by TeoBigusGeekus on 2011-03-06
Run it in terminal and post us the output.

EDIT: Updated? Is this an upgrade? Not a clean installation?

---

### Post by DaveMcC on 2011-03-06
> **TeoBigusGeekus said:**
> Run it in terminal and post us the output.

EDIT: Updated? Is this an upgrade? Not a clean installation?

Would that be the thing in
Applications
Internet ?

Sorry but I know nowt abut ubuntu or linux, but I do hate MS

Dave

---

### Post by TeoBigusGeekus on 2011-03-06
Ok.
Applications>Accessories>Terminal
Type
```
lshw -c display
```
and press enter. Copy and paste the output.

---

### Post by DaveMcC on 2011-03-06
Sorry about this, being so slow, maybe its because I am downloading / updating to ver 10.

As my download is sooo sloowww tonight, maybe after a reboot it may be cured?
But here is what you asked for Teo?

Have a look, tell me what you think, would you mind if we then "if needed" continue this tomorrow night, early start for work

Dave 

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:ec00(size=128) memory:feb80000-febfffff(prefetchable)
david@david-desktop:~$

---

### Post by TeoBigusGeekus on 2011-03-06
It's ok Dave, but ubuntu hasn't recognised your card.
I hope we'll meet tomorrow night.

---

### Post by DaveMcC on 2011-03-06
Final post of the night, then bed
**GeForce 8400 GS 256MB PCI-E Graphics Card**



Thats the full name of my card,
PS Im from Northern Ireland

Dave

---

### Post by albert s on 2011-03-06
I have a Nvidia 8400GS card and it runs perfectly, I did have a few issues previously with my resolution(but got them sorted on here, thank you), but I since got a new 1920x900(or whatever it is) and it recognised it as soon as I plugged it in. BTW Dave, where abouts you at? NI can be a big place if you are walking.  LMFAO.

---

### Post by DaveMcC on 2011-03-07
Update to ver 10.04 also failed
Dont think I will ever get this to run right

Dave
diapointment

---

### Post by mastablasta on 2011-03-07
try to perform a clean install or better yet to try it out first boot from LiveCD or LiveUSB.
 
if you are upgrading it could be that some files related to graphics card drivers from your previous install are messing up the current one.

---

### Post by TeoBigusGeekus on 2011-03-07
> **DaveMcC said:**
> Update to ver 10.04 also failed
Dont think I will ever get this to run right

Dave
diapointment

Do a clean installation: perhaps the partial upgrade resulted in your gc not being recognised.

---

### Post by DaveMcC on 2011-03-07
Live CD being the one I first started with, the one that may be wonk'ie?
To do that is going to be a lot of work

Step 1 Format the drive including the XP part, to clean out the MBR
Step 2 Format the drive using windows, 
Step 3 Reinstall XP "needed"
Step 4 Reinstall Ubuntu and create a ubuntu partition
Step 5 go on knees and (pray) to the thing that this time it will work and not be left with a triple boot up

Hence all the different formating needed

Dave

---

### Post by TeoBigusGeekus on 2011-03-07
You don't have to reinstall winxp. Just ubuntu. The installer will take care of the bootloader and the mbr.

---

### Post by mastablasta on 2011-03-07
> **TeoBigusGeekus said:**
> You don't have to reinstall winxp. Just ubuntu. The installer will take care of the bootloader and the mbr.
 
But back up data anyway just in case.

---

### Post by DaveMcC on 2011-03-07
glad to say its a new hard drive main brd and graphis card, all out of the box last Friday, or 3 days ago
So I ain't no data to back up
But! heres the thing, I first installed ubuntu inside windows "mistake" I then deleted it and reinstalled it from the cd and made it make the hard drive partion, but it failed to remove the first bootloader, and made a larger one with 4 things to pick from
Ubuntu
mem test 
mem test + some thing else
windows XP

The first one just had
windows
ubuntu

See now maybe why the graphics card ain't working? 
Dave

---

