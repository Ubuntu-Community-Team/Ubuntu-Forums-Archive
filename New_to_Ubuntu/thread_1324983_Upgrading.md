---
title: "Upgrading"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by manners2345 on 2009-11-13
I was running 8.04 and just happened to notice that the latest release 9.10 had open office 3.10 in it. That is the suite I use everyday. so I decided to upgrade to it, could not do directly had to go thru all all of the other releases. by the time I got 9.10 to upgrade it said no more room on HDD. so I dumped what I never ever use, such as python,perl, evolution,epiphany and some others. My computer is now a piece of electronic nothingness. I am using a friends machine(windows. I have burned a new cd of 9.10, my machine WILL NOT read a CD. 

HOW DO I GET UP AND RUNNING

---

### Post by jimmy the saint on 2009-11-13
Get a USB stick and create a bootable USB stick.  

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by aquavitae on 2009-11-13
Some packages, e.g. python, perl, are essential to the system, even if you never use them. So uninstalling them probably messed things up quite badly!

Do you mean your computer isn't reading cds in ubuntu, or won't boot off a cd, or doesn't have a cd drive?  If you can't read off a cd then try usb, but if its just that ubuntu won't read it then you should be able to boot off it.

---

### Post by manners2345 on 2009-11-13
I went to the referenced site, the page was as clearv as mud, to what I am supposed to do. have a 4 GB usb stick. looked on the disk Iv burned in windows found no usb creator or any tthing similar

---

### Post by manners2345 on 2009-11-13
it will not read a cd, tried it on the machine I  burned it on, seems to work

---

### Post by aquavitae on 2009-11-13
So it won't boot off a cd?  What error does it give, or does it just completely ignore it?  Are you sure your bios is configured to boot off cd?

---

### Post by manners2345 on 2009-11-13
It used to boot from a cd. now it goes to the cd accesses it for a bit,the cd light flashes, then tries to do a load from the hard drive

---

### Post by aquavitae on 2009-11-13
Ok, so it does look at the cd, but it won't boot.  And the cd will boot in another computer? Did you check that the cd downloaded correctly using [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?  Have you tried burning another copy?

---

### Post by manners2345 on 2009-11-13
My bios says USB bios support enabled.

for boot CD ROM DRIVE IS first on list, with what I interept as a large exclamation point in front of it.

---

### Post by manners2345 on 2009-11-13
I did a m5 check sum on the down load. I have burned it twice. I also have disk 1 of fedora will not load that either, it used to.

---

### Post by aquavitae on 2009-11-13
Not sure what the exclamation is... maybe your cd drive is failing? Sounds like the only option is to use usb. I'm not sure why usb-creator isn't on your cd - I'm just downloading a cd at the moment to check.  Which one did you use - ubuntu-9.10-desktop-i386.iso?

---

### Post by manners2345 on 2009-11-13
how would I do a load from the command line, using the internet?? used to do command line 15 yrs ago

---

### Post by aquavitae on 2009-11-13
"do a load"?  What do you mean?

---

### Post by manners2345 on 2009-11-13
yes to 9.10, I used to have an osbourne back in 1980 been playing with computers since 1960, on the IBM1401.

Now I am just a dumb 70+ yr user

---

### Post by manners2345 on 2009-11-13
one of the options is using root with networking, so direct down load, as if upgrading

---

### Post by aquavitae on 2009-11-13
Oh, you mean upgrade from 9.04 to 9.10 using command line? ```
sudo apt-get dist-upgrade
``` Does that mean your current installation is still working?

---

### Post by manners2345 on 2009-11-13
no it does not boot, tries too, if I go to the recovery option on the booting I get recovery menu, there are 5 options, clean,dpkg,fsck,,grub and the last netroot.

I have tried all the others, no joy!!!!

---

### Post by manners2345 on 2009-11-13
did you find that usb thunmb drive thing on the download you did????? I have 2v 4gb usb drives, one has the download on it so still have 3+gb available

---

### Post by nothingspecial on 2009-11-13
What about [[COLOR="Magenta"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by manners2345 on 2009-11-13
you know what assume spells??? went to the link you sent, will see if I can make heads or tails

---

### Post by manners2345 on 2009-11-13
trying to make usb drive now!!!!

---

### Post by aquavitae on 2009-11-13
> **manners2345 said:**
> did you find that usb thunmb drive thing on the download you did????? I have 2v 4gb usb drives, one has the download on it so still have 3+gb available
Still downloading.  I've got a slow connection! 

If you can get into recovery then maybe your system can still be recovered.  What message do you get when you try to boot normally?

---

### Post by quinnten83 on 2009-11-13
On [www.pendrivelinux.com](www.pendrivelinux.com) there are links with instructions for installing to a usb stick.
if after installation to the usb, the OS on your stick does not want to start, you have to clear the partitions first and format everything to FAT32 (best do it in windows, since it's their native format) and do the install to USB again.
For that follow the instructions on the link on the site and it should work. I myself am running Ubuntu from a memory stick here.

---

### Post by manners2345 on 2009-11-13
made the usb drive, do not think it is working??? thank you for your help more than I can say

got to go now, dinner time here!!!!

---

