---
title: "Need Help Connection To Wireless!"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by xtthew on 2008-02-21
Well I'm new to Ubuntu and I've been trying to get my wireless to work but I can't seem to figure out how to do it.  When I turn on the wireless to free roam or, whatever it's called, It can't seem to find my Wireless Network.

Please Help!  =D
:guitar:

---

### Post by uberlube on 2008-02-21
Do you have your wireless drivers installed?

---

### Post by xtthew on 2008-02-21
I have them installed on my Windows partition, And I tried to do it separately onto Ubuntu but i couldn't run a .exe file on there.  

And my wired connection is broken, so I can't use that.

---

### Post by uberlube on 2008-02-21
Got your PM. So first off, were you ever able to use wifi in ubuntu?

---

### Post by xtthew on 2008-02-21
I wasn't able to get any connection onto there.  I tried manually setting up my network by writing the networks name and the pass for it.  But it didn't connect.

---

### Post by uberlube on 2008-02-21
OK You are going to have to install the windows driver using a tool called ndiswrapper. Do you have your windows driver on CD or are they just in windows?

---

### Post by xtthew on 2008-02-21
I've got it on a flash drive, and where can I find that application?

---

### Post by uberlube on 2008-02-21
I believe that it comes preinstalled in Ubuntu, if not it is available in the repositories. Is the driver just an .exe file or is there an .inf file there as well.

---

### Post by xtthew on 2008-02-21
There are .ini  .inx  and .iss files as well with the name setup.  How do I get to the ndiswrapper application?

---

### Post by uberlube on 2008-02-21
Like I said you probably already have it installed. It is not a program with a GUI but a function you can use in the command line. Ill explain how to use it once i have all the info I need. What is the name of the wirless card you have? And is it internal or is it the USB?

---

### Post by xtthew on 2008-02-21
It's broadcom 802.11 g and it's an internal card.

---

### Post by uberlube on 2008-02-21
Ok thank God its a Broadcom:lolflag: I have the exact same so this will be easy to install. Ok open up a terminal and type in each of these lines individually:

```

sudo su
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
mkdir /root/wireless_driver
cd /root/wireless_driver/
wget http://ftp.us.dell.com/network/R151517.EXE
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf

```

Then if all this works properlly reboot. Ill still be here if you need help:)

---

### Post by xtthew on 2008-02-21
When I did this one

wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

It came up with.. 

failed: Name or service not known

---

### Post by xtthew on 2008-02-21
Was I suppose to do it on Ubuntu or Windows?

---

### Post by uberlube on 2008-02-21
Ubuntu. Tell you what go into your irc client and log into irc.spotchat.org #linuxmint.com and tell me what your username is. ill send you the driver in there.

---

### Post by xtthew on 2008-02-21
What if I just download the driver and transfer it to Ubuntu using my flash drive then put it on my desktop in case you need to know where it's located?

---

### Post by uberlube on 2008-02-21
Before we go that far go into the terminal and type this in

sudo apt-get install wget

tell me if it installs

---

### Post by xtthew on 2008-02-21
It says that wget is the newest version. Nothing upgraded, installed, to remove, or not upgraded.

---

### Post by uberlube on 2008-02-21
hmm interesting OK sure download that file in windows and transfer it into that directory you created in the command line and let me know when you've got it.

---

### Post by uberlube on 2008-02-21
actually just download it in firefox. Im pretty sure you can.

---

### Post by xtthew on 2008-02-21
I don't know what directory you're talking about..:confused:  hahaha..  But i've got it downloaded now and it's on the desktop of Ubuntu.. Am I suppose to put it somewhere else..

And was I suppose to keep that terminal open, cause I closed it :)

---

### Post by uberlube on 2008-02-22
Lol sorry I wasnt more specific you made the directory with this command:

mkdir /root/wireless_driver

OK put that file in that directory and then go back to terminal and make sure that you are in the proper directory by

cd /root/rireless_driver

---

### Post by xtthew on 2008-02-22
rireless_driver  or  wireless_driver?

---

### Post by uberlube on 2008-02-22
2nd one, sorry

---

### Post by xtthew on 2008-02-22
How do I get to that directory.. I'm completely new to Ubuntu, Haven't had the time to discover it yet. :popcorn:

---

### Post by uberlube on 2008-02-22
:) No problem. Also welcome to the open source community, your on the beginning of a grand adventure to release you from the proprietary shackles of Micro-poofter. Anyway, Im assuming you know how to get into your file manager. If not look at the top menu and under places there is a way to get to your file system folder. Inside that you will see files like bin, boot, cdrom, dev etc. go into the 
'Root' directory and drag the file into there.

---

### Post by uberlube on 2008-02-22
sorry, inside Root directory and then inside wireless_driver directory, put file there. my bad

---

### Post by xtthew on 2008-02-22
I don't have permission to move it to there!..

How do I get permission?! ..

---

### Post by uberlube on 2008-02-22
the file system area is like c:\windows. all important system files are housed there, and you need to have root privileges to add or change things in there so what we do is go into the command line and type:

sudo apt-get install nautilus

if nautilus is already installed then just type in 

sudo nautilus

and it will open the root privileged file browser

---

### Post by xtthew on 2008-02-22
Okay I put it in there, and did cd /root/wireless_driver   now what?

---

### Post by uberlube on 2008-02-22
Right on were almost there. So now go into the terminal again and tupe in these commands:

```

sudo su
cd /root/wireless_driver/
wget http://ftp.us.dell.com/network/R151517.EXE
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf

```

Then reboot and once logged back in right click on your network icon at the top right of the screen and you should see some wireless networks! Let me know if this all works.

---

### Post by uberlube on 2008-02-22
Oh ya and feel free to click on the ribbon with the star on it in my post to say thank you, lol.

DING!! 100th Post YAY!! :guitar:

---

### Post by xtthew on 2008-02-22
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)   doesn't work still..

I'm assuming that this is suppose to connect me to the internet.. butk my LAN connector is broken and disabled.

---

### Post by toa on 2008-02-22
> **xtthew said:**
> Well I'm new to Ubuntu and I've been trying to get my wireless to work but I can't seem to figure out how to do it.  When I turn on the wireless to free roam or, whatever it's called, It can't seem to find my Wireless Network.

Please Help!  =D
:guitar:

Hay Xtthew,

Before getting deep, did you try the Live CD if it recognized your hardware and displayed the wireless connection correctly, usually the Live CD is configured for the best most universal hardware.

Try that to know if your wireless is recognized, then other solutions might help.

---

### Post by uberlube on 2008-02-22
Sorry i didnt mean to put that line in there just skip to the next. Im doing like 5 things at once lol:)

---

### Post by xtthew on 2008-02-22
"'*ndiswrapper' is currently not installed*"..

What now? .. :(

---

### Post by uberlube on 2008-02-22
Ok no problem, i guess ndis doesnt come preinstalled.

apt-get install ndiswrapper

and try again.

---

### Post by xtthew on 2008-02-22
It doesn't work..  Comes up with..

E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by uberlube on 2008-02-22
ok type in:

sudo apt-get install ndiswrapper

---

### Post by xtthew on 2008-02-22
Couldn't find package ndiswrapper..

---

### Post by uberlube on 2008-02-22
Grrr Ok go into the menu at the top, the one to the right of places and search in there for the synaptic package manager. At theast i think its in that menu. Just check them all untill you find it. Once in there do a search for ndiswrapper and click the box beside it, then choose apply to install.

---

### Post by xtthew on 2008-02-22
Okay I've got it installed..

What's the next step?  :)

---

### Post by uberlube on 2008-02-22
OK if you havent closed the terminal go back in and repeat the ndiswrapper command. Dont unzip again though cuz youve already done it. Just carry on from the step after.

---

### Post by xtthew on 2008-02-22
K, I did so and rebooted.. And when it loaded.. No more wireless! ..

---

### Post by uberlube on 2008-02-22
No more wireless? When you right click on the network icon at the top right of your screen, what does it show?

---

### Post by xtthew on 2008-02-22
Enable networking
Connection Information
and
About..

---

### Post by uberlube on 2008-02-22
Grrr OK repeat these into the command line and try it one more time. I may not have worked because you exited the command line after blacklisting the restricted drivers earlier. No worries ill get this working if it kills me.


Open a fresh terminal

```

sudo su
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
cd /root/wireless_driver/DRIVER
ndiswrapper -i bcmwl5.inf
reboot

```

---

### Post by xtthew on 2008-02-22
Still No Wireless!  :(

---

### Post by uberlube on 2008-02-22
:confused: Do you have your wirless switch turned on? Also go into terminal and type in:

sudo su
iwconfig
ifconfig

and show me the outputs.

---

### Post by xtthew on 2008-02-22
Yeah, I've got it hooked switched on..

and when I put the iwconfig it says

lo   no wireless extensions

eht0 no wireless extensions

---

### Post by uberlube on 2008-02-22
Well i am honestly at a loss. This has always worked for me, but I have looked around and found 2 threads with other styles of getting this to work. Here they are:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)


And also here is another site that will really help you with installing all the stuff you want:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Sorry again but im really stumped as to why this wont work, ill still be logged on if you need help with the other methodes. :(

---

### Post by xtthew on 2008-02-22
Alright thanks for your help anyways!  

I'm not completely clueless about Ubuntu anymore!  :)

---

### Post by uberlube on 2008-02-22
Hey no problem, and welcome again to the community. You also might want to check out this site:

[http://bcm43xx.spugna.org/](http://bcm43xx.spugna.org/)

And dont forget to click on the ribbon with the star, lol. :)

---

