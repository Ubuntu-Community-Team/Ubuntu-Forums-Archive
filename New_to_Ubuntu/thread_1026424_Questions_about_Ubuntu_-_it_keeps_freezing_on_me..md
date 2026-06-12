---
title: "Questions about Ubuntu - it keeps freezing on me."
date: 2008-12-31
forum: New to Ubuntu
---

### Post by toastface5 on 2008-12-31
Hello, this is my first post on this forum.  Anyway, down to the question.  I have installed Ubuntu over my Windows XP.  I open any window on the system - whether it be Appearance, Add/Remove Program etc.  It just freezes!  The cursor still works andmoves around, but the screen is frozen and nothing is clickable.

(By the way, I do NOT know my comp's specs).

Is this down to my specs or the fact there is no internet on there yet?  If none of these, then what as I really want to get to use Ubuntu.  (please note, I have lost my XP disc in case you suggest to reinstall XP).

Many thanks in advance.

---

### Post by bailbath on 2008-12-31
I would try to reinstall. Check everything twice as you install. If you are using a live disc does that work fine? How old is the pc?
Ian

---

### Post by Michael.Godawski on 2008-12-31
> **toastface5 said:**
> Hello, this is my first post on this forum.  Anyway, down to the question.  I have installed Ubuntu over my Windows XP.  I open any window on the system - whether it be Appearance, Add/Remove Program etc.  It just freezes!  The cursor still works andmoves around, but the screen is frozen and nothing is clickable.

(By the way, I do NOT know my comp's specs).

Is this down to my specs or the fact there is no internet on there yet?  If none of these, then what as I really want to get to use Ubuntu.  (please note, I have lost my XP disc in case you suggest to reinstall XP).

Many thanks in advance.

hi, 
this is a tough one :D. You don't know your specs, we don't know your specs.

What version of Ubuntu have you installed?
Did the installation finished successfully? Any errors?

Did you checked the CD for defects, prior the installation?

Do you installed Ubuntu over Windows, completely deleting it, or "just" doing a dual-boot?

---

### Post by sadaruwan12 on 2008-12-31
> Hello, this is my first post on this forum. Anyway, down to the question. I have installed Ubuntu over my Windows XP. I open any window on the system - whether it be Appearance, Add/Remove Program etc. It just freezes! The cursor still works andmoves around, but the screen is frozen and nothing is clickable.

(By the way, I do NOT know my comp's specs).

Is this down to my specs or the fact there is no internet on there yet? If none of these, then what as I really want to get to use Ubuntu. (please note, I have lost my XP disc in case you suggest to reinstall XP).


This kind of a problem is very rare in Ubuntu 'cos it's a very stable release. I would love to help but I need to know some more thing like what version of Ubuntu you've installed and is it downloaded one from the Ubuntu ftp servers. Please tell me these things I might be able to help you. :D

---

### Post by toastface5 on 2008-12-31
> **sadaruwan12 said:**
> This kind of a problem is very rare in Ubuntu 'cos it's a very stable release. I would love to help but I need to know some more thing like what version of Ubuntu you've installed and is it downloaded one from the Ubuntu ftp servers. Please tell me these things I might be able to help you. :D

Hello, well, I downloaded the .iso from the ubuntu site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I downloaded the desktop edition under 32Bit.

And No, I didn't check the CD for defects at the start of installation.  I also didn't get any error messages during installation.

---

### Post by lcpltyler on 2008-12-31
I had a problem when I changed my login screen theme and it would not load. 
For those who have this problem, this is the way I fixed it.
alt control F1
logged in by text command then I
sudo killall gdm
followed by
startx 
then I got a funky screen with a X on it
then it took me to my desktop 
I didnt mess with anything but when straight to the terminal and 
sudo gdm 
got a blue screen telling me that the display was already 
in use an to use alt control F7 or higher so I then 
alt control F7
it took me back to my desktop I believe (the steps are getting jumblelie for writing them)
then I when to 
System>admin> Login window
and then i was able to change it back to the Human theme and login after i rebooted.
I had to reinstate my graffics card after words but every thing was normal after that.

---

### Post by sadaruwan12 on 2008-12-31
> I downloaded the .iso from the ubuntu site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

OK, good can you use the terminal or is it freezers too.

If you can just enter this code,

```
lsb_release -a
```

and you could see what version you're using and tell me if can't Please reply I'll try to do some thing.

> I didn't check the CD for defects at the start of installation

It's always recommended to check downloaded CD images after burning them 'cos they some times tend to get corrupted and do you have a internet connection there where you're using your Ubuntu PC. And could you please tell me the perches date or the manufactured date even so I could do some thing and Please do reply.

---

### Post by bailbath on 2008-12-31
> **toastface5 said:**
> Hello, well, I downloaded the .iso from the ubuntu site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I downloaded the desktop edition under 32Bit.

And No, I didn't check the CD for defects at the start of installation.  I also didn't get any error messages during installation.
 So did it work with the live cd ok? How old is the pc. Did you have any problems when you ran XP?
Ian

---

### Post by theinnercityhippy on 2008-12-31
It is possible that this is a hardware fault, possibly the fan not cooling the processor adeuately for some reason. can you post the output of

$:> dmesg

---

### Post by toastface5 on 2008-12-31
> **sadaruwan12 said:**
> OK, good can you use the terminal or is it freezers too.

If you can just enter this code,

```
lsb_release -a
```

and you could see what version you're using and tell me if can't Please reply I'll try to do some thing.



It's always recommended to check downloaded CD images after burning them 'cos they some times tend to get corrupted and do you have a internet connection there where you're using your Ubuntu PC. And could you please tell me the perches date or the manufactured date even so I could do some thing and Please do reply.

It is Release 8.10.

And no, I do not have an internet connection on my Ubuntu PC - I am doing this on my dad's XP Laptop next to my PC.

Oh and while writing this, I tried to move the Terminal Window and it froze again...

Sorry, I do not know the purchase date or Manufacture date, do you know where I could find these out?

---

### Post by Michael.Godawski on 2008-12-31
If your dad laptop has a decent Internet connections download the alternate installer and do a fresh install on your machine.

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

If you install it again, and again encounter these freezes there is probably either a hardware issue (corrupt ram, or dont know what), or a compatibility issue with you graphic card or the drives.

It is really difficult to explain such freezes without any hints in form of error messages or additional info.

Can you boot into the recovery mode? If yes try to run these commands there:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

```
dmesg
sudo lshw
```These will give us some more info about your booting process and your hardware.

---

### Post by toastface5 on 2008-12-31
> **bailbath said:**
> So did it work with the live cd ok? How old is the pc. Did you have any problems when you ran XP?
Ian

No I didn't have any problems with the Live CD OR XP.

---

### Post by toastface5 on 2008-12-31
> **Michael.Godawski said:**
> If your dad laptop has a decent Internet connections download the alternate installer and do a fresh install on your machine.

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

If you install it again, and again encounter these freezes there is probably either a hardware issue (corrupt ram, or dont know what), or a compatibility issue with you graphic card or the drives.

It is really difficult to explain such freezes without any hints in form of error messages or additional info.

Can you boot into the recovery mode? If yes try to run these commands there:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

```
dmesg
sudo lshw
```These will give us some more info about your booting process and your hardware.

About the alternate installer, is there a way to get it without torrents?  If so can you link me to that as I don't have a torrent program.

Thanks in advance

---

### Post by Michael.Godawski on 2008-12-31
When you go o my site ( the link posted above)

[LIST]
[*][http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)
[/LIST]
and go to the advanced download site, you will find also a server download of the alternate CD.


[LIST]
[*][http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)
[/LIST]

---

### Post by toastface5 on 2008-12-31
> **Michael.Godawski said:**
> When you go o my site ( the link posted above)

[LIST]
[*][http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)
[/LIST]
and go to the advanced download site, you will find also a server download of the alternate CD.


[LIST]
[*][http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)
[/LIST]

Well, the Alternative download is half way through downloading.

Hope this works!

---

### Post by sadaruwan12 on 2008-12-31
> Well, the Alternative download is half way through downloading.

Hope this works!

Hi,

Did your new download work?. Actually this kinda of freezing happens when the processor or the GPU (Graphical Processor Unit) can't handle graphics or can't process it correctly and the other thing is that you're using the latest version of Ubuntu that is Intrepid Ibex but with this version I personally had few problems. But I recommend you to go for an LTS(Long Term Support) version the latest one of that is version 8.04 known as Hardy Haron. Some people might tell you that it's better to go for the latest version but I recommend LTS versions 'cos they are more stable than the earlies new release. Normally in the world of Linux the saying "Old is Glod" is very true. And another thing if you're planning to use Ubuntu as your default OS on your dads laptop it's advised to hook it up to the net other wise you will run into some problems when you try to install new programs. From your posts I think you're a Windows user for a long time it's OK I'm my self a Windows user that made the transformation and Linux is a very easy and stable OS than windows due to the frequent updates.

And I think the problem is with your GPU or the VGA card so try to use the default settings that get configured when you install Ubuntu. If you were able to get Ubuntu working please update it then you'll get it to become more stable and efficient. Please tell me if your new one installation is working or not.

---

### Post by toastface5 on 2008-12-31
> **sadaruwan12 said:**
> Hi,

Did your new download work?. Actually this kinda of freezing happens when the processor or the GPU (Graphical Processor Unit) can't handle graphics or can't process it correctly and the other thing is that you're using the latest version of Ubuntu that is Intrepid Ibex but with this version I personally had few problems. But I recommend you to go for an LTS(Long Term Support) version the latest one of that is version 8.04 known as Hardy Haron. Some people might tell you that it's better to go for the latest version but I recommend LTS versions 'cos they are more stable than the earlies new release. Normally in the world of Linux the saying "Old is Glod" is very true. And another thing if you're planning to use Ubuntu as your default OS on your dads laptop it's advised to hook it up to the net other wise you will run into some problems when you try to install new programs. From your posts I think you're a Windows user for a long time it's OK I'm my self a Windows user that made the transformation and Linux is a very easy and stable OS than windows due to the frequent updates.

And I think the problem is with your GPU or the VGA card so try to use the default settings that get configured when you install Ubuntu. If you were able to get Ubuntu working please update it then you'll get it to become more stable and efficient. Please tell me if your new one installation is working or not.

Hi,

Points to make:
1)  I am not installing it on my dads laptop I am installing it on my old XP comp.
2) I do not particularly like Windows OS - I am more of a Unix fan - because I have a Mac in my bedroom, and love it to bits.  I just wanted to get rid of my XP and put Ubuntu over it.  Oh and the download still isn't complete of the Ubuntu Alternate Installer, it has 53 minutes to go, apparently, having done 75% of it.  (my download speed at the moment is roughly 60KB/S)  :(

It takes me about 3.5 hours to download the Ubunto .iso file :(

I'll let you know how it goes when I have burnt it on a CD and installed.

Also, if this still fails, I'll try the LTS version.

Thanks for all this help!

---

### Post by sadaruwan12 on 2008-12-31
> I am not installing it on my dads laptop I am installing it on my old XP comp.

I'm sorry for my undestanding.

---

### Post by albinootje on 2008-12-31
> **toastface5 said:**
>  Oh and while writing this, I tried to move the Terminal Window and it froze again... 

Can you post the output of :
```

lspci
sudo fdisk -l
cat /proc/cpuinfo
free -m

```

Copy and paste that into a text file on an usb-stick if possible.
If it freezes again, please boot with these parameters :
```

noapic nolapic

```

1) Hit escape to see the boot menu (Grub).
2) Press e of edit
3) Press arrow down once to move to the second line
4) Press e of edit again
5) Press spacebar once
6) Fill in at the end :  

noapic nolapic

6) Press <enter> key
7) Press b to boot

Please report back whether that helps.

Also turning off "visual effects" could help to find out what the problem is.
-> System -> Preferences -> Appearance -> Visual Effects -> None

---

### Post by albinootje on 2008-12-31
> **toastface5 said:**
> 
It takes me about 3.5 hours to download the Ubunto .iso file :(


Imho the suggestion to starting burning new installation cdroms do not really make much sense.
You did install Ubuntu, and you do have a desktop running, no ?
The problem is with the freezing, which can be a powermanagement problem, an irq conflict problem, a filesystem problem, a videocard driver problem, but I think it's less unlikely to be because your installation cdrom was not OK.

---

### Post by toastface5 on 2008-12-31
> **albinootje said:**
> Imho the suggestion to starting burning new installation cdroms do not really make much sense.
You did install Ubuntu, and you do have a desktop running, no ?
The problem is with the freezing, which can be a powermanagement problem, an irq conflict problem, a filesystem problem, a videocard driver problem, but I think it's less unlikely to be because your installation cdrom was not OK.

That's why I was downloading the alternative Installer, to see if it made a difference.  Iwill try your method (noapic nolapic) and see if that helps.  I will report back when done.

---

### Post by albinootje on 2008-12-31
> **toastface5 said:**
> That's why I was downloading the alternative Installer, to see if it made a difference.  Iwill try your method (noapic nolapic) and see if that helps.  I will report back when done.

See also the other boot parameters suggestion here :
[http://ubuntuforums.org/showthread.php?t=1023990](http://ubuntuforums.org/showthread.php?t=1023990)

---

### Post by zero244 on 2008-12-31
Im not using a laptop. But this machine does not like apic enabled on boot up.
This machine will freeze randomly unless I put this line at the end of my Kernel line in grubs menu.lst
APIC=off
After doing this the computer freezes instantly went away.
Ive had to do this since Edgy.
Or you can try turning off apic on your motherboard and see if that stops your freezes.
When you turn off apic on your motherboard Ubuntu might not shutdown correctly. In other words the OS will shutdown but it may not turn your computer off.

Also try looking in your logs you might see something there to give you a clue.
Good luck.

---

### Post by albinootje on 2008-12-31
> **zero244 said:**
> Im not using a laptop. But this machine does not like apic enabled on boot up.
This machine will freeze randomly unless I put this line at the end of my Kernel line in grubs menu.lst
APIC=off
After doing this the computer freezes instantly went away.
Ive had to do this since Edgy. 
See for a little bit more info here :
[http://wiki.linuxquestions.org/wiki/APIC](http://wiki.linuxquestions.org/wiki/APIC)

---

### Post by duds2008 on 2008-12-31
Have you tried disabling acpi at boot? Is it a laptop or tower? If a laptop perhaps try pass the "vga=771" boot parameter. Or you could try both i.e: acpi=off noapic (NOT nolapic) vga=771. Good luck.

---

