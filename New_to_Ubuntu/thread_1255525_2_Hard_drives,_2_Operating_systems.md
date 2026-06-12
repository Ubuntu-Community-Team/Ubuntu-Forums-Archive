---
title: "2 Hard drives, 2 Operating systems"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Miscible21 on 2009-09-01
Hi everyone. I am about to download 8.04. Im an XP user and I would prefer not to dual boot with ubuntu. I actually want to install ubuntu on a second hard drive that was in my machine but has given me some trouble. Im not sure if it was the os on the hard drive at the time or if the hard drive itself was corrupt. bt i plugged the drive in a moment ago and it booted up absolutely fine as if it never had any problems. Doing an installation on this drive would give me the opportunity to use ubuntu exclusively and have the full experience but not be left in a **** box if i needed XP. Especially since it's the time of year when i have plenty of assignments and deadlines at university. So my question is this...

If i install ubuntu on one hard drive, with my existing os on the other hard drive, would i be able to tell the pc which drive to boot into upon switching it on? Would i run into any problems doing this?

Thanks!

---

### Post by scorp123 on 2009-09-01
> **Miscible21 said:**
>  If i install ubuntu on one hard drive, with my existing os on the other hard drive, would i be able to tell the pc which drive to boot into upon switching it on? Didn't you just say that you did NOT want to dual-boot???

Could you please make up your mind? :D

---

### Post by Miscible21 on 2009-09-01
lol oops! is that a dual boot? I thought a dual boot was generally done on 1 hard drive. My bad if i was wrong:redface:

---

### Post by QIII on 2009-09-01
I find it preferable to dual boot on two separate drives.

I don't know if you are using SATA or IDE drives, but in either case you should be able to use my method here:

[http://ubuntuforums.org/showthread.php?t=1242793](http://ubuntuforums.org/showthread.php?t=1242793)

---

### Post by egalvan on 2009-09-01
What you describe is also called 'dual-booting'....

( the number of drives is totally irrelevant )

having the choice of OS to boot from is what is important. :)

As to your particular question...

"can I choose what drive to boot from"

it depends on your computer...

most all computers made  in the last five years (or more) 
have some sort of "boot menu".

Note that this is NOT the same as "boot order"
it is similar, but different.
and most modern BIOS code have both.

Some may not have it enabled by default. You have to go onto the BIOS to enable the "choice".

Look carefully at the screen the next time you boot your computer...
see if anything that looks like 

'boot option'

'boot order'

or similar pops up...

if not, then you should try enterting the BIOS and checking for a 
'boot order" option.

If it's a Dell, HP, or similar large manufacturer,
calling their support line may help.


And yes, that way of 'dual-booting' is used at times...
although most of us prefer to let GRUB do the honors...

GRUB is a piece of software that helps the multi-boot process...

---

### Post by moster on 2009-09-01
For the future... when installing, you must always install Ubuntu last because windows will overwrite boot. Ok, you do this already. Next, in installation of Ubuntu choose to install grub(boot loader) to windows partition. HDD where is windows installed. And you will not have any troubles.

You can choose that just after partitioning. There is a button "advanced" or similar.

---

### Post by egalvan on 2009-09-01
> **moster said:**
> ... when installing, you must always install Ubuntu last because windows will overwrite boot...

Not a "requirement".... :)

it just makes it easier... :)

And some of us prefer easier to harder...

It is possible to install Windows last, and recover the GRUB.
Not hard, just a few more steps.
Preparing is key to a smoother recovery.

---

### Post by Miscible21 on 2009-09-01
QIII, egalvan and moster, thank you so much for your speedy and helpful replies. I must admit that i am a little more confused than I was before though lol. 

egalvan your reply made the most sense to me. I am familiar with using the boot or setup menu as i had to install XP a few times before. This is how I thought I would deal with ubuntu. unplug my main hard drive like QIII said, and then install ubuntu on the secondary hard drive. Once it's installed i would plug both back in and go into the boot menu to instruct which hard drive the pc should boot from. would that work? or would ubuntu's boot settings conflict with windows once i plug the main hard drive back in?

The SATA header thing confused me a little QIII but i think i get it. As far as i know my XP hard drive would be at the lowest numbered header, what I dont understand is why i should swap the cables? cant I just disconect them?

As for GRUB, i havent got there yet. Im not very far into my ubuntu pocket guide lol

---

### Post by Paqman on 2009-09-01
> **Miscible21 said:**
> This is how I thought I would deal with ubuntu. unplug my main hard drive like QIII said, and then install ubuntu on the secondary hard drive. Once it's installed i would plug both back in and go into the boot menu to instruct which hard drive the pc should boot from. would that work? or would ubuntu's boot settings conflict with windows once i plug the main hard drive back in?


If you have the Windows drive unplugged when you set up Ubuntu then the bootloader (Grub) won't detect Windows and add it to the boot options. You'd have to add it manually.

I'd leave the Windows drive plugged in. Just double- and triple- check that you're installing Ubuntu onto the right drive! :D

It wouldn't hurt to back up Windows just in case. Then you're bombproof.

---

### Post by QIII on 2009-09-01
No.  Grub won't detect Windows and it will have to be added to the menu.lst manually.

As per my suggestion.

The beauty of it is that you take no chance on either boot mechanism being fouled up, OSs overwritten by mistake, no need for SuperGrub, FixMbr, etc.

You can take the Windows drive or the Ubuntu drive to another machine and pop them in and they will run...

---

### Post by ks07 on 2009-09-01
> **Miscible21 said:**
> QIII, egalvan and moster, thank you so much for your speedy and helpful replies. I must admit that i am a little more confused than I was before though lol. 

egalvan your reply made the most sense to me. I am familiar with using the boot or setup menu as i had to install XP a few times before. This is how I thought I would deal with ubuntu. unplug my main hard drive like QIII said, and then install ubuntu on the secondary hard drive. Once it's installed i would plug both back in and go into the boot menu to instruct which hard drive the pc should boot from. would that work? or would ubuntu's boot settings conflict with windows once i plug the main hard drive back in?

The SATA header thing confused me a little QIII but i think i get it. As far as i know my XP hard drive would be at the lowest numbered header, what I dont understand is why i should swap the cables? cant I just disconect them?

As for GRUB, i havent got there yet. Im not very far into my ubuntu pocket guide lol
I get what you mean, and that's how I started up my dual-boot.

Unplugging the main drive and installing will work, but only if your BIOS supports a boot menu. For example, when my computer is turned on it says "Press F12 to pick boot device" owtte. Check you have this option, otherwise you will want to install like the other posters have said.

---

### Post by Miscible21 on 2009-09-01
> **ks07 said:**
> I get what you mean, and that's how I started up my dual-boot.

Unplugging the main drive and installing will work, but only if your BIOS supports a boot menu. For example, when my computer is turned on it says "Press F12 to pick boot device" owtte. Check you have this option, otherwise you will want to install like the other posters have said.
I do have that option. I think i have to press F12 as well. But i also press Del for somthing else as well. will check on my next boot.

---

### Post by ks07 on 2009-09-01
> **Miscible21 said:**
> I do have that option. I think i have to press F12 as well. But i also press Del for somthing else as well. will check on my next boot.
Sounds good. Delete will go into the bios settings, F12 should be the boot menu.

If all's good then you can go ahead and unplug your Windows HDD, plug in the second drive. Boot up from the CD and install. Then you should be able to plug in your Windows drive and next time you boot just go into that menu and pick which HDD you want to boot from. You may have to change your boot order in the bios settings so your preffered OS boots without you having to intervene lol.

IMO this method of install is pretty good if you want to experiment. With the other drive unplugged there's no way you can break it while installing. When you feel like it you can add Windows to GRUB (or add Ubuntu to ntldr), so you don't need to press f12 every time you start up.

---

### Post by Miscible21 on 2009-09-01
Thanks ks07. that solution is a little simpler. Will do some more research, but chances are i will do it that way first.

---

### Post by yanceypd on 2009-09-01
You can boot select from the BIOS during Power up if you desire.  Just unplug power from other drive and load up second drive from live cd.  The grub then only installs on the second drive.  A second data cable to the second drive is probably best.  Soon you will wish you had dual boot set up though.:)

---

### Post by egalvan on 2009-09-01
> **QIII said:**
> 
You can take the Windows drive or the Ubuntu drive to another machine and pop them in and they will run...

I agree on this as refers to Linux...
it can be moved around to different machines, anb odds are good it will boot OK...

But as for Windows XP or Vista...

Unless the machines are virtual clones, this will fail.
Windows hard-codes the chip-set drivers, along with IDE/SATA and video.
Not to mention the infamous "activation"

Yes, it's possible to "prepare" XP to be moved to another platform, but it's certainly not as simple as most *nix's.

---

### Post by ks07 on 2009-09-02
> **Miscible21 said:**
> Thanks ks07. that solution is a little simpler. Will do some more research, but chances are i will do it that way first.
 
Cool, glad I could help. :)
> **egalvan said:**
> Yes, it's possible to "prepare" XP to be moved to another platform, but it's certainly not as simple as most *nix's.
 Lol it's hard enough just updating a couple components in Windows without it complaining about it being too different. :P

---

### Post by QIII on 2009-09-02
> **egalvan said:**
> 
Unless the machines are virtual clones, this will fail.


No more likely than if one replaces a toasted motherboard or just upgraded with a sazzier one, as a gamer might ...

I've done that on XP, but haven't yet had the pleasure with Vista.

With Vista you may get complaints about product registration on a wholesale change like that.   Vista might report you to the Redmond Gestapo.

---

