---
title: "[SOLVED] Still no internet after reading"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by DudsOne on 2008-07-01
Have the specs but can't connect using Hardy.

I ran the following commands and saved them but I don't
know how to insert them to here.

lsusb
lspci
lshw -C network
iwconfig
ifconfig

My internet provider is Verizon dsl which is connected to 
a Westell 327w that is connected to a Buffalo wzr2-g300n
which connects to a D-Link adapter that is a usb receiver.

Hope thats right.

---

### Post by pytheas22 on 2008-07-01
It's hard to do much without the output of those commands.  Please run these:
```

lspci > ~/Desktop/lspci.txt
lsusb > ~/Desktop/lsusb.txt
lshw -C Network > ~/Desktop/lshw.txt
iwconfig > ~/Desktop/iwconfig.txt
```

This is going to produce four files on your desktop in Ubuntu containing the output of those commands.  You can copy those files over to a computer that has an Internet connection and post their contents here that way, by copying and pasting.

---

### Post by DudsOne on 2008-07-01
thank you, I'll log onto Kubuntu right now and enter those commands and hopefully post response as quickly as I can.

thanx again

---

### Post by DudsOne on 2008-07-01
command response
[ATTACH]75991[/ATTACH]

[ATTACH]75992[/ATTACH]

[ATTACH]75993[/ATTACH]

[ATTACH]75994[/ATTACH]

this doesn't look right?

I'm don't know why .....I'll try long hand but THERE"S GOTTA BE AN EASIER WAY OR TUTORIAL ON INSERTING TEXT>

thanks for your help and patience

---

### Post by pytheas22 on 2008-07-01
On inserting text...it works the same way it does in Windows.  Just highlight the text you want to copy, right-click and select copy.  You can also press control-c to select copy, but in the terminal window this doesn't work, so you need to right-click.  Then right-click to paste, or press control-v.  The reason I had you copy that text out into other files is because I thought the trouble you were having was that you didn't know how to get it into this forum, since your Ubuntu machine doesn't have an Internet connection now.  My apologies; if I'd realized that all you needed to know was what keys to use for copying and pasting, I would have just told you.

Anyway, thanks for the files; I'll take a look at them and get back.

---

### Post by pytheas22 on 2008-07-01
From your lsusb output I see that you have a DWL-G122 rev. B device, which has an Ralink chipset (not that you need to know this, but you might be interested).  Ubuntu ships with drivers that are supposed to make this card "just work," but it may be the case that those drivers don't mix well with your card yet.  What kind of behavior were you getting, exactly--could you see wireless networks but just not connect?

Anyway, to get it working please run these commands, which will blacklist the default driver and install a different one which should be more reliable:
```

sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
apt-get install build-essential rutilt
wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
tar -xzvf rt2570*
cd rt2570*/Module
make
sudo make install
```

then reboot and see if you have wireless.  Note that you won't be able to use Network Manager to connect, even if it looks like you can.  You need to use "Rutilt," which can be found under the System>Administration menu.

---

### Post by DudsOne on 2008-07-02
My problem is no internet in hardy.
I ran a duel boot with Feisty and Xp for months last year.
I ran Gutsy until it crashed and took everything with it.
My only complaint with Kubuntu was there were no drivers
for my Epson CX 6600 all in one printer. Therefore I decided 
to wait for hopefully a better version. When I was running
Kubuntu at that time I was wired with cable broadband.

Last week I downloaded and tried to install Ubuntu Hardy but
the disk wanted a login and password, which I never set up. 
But Kubuntu  installed fine other than my Internet.

Today I have the same desktop (amd Athlon 64 x2 processor)and
the same Xp. However I bought a HP 9000 series laptop with built in wireless.

My ISP is Verizon DSL. There modem (Westell 327w) connects a
Buffalo WZR2-G300n router. The desktop is wireless and has a
D-Link receiver and of course the laptop automatically sees
EVERYTHING..bless its little heart.

But so far Vista will not let me install Ubnuntu, may be user error but I cannot afford to lose that at this time. When I get this Desktop up and running Kubuntu/Ubuntu I'll try to duel boot
from a second empty drive on the Laptop.

Thanks for your time and I'll run those new commands and post results

---

### Post by DudsOne on 2008-07-02
By running the blacklist command for the usb I lost my little D-Link usb receiver....OOOoooppps.  

what now?......this is getting comical.

---

### Post by pytheas22 on 2008-07-02
> By running the blacklist command for the usb I lost my little D-Link usb receiver....OOOoooppps. 

Did you run the rest of the commands and reboot?  It's normal for the light to go out on the card while you're installing the new driver, but after a reboot things should work alright.  If not, I may have given you the wrong driver to install, in which case you can just try a couple others and everything should work out.

---

### Post by DudsOne on 2008-07-02
I ran all of the commands and did reboot to no avail. I was leery about blacklisting anything usb....but what the hell. Kubuntu saw eth0 and the wireless, now it only sees eth0. 
I'll paste latest lsub, lspci etc info.

If you could...would you give the commands to undo earlier commands.

thanks again

---

### Post by pytheas22 on 2008-07-02
If you want to undo the commands, you just need to open a terminal and type:
```

sudo gedit /etc/modprobe.d/blacklist

```
a file will open.  At the bottom of the file are the lines:
```

blacklist rt2500usb
blacklist rt2500pci
blacklist rt61pci
blacklist rt2x00pci
blacklist rt2400pci
blacklist rt2x00lib
blacklist rt2x00usb
```

Remove those lines, save the file and reboot, and you'll be back to where you were originally.

But I don't think that this will solve the problem.  The reason that those lines were in that file is that it tells the system not to use certain drivers for your card.  These "next-generation" drivers ship with Ubuntu but they don't seem to work with your card (and a lot of cards similar to yours, including two that I own) because they're still being developed and aren't as stable yet as they should be.  They might make the light come on, but they won't allow you to connect.

Because the drivers that come with Ubuntu aren't reliable, the solution to the problem is to use older, "legacy" drivers that are more reliable.  I may have given you the wrong driver to install--there are a few different versions and I'm not positive which one your card needs.

To try with a different kind of driver, you should leave /etc/modprobe.d/blacklist unchanged, and run these commands:

```
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*/Module
make
sudo make install
```

then reboot and see if you can connect (remember that you need to use Rutilt, not the normal Network Manager utility).

Unless something strange is going on, this should definitely solve the problem.

---

### Post by DudsOne on 2008-07-02
Thank you, I'll try the new commands first. Have thunderstorms here ( Florida)  so this could take even longer but will keep you posted.

Thanks again

---

### Post by DudsOne on 2008-07-02
ps...don;t know how to use rutilt in Kubuntu.

---

### Post by pytheas22 on 2008-07-02
Actually after doing a little more research, I think that the driver I told you to compile was the right one.  I found a [thread]("http://ubuntuforums.org/showthread.php?t=739139") from a couple months ago where I helped someone with the exact same card as you, and it worked for him using the driver that I had you compile yesterday.  The only difference is that he was using 7.10 and you're on 8.04, but that shouldn't make a difference.

So I'm wondering if something else is wrong.  Before you try installing the second driver from my previous post (#11), please run a few commands and post their output here:
```

iwconfig
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/ralink
iwlist scan
```

Sorry for this confusion, but I want to make sure I don't tell you to do something that's not necessary.

---

### Post by pytheas22 on 2008-07-02
> ps...don;t know how to use rutilt in Kubuntu.

I haven't used Kubuntu in a while so I don't know where it would put Rutilt in the menu.  But if you just open a terminal and type "sudo rutilt" it will start.

---

### Post by DudsOne on 2008-07-02
[netests5.doc]("http://ubuntuforums.org/attachment.php?attachmentid=76171&stc=1&d=1215035310") hope this helps

I was looking for a nice long Ethernet cable to hard wire this thing
but when I went "WIRELESS" last year I throw those and 25 or so
audio/video cables away.

---

### Post by pytheas22 on 2008-07-02
Thanks, that output helps.

It looks like the driver was never installed.  Do you not have an Internet connection on your Ubuntu computer?  I was under the impression that you had a wired connection.  The instructions I gave you won't work if you're not online when you're running them (did they return error messages?).

If you're not online, follow these steps to get it working.  It's going to be a bit more complicated since you don't have Internet, but not too bad:

1. On a machine with Internet, click [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) and download that file.  Then put that file on a USB drive or something, transfer it to your Xubuntu computer and save the file to your desktop there.

2. do the same thing as above for the file [http://ubuntu.secs.oakland.edu/pool/universe/r/rutilt/rutilt_0.16-0ubuntu1_i386.deb](http://ubuntu.secs.oakland.edu/pool/universe/r/rutilt/rutilt_0.16-0ubuntu1_i386.deb) and save it to your desktop on Xubuntu.

2. Put your Xubuntu installation CD in your computer and open up *Synaptic Package Manager* from the Applications>System menu.  In Synaptic, under the *Settings* menu, click *Repositories*.  In the window that opens up, you will see a section that says "Installable from CD-ROM/DVD."  Check every box in this section (there will probably only be one box) and close the window.  Then, back in the main screen of Synaptic, click the big button in the upper-left that says "Reload."  When it's done reloading, exit Synaptic.

3. now run these commands:
```

sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf rt2570*
cd rt2570*/Module
make
sudo make install
cd ~/Desktop
sudo dpkg --install rutilt*deb
```

now reboot and the Internet should be working.  If you get any error messages when you run any of these commands, please let me know which command produced the error and approximately what the error said.

By the way, I wrote these instructions with the assumption that: 1) you're using Xubuntu 8.04; and 2) you're using a 32-bit system.  If either of those is wrong, please let me know so that I can change the directions accordingly.

I'm sorry for all of the confusion, but the stuff above should certainly work.

---

### Post by DudsOne on 2008-07-02
I;m trying to run Kubuntu and the desktop is duel boot and Xp is online,check post #7
in this thread.

It very close, it sees Ethernet and Wireless and I think it may be assigning ip address
issue. Tomorrow I'm going to get an Ethernet cable and try wired.

I will try the new commands just to learn and I may even replace Kubuntu with
Ubuntu. 

thanks again

---

### Post by pytheas22 on 2008-07-03
Yeah, I realized later on yesterday that I had mistakenly thought you were using Xubuntu.  I was confusing you with someone else; sorry about that.

In any case, if the wireless seems to be working, that's really good.  Start Rutilt (again, I don't know where KDE puts it, but if you just type "sudo rutilt" in a terminal it will open) and that should connect you.  Network Manager probably won't be able to get you an IP address, even if it looks like it can.  I'm not familiar with the other KDE wireless managers, but they probably also won't work well.  Rutilt is built especially for the wireless driver that you're using.

---

### Post by DudsOne on 2008-07-03
I have installed wubi and now I have Xp running and online, Kubuntu running but off line,and Ubuntu running in safe offline but it is very close. Its seems like I download
bad copies.

I had no problems with Feisty or Gutsy and I will not give up on Ubuntu. However I read this forum 6 or 7 times a day and  I find  a ton  of people having trouble with Hardy so I don't  feel  bad.  Also  I'm  used  to  a  crash  now and then.

I do find the tutorials lacking and way to many people  in this  forum  not  realizing  most of the  people  are  coming  from  Windows.  I find  the  tutorials and some of the help more complicated than the DOS days. But for the price why complain. With all the interest and great strides made by Ubuntu things need to be user friendly.

Can't thank you enough for your help and I'll need more real soooooon I'm sure.

---

### Post by pytheas22 on 2008-07-03
I'm glad it's working better now.
> 
Its seems like I download bad copies.

It's possible; if you're installing from CD, you should burn the CD at low speed and check it for defects before installing.
> 
I had no problems with Feisty or Gutsy and I will not give up on Ubuntu. However I read this forum 6 or 7 times a day and I find a ton of people having trouble with Hardy so I don't feel bad.

I agree.  Hardy has some major issues.  They introduced a lot of brand-new stuff in Hardy (Broadcom b43 driver, gvfs, new X11, for example) and a lot of it seems to cause problems in many cases.  These new features will be great when they work properly for everyone, but I wish Ubuntu had kept them out of the stable release until they'd matured more, especially given that Hardy is LTS.  On the other hand, for me, Hardy was the first Linux release I've ever tried that "just worked" perfectly in every respect out-of-the-box (but that's on a computer whose hardware I chose carefully for easy Linux compatibility), so for some of us, Hardy was an improvement.
> 
I do find the tutorials lacking and way to many people in this forum not realizing most of the people are coming from Windows.

Again, I agree that it's a problem.  A lot of the documentation is outdated, poorly written or gives instructions that are plainly wrong--for example right at the top of the [ndiswrapper community documentation page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), someone implies that using bcm43xx is an alternative to ndiswrapper.  Not only is this now outdated (bcm43xx is replaced by b43 since Hardy), but it's very wrong--only people with Broadcom chipsets should look at bcm43xx.  Stuff like this is a major problem.  I wish there were more centralization so that problems like these could be addressed comprehensively...but on the other hand, centralization of authority is part of the reason I don't like Windows and Macs, so I guess you can't have everything.


> 
But for the price why complain.

Free software doesn't mean bad software.  Don't lower your expectations just because Ubuntu doesn't cost money.  When you see problems, please bring them up.

---

### Post by DudsOne on 2008-07-03
Great reply...same page I see. Wish the powers that be "Would See"...pun intended.

The change in just the last year, year an a half  is  very  noticeable and mostly negative.
If I could have a central figure involved it would be someone with STRONG technical writing skills. Most of us just choose shortcuts in our responses and reply but if you need to be exact in technical guidance ......there are no shortcuts. IMHO.

I've hit a snag with Wubi and Ubuntu Hardy and I've been working on it for 5 or 6 hours and maybe I'll figure  it out,  if not  I'll shout  out  for help.  I seem to be constantly  downloading
bad ISOs (from Georgia ....nearest mirror...8  so far) and   will download from a different
mirror this time. To my amazement I haven;t crashed yet. Next time I post I'll have all
outputs from the commands......iwlist scan, lshw -C Network, etc

Thanks Again for all the help

---

### Post by DudsOne on 2008-07-05
I' m replying to this thread via Ubuntu HH wubi 8041 Finally. However I had to run 40 feet of dsl cable and direct connect. After a week of screwin around with Kubuntu/Ubuntu and wireless Attempts. As soon as I plugges in the ethernet cable Ubuntu instantly came to life and Without a command from me open FF and downloaded and installed updates. I'm very impressed and Learned Alot. I'm going close this thread even the the Wireless issue was not resolved and many thanks to PYTHERS22 for his time , patiance  and help

---

### Post by pytheas22 on 2008-07-05
No problem, sorry the wireless never got solved but at least you have a connection now.

---

