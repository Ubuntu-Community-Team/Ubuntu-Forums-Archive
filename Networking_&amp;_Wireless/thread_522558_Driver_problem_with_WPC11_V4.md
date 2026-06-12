---
title: "Driver problem with WPC11 V4"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by dogshoe21 on 2007-08-10
I have seen several posts regarding this issue and I need to mention that I'm an infant in the Linux world so I need some clarity on how to make this NDISWrapper program work. I have installed the NDISWrapper program and I have ready that you download the windows driver and this program is supposed to make this wireless card work. The problem is I don't know what kind of file I'm supposed to use for this driver. I've downloaded the driver from the RealTek chipset 8180 site but its an EXE and those dont work in Linux right? So I believe I need the INF file but I can't find this anywhere. Anyone have an idea???

Joel

---

### Post by Jamie Jackson on 2007-08-10
> **dogshoe21 said:**
> I have seen several posts regarding this issue and I need to mention that I'm an infant in the Linux world so I need some clarity on how to make this NDISWrapper program work. I have installed the NDISWrapper program and I have ready that you download the windows driver and this program is supposed to make this wireless card work. The problem is I don't know what kind of file I'm supposed to use for this driver. I've downloaded the driver from the RealTek chipset 8180 site but its an EXE and those dont work in Linux right? So I believe I need the INF file but I can't find this anywhere. Anyone have an idea???

Joel

There's a chance that this is a zip or a cab file. Try the following
```

# install the extraction tools you need
sudo apt-get install cabextract unzip
# try expanding it with cabextract
cabextract yourfile.exe
# if that doesn't work, try
unzip yourfile.exe

```

...otherwise, I suppose you could run the exe in wine to get the inf and sys.

---

### Post by dogshoe21 on 2007-08-10
So once a driver is installed, there should be an INF file associated with this driver that stays on the machine? Cause if so, I could also get this file by booting into windows XP and then finding this file, copying it to the USB drive and then booting back into Linux and bringing the file in... How does that sound?

---

### Post by Jamie Jackson on 2007-08-10
That might be fine (depending whether that particular driver/version is supported by ndiswrapper), but I think you'll need both the .INF and the .SYS.

---

### Post by dogshoe21 on 2007-08-11
Thanks for the help, I have made some progress... I have copied the LSRTNDS.INF file from the executable driver that I downloaded and used the NDISWrapper and now if I go to System/Administration/Network I now see Wireless in my network settings. The problem is that all the settings are grayed out so I believe its not fully enabled. Any ideas now?

---

### Post by dogshoe21 on 2007-08-11
I found another thread that suggested removing the blacklist of the 8180 driver so I did this and now I can see wireless networks but I can not connect to any of them no matter what I do. Any one have any ideas on what comands I need to use to get this working?

---

### Post by Jamie Jackson on 2007-08-11
> **dogshoe21 said:**
> I found another thread that suggested removing the blacklist of the 8180 driver so I did this and now I can see wireless networks but I can not connect to any of them no matter what I do. Any one have any ideas on what comands I need to use to get this working?

Where are you "seeing" these networks? NetworkManager (applet in the status panel in default Feisty installations)? Or are you seeing them in "iwlist ethX scanning"? Somewhere else?

---

### Post by dogshoe21 on 2007-08-11
I see these networks when I click on the network Icon on the menu bar on the top. It show the wired connection and then several wireless networks with no signal...

---

### Post by Jamie Jackson on 2007-08-12
> **dogshoe21 said:**
> I see these networks when I click on the network Icon on the menu bar on the top. It show the wired connection and then several wireless networks with no signal...

Okay, that's probably NetworkManager's nm-applet that you're looking at.

[This wiki article]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") goes into driver installation for another kind of card, but it has some stuff that's probably pertinent in your case, too.

In particular, here are some lines from the above howto that you might be missing, to let NetworkManager control your network interfaces:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
```

Then, try:
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

There might be some other interesting bits in the wiki for you, too

---

### Post by dogshoe21 on 2007-08-12
Below is my fix for anyone that has a linksys WPC11 V4 wireless card and is using Feisty. This is a RealTek 8180 chipset.

When I installed Ubuntu Feisty I couldn't connect via wireless, and the system didn't see the card at all. I then realized after looking on all the forums that I'm not alone and there is a lot of confusion on how to get this working. I am writing this as a complete newbie so please bare with me.

Once I had Feisty installed, I connected to the web via a wired Ethernet connection and then went to: SYSTEM >  ADMINISTRATION >  UPDATE MANAGER. ( I read that I needed NDISWrapper and that it was on my cd but I couldn't find it) I then ran all of the updates (which took 30 minutes) and once they were installed, I rebooted the system. 

Once the machine was up I went to SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER and viewed “Not Installed” and scrolled down until I found NDISWrapper, selected it and then applied the update it to install it. 

After this was installed I then rebooted the system again, only in my case I have a dual boot setup so I have a working version of windows xp that this wireless card works just fine on. I went online and since my disc with the driver's is missing I went online and found it to download. The file name you want is:
WPC11v4_20040217.exe I got this file from Linksys's website under downloads and then drivers. (Don't ask me why this isn't a .zip file but its an .exe file that when you run it, it unzips) I unzipped this file in windows and then located these 4 files that were extracted:

LSRTNDS.INF
LSWL2NDS.INF
LSWLNDS.SYS
RTL8180.SYS

Save these files to a USB flash drive or CD or if you know what your doing (I sure don't) unzip this file in Linux and then place these specific files in a folder that is easy to remember.

Once you are booted up in linux and have these files saved somewhere you can get to again, go up to SYSTEM > ADMINISTRATION > WINDOWS WIRELESS DRIVERS. Now in the box that popped up, click on “install new driver” and then browse to the files that you saved earlier and select LSRTNDS.INF and click “open” and then click “install”. Once this is done I rebooted the machine again.

After the machine is back up I then was able to see wireless networks but was unable to connect to any of them. I then ran this command and got this response:

lsmod | grep 818

r818x                  89996  0 

ieee80211_rtl          80392  1 r818x


Then I was told by some people in the chat to type these commands:

joel@ubuntu:~$ sudo modprobe -r r818x


joel@ubuntu:~$ sudo modprobe -r ndiswrapper


joel@ubuntu:~$ sudo modprobe ndiswrapper


joel@ubuntu:~$ iwconfig


lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b  ESSID:"uoykcuf"  

          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:02:B1:9E   

          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  

          RTS thr=2432 B   Fragment thr=2432 B   

          Power Management:off

          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:1  Invalid misc:264167864   Missed beacon:0




Once I got these responses, I went up to the top menu bar and clicked on the network Icon, selected my Network and then PRESTO!!! I was online. Now I did do a few things to my router to ensure I could connect, I removed all security, (No WEP) and then removed my Access list settings, so pretty much anyone could log on and use my connection. I am working on putting the security back on, I'm going to put the access list back on and I imagine that should suffice for now. Now, you need to type in this command:
joel@ubuntu:~$ gksudo gedit /etc/modules


and then in the editor, add the word: ndiswrapper on one of the blank lines and make sure you save it by going to the top to “Documents” and choosing “Save All”. Please post if you have any issues, I am going to blow up this machine and try these steps myself to ensure they work perfectly again. Try these steps and let me know...

:)

---

### Post by Jamie Jackson on 2007-08-12
> **dogshoe21 said:**
> Once you are booted up in linux and have these files saved somewhere you can get to again, go up to SYSTEM > ADMINISTRATION > WINDOWS WIRELESS DRIVERS.

Note: This requires the ndisgtk package ("sudo apt-get install ndisgtk").

---

### Post by myk.dinis on 2007-08-17
How do I apt-get when I have no Internet connection? I have it on another wired machine but I don't have a wired port for the notebook...

Any thoughts...

---

### Post by numus on 2007-08-17
> **dogshoe21 said:**
> 

Then I was told by some people in the chat to type these commands:

joel@ubuntu:~$ sudo modprobe -r r818x


joel@ubuntu:~$ sudo modprobe -r ndiswrapper


joel@ubuntu:~$ sudo modprobe ndiswrapper


joel@ubuntu:~$ iwconfig

:)
This actually gets my wireless card to pick up signals.. my question is am i going to have to do this every time i turn on my computer? everytime i restart i get the same problem and have to do this or is there a fix for it....

---

### Post by dogshoe21 on 2007-08-17
Numus, if you follow this, you won't have to do this every time, you'll see the wireless networks once your machine boots:

gksudo gedit /etc/modules


 in the editor that opens up add the word: ndiswrapper on one of the blank lines and make sure you save it by going to the top to “Documents” and choosing “Save All”.

This is make sure everything starts correctly after you reboot.

---

### Post by dogshoe21 on 2007-08-17
Myk.dinis, from what I read, the NDISWrapper is supposed to be on the latest Feisty Fawn ISO, you could try and download the latest ISO and then use the Synaptic Package Manager to install the NDISWrapper tool. I would try this, maybe someone else that's got more experience would have more ideas...

---

### Post by Jamie Jackson on 2007-08-17
> **myk.dinis said:**
> How do I apt-get when I have no Internet connection? I have it on another wired machine but I don't have a wired port for the notebook...

Any thoughts...

[This]("http://ubuntuforums.org/showpost.php?p=3022036&postcount=21") is from a different topic, so the files won't be exactly as advertised, but you should be able to adapt them to the files you need.

---

### Post by gabe6118 on 2007-08-20
I am having a similar problem but when I enter these commands I get a message saying "-r is not an option" any help here?

---

### Post by DarkN00b on 2007-10-11
I know I'm dragging up an old thread here, but I thought I'd point out that Gutsy Gibbon kernel 2.6.22-14 has native support for this chipset. I found a a Linksys WPC11 ver. 4 PCMCIA card at Goodwill for US$2.99. :mrgreen:

I plugged it in, configured WICD to use the card and scan for networks and it worked just fine.

---

### Post by josephcherng on 2007-11-18
i've just dug out an old Thinkpad 390 E and installed Xubuntu 7.10...Like the previous post, the Linksys WPC11 v.4 is recognized and does scan for networks. problem is, when i'm about to connect to a network, the computer locks-up and doesn't respond. Any help?

I've already modified the config.opts file following the steps from the community docs.

thanks in advance.

---

### Post by killdragon on 2007-11-18
Join Date: Mar 2006
Beans: 9
Re: Linux driver or ndiswrapper for RTL8180L chipset?
Quote:
Originally Posted by killdragon View Post
Hi, try the following I used it and it works for me. And this is the the title of the thread

that I found it at. The only reason is that you have a realtek card that I think it might

work.




Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty




To use the native driver, you need to remove the r818x blacklist entry, like so:

Code:

sudo editor /etc/modprobe.d/blacklist

Page down to the bottom, and you'll find some lines that look like this:

Code:

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

Any line that begins with "#" is ignored, so add "#" in front of the r818x line to turn off the blacklisting of this module. Save the file, eject and re-insert the card, and it should be recognized. Again, see the thread I linked above for more info.


Additionally, another thread discovered that for the essid, an additional character needs to be appended to the end (any character will do, although 'x' seems to be the current favorite). Thus, if your essid is "ducky", you'll need to use "duckyx".

So, without further delay, here is what is currently working well for me (after I plug in the card):

Code:

sudo modprobe r818x
sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0




I have also found that you should only use Ubuntu's network tool.
__________________

---

