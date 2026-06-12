---
title: "Dlink DWA130 revb can see networks but can't connect, please help ^^,"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by iMattcotv on 2010-05-25
Ok so.. I am that thing you call a n00b, only difference is I learn fast.

My problem is i don't understand exactly what to do in order to get my DLink DWA130 USB adapter connecting.

It can scan and see networks, but it cannot connect to them (open or known passwords lol)
Here are my PC Specs:
AMD Athlon64 II X 4
4GB Ram
Dual booting W7 and Ubuntu 10.04 (the regular 699mb .iso)

I followed the instructions on another forum stating to download and save on the desktop:
- ndisgtk_0.8.3-1_i386.deb
- ndiswrapper-common_1.50-1ubuntu1_all.deb
- ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb

and then enter:
cd ~/Desktop
sudo .... *.deb (I can't remember that part)

It worked, I then opened ndisgtk through terminal but I have a question here..
The driver files that I downloaded off their site for my adapter contains all XP, XP2K, Vista32, Vista64 each having their own .cat .inf and .sys file, which one do I install?

I tried entering 1susb, 1susb -v and 1spci -v but I get this:
No command '1susb' from package 'usbutils' (main)
1susb: command not found

I also get this after entering iwconfig:
lo no wireless extensions

eth0 no wireless connections

wlan0 IEEE 802.11bn 
and a bunch of info for wlan0

nothing else after that.

So what I'm trying to know and figure out is how to get Internet access working and how to install the drivers and stuff, thanks 

p.s, I am willing to learn, I'm not your average n00b. Oh, and I'm using my iPod touch to type all this so if there are any typos, it's spell correct.


******************************
EDIT: This problem is solved, follow these instructions if you have the same issue:

> BTW, for those who may run into this problem with their D-Link DWA130 REVB USB Router, heres what I did to eventually get it to connect to a network:

1. Downloaded ndiswrapper, ndisgtk and the dlink driver (WindowsXP2K will work).
You can download these files:
- ndisgtk_0.8.3-1.deb
- ndiswrapper-common_1.50-1ubuntu1_all.deb
- ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
- rt2870.inf (and rt2870.sys rt2870.cat)
Here: [http://uploading.com/files/d5a481a1/DWA130-Ubuntu.RAR/](http://uploading.com/files/d5a481a1/DWA130-Ubuntu.RAR/)
(I personally uploaded them into 1 .rar file because I couldnt remember where I originally downloaded them, except for the dlink driver which was on the dlink support website. If you dont trust me, then you can just google search each file above and you should find them)

2. Drag all files from file above to the desktop.

3. I opened up Terminal (Applications > Accessories > Terminal) and typed:
```
cd ~/Desktop
[Press Enter]
sudo dpkg -i *.deb
```
This installs ndiswrapper and ndisgtk.

4. Type "ndisgtk" in Terminal to open it up.

5. Click "Install New Driver" and go to your desktop and choose the file "rt2870.inf"

6. It should give you an error message, IGNORE it. After you install the driver and press close when the error pops up (if it does), a new driver should appear at the left side, and should say "Hardware Present: Yes" under the name of the driver.

7. Restart ubuntu and it should work.

******************************

---

### Post by Peter09 on 2010-05-25
OK the commanf is 
lsusb (it starts with an l not a 1)

Be good if you could post the output of the command

```
lsusb
```
and
```
ifconfig
```


Do these commands without the wired network connected.

---

### Post by iMattcotv on 2010-05-25
lmao I found that out like a minute before reading this. I swear the 1 and l look identical on the instructions sites -.-

anyway, after typing "lsusb":

Bus 002 Device 002: ID 07d1:3c13 D-Link System
(there were alot of other similar but were all Linux)

and for ifconfig, interface eth0, l0 and wlan0 all pretty much have the same type of info except for eth0 which at the bottom shows "Interupt: 17"

and iwconfig:

l0 and eth0 show "no wireless extensions"

wlan0 shows:

 IEEE 802.11bgn ESSID (a bunch of letters and numbers divided like "\xA3\xH9\")
Mode: Managed Frequency: 2.437GHz Access Point: Not-Associated
Tx-Power=11 dBm
Retry long limit:7 RTS thr:off Fragent thr:off
Power Management:on

sorry for cutting down the exact results, I'm typing this stuff on my iPod touch -.- lol

---

### Post by Peter09 on 2010-05-25
If you look at my signature it shows you how to get the output into a file.

---

### Post by Peter09 on 2010-05-25
This looks like an upto date solution to your device.
 
 
[http://ubuntuforums.org/showthread.php?t=1354191](http://ubuntuforums.org/showthread.php?t=1354191)

---

### Post by iMattcotv on 2010-05-25
hmmm Ill try that and see if it works.

They say my rev should already work since its B and it has a linux driver... I guess ill just have to re install the drivers again.

See ya in a bit!

---

### Post by iMattcotv on 2010-05-25
1 problem actually..

I have absolutely no way of getting a wired connection, but the instructions are telling me:

> With you wired connection go to System---Administration--Synaptic package manager and search for Ndisgtk. It will find three files, check these off and tell it to load them.

After this, put those two files somewhere (mine are in my home folder) Plug in the usb dongle and go to System---Administration--windows wireless drivers and tell it to install a new driver---pointing it at the .inf file (wherever you stored it). 
It will first say hardware not found ignore it. And if you press configure the network it will say tool not found ignore that too.
It will eventual show up if the drivers are correct versions.
Go to System--Preferences--Network connections and set up your network connections. Right now something in 9.10 is preventing you from using encryption so remove it from your AP for now. Hopefully, it will be corrected soon. Reboot the system.


Remove the wired connection and hopefully enjoy the wireless.
If you want to make sure that your device has been found correctly you can go to the terminal Applications---Accessories---Terminal and type in lsusb (LSUSB) in lowercase and it should show up.

Would these instructions be able to work if I get the files for ndisgtk manually? I think I have the right files, the GUI does come up but I know there were a few errors after adding a driver and showing up in terminal

---

### Post by Peter09 on 2010-05-25
You can get the files using the wired connection - but when you do the install you should remove the wired connection.

---

### Post by iMattcotv on 2010-05-25
but I dont have access to any wires, so I dont have a wired connection, at all.

The only thing I got is a USB adapter, what can I do?

---

### Post by Peter09 on 2010-05-25
If you have never connected to the internet to do an upgrade then this is may be the main cause of your problem. You really need to get connected somehow.
 
..... thinking.....thinking....

---

### Post by Peter09 on 2010-05-25
Do you not have physical access to your wireless router?

---

### Post by bkratz on 2010-05-25
> **iMattcotv said:**
> 1 problem actually..

I have absolutely no way of getting a wired connection, but the instructions are telling me:



Would these instructions be able to work if I get the files for ndisgtk manually? I think I have the right files, the GUI does come up but I know there were a few errors after adding a driver and showing up in terminal

Just noticed your thread. Sorry to but in so late--but you already seem to have the necessary files and a functional interface, since it says managed and you can actually see AP's. It was the hardway, but you seem to have gotten the correct ndis...files and installed them. If you left click on the network manager icon, do you see available connections? I was never able to get wep working (if that is what your connection is), but changing the router to wpa2 with aes encryption only allows perfect connections (and is way more secure). I will subscribe and check back later.


sorry, I am the one in that other thread!

---

### Post by iMattcotv on 2010-05-25
:o Thanks for subscribing :)
I was looking around and your name was popping up  erywhere lol

So yea my adapter is able to see aps and it does try to connect but after a minute or 2 it just fails.
I do have acces to my router/modem but they are sepperated very far away from my pc.   

The router is in the basement, my room is on the 1st level and the modem is on the second level (I have no idea why.. lmao)

The aps thati am connecting to are either not protected, or are wpa-wpa2 psk/aes.

And actually, i don't even seem to see my own network.. It sees everyone elses but mine and it's protected with wpa (or wpa2 can't remember).

If I boot back into windows the adapter finds my network easily.

---

### Post by iMattcotv on 2010-05-25
wtf.. I don't know what the hell I did, but now it works lol

I think it would be best to understand why it's working, so that I know and can understand.

Now that I have a connection, are there any updates I need to do, plugin I need to download?

---

### Post by bkratz on 2010-05-25
> **iMattcotv said:**
> wtf.. I don't know what the hell I did, but now it works lol

I think it would be best to understand why it's working, so that I know and can understand.

Now that I have a connection, are there any updates I need to do, plugin I need to download?



Just got home and was pleasantly surprised, congratulations! Did you perhaps happen to reboot the router? That seems to make a difference sometimes. It would be nice to know whether you are using wpa or wpa2, and tkip or aes  or a combination of both. I ended up having to choose wpa2 only with aes only to get mine to work and I tried everything.  It also made a difference with version of ndiswrapper ( 1.55 was not good with 9.10) was used. I had to build my own ndiswrapper and update to a different kernel to get that version to work. In 10.04 it seemed to use the newer kernel and version 1.54 connecting immediately. After you have enjoyed your accomplishment, if you wish to pursue it further please PM me.  You probably should mark the thread as solved with the above thread tools in case it helps someone else.


and no-no special updates are required-just your standard normal ones.

---

### Post by iMattcotv on 2010-05-25
ahh, well thank you to everyone who helped me out, i'm glad I finally got it working!

Ubuntu is ridiculously fast.. I mean, running it heavily on a live cd is faster than windows 7 on my machine lol

my network encryption is WPA-Personal

btw, the first time I shutdown my computer through ubuntu and then loaded it back up, i could not load windows 7 at all. the monitor went completely black for about a minute and then a thin line of pixilated colors showed up at the very top of the screen the width of the screen.

It was weird and I was scared <snip> because I have so much info on my pc that i absolutely need.

So i freaked out, grabbed my external hdd and did a back up, but after I restarted the computer it booted w7 fine... I was absolutely shocked and happy that it worked but <snip> that i wasted 9 hours backing up all my crap..

Why did that happen? lol

---

### Post by iMattcotv on 2010-05-25
BTW, for those who may run into this problem with their D-Link DWA130 REVB USB Router, heres what I did to eventually get it to connect to a network:

1. Downloaded ndiswrapper, ndisgtk and the dlink driver (WindowsXP2K will work).
You can download these files:
- ndisgtk_0.8.3-1.deb
- ndiswrapper-common_1.50-1ubuntu1_all.deb
- ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
- rt2870.inf (and rt2870.sys rt2870.cat)
Here: [http://uploading.com/files/d5a481a1/DWA130-Ubuntu.RAR/](http://uploading.com/files/d5a481a1/DWA130-Ubuntu.RAR/)
(I personally uploaded them into 1 .rar file because I couldnt remember where I originally downloaded them, except for the dlink driver which was on the dlink support website. If you dont trust me, then you can just google search each file above and you should find them)

2. Drag all files from file above to the desktop.

3. I opened up Terminal (Applications > Accessories > Terminal) and typed:
```
cd ~/Desktop
[Press Enter]
sudo dpkg -i *.deb
```
This installs ndiswrapper and ndisgtk.

4. Type "ndisgtk" in Terminal to open it up.

5. Click "Install New Driver" and go to your desktop and choose the file "rt2870.inf"

6. It should give you an error message, IGNORE it. After you install the driver and press close when the error pops up (if it does), a new driver should appear at the left side, and should say "Hardware Present: Yes" under the name of the driver.

7. Restart ubuntu and it should work.

---

### Post by anewguy on 2010-05-25
> **iMattcotv said:**
> .... I was scared <snip> ....

Please see the forum rules for language.

Glad you have things working!

Dave ;)

---

