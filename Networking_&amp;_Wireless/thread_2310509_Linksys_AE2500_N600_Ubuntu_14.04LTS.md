---
title: "Linksys AE2500 N600 Ubuntu 14.04LTS"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by dogdaysunrise on 2016-01-19
I just installed ubuntu and I am an absolute noob. After many years of windows and reinstalling windows almost once a year due to issues, I am trying this.

Anyway, I want to install my Router. I searched the forums and googled.

Here's what I have done so far:
I installed ndiswrapper, I downloaded the XP Driver for said router.
From another Thread, I did this:

============
5) Open "bcmwlhigh5.inf" in gedit and add this line, around line 170:

 	Code:
 	[Linksys_AE2500.files.NTamd64]
  AE2500xp64.sys,,,6 
6) Run this command: `ndiswrapper -i bcmwlhigh5.inf`

At this point, the driver should be installed successfully. `ndiswrapper -l` should return

 	Code:
 	bcmwlhigh5 : driver installed
    device (13B1:003A) present
=============

When I run the command in Step 6, I get "



No such file or directory at /usr/sbin/ndiswrapper-1.9 line 162."

So I wasn't able to move the bcmwlhigh5.inf to usr/sbin/ so I followed these steps:

========================
 	Code:
 	sudo chown -R yourusername:yourusername /fullpath/tofolderyouwant 
If your username was dude and the path to minor bin one like this: /media/minorbin
Then the command would look like this for you:

 	Code:
 	sudo chown -R dude:dude /media/minorbin
======================

Now the inf file is in usr/sbin and so is ndiswrapper.

But when I run the Command `ndiswrapper -i bcmwlhigh5.inf` it still says the file is not there.

???

P.S.:
I also found this in another Thread and what Fernando posts there seems to have helped others, 
[https://answers.launchpad.net/ubuntu/+source/unity-2d/+question/224141](https://answers.launchpad.net/ubuntu/+source/unity-2d/+question/224141)
however I can't even follow this after step 5, that's all just way way over my head.

---

### Post by dogdaysunrise on 2016-01-20
Anybody? I can't figure it out.

---

### Post by kurt18947 on 2016-01-21
I'm not knowledgeable about nor a fan of NDISwrapper so no help there but a router is a box with one or more network cables plugged into it. You appear to be talking about a wireless network adapter. Correct terminology helps.  Here are some details about your adapter:

[https://wikidevi.com/wiki/Linksys_AE2500](https://wikidevi.com/wiki/Linksys_AE2500)

It uses a Broadcom  BCM43236chipset (chipsets are what matter in linux, more than manufacturer) which does not presently have a linux driver. It sounds like NDISwrapper is your only shot for now and NDISwrapper is far from 100% guaranteed to work. All I think I know about NDISwrapper is that you have to use the correct 'bitness'. If you have a 64 bit linux system you must use a 64 bit windows driver. I think Windows XP drivers are preferred and 64 bit Windows XP drivers may not be plentiful. I have no idea if Windows 7-8-10 drivers work or not. A native driver may appear for this device but there are no guarantees. 

Sorry I can't be of more help. I do a bit of research and buy devices that are known to work. It makes my life simpler.

---

### Post by Vladlenin5000 on 2016-01-21
A big +1 for the post above.

Bottom line: Use a natively supported wireless adapter. Anything you can find now will be better and cheaper than that one.
Most Intel, Atheros and Realtek work out-of-the-box.

---

### Post by slickymaster on 2016-01-21
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by dogdaysunrise on 2016-01-21
Yes , my bad, I'm talking about a wireless network adapter, however all that's been said I know or have stated in my own post.
I know ndiswrapper might not work 100 percent, but it is my only shot. And yes XP Drivers are the only ones more likely to be working.
My problem is a different matter and I'm too much of a noob to get it resolved I believe. I'm about to go back to Windows.

I got the ndiswrapper, I got the modifed xp driver. They are all in my downloads and have been extracted.
When I type the commands in the terminal it tells me they are not there.

[LIST]
[*]cd /Downloads/bcmwl_4323x/xp/ 
[*]:~/Downloads/bcmwl_4323x/xp$ sudo ndiswrapper -i bcmwlhigh5.inf 
[*]sudo modprobe ndiswrapper 
[/LIST]

Then I realized the commands just said downloads.....etc, so I have to add /home/"myname"/downloads/bcmwl_4323x/xp/

That worked, but everything after that fails. 
:~/home/"myname"/Downloads/bcmwl_4323x/xp$ sudo ndiswrapper -i bcmwlhigh5.inf
This second command says bcmwlhigh5.inf file or directory not found, but it is there! 
'

I followed the instructions of the second post in this thread, but I don't get past the second command.
[http://ubuntuforums.org/showthread.php?t=2223902](http://ubuntuforums.org/showthread.php?t=2223902)

---

### Post by chili555 on 2016-01-22
> :~/home/"myname"/Downloads/bcmwl_4323x/xp$ sudo ndiswrapper -i bcmwlhigh5.inf
This second command says bcmwlhigh5.inf file or directory not found, but it is there!
'Please show us:```
cd   ~/Downloads/bcmwl_4323x/xp
ls -al
```Thanks.

By the way, in the world of Linux the symbol ~ located above the ` on the left side of my US keyboard, is a shortcut for /home/"myname".

---

### Post by dogdaysunrise on 2016-01-23
> **chili555 said:**
> Please show us:```
cd   ~/Downloads/bcmwl_4323x/xp
ls -al
```Thanks.

By the way, in the world of Linux the symbol ~ located above the ` on the left side of my US keyboard, is a shortcut for /home/"myname".

Thank you sir for your efforts to help!


drwxrwxr-x 2 chris chris    4096 Jan 28  2012 .
drwxrwxr-x 5 chris chris    4096 Jan 20 20:52 ..
-rw-rw-r-- 1 chris chris 1176064 Mar 29  2011 AE1200xp64.sys
-rw-rw-r-- 1 chris chris 1034240 Mar 29  2011 AE1200xp.sys
-rw-rw-r-- 1 chris chris 1176064 Mar 29  2011 AE2500xp64.sys
-rw-rw-r-- 1 chris chris 1034240 Mar 29  2011 AE2500xp.sys
-rw-rw-r-- 1 chris chris    7179 Apr 27  2011 bcmh43xx64.cat
-rw-rw-r-- 1 chris chris    7993 Apr 27  2011 bcmh43xx.cat
-rw-rw-r-- 1 chris chris   95544 Mar 29  2011 bcmwlcoi64.dll
-rw-rw-r-- 1 chris chris   91448 Mar 29  2011 bcmwlcoi.dll
-rw-rw-r-- 1 chris chris   90948 Feb  6  2012 bcmwlhigh5.inf

---

### Post by chili555 on 2016-01-23
We do indeed see the file. Now, let's see:```
cd ~/Downloads/bcmwl_4323x/xp
sudo ndiswrapper -i bcmwlhigh5.inf
```Please check your spelling carefully. I have often typed bcmwhigh5.inf when I really meant bcmw[COLOR="#FF0000"]l[/COLOR]high5.inf. 

If there is an error or warning, please let us see it exactly.

---

### Post by dogdaysunrise on 2016-01-23
> **chili555 said:**
> We do indeed see the file. Now, let's see:```
cd ~/Downloads/bcmwl_4323x/xp
sudo ndiswrapper -i bcmwlhigh5.inf
```Please check your spelling carefully. I have often typed bcmwhigh5.inf when I really meant bcmw[COLOR=#FF0000]l[/COLOR]high5.inf. 

If there is an error or warning, please let us see it exactly.

You are the man! So far everything worked!
 This is what I got:

chris@chris-HP-G72-Notebook-PC:~$ cd ~/Downloads/bcmwl_4323x/xp
chris@chris-HP-G72-Notebook-PC:~/Downloads/bcmwl_4323x/xp$ sudo ndiswrapper -i bcmwlhigh5.inf
[sudo] password for chris: 
installing bcmwlhigh5 ...
chris@chris-HP-G72-Notebook-PC:~/Downloads/bcmwl_4323x/xp$

Now, what's the next step?

---

### Post by chili555 on 2016-01-23
Good! No errors! Now, let's see:```
ndiswrapper -l
iwconfig
```That's a lower-case L for 'list'; not a one.

---

### Post by dogdaysunrise on 2016-01-24
This is what I get: 
chris@chris-HP-G72-Notebook-PC:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (13B1:003A) present
chris@chris-HP-G72-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Shawn 2G"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D4:05:98:37:D3:00   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

lo        no wireless extensions.

chris@chris-HP-G72-Notebook-PC:~$ 


First off, really appreciate you helping me here, I'm starting to like ubuntu, I downloaded Windows 7 ISO, but I guess I'm not going to use it. I found out chrome browser loads vimeo videos and other webpages that firefox does not and I am currently trying to get itunes to work. So I installed wine and playonlinux.

Anyway, so to give you a heads up on "our" matter, I am currently using the Laptop's built in Wifi Antenna which is only capable of 2G, which is what you see in the result "Shawn 2G. There's also a Shawn 5G wifi signal that I would like to access with the Linksys USB Wifi adapter.

---

### Post by chili555 on 2016-01-24
> I am currently using the Laptop's built in Wifi Antenna which is only capable of 2G, which is what you see in the resultLet's also see:```
dmesg | grep ndis
lspci -nnk | grep 0280 -A2
```When you refer to 5G, do you actually mean 5 gHz? I haven't seen many internal wireless cards that won't connect to 5 gHz unless it's set to N speeds only. May we see:```
iwlist wlan0 freq
```I doubt you will get ndiswrapper to utilize N speeds since it relies on the aging and creaky Windows XP driver files.

---

### Post by dogdaysunrise on 2016-01-24
chris@chris-HP-G72-Notebook-PC:~$ dmesg | grep ndis
chris@chris-HP-G72-Notebook-PC:~$ lspci -nnk | grep 0280 -A2
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:1467]
	Kernel driver in use: rtl8192se
chris@chris-HP-G72-Notebook-PC:~$ iwlist wlan0 freq
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.462 GHz (Channel 11)


chris@chris-HP-G72-Notebook-PC:~$ 



It's a Time Warner Cable Router and it lists 2G and 5G as the 2 available networks under our account. I bought the Linksys adapter to access the 5G option, which worked fine under windows, because my laptop only detects the 2G with 
it's build in Wifi adapter.

---

### Post by chili555 on 2016-01-24
Let's dig a little deeper:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Please post any and all warnings, errors, etc.> wlan0 [COLOR="#FF0000"]11 channels in total[/COLOR]; available frequencies :Crazy!

What does this report?```
sudo iw reg get
```

---

### Post by dogdaysunrise on 2016-01-24
```
chris@chris-HP-G72-Notebook-PC:~$ sudo modprobe ndiswrapper
[sudo] password for chris: 
chris@chris-HP-G72-Notebook-PC:~$ dmesg | grep ndis
[10537.437967] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[10537.439070] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[10537.520900] usbcore: registered new interface driver ndiswrapper
```

```
chris@chris-HP-G72-Notebook-PC:~$ sudo iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
chris@chris-HP-G72-Notebook-PC:~$
``` 



I have no idea what this is or what I'm doing, I'm just doing what you tell me to...:-)))

---

### Post by chili555 on 2016-01-24
> $ sudo iw reg get
country US:Perfect.> $ dmesg | grep ndis
[10537.437967] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[10537.439070] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[10537.520900] usbcore: registered new interface driver ndiswrapper
Good so far. After doing so, was a new wireless interface created?```
iwconfig
```If not, how about now?```
sudo modprobe -r  rtl8192se
iwconfig
```

---

### Post by dogdaysunrise on 2016-01-24
```
chris@chris-HP-G72-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Shawn 2G"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D4:05:98:37:D3:00   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


lo        no wireless extensions.


wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Okay and the good news is, the blue light on the linksys came finally on. How do I connect now!? We're so close.


Bad news is, that I did your second command and now the linksys is not listed in the upper bar Wifi selection menu anymore.

EDIT: Actually you made it work, it was connected via the linksys, when I pulled it, Wifi was gone. Problem is, it does not detect the 5G network, so I did a restart and went back to the built in adapter and the 2G connection.

---

### Post by chili555 on 2016-01-24
Let's have a look at:```
iwlist wlan1 freq
sudo iwlist wlan1 scan
```I am not interested in all the scanned access points; just whether the 5 gHz access point is seen. If so, post its details.

Is the 5 gHz access point set to N speeds only, by chance?

---

### Post by slickymaster on 2016-01-25
@dogdaysunrise
I've add code tags to several posts. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention.

---

### Post by dogdaysunrise on 2016-01-25
```
chris@chris-HP-G72-Notebook-PC:~$ iwlist wlan1 freq
wlan1     no frequency information.

chris@chris-HP-G72-Notebook-PC:~$ sudo iwlist wlan1 scan
[sudo] password for chris: 
wlan1     Interface doesn't support scanning.
```


> Is the 5 gHz access point set to N speeds only, by chance?                 

I don't know and don't even know what n speeds are or where to look for it. 

Hey chili, you helping me is awesome and I appreciate it but if it's too much because I'm such a noob here, it's not a big deal, I'm okay with the 2G, it's not too bad or slow.

---

### Post by chili555 on 2016-01-25
>  but if it's too much because I'm such a noob here, it's not a big dealNo worries at all. I remember many years ago when I was a nob and was treated, on a few forums, like dirt under a shoe. I promised myself to never be that guy. 

When you unload the driver for the internal device:```
sudo modprobe -r rtl8192se
```...I am sure the wlan0 interface goes away:```
iwconfig
```But does that help wlan1, the USB, to work as expected?```
iw list
dmesg | grep -e wlan1 -e ndis
sudo iwlist wlan1 scan
```> Is the 5 gHz access point set to N speeds only, by chance?
I don't know and don't even know what n speeds are or where to look for it.
It is in the settings for the router. [http://screenshots.portforward.com/routers/Actiontec/Q1000_-_Qwest/Wireless_802.11b_g_n_Mode.jpg](http://screenshots.portforward.com/routers/Actiontec/Q1000_-_Qwest/Wireless_802.11b_g_n_Mode.jpg) Notice, in this example, the Compatibility Mode is set to B, G and N.

N speeds are typically very high rates. However, if your card doesn't have N capability and the router is set on N *only*, then, obviously, it won't see it nor connect.

[https://en.wikipedia.org/wiki/IEEE_802.11n-2009](https://en.wikipedia.org/wiki/IEEE_802.11n-2009)

>  Its purpose is to improve network throughput over the two previous standards—802.11a and 802.11g—with a significant increase in the maximum net data rate from 54 Mbit/s to 600 Mbit/s

---

### Post by dogdaysunrise on 2016-01-25
Thanks that's nice of you. We've all been noobs at some point. I'm pretty good with windows and mac somewhat, this is all new and chinese to me, haha.

Yes it does go away, then I have no connection at all and can't seem to reselct any wifi networks from the top task bar, only a restart helps, that's why I couldn't post the results.

I'll have to check back on the router, I just opened some ports the other day for the PS4.
The only thing I can tell you in regards to the N setting is, that before on windows the linksys adapter detected the 5G Network, now it doesn't. When you got it working yesterday, it only did the 2G.
Probably since it's running on XP drivers through ndiswrapper.

---

### Post by chili555 on 2016-01-26
> that's why I couldn't post the results.Let's create a text document in your home directory that you can post later:```
sudo modprobe -r rtl8192se
sudo modprobe ndiswrapper
dmesg | grep -e wlan1 -e ndis  >  wireless.txt
sudo iwlist wlan1 scan  >>  wireless.txt
```> only a restart helpsWell, that's the foolproof way to reload the driver for the internal, but you can do it easily from the terminal without rebooting:```
sudo modprobe rtl8192se
```Now, please look in your home directory for the text file *wireless.txt* and post it here.

---

### Post by dogdaysunrise on 2016-01-26
Thanks, I will have to do this on the weekend. It's been a long day at work, tomorrow and Thursday don't look any better. Plus Chromium, Firefox were constantly crashing and ubuntu gave me error messages.
So I reinstalled last night and have to reinstall ndiswrapper and the driver again.
Is it even possible to get this thing going on a faster network, is it's running on XP drivers?!

---

### Post by chili555 on 2016-01-27
> Is it even possible to get this thing going on a faster network, is it's running on XP drivers?! Probably not. Frankly, if the 5 gHz network is set to utilize N speeds, I doubt that this device is even N capable. 

I am beginning to wonder if it's possible to get it working *at all*!

---

### Post by dogdaysunrise on 2016-01-27
Then let's stop. I really do appreciate all your help and you are awesome, I learned a thing or two about the terminal and ubuntu in general.
Thank you sir!

---

