---
title: "Grub, deleting Ubuntu"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by pathfindermwd on 2010-01-11
Hi all.  

New to all this and not super computer savy.  I installed Ubuntu to my netbook and have lost my boot ladder.  All I get is "Grub loading".

I think I need to install a usb grub.  I did download it from here: 

[http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7)

I unzipped it to the USB but that's about the extent of my ability (so far).
I simply don't fully understand the instructions!

Once I can recover my boot ladder I think I need to uninstall Ubuntu.  I don't need it on the HDD because I have a USB version (I should have left it alone at).

Please comment on Grub in plain english for me, and how to uninstall Ubuntu.

---

### Post by Jackzor on 2010-01-11
Well, What exactly do you want to do here? Get ubuntu to work or get rid of it?

---

### Post by philinux on 2010-01-11
> **pathfindermwd said:**
> Hi all.  

New to all this and not super computer savy.  I installed Ubuntu to my netbook and have lost my boot ladder.  All I get is "Grub loading".

I think I need to install a usb grub.  I did download it from here: 

[http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7)

I unzipped it to the USB but that's about the extent of my ability (so far).
I simply don't fully understand the instructions!

Once I can recover my boot ladder I think I need to uninstall Ubuntu.  I don't need it on the HDD because I have a USB version (I should have left it alone at).

Please comment on Grub in plain english for me, and how to uninstall Ubuntu.

The website has the instructions. I'm afraid you'll have to read and follow them.
[http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).

---

### Post by kayvortex on 2010-01-11
Hopefully some more info will help solve your problem: can you tell me exactly what happens when you start your netbook up (all the message that come up, and especially GRUB and any error messages), and what is different now than what happened before when your system was OK. What operating systems were on the netbook before? Vista? Windows 7? Could you also tell me exactly what you did that caused the problem (i.e. did you put a LiveCD in and select "Install"?).

Probably, I'll still need to ask you more questions before you start to do anything so that I know exactly what is/went wrong; so be patient with me.

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> Well, What exactly do you want to do here? Get ubuntu to work or get rid of it?

Hi Jackzor

Well first I love Ubuntu, and am really excited about a departure from being reliant on windoze.  Thanks to all you Linux producers, and supporters here.

My USB OS works great, I was just playing around to see if a HDD application would be faster.  I am sold enough on the security of Linux that I felt there would probably be no downside to installing it to the HDD.  But, this is a windows 7 netbook.  On Harware/Install forum a guy there is talking about how you cant install both 7 and ubuntu on a machine, and I  found out the hard way!

I still want to be able to use windows 7 for whatever few applications I use there.  If it means I have to delete Ubuntu and just use my Live USB, I'm ok with that.

---

### Post by Jackzor on 2010-01-11
So you want to just remove ubuntu and run the usb? Can you still boot to windows?

Edit:

I think I see what you need done here. What you want is to restore the windows boot loader?

If thats what you need then you need to repair your installation of windows 7 with your repair disc.

Do you have a repair disc or the installer disc?

---

### Post by pathfindermwd on 2010-01-11
> **kayvortex said:**
> Hopefully some more info will help solve your problem: can you tell me exactly what happens when you start your netbook up (all the message that come up, and especially GRUB and any error messages), and what is different now than what happened before when your system was OK. What operating systems were on the netbook before? Vista? Windows 7? Could you also tell me exactly what you did that caused the problem (i.e. did you put a LiveCD in and select "Install"?).

Probably, I'll still need to ask you more questions before you start to do anything so that I know exactly what is/went wrong; so be patient with me.


Hi kayvortex.  I have a emachines netbook with 250 gig hard drive.  Brand new, nothing loaded but windows 7.  I  had just made myself an Ubuntu Karmic Koala 9.10 USB 4 gig persistent.  I used it a few times, got on the internet, was enjoying it.  But i wanted to see how it worked on a hard drive.  So, on the Ubuntu boot screen I chose to instal Ubuntu.  I followed the steps basically splitting the hard drive in half at the partition window.

Ubuntu installed fine, though I couldnt get the wireless driver to install.  After a few reboots I decided to set aside the problem and load windows 7.

When I went to load windows 7 at the boot screen (which gives options on what os to load)  it wouldnt load windows 7, it just brought me back, so I loaded vista (listed).  Then it made me do a full windows recovery!

Windows 7 fully recovered and rebooted for the final time and then...nothing would boot.  All I get is the Emachines logo and it flashes "Grub loading" and the repeats this process.

:confused:

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> So you want to just remove ubuntu and run the usb? Can you still boot to windows?

Edit:

I think I see what you need done here. What you want is to restore the windows boot loader?

If thats what you need then you need to repair your installation of windows 7 with your repair disc.

Do you have a repair disc or the installer disc?


There isnt one.  There isnt an optical drive.  i was considering trying to backup windows 7 to an external hdd, but never did get to looking how to do that.

---

### Post by ajgreeny on 2010-01-11
> **Jackzor said:**
> So you want to just remove ubuntu and run the usb? Can you still boot to windows?

Edit:

I think I see what you need done here. What you want is to restore the windows boot loader?

If thats what you need then you need to repair your installation of windows 7 with your repair disc.

Do you have a repair disc or the installer disc?
If you can get supergrub to run on the usb drive that you mentioned earlier, you can use that to repair the windows bootloader, as well as repair grub, if needed.  Supergrub is a very useful tool to have available at any time, but I have no personal experience or knowledge of how to use it on a usb drive, so can't help you with that;  you will need to get all that from the supergrub site.

---

### Post by pathfindermwd on 2010-01-11
> **philinux said:**
> The website has the instructions. I'm afraid you'll have to read and follow them.
[http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).



I am sorry i am so dumb with this, and need some hand holding.  I got myself into this by trying to do more than I really knew how to do.  At least i try, right?

---

### Post by Jackzor on 2010-01-11
> **pathfindermwd said:**
> I am sorry i am so dumb with this, and need some hand holding.  I got myself into this by trying to do more than I really knew how to do.  At least i try, right?

Just give me a little while. I'm doing my best to figure this out for you.

---

### Post by Jackzor on 2010-01-11
Which OS do you have? 

Windows 7 Starter

Windows 7 Home Premium

Windows 7 Professional

Windows 7 Ultimate

Which is it?

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> Which OS do you have? 

Windows 7 Starter

Windows 7 Home Premium

Windows 7 Professional

Windows 7 Ultimate

Which is it?


Windows 7 starter

---

### Post by Jackzor on 2010-01-11
Okay. best thing I can find is installing the recovery disc onto a usb drive. Do you have access to another computer? (doesn't matter if it has an optical drive)

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> So you want to just remove ubuntu and run the usb? Can you still boot to windows?

Edit:

I think I see what you need done here. What you want is to restore the windows boot loader?

If thats what you need then you need to repair your installation of windows 7 with your repair disc.

Do you have a repair disc or the installer disc?







Yes, I mean the boot loader, sorry, lol!  The boot ladder is in the bios and I can f2 to that fine.

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> Okay. best thing I can find is installing the recovery disc onto a usb drive. Do you have access to another computer? (doesn't matter if it has an optical drive)

Yes, I have my xp laptop I am using now, with my Ubuntu USB.  It's fully functional.

---

### Post by Jackzor on 2010-01-11
Okay well lets start here:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Pick whether you have 32bit or 64

And download




Then go here [http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key?page=0%2C1](http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key?page=0%2C1)


post back when you have it on a usb drive



Edit: Just so you know. I have never had to do this before, I'm doing the best I can searching on google.

So if this doesn't work don't give up. We will get this figured out.

---

### Post by kayvortex on 2010-01-11
> When I went to load windows 7 at the boot screen (which gives options on what os to load) it wouldnt load windows 7, it just brought me back, so I loaded vista (listed). Then it made me do a full windows recovery!

Didn't you say that you only had windows 7 on it? Exactly what options did the GRUB screen show?

It's possible to restore your Windows bootloader off a USB stick (I think Trinity Rescue Kit can do it); but, first, I want to make sure that you didn't ruin your Windows install during the partition phase of the installation. Can you put the Ubuntu USB stick in and boot off that. If you can, I want you to mount your partitions and check the files are still there. If you open up a terminal (if you manage to get Ubuntu booted off the USB) and then type:
```
sudo fdisk -l
```
Post what comes up and I'll explain what to do next.


Edit: you can follow *Jackzor's* steps to recover your system, but I'd advise you to check whether your Windows installation is OK first just in case. It's not strictly necessary, though.

---

### Post by pathfindermwd on 2010-01-11
> **Jackzor said:**
> Okay well lets start here:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Pick whether you have 32bit or 64

And download




Then go here [http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key?page=0%2C1](http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key?page=0%2C1)


post back when you have it on a usb drive




Edit: Just so you know. I have never had to do this before, I'm doing the best I can searching on google.

So if this doesn't work don't give up. We will get this figured out.


Jackzor do I need to be reboot into windows to work with this/these file or can I do it fine from Ubuntu (currently)

---

### Post by Jackzor on 2010-01-11
> **pathfindermwd said:**
> Jackzor do I need to be reboot into windows to work with this/these file or can I do it fine from Ubuntu (currently)

The way that I was having you do it was through windows. I didn't know that you have another ubuntu install running. But honestly I would do it through windows Because I'm sure that you have a much better understanding of windows.

---

### Post by pathfindermwd on 2010-01-11
Everyone, Jackzor, thanks for all the help.  I got lucky and found a friend locally who looked at it and got it straightened out, using the same approach you discussed Jackzor.



Thanks again!

---

### Post by Jackzor on 2010-01-11
Congratz

---

