---
title: "help with wirless drivers on laptop"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Grukmuck on 2008-12-20
okay, so im dual booting windows xp and ubuntu 8.04 and low and behold my wireless internet doesnt work when i use ubuntu. i am unable to get a wired connection so i cant get fwcutter or ndiswrapper to work. i was curious if i could get what i need onto a disc to get my wireless to work in ubuntu and if so where can i get it.

just a side note, im new to ubuntu and linux and really have no idea what im doing. im looking forward to getting my internet to work because i want to make the switch from xp to ubuntu.

any help would be appreciated. thanks in advanced.


-gruk

---

### Post by nhasian on 2008-12-21
actually Ubuntu 8.10 is supposed to have better support for wifi adaptors.  you should try upgrading to the new version.  also you can show us which network adaptor you have if you type in a terminal:

```
lshw -C network
```

---

### Post by Grukmuck on 2008-12-21
i tried booting a live cd of 8.1 but my wireless still doesnt work. my network adaptor is a broadcom BCM4318. 

my problem is that i am unable to get a wired connection to the internet to update the firmware.

my question is: can i get the firmware using xp and put it onto a disc so that i can just install from the disc in ubuntu? or do i have to find a wired connection to do the update?

---

### Post by igknighted on 2008-12-22
> **Grukmuck said:**
> i tried booting a live cd of 8.1 but my wireless still doesnt work. my network adaptor is a broadcom BCM4318. 

my problem is that i am unable to get a wired connection to the internet to update the firmware.

my question is: can i get the firmware using xp and put it onto a disc so that i can just install from the disc in ubuntu? or do i have to find a wired connection to do the update?

Download this file in XP [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) (you should be able to browse that partition if it is a dual boot, no disk transfer needed).  The b43-fwcutter app should be installed already.  Then follow these directions on the terminal:
```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

---

### Post by Grukmuck on 2008-12-24
ok, so i have decided to re-install ubuntu for reasons that i wont go into. im going to re-partition my drive and try the tips you guys gave me and let you know how it works.

---

### Post by Grukmuck on 2008-12-26
okay, so this is what it says:

tar: broadcom-wl-4.150.10.5.tar.bz2 Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Grukmuck on 2008-12-28
i have an idea and wanted to know if it would work.

the ideas is: i download the file that lgknighted posted in xp and put it in my documents, then reinstall ubuntu 8.1 and migrate my files from xp. that should work, right?

if that does, how do i go about getting it installed once in ubuntu?

---

### Post by Grukmuck on 2009-01-09
is anyone reading this anymore?

---

### Post by igknighted on 2009-01-09
A simple bump would suffice, no need to get snippy.

That could work, but hardly necessary.  I think you simply forgot to change directories in the terminal before running that command.  For example, if you put the file on your desktop, you would get that error if you simply opened the terminal and typed the command.  You need to change to the desktop directory, with the cd command.  For the desktop it would be 'cd ~/Desktop'.

EDIT: sorry, you should also drag/drop that file onto your linux drive as well.

---

### Post by Grukmuck on 2009-01-12
im sorry, i wasnt trying to be snippy.

---

### Post by Grukmuck on 2009-01-15
after i switched directories this is what i got:

gruk@laptop:~/Desktop$ cd broadcom-wl-4.150.10.5/driver
gruk@laptop:~/Desktop/broadcom-wl-4.150.10.5/driver$ sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
sudo: b43-fwcutter: command not found

---

### Post by Grukmuck on 2009-01-17
bump...

---

### Post by Grukmuck on 2009-01-20
bumpidy bump

---

### Post by carml on 2009-01-20
Are you sure you've already unzipped the file?:confused:

---

### Post by anewguy on 2009-01-20
Okay, I can also give you info for another approach - the firmware cutter is very valid, so don't get me wrong, but sometimes it ends up easier just to use ndiswrapper.  If you have the Windows (non-vista, non-64 bit) driver you should be able to make this work.  With no network connection, you can still install ndiswrapper by the following:

- put the LiveCD in the cd drive (don't boot from it, just put it in while Ubuntu is up)

- in the file explorer, navigate to the /pool/main/n/ndiswrapper folder and double-click the 2 files there to install ndiswrapper and utils

- in this same file explorer, navigate to the /pool/main/n/disgtk folder and double-click the file there to install the gui'd front end to ndiswrapper

- run ndisgtk and install the Windows driver using it

Then try your wireless again.

I don't use the firmware cutter, but I know that it is very valid - sometimes it's just quicker to use ndiswrapper.

The b43-fwcutter_011-1_i386.deb package is also on the cd in the /pool/main/b/b43-cutter folder.  I've never tried extracting it but if you can't get any form of connection so you can't download the firmware cutter, you may want to try double-clicking it to install the firmware cutter and try the steps already mentioned by others in this post, but from the looks of your error message the firware cutter is already installed and it is a matter of getting the file previously mentioned earlier.  

Dave :)

EDIT:  if you decide to use ndiswrapper, remember it is the .inf and .sys files for your wireless driver that you need, and they must be the non-Vista drivers, 32-bit.

---

### Post by ugm6hr on 2009-01-20
> **anewguy said:**
> - in the file explorer, navigate to the /pool/main/n/ndiswrapper folder and double-click the 2 files there to install ndiswrapper and utils

- in this same file explorer, navigate to the /pool/main/n/disgtk folder and double-click the file there to install the gui'd front end to ndiswrapper

- run ndisgtk and install the Windows driver using it


You will have to ndiswrapper-common, ndiwsrapper-utils-1.9, ndisgtk in that order.

I would suggest you confirm what wifi device you have first though, with:
```
lshw -class network
lspci
```

---

### Post by anewguy on 2009-01-20
> **ugm6hr said:**
> You will have to ndiswrapper-common, ndiwsrapper-utils-1.9, ndisgtk in that order.

I would suggest you confirm what wifi device you have first though, with:
```
lshw -class network
lspci
```

I didn't think to look to see if they were in sequence in the folder, so thanks for giving him a heads up!

Also, I completely missed that he hadn't actually posted the outputs so we could be sure he was working with the correct drivers.  I did that old assume thing again, thinking he had already gotten that far - me bad!

Thanks for giving him the heads up on the things I forgot!

Dave :)

---

### Post by ugm6hr on 2009-01-20
> **archeryguru2000 said:**
> ~~archery~~

Sorry to ask - but are you the same person who started this thread?

If not - I will move your posts to a new thread.

---

### Post by anewguy on 2009-01-20
If I remember correctly, I think that if you use the fwcutter method you still have to blacklist at least bcm43xx - someone else out there may know that for sure.

If you post back the make/model of your laptop, I may be able to download the driver and extract the files you would need, then post them back here tar'd.  I think that is allowed but not sure since they are not "open" drivers.

Dave :)

---

### Post by Grukmuck on 2009-01-21
thanks for all the advice guys. as soon as i get home from work im gonna try it all and hopefully i can get my wireless up and running.


ugm6hr:
no, archeryguru2000 is not me. thanks for asking. just to save on confusion, i think his posts should be moved.

anewguy: 
i dont know if you were asking archeryguru200 for his make and model, but heres mine if you were asking me. i have a a geatway 7330GZ

---

### Post by vikingman on 2009-01-21
[FONT="Lucida Console"]hej, if u can understand french [_[COLOR="RoyalBlue"]here[/COLOR]_]("http://www.siteduzero.com/tutoriel-3-36980-installer-un-reseau-wi-fi-sur-ubuntu-et-derives.html") u can find a solution to ur problem, otherwise, try this in a terminal and gimme the feed back ```
lspci | grep -i network
```, ill try to help u, i had the same pbl as u just days back, but now its resolved[/FONT]

---

### Post by anewguy on 2009-01-21
I downloaded the driver executable from Gateway for your laptop and extracted the files.  If you are running 32-bit ubuntu (I think that is the default unless you purposely download the 64-bit version), the 2 driver files you need are:

bcmwl5.inf and bcmwl5.sys

these files should be located on your Windows partition in the \windows\system32 and \windows\system32\drivers, I believe.  you could search for them, or just have your Windows partition mounted when you run ndiswrapper and point to them.

In addition, you will need to blacklist a couple of things so they don't load with the kernel at boot:

cd /etc/modprobe.d
sudo gedit blacklist

this will call up the editor on the main blacklist file.  Scroll to the end, then add the following 2 lines:

blacklist bcm43xx
blacklist b43

save the file and exit.  Please note that I don't know if the b43 module is actually B43 or just b43 - perhaps someone else can clarify that.

after ndiswrapper, be sure you have done the following:

- set up the dependency:  sudo depmod -a

- tell ndiswrapper to load at boot:  sudo ndiswrapper -m

- modify the modules file to tell the system to load the ndiswrapper module at boot:

cd /etc
sudo gedit modules

scroll to the end of the file then add the following line:

ndiswrapper

save the file and exit

Now reboot.  See if your wireless comes up after the boot.

Dave :)

---

### Post by Grukmuck on 2009-01-22
WOOT! WOOT! thank you so much for helping me get my wireless up and running! i really appreciate it. im writting this on my laptop with ubuntu and it feels great!

i extracted the fwcutter from the live cd and used the files that igknighted provided. i also extracted the ndiswrapper but used the  fwcutter.


im really just too excited. now i can start to fully make the switch from xp!


thank you all again.


-gruk

---

