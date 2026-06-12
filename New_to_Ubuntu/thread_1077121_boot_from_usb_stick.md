---
title: "boot from usb stick"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by fredfelter on 2009-02-22
I have done a rather extensive search and can't seem to find the solution to this important issue:

There are numerous references on how to make a bootable version of Ubuntu on a USB flash drive. I used the live CD of ver. 8.10 to do that, seemingly without a hitch. When I try to boot from it I get "Could not find kernal image: Linux boot:_. This on 2 different computers.

So I downloaded Crunchbag linux to a flash drive using the appropriate instructions. Same result!

I can find no definitive fix to this problem although I see many people asking the same question. Why is this so arcane?

Thanks for any  help.

---

### Post by theozzlives on 2009-02-22
Did you try the pendrivelinux version? Some brands of USB won't boot. My 8 GB SanDisk & my 2 GB Verbatum will, but a 128 MB I got from school won't boot Damn Small Linux, or Puppy Linux for the life of me.

---

### Post by fredfelter on 2009-02-22
> **theozzlives said:**
> Did you try the pendrivelinux version? Some brands of USB won't boot. My 8 GB SanDisk & my 2 GB Verbatum will, but a 128 MB I got from school won't boot Damn Small Linux, or Puppy Linux for the life of me.

So you think a version I would get from pendrivelinux would be different from from the one off the 8.10 CD? The other thing is that this USB stick works fine with both computers in other respects so I can´t see how that could be the issue, but then Linux keeps on presenting me with new conundrums.

---

### Post by theozzlives on 2009-02-23
put your 8.10 CD in and boot from it, open a terminal and type:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
```
chmod +x u810.sh && sh u810.sh
```
follow the prompts after that, oh, make sure your drive is in.

---

### Post by djneve on 2009-02-23
Thank you so much for this solution.  I didn't write the original question but I COULD HAVE, word for word.

My little Kingston Traveller 8 Gb USB stick will NOT boot, no matter what I do, neither here on my laptop nor anywhere else around here.  I used the little program in 8.10 to prepare it and I tried your advice above.

What happened now is that I got error messages from the terminal output and now I have TWO partitions on the stick sdb1 and sdb2 although I only gave "1" as an answer to the prompt.

Any help greatly appreciated!

Very new ubuntu user

---

### Post by fredfelter on 2009-02-23
> **djneve said:**
> Thank you so much for this solution.  I didn't write the original question but I COULD HAVE, word for word.

My little Kingston Traveller 8 Gb USB stick will NOT boot, no matter what I do, neither here on my laptop nor anywhere else around here.  I used the little program in 8.10 to prepare it and I tried your advice above.

What happened now is that I got error messages from the terminal output and now I have TWO partitions on the stick sdb1 and sdb2 although I only gave "1" as an answer to the prompt.

Any help greatly appreciated!

Very new ubuntu user

So DJNeve, it appears the solution offered by Theozzlives still is not the answer. I write this to keep the thread open as I am sure there are very many users experiencing the same frustration of being promised a USB bootable Ubuntu but only to have their hopes dashed by the reality of Linux.

---

### Post by djneve on 2009-02-24
> **fredfelter said:**
> So DJNeve, it appears the solution offered by Theozzlives still is not the answer. I write this to keep the thread open as I am sure there are very many users experiencing the same frustration of being promised a USB bootable Ubuntu but only to have their hopes dashed by the reality of Linux.

That describes me exactly!  So what IS the answer?  If it works for so many others, why not me? :)

Especially as I think this would be the ideal thing for my daily usage between laptop at home and office machine.

Derrick

---

### Post by theozzlives on 2009-02-24
I've heard tell that some brands won't boot. I've got a 128 MB that I can't boot Damn Small Linux for the life of me. My SanDisk 8 GB and Verbatum 2 GB work fine with the solution I provided.

---

### Post by djneve on 2009-02-24
> **theozzlives said:**
> I've heard tell that some brands won't boot. I've got a 128 MB that I can't boot Damn Small Linux for the life of me. My SanDisk 8 GB and Verbatum 2 GB work fine with the solution I provided.

Say, I've got an idea: has ANYBODY got a stick just like mine and made it work? :)

I have a Kingston DataTraveler 8 GB stick, brand new when I started but who knows what I've done to it by now by trying scripts, USB-maker programs, and gParted!  I've tried on a live boot, and on my regular laptop boot.  I've tried 8.04 (just this afternoon) but it's the same result as 8.10.

Just don't understand it!

Derrick

---

### Post by gandaran on 2009-02-24
> **djneve said:**
> Say, I've got an idea: has ANYBODY got a stick just like mine and made it work? :)

I have a Kingston DataTraveler 8 GB stick, brand new when I started but who knows what I've done to it by now by trying scripts, USB-maker programs, and gParted!  I've tried on a live boot, and on my regular laptop boot.  I've tried 8.04 (just this afternoon) but it's the same result as 8.10.

Just don't understand it!

Derrick
is your computer able to boot usb drives? (check bios) I too have a Kingston 4GB stick and no way can I make my box boot usb!

---

### Post by furialis on 2009-02-24
I used remastersys to make a liveCD of my system. Then set my bios to boot from CD > USBHDD > HDD and unplugged the HD and restarted with the USB stick and the livecd in. I installed to the USB and plugged my HD back in. Works great.

---

### Post by djneve on 2009-02-24
> **gandaran said:**
> is your computer able to boot usb drives? (check bios) I too have a Kingston 4GB stick and no way can I make my box boot usb!

Yes, the BIOS shows four different options for booting off USB sticks.  I have it set now to boot off USB first, CD second, then notebook drive third.  So it should work (it's a new hp laptop) but I've never been able to get it to.  Is there a different distro that I could try just to confirm the thing DOES boot?

Derrick

(Thanks for your help!)

---

### Post by Miljet on 2009-02-24
Have you tried reformating the pen drive with the option to make it boot-able?  I may be wrong but I think that if it is formatted as a data disk, no space is reserved for a master boot record, in which case the BIOS will not see it as a boot-able device.

---

### Post by theozzlives on 2009-02-24
Use gparted, delete both partitions, make a FAT32 partition and it'll be like new again. I did that with my 8 GB cause it was too big for my purposes. My 2 GB is fine. Sounds like you got one of those with a built-in program that runs under Windows (I forget what it's called). I put my SanDisk Cruiser in Windows and it gave me the option to delete that program.

---

### Post by fredfelter on 2009-02-24
> **gandaran said:**
> is your computer able to boot usb drives? (check bios) I too have a Kingston 4GB stick and no way can I make my box boot usb!

Yup; 2 of them but on neither will the Ubuntu install open.

---

### Post by fredfelter on 2009-02-24
I GOT IT!!! at least for my system.

Turns out that the usb bootable Ubuntu that I built from the 8.10 CD will boot only in Linux. See this: < [http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems](http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems) > Look at Ubuntu Live USB Creator - "runs only on Linux". I was trying to boot it on a Windows based machine.

Solution that works: Use UNetbootin like this: < [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) > So I downloaded the iso version of Crunchbang to my DT, opened UNetbootin > directed it to the iso > directed it to the already plugged in and formatted usb drive > OK > and within a few minutes it did the deed. Then I told it to reboot my computer > hit F12 on the bootup > selected the USB option > and up came a gorgeous version of Linux.

Hope this helps. Sorry about the links - the hyperlink function here doesn't open for me.

---

### Post by fredfelter on 2009-02-25
Addendum.
The news is not as good as I had hoped. Turns out that the UNetbootin version is not "persistent", that is it doesn't retain setting after it is shut down. That, to me, is a fatal flaw and I'm still searching for a workable persistent distro that I can boot from a Windows machine (I haven't managed to get the Ubuntu one to save on shutdown).

---

