---
title: "[SOLVED] Belkin F5D7000 v7000 - Here's my solution"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by garyj1972 on 2007-11-19
Okay I'm new to Linux/Ubuntu so not best qualified to give advise, but this PCI WIFI card gave me real headaches, with the help of various other forum entries I got this working.

I decided to cut down the instructions to the bear minimum that work everytime for me, I hope it help you too.

Firstly, if you need to check which version of Belkin card you have and still have the original driver CD, just chuck it in the drive and you should find the CD title is F5D7000 v7000 if it's the same model.

I can only say this works with Ubuntu Gutsy i386 32-bit with F5D7000 v7000, I have never got it to work in a 64-bit environment and never tried any of the other versions of this card.

Here goes...

(1) get driver from REALTEK website, currently this link will get you there:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

download driver named:
Driver_1097_2KXP
Extract it and place folder WINXP on your Ubuntu desktop
(you will require some kind of .rar application to do this such as 7zip)

(2) open up a terminal window ( Applications>Accessories>Terminal )

(3) type
sudo apt-get install ndiswrapper-utils-1.9
press enter
follow on screen instructions answering "Y"es to any questions

(4) type
sudo ndiswrapper -i Desktop/WINXP/net8185.inf
press enter

(5) type
sudo ndiswrapper -a 1799:700f net8185
press enter
you will get a message about this being okay under certain conditions, ignore this is usual

(6) type
sudo depmod -a 
press enter
the machine will pause for a few seconds while it performs this instruction

(7) type
sudo modprobe ndiswrapper
press enter
again there will be a pause

this time when the prompt reappears, left or right clicking on the network icon (next to sound icon, near time & date, top right of screen) should show wireless networking enabled.

One last suggestion

To avoid the need to reinstall the WIFI card everytime you reboot. I suggest you save this configuration by the following:

Before closing the terminal window (or reopen it as described above)

type
sudo ndiswrapper -m
press enter

type
gksudo gedit /etc/modules
press enter

A text editor will appear, in the text editor, go to the bottom of the text and on the next line down type :
ndiswrapper

then save and exit

now Ubuntu will recall your working WIFI settings every startOne last suggestion

---

### Post by garyj1972 on 2007-11-19
Okay I'm new to Linux/Ubuntu so not best qualified to give advise, but this PCI WIFI card gave me real headaches, with the help of various other forum entries I got this working.

I decided to cut down the instructions to the bear minimum that work everytime for me, I hope it help you too.

Firstly, if you need to check which version of Belkin card you have and still have the original driver CD, just chuck it in the drive and you should find the CD title is F5D7000 v7000 if it's the same model.

I can only say this works with Ubuntu Gutsy i386 32-bit with F5D7000 v7000, I have never got it to work in a 64-bit environment and never tried any of the other versions of this card.

Here goes...

(1) get driver from REALTEK website, currently this link will get you there:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

download driver named:
Driver_1097_2KXP
Extract it and place folder WINXP on your Ubuntu desktop
(you will require some kind of .rar application to do this such as 7zip)

(2) open up a terminal window ( Applications>Accessories>Terminal )

(3) type
sudo apt-get install ndiswrapper-utils-1.9
press enter
follow on screen instructions answering "Y"es to any questions

(4) type
sudo ndiswrapper -i Desktop/WINXP/net8185.inf
press enter

(5) type
sudo ndiswrapper -a 1799:700f net8185
press enter
you will get a message about this being okay under certain conditions, ignore this is usual

(6) type
sudo depmod -a 
press enter
the machine will pause for a few seconds while it performs this instruction

(7) type
sudo modprobe ndiswrapper
press enter
again there will be a pause

this time when the prompt reappears close the terminal window, left or right clicking on the network icon (next to sound icon, near time & date, top right of screen) should show wireless networking enabled.

Hope this worked for you too. Gary

---

### Post by garyj1972 on 2007-11-19
One last suggestion

To avoid the need to reinstall the WIFI card everytime you reboot. I suggest you save this configuration by the following:

Before closing the terminal window (or reopen it as described above)

type
sudo ndiswrapper -m
press enter

type
gksudo gedit /etc/modules
press enter

A text editor will appear, in the text editor, go to the bottom of the text and on the next line down type :
ndiswrapper

then save and exit

now Ubuntu will recall your working WIFI settings every startOne last suggestion

To avoid the need to reinstall the WIFI card everytime you reboot. I suggest you save this configuration by the following:

Before closing the terminal window (or reopen it as described above)

type
sudo ndiswrapper -m
press enter

type
gksudo gedit /etc/modules
press enter

A text editor will appear, in the text editor, go to the bottom of the text and on the next line down type :
ndiswrapper

then save and exit

now Ubunto will recall your working WIFI settings every start-up

---

### Post by richarglamb on 2008-03-04
Thank you. 

You saved me a lot of hassle and effort.

Cheers

---

### Post by TonyVF on 2008-04-25
Thank you so much:KS I've been trying to solve this for a week now.  The only set I missed out was sudo depmod -a 
That made all the difference.

Anyone care to enlighten me as to what it does thanks !

---

### Post by cmosguy on 2008-05-17
Hey all,

I tried this procedure yesterday, with the Live CD, and it worked great (Thanks!).

But, today, I installed Ubuntu 8.04 within Windows (using wubi).  Now, when I type the command:

sudo apt-get install ndiswrapper-utils-1.9

I get an error message that it can't find the package ndiswrapper-utils-1.9.  I'm new to linux, and aren't sure what to try next. 

Any suggestions?

---

### Post by meeces2911 on 2008-07-21
Sorry, about opening this threed, but this has been a big help for me, and i thought i would update it.

You need to run the command:
sudo apt-get install ndiswrapper-common
this should not install the latest version.
Then goto the cd and find the Win2kXP drivers, or download the latest ones, [http://www.belkin.com/uk/support/article/?lid=enu&pid=0&aid=6199&scid=0&fid=3236&fn=f5d7000v7drivers.exe](http://www.belkin.com/uk/support/article/?lid=enu&pid=0&aid=6199&scid=0&fid=3236&fn=f5d7000v7drivers.exe)
Then run this:
sudo ndiswrapper -i Desktop/WINXP/BLKWGDv7.inf
sudo ndiswrapper -a 1799:700f blkwgdv7
sudo depmod -a 
sudo modprobe ndiswrapper

This worked for me, but i did follow a few guides before this, to try and get this working, so hopefully i havn't missed anything out.

---

