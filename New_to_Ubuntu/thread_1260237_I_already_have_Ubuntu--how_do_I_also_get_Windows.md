---
title: "I already have Ubuntu--how do I also get Windows?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by sjul on 2009-09-07
Hi everyone--I'm looking for some guidance.  

I have Ubuntu running on a Dell Inspiron (one of the ones Dell sold with out-of-the-box Ubuntu installed on them).  I'm now in school, and I need to be able to use Microsoft Office for a class that's specifically about PowerPoint (ugh, I know).  As well as I can figure, there are a few options:

* partition the hard drive and install Windows (although I gather that this can erase Ubuntu and require me to re-install Ubuntu?)

* install Windows on my external hard drive and use it from there

* do some kind of WINE work-around

Any ideas about which option would be the most likely to be problem-free for an absolute beginner?   Are there better options I don't know about?

I know next to nothing about this stuff....I'm willing to learn, but I'd rather find out which is the most newbie-friendly option and spend my time learning how to execute that one, instead of spending a lot of time on the most complicated and risky option. 

Thanks, everyone!

---

### Post by ChrT on 2009-09-07
Just put windows on a VM

---

### Post by credobyte on 2009-09-07
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Jazzy_Jeff on 2009-09-07
I would install VirtaualBox on your linux system and install Windows there. If you need usb support get the one from [http://www.virtualbox.org/](http://www.virtualbox.org/). If you don't need the usb function then you can install it from the repositories.

---

### Post by NoaHall on 2009-09-07
Well, you can use open office instead of powerpoint.

But if you must use microsoft(I never have in school, I've always used open source alternatives), then use VirtulBox to install windows. I'd use the ones from the official site, and not the OSE(open source edition) because it doesn't have as many features.

---

### Post by pythonscript on 2009-09-07
VirtualBox would be your best bet, definitely. Partitioning your hard drive would be more work than is necessary, and if you're only going to be using PowerPoint, it'd be a waste of time to keep rebooting every time you need to use powerpoint.

---

### Post by XCan on 2009-09-07
+1 for VirtualBox. Since it's only one class, it will save you some needless reboots.

---

### Post by sjul on 2009-09-07
Oh, great, guys!  I was getting nervous about trying to successfully do a partition.  Virtualbox it is.  Thanks so much!

---

### Post by mejohnsn on 2009-09-07
> **NoaHall said:**
> Well, you can use open office instead of powerpoint.

But if you must use microsoft(I never have in school, I've always used open source alternatives), then use VirtulBox to install windows. I'd use the ones from the official site, and not the OSE(open source edition) because it doesn't have as many features.


Please recall that the OP asked specifically about running Microsoft's Powerpoint, as it is a class requirement.

Now it may very well be true that he could use Open Office instead, but surely you remember how these "class requirments" often are: they may very well insist that it must  be Powerpoint.

Nor is that entirely unreasonable, since Open Office is still not a "drop-in replacement" for Powerpoint. I have seen too many Powerpoint presentations that simply do not render correctly under Open Office, and the commands are different, too.

The Virtual Machine approach others have suggested is workable, but he still has to pay for Windows and Microsoft Office. Or can he get by using WINE instead of Windows, then paying only for MSFT Office?

In any case, it would have been easier if he had first installed Windows and only then Linux on his Dell, since it is impossible to do it the other way around. But apparently that is not an option.

---

### Post by mejohnsn on 2009-09-07
> **sjul said:**
> Oh, great, guys!  I was getting nervous about trying to successfully do a partition.  Virtualbox it is.  Thanks so much!

Well, don't be too nervous about it. But be sure to back up your MBR and IPL before changing the partition. Sometimes it is helpful to display the current partitioning in two or more different tools just to make sure you know what is going on, too. fdisk is a popular tool, but GParted is easier to use.

By all means, WRITE DOWN what the current partitioning is before you change it.

I used 'dd' to backup my MBR and IPL before installing this copy of Ubuntu. The direction at [http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/](http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/) are pretty good, read the man page (type 'man dd' in a Terminal window) to get a better idea of what the options mean.

---

### Post by mike555 on 2009-09-07
Using VM requires a good amount of RAM ,make sure you have enough ......

---

### Post by sjul on 2009-09-07
> **mejohnsn said:**
> Please recall that the OP asked specifically about running Microsoft's Powerpoint, as it is a class requirement.

Now it may very well be true that he could use Open Office instead, but surely you remember how these "class requirments" often are: they may very well insist that it must  be Powerpoint.
.
.
.
The Virtual Machine approach others have suggested is workable, but he still has to pay for Windows and Microsoft Office. Or can he get by using WINE instead of Windows, then paying only for MSFT Office?

I would happily used Open Office, but yes, the prof specifically wants us to use PowerPoint.  And I can get Office/Windows for free through the student package at my university--otherwise, I would be annoyed indeed at having to pay for it just to get PowerPoint. 

Thanks for all the help!

---

### Post by sjul on 2009-09-07
> **mike555 said:**
> Using VM requires a good amount of RAM ,make sure you have enough ......

Does it use a lot while you're using it only, or all the time?

---

### Post by pythonscript on 2009-09-07
VirtualBox will only use the ram while you're using it. If it's not started, it's not taking up the ram.

---

### Post by fela on 2009-09-07
> **Jazzy_Jeff said:**
> I would install VirtaualBox on your linux system and install Windows there. If you need usb support get the one from [http://www.virtualbox.org/](http://www.virtualbox.org/). If you don't need the usb function then you can install it from the repositories.

You'd only ever NEED usb support if you want to use a USB device directly such as a webcam or such.

You can work around using USB flash drives by using virtualbox shared folders.

---

### Post by pythonscript on 2009-09-07
Downloading the version directly from Sun's website will save you the hassle of using VirtualBox shared folders, though, which sometimes suffer pretty major bugs. 

[http://www.virtualbox.org/ticket/313](http://www.virtualbox.org/ticket/313)

---

### Post by pedro3005 on 2009-09-07
I run MS PowerPoint with wine flawlessly. It may be less trouble than booting into a VM. It was also really easy to install it, just using PlayOnLinux.

---

### Post by NoaHall on 2009-09-07
> **mejohnsn said:**
> Please recall that the OP asked specifically about running Microsoft's Powerpoint, as it is a class requirement.

Now it may very well be true that he could use Open Office instead, but surely you remember how these "class requirments" often are: they may very well insist that it must  be Powerpoint.

Nor is that entirely unreasonable, since Open Office is still not a "drop-in replacement" for Powerpoint. I have seen too many Powerpoint presentations that simply do not render correctly under Open Office, and the commands are different, too.

The Virtual Machine approach others have suggested is workable, but he still has to pay for Windows and Microsoft Office. Or can he get by using WINE instead of Windows, then paying only for MSFT Office?

In any case, it would have been easier if he had first installed Windows and only then Linux on his Dell, since it is impossible to do it the other way around. But apparently that is not an option.

First of all - I did note, but I used OpenOffice.org against my teacher's wishes, and I got the highest mark possible.

It is possible to install the other way round, using Super Grub.

---

### Post by fela on 2009-09-07
> **mejohnsn said:**
> In any case, it would have been easier if he had first installed Windows and only then Linux on his Dell, since it is impossible to do it the other way around. But apparently that is not an option.

No, wrong. Just boot up a livecd and replace the windows MBR with the GRUB MBR (using grub ; root (hdx,x) ; setup (hdx) ; quit). Then add a windows entry such as:

title Windows
root (hdx,x)
makeactive
chainloader +1

---

### Post by pythonscript on 2009-09-07
> **pedro3005 said:**
> I run MS PowerPoint with wine flawlessly. It may be less trouble than booting into a VM. It was also really easy to install it, just using PlayOnLinux.

Could you maybe elaborate on this? This really interests me. Did you successfully install Office 2007, or if not, what version did you install? Thanks!

---

### Post by mejohnsn on 2009-09-07
> **fela said:**
> No, wrong. Just boot up a livecd and replace the windows MBR with the GRUB MBR (using grub ; root (hdx,x) ; setup (hdx) ; quit). Then add a windows entry such as:

title Windows
root (hdx,x)
makeactive
chainloader +1

It is presumptuous to say "wrong", when it is you who do not understand how this procedure has failed for so many users. Especially when you did not cover how to INSTALL windows. You only mention how to include it in GRUB.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux) shows examples of some of the difficulties you can get yourself into by installing Linux first, and then Windows. It really is much better to install Windows first, and only then Linux.

---

### Post by mejohnsn on 2009-09-07
> **NoaHall said:**
> First of all - I did note, but I used OpenOffice.org against my teacher's wishes, and I got the highest mark possible.

It is possible to install the other way round, using Super Grub.

Congratulations on the high mark. I am glad to hear the teacher was more flexible than I expected.

As for Super Grub, it is a nice tool, but it does not install Windows for you. Nor does it protect you from the pitfalls. It is still much safer to install Windows first, and only then Linux.

The wording of your original post implied that you do not have Windows installed on your Dell at all. Isn't that the case?

---

### Post by NoaHall on 2009-09-07
Thank you. It was quite easy really, mysql to make database is simple ;) 

Super grub adds windows and linux, and replaces the windows MBR(Master boot record), so you can boot into both. It's a iso file you can download from the website, and burn to disk.
But still, I think you should use virtual box . just make sure you give it enough ram

---

### Post by fela on 2009-09-07
> **mejohnsn said:**
> It is presumptuous to say "wrong", when it is you who do not understand how this procedure has failed for so many users. Especially when you did not cover how to INSTALL windows. You only mention how to include it in GRUB.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux) shows examples of some of the difficulties you can get yourself into by installing Linux first, and then Windows. It really is much better to install Windows first, and only then Linux.

Just because the procedure has failed for many users due to their own mistakes (it is never literally impossible unless the bootloader or something has been hacked, provided they're running a normal PC with Basic Input Output System or Extensible Firmware Interface Read Only Memory on the motherboard, and standards compliant), doesn't mean that it's impossible. Why should it?

And also why should I include how to install windows? I wasn't making a howto, I was just outlining the normal procedure of recovering GRUB to the MBR of your HDD after windows has taken it over with NTLDR or whatever bootloader it uses.

**Just because an ignorant user may run into problems, doesn't mean something's impossible.**

It is a matter of opinion what to install first, sure you don't need to restore grub if you install windows first but you have a working system either way if you know how to do it right.

---

