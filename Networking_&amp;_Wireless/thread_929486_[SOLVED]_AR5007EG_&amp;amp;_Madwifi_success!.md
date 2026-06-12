---
title: "[SOLVED] AR5007EG &amp;amp; Madwifi success!"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-09-25
Xubuntu 8.04 LTS

*First, uncheck the Hal & Atheros boxes in the Restricted Drivers preferences.

1) Download [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)

2) Uninstall network-manager from Synaptic

3) Download & install Wicd from the repository or from here [https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=626151](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=626151)

3) Install build-essential from the LiveCD by adding the CD from the Edit menu of Synaptic & then typing "sudo apt-get install build-essential" from terminal.

4) Right-click on the madwifi file & choose to "open terminal here".

5) Type "make"

6) Type "sudo make install"

7) Type "sudo mousepad /etc/modules" & add the following two lines, then save...

wlan_scan_sta
ath_pci

8 ) Type "sudo modprobe ath_pci" & "sudo modprobe wlan_scan_sta" for good measure!

9) Restart

10) In terminal, type "sudo mousepad /etc/network/interfaces" & make sure that these lines follow the first two "lo" lines and save...

auto ath0
iface ath0 inet dhcp

11) Open Wicd, and you should be looking at your network connection. Since mine required WPA encryption, I made sure that "WEXT" was present in the preference tab, then I proceeded to configure the advanced settings tab located under the network name. You'll have to select encryption and enter your key, as well as choose to have Wicd connect automatically at start-up and at connection loss.

12) That should be about it, although you may have to reboot once to set it.

(Also added ath_pci & ath5k to the blacklist folder)

---

### Post by fewjr on 2008-09-25
Hello Dapper,
     I have been having issues with my wireless and haven't gotten any response to my post as of yet. You can read it here:

[http://ubuntuforums.org/showthread.php?t=927123](http://ubuntuforums.org/showthread.php?t=927123)

I had similar problems with my first Ubuntu box. I never got an answer to this post either. I got it to work some how. I'm not sure how, it just started working. That post is here:

[http://ubuntuforums.org/showthread.php?t=838806](http://ubuntuforums.org/showthread.php?t=838806)

I am running Ubuntu not Kbuntu, but I am going to give your suggestions a try and let you know what happens. Mousepad I take it is a Kbuntu specific app. I will use gedit in its place. When I downloaded the newest release of Madwifi it promped me to remove old modules. I had already disabled HAL in restricted drivers and rebooted before I compiled the new driver. When I was done making new Madwifi driver, HAL didn't show up in Restricted drivers anymore. So I guess removing old modules took care of it. I'm not sure if the new Madwifi driver was supposed to add an updated HAL or not, or if it doesn't use it. I thought ath5k was doing away with HAL. Anyway, I did get my card to acquire an IP address and ping Google once, but it hasn't worked since. I was thinking of uninstalling Network Manager, and when I saw your post I knew I might be on the right track. Thanks and I'll let you know.

Regards
fewjr

---

### Post by mlnsharma on 2008-09-25
Hi Guys, I am a new user...iHave Ubuntu 8.04 installed in my pc now.. I use an ethernet card for accessing Internet in a LAN..When i use in xp it automatically detected the ethernet card..But in ubuntu it didnt...And even after manually configuring it is not detecting the card...Can any one help me with this issue...Pls do reply !!

---

### Post by DapperMe17 on 2008-09-25
I installed this madwifi right after a fresh install, so I didn't have to remove other modules. I suspect your on target though!

Wicd is hard to pass on1

The key part of this tutorial is definitely the part where you add 
"wlan_scan_sta" & "ath_pci", in that order. This part was the one that kept me up for days:popcorn:

Once I rebooted, the "wlan_scan_sta" entry allowed Wicd to "see" my network & "ath_pci" to load the driver.

I had my connection working by manually adding my network to the "/etc/network/interfaces" folder, along with Wieman01's WPA instructions. I almost gave up on Wicd!

However, I finally deleted all of the manual entries in the above folder, keeping only the two "lo" lines & then adding
"auto ath0" & "iface ath0 inet dhcp"....then trying configuration via Wicd & viola!!!

Good luck with yours:)

---

### Post by DapperMe17 on 2008-09-25
Yes, mousepad is the default file manager in Xubuntu, you'll just use "gedit" there.

---

### Post by fewjr on 2008-09-25
WOW:shock:...thats the fastest reply I've ever gotten on here! thanks for following up. My install is only a week or two old, so fresh I suppose. Like I said, the new Madwifi driver I downloaded prompted me to remove old modules when I did "make install" I believe. I have been following Madwifi beginner user guide on their homepage. It took me quite some time to get Hardy to install on this new computer. I finally had to add pci=nomsi to get it to work. The two issues I'm having are the wireless and the onboard video not working right with the nvidia driver (trying to get Compiz Fusion to work). I'm at work now...will update you tomorrow after I try it. Thanks again.

---

### Post by fewjr on 2008-09-25
mlnsharma said> Hi Guys, I am a new user...iHave Ubuntu 8.04 installed in my pc now.. I use an ethernet card for accessing Internet in a LAN..When i use in xp it automatically detected the ethernet card..But in ubuntu it didnt...And even after manually configuring it is not detecting the card...Can any one help me with this issue...Pls do reply !!

     You say ethernet card. Are you trying to connect with wireless or are you talking about a NIC that you plug a ethernet cable into?

---

### Post by DapperMe17 on 2008-09-25
I did read your previous post & see that your have a slightly different Atheros chip. 

Give my steps a shot, it may still work for you.

"Hardly" working I see :^o

---

### Post by DapperMe17 on 2008-09-25
mlnsharma,

I recommend that you start a new thread in the wired network forum.
You'll get more accurate advice there.

---

### Post by fewjr on 2008-09-25
Yeah...I know. AR-2413 = AR5005G. What is the difference in the numbers. If AR5005G is the chipset, what is the AR-2413?

---

### Post by fewjr on 2008-09-25
Also.....do you think I should start over and use the driver you show in the first step? I downloaded mine from Madwifi site (madwifi-0.9.4.tar.gz).

---

### Post by DapperMe17 on 2008-09-25
One is the Atheros card model #, while the other is the chipset #. 

Yes, I would start over & follow my tutorial. The madwifi link I provided above includes the latest HAL.

---

### Post by fewjr on 2008-09-25
How should I go about removing what I installed? I don't want to mess anything up. Talk to you tomorrow...got to do some work now. Thanks again.

---

### Post by DapperMe17 on 2008-09-25
Well, because I executed the tutorial after a fresh install of Ubuntu, I didn't have to remove anything. You might not have to, it would tell you while you were compiling the new madwifi from terminal. If you don't get an error, you can continue forward.

If you get an error, search the forum for a short list of commands to uninstall your madwifi version first.

Good luck!

---

### Post by fewjr on 2008-09-25
Ok....I am home now. Before I go to bed I thought I would try it. Since I already had a new driver I thought I would start at uninstalling network-manager and going from there. If that didn't work I was going to use the driver you used. I went to Synaptic>uninstalled network-manager. When I went to download wicd I had no connection on eth0. I tried to bring up eth0> "sudo ifconfig eth0 up". I still have no internet. I'm on my other computer now. What should I do. I'm thinking about a clean install already...lol.

---

### Post by DapperMe17 on 2008-09-25
Go for a clean install, it'll only take 15-30 minutes.

From your other PC, download Wicd & the Madwifi driver I mentioned...save it to a CD. 

You will have to install "build-essential" from the LiveCD. You go to synaptic, click on Edit in the navigation bar. You'll see a link to get files from the "CD". Click that, you'll maybe get a few mount errors. Don't worry about those. Then, go to a terminal window & type "sudo apt-get install build-essential". You'll see it install from the disk.

Copy the files on your other CD to your home folder. 

From there on out, follow my directions.

---

### Post by fewjr on 2008-09-26
Hi Again DapperMe17,
     When I got up today I tried to install wicd, which I put on a flash drive and transferred to the linuxbox in question. I couldn't do make...looked in wicd folder and followed install readme. I think it used some kind of perl commands. Anyway...it seemed to install okay. When I rebooted, I didn't see any icon in the bar for wicd, but under Applications>Internet there was an icon for the progam. When I clicked on it nothing happens, and I think it needs to be set to run on startup. Anyway, I think I will reinstall. We're going to the Winefest in Ocean City, Maryland tomorrow morning for the weekend. Thanks for all your help, and I will update you as soon as I get to work on it.

---

### Post by DapperMe17 on 2008-09-27
Fewjr,

You don't have to compile Wicd, you simply double-click on it & the package manager will take over & install it. Once you've rebooted, it will show in the panel. It should automatically show up in preferences-sessions.

Again, follow my instructions to a "T".

---

### Post by fewjr on 2008-09-29
Hello DapperMe17,
     I am back from the Winefest in Ocean City, MD. I reinstalled HardyHeron. The first thing I did after the fresh install was to go to Synaptic and install wicd...it prompted me to remove network manager and it installed wicd fine. I went to System>Preferences>Sessions....Startup Tab, added a new called Wicd and made the command /opt/wicd/tray.py to get the tray icon to showup at boot. I rebooted...good to go there. Next I ran this in the terminal:

```
sudo apt-get install build-essential linux-headers-generic
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
```

The file that was extracted was newer than the one here...the 20080801 number. Then I ran:

```
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```

     So I should have the latest Madwifi and wicd. I opened wicd and disconnected from my wired connection and tried to connect to my wireless connection. There is a problem though. There is no way to specify a shared or open network. It will let me put in my WEP key, but I can't put in shared. It would not connect to the wireless. So now what. I cannot find anything telling me how to apply that setting. I think I read that wicd uses wpa_supplicant to connect to WEP. There is a way to add startup,connect and shutdown scripts. I don't know what to do there. I'm stuck again my friend. Any ideas?

Regards,
fewjr/Buddy

---

### Post by DapperMe17 on 2008-09-29
Be sure to inactivate your wired connection in the "network" area of your system, preferences area. You can't have an active ethernet connection & expect the wireless to work without conflict.

If Wicd is seeing your network, it's a positive. However, I don't use the insecure WEP encryption, so I have no clue what you mean by "shared". Maybe you mean "restricted"? WEP definitely wouldn't be "open", it's an encryption process. 

Again, my suggestion is to follow my how-to above, it worked for me. 

If it doesn't help you, then you'll have to search the forum for help with your chip.


Bless you

---

### Post by fewjr on 2008-09-30
Okay...I guess I'm on my own now...LOL. Well when I set up my router a couple years ago, I set it up as WEP. There are settings for an open or shared network. I decided in my ignorance that 'shared' sounded more secure than 'open'. So thats how it is set up. I know from all this reading that WEP has been cracked for a while and I need to change to Wpa. I'll have to change all my wireless computers in the house too. Another project..yippee! Thanks though...I'll let you know when I figure it out.

---

### Post by fewjr on 2008-09-30
Okay....guess what. It works with wpa personal. So I hope anyone looking at this will see that wep was my problem. I changed my router to wpa personal....first with AES...but the two wireless laptops running Vista didn't like that. So I had to set it to AES and TKIP to allow those to connect. I am using network-manager with those settings and am connected. In my router it says I have a 100% signal. On Ubuntu network-manager it says I am at 12 Mbps. The card I'm using is supposed to be running 54Mbps. So now I have to figure this out. This is fun huh? So I guess I have to say solved for connection problem. Maybe next version of Ubuntu will work better...in case someone out there has no choice but to use WEP. Thanks Dapper.

Regards,
fewjr/Buddy

---

### Post by DapperMe17 on 2008-09-30
Depending on your router, sometimes "shared" can be confused with broadcasting both WPA1 & WPA2 signals (mixed-mode). 

Well done on your wireless, anyway you can get it done...well, will work!

Each individual network manager can give false readings. I've found Wicd to offer the most acurate. Keep in mind that these are open-source projects, mostly not supported by "official" wireless card manufacturers. So, readings "can" be off a bit. 

I've found that using Ndiswrapper & the Windows driver get me that accuracy. 

Consider 12mb/s plenty for any internet activity. Internal network transfers should be the only thing affected.

But, just don't ask me how to get it with this Atheros card...I had a hard enough time with mine!!!

---

### Post by jijin on 2008-10-09
A few notes about the tutorial... It works for me first of so..

tytytytytytytytytyty I have been at this for days...

Now I want to see if I can get aircrack working.

Anyway ... In the tutorial if you can rearrange it so that a n00b doesn't remove network-manager **before** they need to downlad wicd I'm sure it'll help alot more.  got stuck for a second after removing it and couldn't connect at all. :lolflag:

Also I had to add ath0 to the *preferences>wireless device* field as it didn't find the wifi card right of the bat. Note: "ath0" might not work for everybody.

To find out what you will need in that field type this into terminal

```
iwconfig
```

and it'll output something that looks like this:

```
jijin@pinja:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Not Yours - Go Away"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:6B:44:9C:01   
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:31  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ath0 was mine, yours might be wifi0 or even wifi1

Anyway, thanks for this... I wasn't too fond of network-manager in the first place.

---

