---
title: "Help, I wrecked X server with the upgrade!"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by redjeep0 on 2009-04-29
I'm a longtime Windows User, who decided to dabble with 8.04, but I'm still very much a n00b, so Thanks in advance for any assistance.  

I have an ECS NForce 570 slit-A mobo with dual NVidia SLI cards, and I was running Hardy Heron without any major operational problems.  I couldn't get my logitech webcam to work properly, and also a linksys skype cordless USB phone, but general web surfing, DVD viewing, etc, seemed to work fine. 

About a week ago, I decided to try the 8.10 upgrade, and, from what I can learn from the forums, there's a problem with the Nvidia drivers for 8.10, and the Xserver doesn't load.  I can get to shell, but when I try to startx, I encounter a "fatal server error: no screens found"

9.04 was released a couple of days later, and my tries at envyNG and other suggestions from the forums weren't working, so I thought, perhaps 9.04 will fix the problem, so I d/l'd the iso and tried to reinstall, but now my machine doesn't seem to load from CD?  I have set CD-ROM as 1st thru 3rd boot devices (in other words, taken HD out of the equation), but 8.10 is still my only option for loading.  I've also tried a freshly burned 8.04 CD-ROM, again, GRUB seems to only load the 8.10, not the CD 8.04

Can someone steer me back into the right direction?
I can get to terminal, 8.10 tty1, but I really just want my machine back.  
I suspect if I can 'upgrade' back to 8.04 from terminal, it might solve my problems?
I have fooled around with the BIOS a little bit, during all of this, but I've set things back to 'load optimized defaults,' and still no dice.

If this is the wrong forum, please steer me to the correct one.
Thank you!

---

### Post by oOarthurOo on 2009-04-29
If you are burning these cd's on another computer, it is possible that your hardware cannot recognize the cdrom type. Especially if you are actually using DVD's to install. Take a look at the kind of CD rom that you are actually able to boot from and make sure that your other cdroms are of the same type. 

Assuming they are fine, it is possible that the burn went badly. Try burning again, but at the lowest possible speed. 

You cannot 'upgrade' back to 8.04.

One option you do have, is to install the 8.10 apply all updates, then upgrade to 9.04.

---

### Post by redjeep0 on 2009-04-29
I have a working WinXP PC that I am writing this on.  It has a CDRom, and I'm burning CD ISO's.  I checked the MD5SUM hashes for the .iso downloads, and they are correct for both 9.04 and 8.04 disks.

The Ubuntu PC has a DVDROM, so all should be readable.

I understand that I'm going to 'downgrade' and not 'upgrade,' I just need a mechanism for accomplishing it.  likewise with the 9.10 upgrade, since the CD install isn't working.

At this point, I'm happy with a fresh install.  There was nothing critical on the PC.

Thanks again.

---

### Post by oOarthurOo on 2009-04-29
Yes, I was aware that you wanted to 'downgrade', but that's not possible. To go down, you have to fresh install. To go up you can upgrade or fresh install.

I have encountered cheap cds that work fine on my ubuntu laptop and not at all on my brother's mac. You never mentioned if they were all the same type. E.g., CD-R's might not work, even though CD+RW do. Hardware can sometimes be quirky.

---

### Post by redjeep0 on 2009-04-29
I hadn't considered the optical drive not recognizing the data, but good idea. 
Both 8.04 and 9.04 CDs are readable on this machine (the one that burned them).
can I apt-get update to the 9.04 release from terminal?

---

### Post by kansasnoob on 2009-04-29
Post the output of:

```
cat /etc/issue
```

---

### Post by skeetre on 2009-04-29
Have you tried booting the computer you're on, the one you burned the cd with to make sure -it- can boot from the cd? If it boots from the cd and the other computer is set to boot from cd and isn't, then it must not be able to read that type of cd. You could switch your graphics to vesa or nv instead of the nvidia driver. Since you can boot up and get a terminal.  It doesn't give you the option to reconfigure your graphics for gdm since it can't start with the Nvidia driver?

Try from a terminal removing the nvidia driver and reconfiguring x. 

# sudo apt-get purge nvidia*
# sudo dpkg-reconfigure xserver-xorg

And then you might get into 8.10 and be able to continue to upgrade to 9.04 if you want.

---

### Post by redjeep0 on 2009-04-29
I'd be happy to post the output, but I haven't done that before.  Can you tell me how to do it?
Is there an easy way to copy the output from that file to a different machine? or will I need to retype?

---

### Post by redjeep0 on 2009-04-29
ugh.  ubuntu box now hanging at Checking battery state.
I have a ton of tabs still open on this pc, and have been reluctant to reboot.
I do have a boot from CD for the 9.04 iso loading successfully on a laptop, however.

---

### Post by skeetre on 2009-04-29
Have you tried uninstalling the nvidia drivers and/or reconfiguring the xserver-xorg? I've had problems in the past where I couldn't start x and I reconfigured the xserver and got in with the standard vesa driver. Or... you can reboot and in the grub menu, edit the kernel line and add to the end: xforcevesa and see if that forces X to load the vesa driver.

---

### Post by redjeep0 on 2009-04-29
I have tried uninstalling the nvidia drives and reconfiguring the xserver-org, but this didn't work.  (I can't remember if I ran across an error with this.  I'll try again as soon as I get past the battery hang.)

---

### Post by redjeep0 on 2009-04-29
The 8.10 upgrade, I downloaded using synaptic from my 8.04 environment.
Everytime I go to recovery (esc key during grub loading), my options are all 8.10, implying to me that my CD drive is not even being looked at for boot?
Concurrently, I've just made a USB bootable 9.04, but, even though my bios settings are to load usb-fdd and usb-zip before cd-rom, it's still booting into 8.10
Arrrgghhh...

---

### Post by oOarthurOo on 2009-04-29
> I do have a boot from CD for the 9.04 iso loading successfully on a laptop, however.

I'd boot from the cd, test it for errors, and install it.

---

### Post by skeetre on 2009-04-29
Ok... do you have an option like F8 or F10 or F12 or something to get a boot menu during boot up? So you can select from cdrom, usb, hd, etc?  If not, in your bios does your usb device show up as a hard drive, or in the boot order? Sometimes if you go to the boot order and or ide configuration you can change the hd to the usb drive.

2nd thing... when you hit escape to show the grub menu for 8.10
Can you hit 'e' to edit the kernel line and append to the end of it, "xforcevesa" and then boot? 

I'm not sure what the battery hang thing is, never heard of that. If it's a laptop that's plugged in, just remove the battery temporarily?

---

### Post by redjeep0 on 2009-04-29
Agreed, however, as far as I can tell, all of the boots are coming from the 8.10 upgrade I downloaded, even though I have the CD in the drive.

Currently, I'm trying to boot with the original 8.04.1 CD that I made months ago when I started using ubuntu on the PC (I had loaned it to a neighbor and now have it back).  

I removed the IDE hard drive with the 8.10 upgrade from BIOS (I have other SATA drives).

My BIOS seems to be hung @ Boot from CD, as if it's not reading the drive correctly.  

Perhaps my CD drive is dead, and that's been causing the problem all along...the BIOS recognizes it correctly....  

Is there a BIOS check I can do to ensure the drive is working?

---

### Post by skeetre on 2009-04-29
not that I'm aware of. Do you have any other cd's you can try in it? We have a lot of dead cd drives here at work... but I've used canned air to blow in some of them to bring them back to life.

---

### Post by redjeep0 on 2009-04-29
Good Idea.  I'll try some old Windows install CDs.
also, about to go out for dinner, and I can pick up some canned air.

---

### Post by redjeep0 on 2009-04-30
Wow, I've spent days checking everything but the DVD drive itself.  I bought a new drive at BestBuy, but I didn't have SATA power cables, so I cannibalized an old machine's CD drive and voila! the 8.04 distro CD loaded right up.  I'm trying the 9.04 CD now (I'm gonna try this before going back to 8.04)

Thanks for the help so far!

---

