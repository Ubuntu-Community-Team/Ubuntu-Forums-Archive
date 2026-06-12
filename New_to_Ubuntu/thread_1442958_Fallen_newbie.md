---
title: "Fallen newbie"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Maverick52 on 2010-03-30
Hey there everyone! thx for the warm welcome!!

Big problem: 

Yesterday I installed my first linux distro ever, chose Ubuntu Studio 9.10 Karmic Koala. It was a clean install from the start, as I chose to totally replace Vista in my Toshiba Satellite A305D laptop. First thing I thought: "Why didn't I switch before?".

Today I'm living every newbie's nightmare.

I closed the laptop, which made it hybernate, I suppose. Now, when I try to get it running it's like a vegetable, no activity, no drivers, no processing, just black screen. Well the leds turn on, but that's the only sign it's turned on.

If I do a hard shutdown, wait and turn it on again, same thing. I don't think controllers or drivers are being loaded at all.

Tried booting it with the live DVD - nothing.
Also tried "ctrl-alt-F1 and then ctrl-alt-F7" (as user Liquen suggested in a thread), but no screen, it's like it was off.

Help! I want to make it work on linux, I really do, but I need it working at all, first!

Any ideas, leads, thing?

---

### Post by Paqman on 2010-03-30
What's the exact model of laptop? Some hardware has bugs in it's power management setup that mean it works fine with Windows, but not with Linux. There may or may not be a workaround for it. Often these things only get fixed by kernel updates.

---

### Post by Maverick52 on 2010-03-30
Toshiba Satellite A305D-SP6801

AMD Turion 64 X2 processor 2.10 ghz
2 GB RAM
ATI Radeon X1250
BIOS RS690 long horn_rtm...

... and I have some more info I was able to write down before it crashed.

Is that enough info, or should I be looking for something else to give you?

... all I want to do right now is to see some response... any response from my computer

thanks for the interest & support

---

### Post by George Zafiris on 2010-03-30
**Good luck with your install. I am a newbie too.Actually I know how to use the environment of ubuntu but I'm still learning about codelines.Good Luck again...let's roll together dude...**

---

### Post by Daveth on 2010-03-30
this

[http://www.linlap.com/wiki/toshiba+satellite+a300d-a305d](http://www.linlap.com/wiki/toshiba+satellite+a300d-a305d)

suggests that it is an acpi issue with the kernel, and that you would need to edit the file with the 'acpi=off' option.

If you hunt that out on this forum you should find some guides to allow you to tackle that.

---

### Post by waspbr on 2010-03-30
k, solving this shouldn't be horribly difficult, I am assuming that you can get to you grub menu, (The list with you installed OS). 

In that menu, make sure it is on the ubuntu you normally boot to, (it should be there by defualt) and press 'e', this will take you to and edit menu. 


you should see something like this, the numbers will be different

```
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7dfdcf5f-76e2-428c-8cff-b7080a757e0a
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7dfdcf5f-76e2-428c-8cff-b7080a757e0a ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
```

now, I know this can be a little scary but you need to add the term

```
acpi=off
``` in this manner


```
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7dfdcf5f-76e2-428c-8cff-b7080a757e0a
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7dfdcf5f-76e2-428c-8cff-b7080a757e0a ro **acpi=off** quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
```

Once that is out of the way you get out of that menu (think you either need to press 'b' or enter, there should be instructions) and resume booting ubuntu. 

Hopefully this should work.

---

### Post by Maverick52 on 2010-03-30
I actually, CAN'T get to the grub menu, what can I do to get it?

---

### Post by Maverick52 on 2010-03-30
> **George Zafiris said:**
> **Good luck with your install. I am a newbie too.Actually I know how to use the environment of ubuntu but I'm still learning about codelines.Good Luck again...let's roll together dude...**
**Thx for your wishes man! good luck to you too, with those ****codelines. I hope can join you rolling again soon!!**

---

### Post by Maverick52 on 2010-03-30
> **Maverick52 said:**
> Hey there everyone! thx for the warm welcome!!

Big problem: 

Yesterday I installed my first linux distro ever, chose Ubuntu Studio 9.10 Karmic Koala. It was a clean install from the start, as I chose to totally replace Vista in my Toshiba Satellite A305D laptop. First thing I thought: "Why didn't I switch before?".

Today I'm living every newbie's nightmare.

I closed the laptop, which made it hybernate, I suppose. Now, when I try to get it running it's like a vegetable, no activity, no drivers, no processing, just black screen. Well the leds turn on, but that's the only sign it's turned on.

If I do a hard shutdown, wait and turn it on again, same thing. I don't think controllers or drivers are being loaded at all.

Tried booting it with the live DVD - nothing.
Also tried "ctrl-alt-F1 and then ctrl-alt-F7" (as user Liquen suggested in a thread), but no screen, it's like it was off.

Help! I want to make it work on linux, I really do, but I need it working at all, first!

Any ideas, leads, thing?
This is what I see:

I push the ON button, and I get to see exactly about 2 seconds normal startup behavior -no time to load a thing, in my opinion. 

As a matter of fact, when I WAS able to run it properly (on ubuntu studio, and all), the very first thing that showed up on screen was the TOSHIBA welcome screen with the notice to hit F12 for boot options, the same screen that I had pre-installed when I got the computer with Vista.

So I guess I don't even know what the GRUB menu looks like, although I keep reading a lot about it! lol.... How I wish it just "popped-up" out of nowhere...

---

### Post by J V on 2010-03-30
Sounds like a currupted bios/hardware...

Try to get into your bios, if you can't power down, remove the battery, put it back together and try again.

If its still a no-show, send it to toshiba for repair, or get the HD out and save the data while you still can ;)

---

### Post by Maverick52 on 2010-03-30
> **J V said:**
> Sounds like a currupted bios/hardware...

Try to get into your bios, if you can't power down, remove the battery, put it back together and try again.

If its still a no-show, send it to toshiba for repair, or get the HD out and save the data while you still can ;)


Man you were right!!! simple but genious... I can't thank you enough

I was frustrated. Really, there was nothing left to do, removing the battery is what finally worked for me... I really didn't care about my info, I did a good backup before installing.


Can you help me understand what happened? What can I do to avoid this? For instance, I'll never let it go to hybernate or suspend until that bug is fixed for good!!    lol

---

### Post by lidex on 2010-03-30
After the bios screen, hold down your shift key to get grub menu.

---

### Post by admiralspark on 2010-03-30
When hibernating (and suspending too?) I believe some information is saved to the "Linux Swap" you should've made in the installation. If that's not large enough (for ex: mine is 512mb, but I have 1.25gb ram), the suspend/hibernate will not work properly. The technicalities are lost to me ATM, but I'm sure someone else can explain.

---

### Post by Maverick52 on 2010-03-30
So I should just find a way to make the linux swap partition larger? I'll explore the resident application that manages partitions... although, to tell you the truth, after what I've been through today, I'm unlikely to do any changes right now...

thanks for the tip, I'll dig a little deeper!!

---

### Post by KIAaze on 2010-03-31
I'd recommend avoiding the use of suspend and hibernate for now.
Suspend never worked for me.
Hibernate did, but considering what happened to you, you should probably avoid using it. ^^
Make sure it's deactivated when laptop lid is closed. Should be somewhere in the power management settings.

I didn't know about the swap size having to be at least as big as the RAM for suspend/hibernate to work. Interesting. (It's the case on my laptop, but not my desktop.)

Anyway, you can't resize partitions in use, so you'll probably have to boot from a Live-CD/Live-DVD to resize the swap partition. ;)

> I'll explore the resident application that manages partitions...
It's "gparted". "System/Administration/Partition Editor" in the menu.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Maverick52 on 2010-03-31
> **KIAaze said:**
> deactivated when laptop lid is closed. 
done :D

> **KIAaze said:**
> I didn't know about the swap size having to be at least as big as the RAM for suspend/hibernate to work. 
me neither, but I checked and my swap is 5GB, so I guess no prob there..

> **KIAaze said:**
> Anyway, you can't resize partitions in use, so you'll probably have to boot from a Live-CD/Live-DVD to resize the swap partition. ;) 
Didn't know, thx for the tip

> **KIAaze said:**
> It's "gparted". 
lol, I was really lost trying to use Palimpsest, wasn't I.. again, thx!

---

### Post by quadproc on 2010-03-31
> **admiralspark said:**
> When hibernating (and suspending too?) I believe some information is saved to the "Linux Swap" you should've made in the installation. If that's not large enough (for ex: mine is 512mb, but I have 1.25gb ram), the suspend/hibernate will not work properly. The technicalities are lost to me ATM, but I'm sure someone else can explain.
Sure: when the system is to be powered down but you wish to have the system remember everything that it was doing, the system needs to copy everything from RAM memory to disk.  It uses the swap space as the recipient of everything that was in RAM.  So the swap space needs to be at least as big as the RAM.  In practice, it is a good idea to make your swap space at least twice as big as your RAM (or as big as your RAM will be, if you plan to get more in the future).  Also, excess swap space can improve performance if you are low on RAM.

quadproc

---

### Post by KIAaze on 2010-03-31
Well, it seems it's possible to suspend/hibernate without a swap partition by using a swap file. :)
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt](http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt)
[http://superuser.com/questions/21020/can-i-hibernate-linux-without-a-swap-partition/21021](http://superuser.com/questions/21020/can-i-hibernate-linux-without-a-swap-partition/21021)
[http://superuser.com/questions/16280/swap-partition-size-for-4gb-ram](http://superuser.com/questions/16280/swap-partition-size-for-4gb-ram)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

