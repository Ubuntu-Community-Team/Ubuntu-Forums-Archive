---
title: "broadcom 4328--still trying"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by flyingsolo on 2007-01-11
I've been frustrated before trying to get this to work & put it aside for some time but going to go at it again. (much thanks to frodob for patience & assistance 1st time)
I haven't seen another successful post for this device but am wondering if it is reasonable to follow one of the posts dealing with broadcom 4318 or broadcom 43** while just substituting my particular broadcom drivers extracted from windows?  Must I have the very latest ndiswrapper?  Are there any other particular problems I should be aware of starting out again?

---

### Post by revmc on 2007-01-11
Although this is written for Dapper, it is the process I followed for my BCM43xx, I works and I use Edgy.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

I a newbie but I think the process works for all bcm43xx's.

Bill

---

### Post by flyingsolo on 2007-01-11
Thanks--I'm using Edgy but maybe this can be adapted.  I currently have ndiswrapper utils version 1.9 & driver version 1.29.  I have driver bcmwl5 installed but ndiswrapper calls this  an "invalid driver!".  I had obtained it from the downloaded windows driver for my wireless.

---

### Post by flyingsolo on 2007-01-12
Any thoughts on how to proceed would be appreciated!  (started this post late last night)

---

### Post by oyvinvo on 2007-03-05
I've been trying to get my wireless card to work aswell. Fetched the drivers from acers ftp server but it looks like ndiswrapper only recognice the drivers as 64bit version. If I try to delete the bcmwl564.sys and use ndiswrapper with just bcmwl5.sys and the .inf file I get the same error as you. Been trying to get this to work for some days now, but I'm stuck:X

---

### Post by oyvinvo on 2007-03-06
Hey, I got mine working now.
After trying many different drivers I finally found one working. Try it yourself and maybe you're lucky;)
[R140746.EXE]("http://ftp.us.dell.com/network/R140746.EXE")

use unzip R140746.EXE to unpack it.

Hope this works for you aswell.

---

### Post by flyingsolo on 2007-03-09
Oyvinvo--sorry, I missed your posts when they were fresh; can you post more details of how you set it up or which tutorial you may have followed?  Were there any other issues encountered getting this to work?  Yours is the most hopeful post about getting this chipset to work I've seen yet!

---

### Post by kayvortex on 2007-05-28
Hi. I'm in the same situation as you: apparently, my Dell 1500 Draft 802.11n WLAN mini card (on an Inspiron 9400) won't work because it uses the bcm 4328 chipset. I'm no expert, but this is what I'm trying:

1) I download a Dell 1500 driver from [http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INS_PNT_P4_9400&servicetag=&os=WW1&osl=en&deviceid=12300&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INS_PNT_P4_9400&servicetag=&os=WW1&osl=en&deviceid=12300&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136), but note that it is an "outside Japan/US" version (although I don't think that matters much for what we're doing.....I think!)

2) I unzip that file (R151517.EXE). Note that this will spill quite a few files into the directory that R151517.EXE is in. The file that I will be using is in an unzipped directory called "DRIVER" and is called "bcmwl5.inf".

3) I then followed the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) , to install ndiswrapper (except that I used ndiswrapper-1.9 instead of ndiswrapper-1.8 ) and installed that "bcmwl5.inf" file.

4) Then I stopped. I can't check to see if my wireless connection is working right now, so i didn't configure the wireless card.

Note, there are some other drivers that I could use if the one above doesn't work: there is the one oyvinvo suggested, and there is this one: [http://ftp.us.dell.com/network/R129083.EXE](http://ftp.us.dell.com/network/R129083.EXE) (according to [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)).

I will look to see if this has worked in about a month's time, but until then, good luck!

---

### Post by eddbaez on 2007-06-05
I'm in the same situation if you have any info how to install broadcom 4328 in ubuntu please let me know ,I have try pretty much everything I have found in google and ubuntu forums 
thanks

---

### Post by hurricanesfan66 on 2007-06-06
Same here.  Got the 4328 in an Inspiron E1705.  Tried all the methods on the forums, to no avail.

---

### Post by hurricanesfan66 on 2007-06-10
Ok, somehow I made it where it is recognizing the card, *I think.*

This is what iwconfig spits out:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=270 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

No Wifi light or connection though...

---

### Post by kayvortex on 2007-06-13
Right, I got my Dell Wireless 1500 Draft 802.11n WLAN mini card (which uses the Broadcom bcm4328 chipset) to work on my Inspiron 9400 (also called the E1705). This is what I did:

**[SIZE="2"]Download Driver[/SIZE]**

Go to the Dell Support page and download the "Dell Wireless 1500 Draft 802.11n WLAN mini Card" driver, which is called "R151517.EXE". I haven't tried the US or Japanese drivers because, basically, I can't be arsed to wait for the 52MB download to finish...I will do later though.

*Edit: The drivers can be downloaded at Dell's ftp site: there is a [US driver]("ftp://ftp.dell.com/network/R151519.EXE"), a [Japanese driver]("ftp://ftp.dell.com/network/R151518.EXE"), and an [Everywhere-else driver]("ftp://ftp.dell.com/network/R151517.EXE"). Note that I have only tried the "Everywhere-else" driver yet, but I'm not sure that they differ at all in what we want to do with them.*

*Note that if you don't have a Dell computer/notebook, you should try a driver provided by your supplier first since that is more likely to work.*

Unzip the file, but beware that it will spill out quite a few files:

```
unzip /*download_directory*/R151517.EXE
```

**[SIZE="2"]Install Ndiswrapper[/SIZE]**

We'll be using the ndiswrapper program, so we need to install that. Note that it is provided on the Ubuntu install CD (and the Alternate CD) so we're not stuck in the ridiculous position of requiring an internet connect in order to provide an internet connection (at least for a wireless connection). Also, there is no pre-installed driver provided for this chipset, so there is no need to worry about conflicts until one appears.

The particular files we need from the R151517.exe driver are the ones in the directory "DRIVER". They are all required (I gather), but we only need to tell ndiswrapper about the one with the .inf extension: for this driver, it is called "bcmwl5.inf" (but may be called a different name for different drivers).

Install Ndiswrapper and the .inf file:

```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /*download_directory*/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
```

Then, set ndiswrapper to load on startup:

```
sudo ndiswrapper -m
gksudo gedit /etc/modules
```

and add the following module to the list 

[INDENT]ndiswrapper[/INDENT]

That's it!

Finally, don't forget to check if the wireless card is switched on! And, also note that although the Dell driver is for both i386 and x86-64 systems, it's functionality on Linux x86-64 systems is a bit hit-and-miss (which may also be true for drivers from other manufacturers).



Now, hurricanesfan66, which driver did you use? Your iwconfig output is what I get when I'm not connected, but I just wait a minute and try connecting again. After a few tries, I can usually connect. Also, if your wireless light is not on, it might just mean that your wireless card might be switched off (Fn - F2 on my E1705 toggles it on/off). If I remember correctly, without this installation procedure that I describe above, Fn - F2 did not switch the light on/off; only afterwards could I do so. Try pressing Fn - F2 (or the appropriate button), wait a while, and if the light comes on it *could* be a good sign; then try connecting.

---

### Post by hurricanesfan66 on 2007-06-15
Wow!!!  It was just that easy--toggling the FN-wifi button.  (-:  I wonder if that is a problem many are having.  I never even thought to do that, as with Windows, it was always turned on...

Thanks!!!

---

### Post by kayvortex on 2007-06-24
That's ok! I'm glad to help. Maybe forgetting to switch the card on might be the problem some people are having! ... But I think you, and others, would have realized that yourselves after a while (I hope!): they *must* have some more fundamental a problem.

On that note, I wonder if this solution is general, rather than only a solution that works for a few people. If this does work for anybody else, maybe they could just mention so. If there are any problems, I'll try my best to help.

---

### Post by Jrscienceguy on 2007-07-26
So i dont know if im dong something wrong here or what but when i run the command 

james@james-laptop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

shows up. Now im not very terminal savvy so i have no idea even where to begin to solve this problem. 

Any Help would be greatly appreciated.
Thanks

Edit : So i fixed the error by compiling ndiswrapper from source, but my wireless card is still not showing up with iwconfig or anything. Ive tried toggling the wireless switch to no avail, if anybody has any ideas or knows whati might be doing wrong, help would be greatly appreciated.

---

### Post by Jrscienceguy on 2007-07-27
Some haow i fixed the problem... I have no idea what i did because i just tried like 50 different drivers and reinstalled many times, but whatever it was it worked, YAY BLUE LIGHT ! :)

---

### Post by kayvortex on 2007-08-05
Well, I suppose it must have been some sort of a driver issue (~50? That's impressive: I'd have given up about 45 attempts before that)! I was going to install a couple of different drivers and evaluate which ones seem to do a good job: the one that I currently use sometimes can't make a connection at all. Strange. Although, recently its been behaving admirably. Very strange. Can I ask which one you are currently using? 

Anyway, I'm glad you (somehow!) got your wireless working. Happy surfing!

---

### Post by Er1ck on 2007-11-12
Thank you sooo much. I had purchased a HP Pavilion DV6646US with the draftN wireless card broadcom 4328 and I couldn't get the wireless to work until I read this thread and got it working. Thank you soo much and I appreciate all of your efforts.

---

### Post by oyvinvo on 2008-01-24
For some reason I got this working at the first try on my ferrari 1005 and 32-bit install of ubuntu now. Here's how:

First I installed ndiswrapper utils.
```
sudo aptitude install ndiswrapper-utils-1.9
```

Then I downloaded the windows driver from acer support and unzipped them. 
```
wget ftp://ftp.work.acer-euro.com/notebook/ferrari_1000/driver/WLan%20Driver%20802.11n%20Rel.%204.80.28.7.zip
unzip WLan\ Driver\ 802.11n\ Rel.\ 4.80.28.7.zip

```

Next step is to make ndiswrapper use this windows driver.
```

cd 80211n
sudo ndiswrapper -i bcmwl5.inf

```

Which gave me this ouput.
> 
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2


ndiswrapper should now tell you that the device is present,
```
sudo ndiswrapper -l
```
> 
bcmwl5 : driver installed
        device (14E4:4328) present


Next step is to add an alias.

```
sudo ndiswrapper -m
```
> adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

Now try modprobe it and it will hopefully work as it did for me:)
```
sudo modprobe ndiswrapper
```

Last you should add ndiswrapper to /etc/modules so it will load ndiswrapper on startup.
Just use your favourite editor and add a new line at the bottom of the file and type in: ndiswrapper
save and close the file.

---

### Post by hasin on 2008-02-27
Hi kayvortex

Thanks a lot. I've got my BCM4328 Working on my lappy (Dell Inspiron 6400). After trying, searching and crying for more than one month I just got it working. Thanks a :lolflag:

-Hasin 

> **kayvortex said:**
> Hi. I'm in the same situation as you: apparently, my Dell 1500 Draft 802.11n WLAN mini card (on an Inspiron 9400) won't work because it uses the bcm 4328 chipset. I'm no expert, but this is what I'm trying:

1) I download a Dell 1500 driver from [http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INS_PNT_P4_9400&servicetag=&os=WW1&osl=en&deviceid=12300&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INS_PNT_P4_9400&servicetag=&os=WW1&osl=en&deviceid=12300&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136), but note that it is an "outside Japan/US" version (although I don't think that matters much for what we're doing.....I think!)

2) I unzip that file (R151517.EXE). Note that this will spill quite a few files into the directory that R151517.EXE is in. The file that I will be using is in an unzipped directory called "DRIVER" and is called "bcmwl5.inf".

3) I then followed the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) , to install ndiswrapper (except that I used ndiswrapper-1.9 instead of ndiswrapper-1.8 ) and installed that "bcmwl5.inf" file.

4) Then I stopped. I can't check to see if my wireless connection is working right now, so i didn't configure the wireless card.

Note, there are some other drivers that I could use if the one above doesn't work: there is the one oyvinvo suggested, and there is this one: [http://ftp.us.dell.com/network/R129083.EXE](http://ftp.us.dell.com/network/R129083.EXE) (according to [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)).

I will look to see if this has worked in about a month's time, but until then, good luck!

---

### Post by deerewright on 2008-02-28
Thanks to this thread and maybe some bios setup I was able to get mine to work as well!!

I have a Dell XPS m1210 with the BCM4328 wifi card installed.  I have had ubuntu 7.04 working and a previous install of 7.10 also working earlier, but after getting some kind of virus or trojan horse (something kept downloading invisible files to my hard drive and filling it up), I reformated / and did a fresh install of 7.10.  Afterwords, no matter what I tried, I could not get the adapter to power up. 

I was able to get it to work yesterday just using the "ndisgtk", but when Gutsy failed to boot after some updates, I started all over again, and no matter what I tried, worked.

I THINK what finally did it was adding the ndiswrapper to the modules file.  But modprobe would not load it.  I had to reboot to get it to power on.  

Another thing I did was to change my wireless settings in bios.

The XPS m1210 has a wireless switch on the side that can be setup to control BT, wifi, cellular, etc.  There are several options in the setup.  You can use the switch to control an individual TX/RX or just about any combination, including "ALL"

   Mine was set to"ALL, but I only have BT and wifi, so I changed it to "BT and WiFi".  It took quite a bit longer to boot the first time, but the wifi powered  on during ubuntu boot.

Sorry, I got so long winded, but hopefully it will save someone else the time and aggravation!

---

### Post by jkeyes0 on 2008-03-28
I followed the directions a lot of you posted in this thread (I have a Dell XPS m1530 with a Dell wireless 1505 draft-n card, bcm4328 ) and I managed to get connected, but only at a maximum of 130Mbps. In Windows, it will connect up to 270Mbps. 

I think it has something to do with the band it's using (20mhz vs 40mhz needed) but I'm not sure where to go from here.

I'm going to attempt this evening to use the newest driver (from 12/18/07) and see if I can get a faster speed. I've currently got Vista on it, and I'd really love to do away with that...

---

### Post by LeslieL on 2008-04-28
This thread and (similar) help at [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes) and the related [http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html](http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html) helped me get a broadcom 4328 working under Hardy Heron. I may have spoken too soon - it seems to take some fiddling to get it working when I restart - but I'm using it to write this message. Thanks, everyone.

---

### Post by rbolio on 2008-04-28
well, let me tell you that you aint the only ones with that problem, i have a inspiron 6400 with a broadcom 4401 ....and it ain't working! -.- it was working with gutsy but no luck with hardy, and i have tried everything too... DAMN...

---

### Post by jjremy on 2008-04-29
Kayvortex: I can't thank you enough! I've been trying to get my wifi working for days to no avail. THANK YOU! Now Ubuntu is everything I need it to be!

---

### Post by adamos on 2008-04-30
> **rbolio said:**
> well, let me tell you that you aint the only ones with that problem, i have a inspiron 6400 with a broadcom 4401 ....and it ain't working! -.- it was working with gutsy but no luck with hardy, and i have tried everything too... DAMN...

I made a write up for the 4328 which explains it pretty forward. 4401 - i ve never worked with this card. Go get a usb wifi adapter. they are cheap. check the sticky list for supported usb wifi adapters

---

### Post by bishboria on 2008-05-04
> **kayvortex said:**
> Right, I got my Dell Wireless 1500 Draft 802.11n WLAN mini card (which uses the Broadcom bcm4328 chipset) to work on my Inspiron 9400 (also called the E1705). This is what I did:

**[SIZE="2"]Download Driver[/SIZE]**

Go to the Dell Support page and download the "Dell Wireless 1500 Draft 802.11n WLAN mini Card" driver, which is called "R151517.EXE". I haven't tried the US or Japanese drivers because, basically, I can't be arsed to wait for the 52MB download to finish...I will do later though.

*Edit: The drivers can be downloaded at Dell's ftp site: there is a [US driver]("ftp://ftp.dell.com/network/R151519.EXE"), a [Japanese driver]("ftp://ftp.dell.com/network/R151518.EXE"), and an [Everywhere-else driver]("ftp://ftp.dell.com/network/R151517.EXE"). Note that I have only tried the "Everywhere-else" driver yet, but I'm not sure that they differ at all in what we want to do with them.*

*Note that if you don't have a Dell computer/notebook, you should try a driver provided by your supplier first since that is more likely to work.*

Unzip the file, but beware that it will spill out quite a few files:

```
unzip /*download_directory*/R151517.EXE
```

**[SIZE="2"]Install Ndiswrapper[/SIZE]**

We'll be using the ndiswrapper program, so we need to install that. Note that it is provided on the Ubuntu install CD (and the Alternate CD) so we're not stuck in the ridiculous position of requiring an internet connect in order to provide an internet connection (at least for a wireless connection). Also, there is no pre-installed driver provided for this chipset, so there is no need to worry about conflicts until one appears.

The particular files we need from the R151517.exe driver are the ones in the directory "DRIVER". They are all required (I gather), but we only need to tell ndiswrapper about the one with the .inf extension: for this driver, it is called "bcmwl5.inf" (but may be called a different name for different drivers).

Install Ndiswrapper and the .inf file:

```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /*download_directory*/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
```

Then, set ndiswrapper to load on startup:

```
sudo ndiswrapper -m
gksudo gedit /etc/modules
```

and add the following module to the list 

[INDENT]ndiswrapper[/INDENT]

That's it!


Worked perfectly!  Cheers

---

### Post by joshr799 on 2008-05-28
There is also a solution here along with a script that automatically installs ndiswrapper, downloads the driver and installs it.  

[http://speedbump.ws/?p=12](http://speedbump.ws/?p=12)

This was tested on a Dell with the broadcom 4328 chipset using the Ubuntu 8.04 live cd and ndiswrapper version 1.50.

---

### Post by s1337m on 2008-06-20
> **joshr799 said:**
> There is also a solution here along with a script that automatically installs ndiswrapper, downloads the driver and installs it.  

[http://speedbump.ws/?p=12](http://speedbump.ws/?p=12)

This was tested on a Dell with the broadcom 4328 chipset using the Ubuntu 8.04 live cd and ndiswrapper version 1.50.

I have a Dell Wireless Dell 1500 WLAN, a BCM4328 card.  I tried the above tutorial and some other ones (notably that feisty one) with no luck.  I can detect all networks, but can only connect to unsecured networks.  Has anybody else encountered this... and if so please help!

---

