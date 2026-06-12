---
title: "few virtualbox problems"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-12
i have 2 problems running xp in virtualbox
1. no usb support
2. no sound 

any help would be appreciated

---

### Post by DGortze380 on 2009-03-12
> **mamamia88 said:**
> i have 2 problems running xp in virtualbox
1. no usb support
2. no sound 

any help would be appreciated

Sound - 
In settings, under Audio, click enable audio. Use the Core Audio Driver and the Soundblaster 16 virtual card.

USB - 
In Settings, under Ports, click enable USB Controller. You probably also want to enable USB 2.0. Just click the box.

---

### Post by mamamia88 on 2009-03-12
where are these setting options i can't find them

---

### Post by DGortze380 on 2009-03-12
Open VirtualBox. 
Click on the VM you wish to configure.
Click on the Big Settings Button at the top of the window.

---

### Post by mamamia88 on 2009-03-12
ok i enabled usb but it still won't let me mount my flashdrive and i enabled sound but still no sound

---

### Post by drs305 on 2009-03-12
> **mamamia88 said:**
> where are these setting options i can't find them

At least in the non-OSE version, if you highlight the windows VM you created (left pane), in the "Details" tab on the right side you should see various categories in bold, blue. Double click on "Audio", for instance, and you should be able to select the Audio Host Driver and Controller. Once you start the VM, you may need to install the Soundblaster card from within windows.

---

### Post by howefield on 2009-03-12
> **mamamia88 said:**
> ok i enabled usb but it still won't let me mount my flashdrive and i enabled sound but still no sound

Have you created a filter for your USB device ?

In USB settings, click the graphic (usb symbol with the plus sign) to add your memory device, then start your vm.

Play around with the sound options, I find it works best with PulseAudio selected but your system may be different.

---

### Post by mamamia88 on 2009-03-12
ok ill try again

---

### Post by mamamia88 on 2009-03-12
still not letting me mount usb even though i created exception for it

---

### Post by mamamia88 on 2009-03-12
anyone the only reason i installed xp in the first place was to use office 2007 for school and sopcast and that requires sound would be appreciated

---

### Post by howefield on 2009-03-12
There is a Linux version of sopcast, not sure how well it works. It has been a while since I used it.

What are the options in your audio settings for Host Audio Driver and Audio Controller ?

---

### Post by mamamia88 on 2009-03-12
i was an idiot didn't realize i had it muted works fine now.  only thing is usb i can't get it to work and i need to so i can do my work that i save on a flash drive in office

---

### Post by sneeks on 2009-03-12
in the v box screen,go to usb enable it and usb 2,then plug in your drive,if u click add it will give the option of the specific device,and not an open one.
also is it the most current version of vbox..

---

### Post by mamamia88 on 2009-03-12
yeah and its most current and i did enable the specific device

---

### Post by sneeks on 2009-03-12
> **mamamia88 said:**
> yeah and its most current and i did enable the specific device

ok,i just tried it another machine i have here running hardy,and it seemed to work for me,just one thing,on some older usb sticks,they had a little switch on the side,e.g. lock/unlock ??

---

### Post by mamamia88 on 2009-03-12
> **sneeks said:**
> ok,i just tried it another machine i have here running hardy,and it seemed to work for me,just one thing,on some older usb sticks,they had a little switch on the side,e.g. lock/unlock ??

theres no switch

---

### Post by Shpongle on 2009-03-12
why not try the open office suites they can save in .doc formats which work with windows. or if you can email the files to yourself from xp in virtual box.

---

### Post by mamamia88 on 2009-03-12
yeah i have it and love it but still need to print my papers in office font way too big when i print in open office

---

### Post by cristobal78 on 2009-03-12
hi all

I was recently offered a nice laptop but with a rotten vista. I erased it and tried to replace it with an official XP. That will do the trick I thought.
It did not work. Impossible to install an official xp on that PC. I suspect the pc to be tattooed by HP and as I don't have the official vista intallation CDs I am stuck !
It is not that I like xp that much but some of my applications simply won't work with ubuntu.
Finally I installed ubuntu Hardy alone until a friend suggested to try virtualbox.
So I decided to try a virtual xp hosted by my ubuntu 8.04.
I succeeded with the installation but I've had the same problems as those of mamamia88 for the last 2 months.

Two friends of mine both linux experts tried in vain to solve the usb issue discussed here. Initially they suspected it had something to do with the virtualbox ose version I had chosen (at that time ose was the obvious choice to me) so they uninstalled it and replaced it with the NON-ose version of virtualbox.:D

I can now access win-XP virtually, surf on the net and of course use my emails.
However I still can't save any data on a writable cd/dvd and I still can't write on or read from the usb stick as both are invisible to xp.:(

Apparently this seems a real issue.

---

### Post by mamamia88 on 2009-03-12
im using the non ose version

---

### Post by kelvin spratt on 2009-03-12
Have you installed virtualbox guest additions in your guest operating system, USB should work flawlessly. to write to cd/dvd you need to enable passthrough in vbox settings cd/dvd rom but it does not recognise audio cd.

---

### Post by mamamia88 on 2009-03-12
yeah i have guest additions enabled

---

