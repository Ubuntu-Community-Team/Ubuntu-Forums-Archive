---
title: "Realtek RTL8188CE Unstable"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by Mel_Blakey on 2016-01-31
The good Doctor chili555 fixed my Wifi around 10 months ago [http://ubuntuforums.org/showthread.php?t=2267853](http://ubuntuforums.org/showthread.php?t=2267853)
But unfortunately it is playing up again.

I've tried different settings, Channels etc in the WiFi unit but it still goes slow and has a habit of dropping out. I have been following a few threads on the subject and I've now got 2 antenna's (one on each connector) on my card. It has improved the signal strength, but not the speed, which is painful at times.

I rebuild the drivers as per the good Doctor's instructions whenever there is a change to the Kernal. But of late I have been getting the following errors when running the code:

```
mel@Presario-CQ57:~$ cd backports-3.19-rc1-1
mel@Presario-CQ57:~/backports-3.19-rc1-1$ make clean
Generating local configuration database from kernel ... done.
  CLEAN   /home/mel/backports-3.19-rc1-1/.tmp_versions
  CLEAN   /home/mel/backports-3.19-rc1-1/Module.symvers
mel@Presario-CQ57:~/backports-3.19-rc1-1$ make defconfig-rtlwifi
[COLOR=#b22222]make[2]: execvp: ./lxdialog/check-lxdialog.sh: Permission denied
make[2]: execvp: ./lxdialog/check-lxdialog.sh: Permission denied[/COLOR]
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
mel@Presario-CQ57:~/backports-3.19-rc1-1$ make
[COLOR=#b22222]make[5]: execvp: ./lxdialog/check-lxdialog.sh: Permission denied
make[5]: execvp: ./lxdialog/check-lxdialog.sh: Permission denied[/COLOR]
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/mel/backports-3.19-rc1-1/compat/main.o
  LD [M]  /home/mel/backports-3.19-rc1-1/compat/compat.o

  CC [M]  /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/rtl8821ae/trx.o
  LD [M]  /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.o
  CC [M]  /home/mel/backports-3.19-rc1-1/net/mac80211/main.o
  CC [M]  /home/mel/backports-3.19-rc1-1/net/mac80211/status.o

  LD [M]  /home/mel/backports-3.19-rc1-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 18 modules
  CC      /home/mel/backports-3.19-rc1-1/compat/compat.mod.o
  LD [M]  /home/mel/backports-3.19-rc1-1/compat/compat.ko

  LD [M]  /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/mel/backports-3.19-rc1-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/mel/backports-3.19-rc1-1/net/mac80211/mac80211.ko
  CC      /home/mel/backports-3.19-rc1-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/mel/backports-3.19-rc1-1/net/wireless/cfg80211.ko
mel@Presario-CQ57:~/backports-3.19-rc1-1$ sudo make install
[sudo] password for mel: 
  Building modules, stage 2.
  MODPOST 18 modules
  INSTALL /home/mel/backports-3.19-rc1-1/compat/compat.ko
[COLOR=#b22222]Can't read private key[/COLOR]
  INSTALL /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
Can't read private key
  INSTALL /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/mel/backports-3.19-rc1-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/mel/backports-3.19-rc1-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/mel/backports-3.19-rc1-1/net/wireless/cfg80211.ko
[COLOR=#b22222]Can't read private key[/COLOR]
  DEPMOD  3.19.0-47-generic
make[1]: execvp: ./scripts/blacklist.sh: [COLOR=#b22222]Permission denied[/COLOR]
make[1]: *** [install] [COLOR=#b22222]Error 127[/COLOR]
make: *** [install][COLOR=#b22222] Error 2[/COLOR]
mel@Presario-CQ57:~/backports-3.19-rc1-1$ ^C
mel@Presario-CQ57:~/backports-3.19-rc1-1$ ^C
mel@Presario-CQ57:~/backports-3.19-rc1-1$ make defconfig-rtlwifi^C
mel@Presario-CQ57:~/backports-3.19-rc1-1$
```

I have cut a lot of the code out. But, left in the Errors and Permissions Denied.


[ATTACH]267049[/ATTACH]

---

### Post by chili555 on 2016-01-31
I doubt that building backports-3.19-rc1-1 when you are already running kernel version 3.19.0-47-generic is productive. I doubt that the backports driver differs at all from the default driver that comes with 3.19.0-xx.

This mystifies me:> rt2x00lib: Unknown symbol ieee80211_queue_delayed_work (err -22)rt2x00lib is part of the rt2800usb and rt2800pci suite of drivers for Ralink devices. That's a whole different family from the rtl8192xx family for Realtek devices. Did you have a USB wireless inserted temporarily?

What happens if you simply *don't* recompile backports and let the default driver load? Unstable? Won't connect at all? Smoke? Sparks??

---

### Post by Mel_Blakey on 2016-01-31
> **chili555 said:**
> I doubt that building backports-3.19-rc1-1 when you are already running kernel version 3.19.0-47-generic is productive. I doubt that the backports driver differs at all from the default driver that comes with 3.19.0-xx.
Sorry, I was just carrying out instructions from last time. Each time the Kernal was updated I rebuilt the driver.
If I didn't, it used to be the case that it would play up. It will connect most of the time. But sometimes I have to reboot the lappy and the Wifi itself. If I move away from the unit the signal gets poor. This doesn't happen if I boot it in windoze.

I wasn't aware that there was no longer a requirement to rebuild the driver. Should I clear out the backports folder now?

> **chili555 said:**
> This mystifies me:rt2x00lib is part of the rt2800usb and rt2800pci suite of drivers for Ralink devices. That's a whole different family from the rtl8192xx family for Realtek devices. Did you have a USB wireless inserted temporarily?

I build websites and I really need a stable connection and it can get extremely frustrating when it slows right down. So yes. I have been experimenting with a USB adaptor. I will do anything rather than go back to the darkside.

Thanks for checking this out I really do appreciate it!

---

### Post by chili555 on 2016-01-31
> Should I clear out the backports folder now?Yes, please and let's try a whole new approach. With a working connection, open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```Reboot and I will probably have one more step.

---

### Post by Mel_Blakey on 2016-01-31
Everything seems fine Doc and my Home folder looks a lot tidier!!

Yup....it's a lot quicker.

---

### Post by chili555 on 2016-01-31
> **Mel_Blakey said:**
> Everything seems fine Doc and my Home folder looks a lot tidier!!

Yup....it's a lot quicker.Please test for another day or so and, if you are satisfied, then please use thread tools at the top to mark Solved.

As before, when a new kernel version is installed, recompile:```
cd rtlwifi_new
make clean
make
sudo make install
```And then reboot.

---

### Post by Mel_Blakey on 2016-01-31
Will do!

Thank You So Much

Really Appreciated!

---

### Post by Mel_Blakey on 2016-02-04
I decided to give it a couple of days trial because it was still a bit 'slugish' occasionally / rarely. But the overall performance is very good.... !!

Yesterday, however I had a security update come through and it has change the kernel from 3.19.0-47 to 3.19.0-49. So I assumed that it was time to run:
```

cd rtlwifi_new
make clean
make
sudo make install
```


                  And it came back with this:
> mel@Presario-CQ57:~$ cd rtlwifi_new
bash: cd: rtlwifi_new: No such file or directory
mel@Presario-CQ57:~$ make clean
make: *** No rule to make target `clean'. Stop.
mel@Presario-CQ57:~$ make
make: *** No targets specified and no makefile found. Stop.
mel@Presario-CQ57:~$ sudo make install

I searched for rtlwifi and it does exist at: /system/module/rtlwifi

Any thoughts?


Regards

---

### Post by chili555 on 2016-02-04
It appears that you didn't download, or, in this case, git clone, the files into your home directory. Did you send it to your desktop? Downloads? Or...??

The kwik-n-durty way to find it is with *locate*:```
sudo updatedb
```This will take a few moments; please be patient. Next:```
locate rtlwifi_new
```When you find it, change directories (cd) to that location and try again:```
cd ~/Desktop/rtlwifi_new
```Or wherever it is found, if not Desktop. Then proceed as before.

Just as an example, here is the reading from my machine:```
chili@T440p:~$ locate rtlwifi_new
/home/chili/rtlwifi_new-rock.new_btcoex
/home/chili/Desktop/Forum/rtlwifi_new
/home/chili/Desktop/Forum/rtlwifi_new-rock.new_btcoex
/home/chili/Desktop/Forum/rtlwifi_new-rock.new_btcoex.zip
<snip>
```So, in my case, to recompile the package, I'd need to do:```
cd ~/Desktop/Forum/rtlwifi_new
```The squiggly ~ is sort of terminal shorthand for /home/user_whoever.

---

### Post by Mel_Blakey on 2016-02-04
> It appears that you didn't download, or, in this case, git clone, the  files into your home directory. Did you send it to your desktop?  Downloads? Or...??

Earlier I did what you said to do in post #4 and I thought, that's all I had to do. I didn't purposefully send or save it anywhere....

*Anyway*
I did the stuff you asked and located:

**[B]rtlwifi_new-rock.new_btcoex.zip**-rock.new_btcoex.zip (locked) [/B]in the Downloads folder

I unpacked this with 'Archive Manager' to the desktop but there is NO '**rtlwifi_new' **folder inside it.

---

### Post by Mel_Blakey on 2016-02-04
Doc
Just been called on a job. I'm not ignoring you. Be back later, I hope!

---

### Post by chili555 on 2016-02-04
I believe this is the incorrect, or at least, less-than-ideal package for you:> rtlwifi_new-rock.new_btcoex.zip-rock.new_btcoex.zip (locked) Let's begin anew. Please walk over to the router, hook up an ethernet and do:```
cd ~/Desktop
```Now we know that whatever we get will end up on your desktop and, hopefully, be accessible from now on. Next:```
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```Reboot.

---

### Post by Mel_Blakey on 2016-02-04
Hi I've done that and got **rtlwifi_new** on my desktop :KS

---

### Post by chili555 on 2016-02-04
> **Mel_Blakey said:**
> Hi I've done that and got **rtlwifi_new** on my desktop :KSMay I assume that you recompiled and the wireless is again working as expected?

---

### Post by Mel_Blakey on 2016-02-04
I did this:

```
cd Desktop/rtlwifi_new

make clean
make
sudo make install
```


And it ended with:
> make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-49-generic'
Install rtlwifi SUCCESS

It has made it worse (slower) and I need to undo what I just did!

---

### Post by chili555 on 2016-02-04
The easiest way to load the new module is to reboot. Did you? Is it worse after the reboot?

---

### Post by Mel_Blakey on 2016-02-05
Hi Doc

Sorry, but I needed a sleep last night....

Yes, it is worse after reboot!

I did a new wifi-info.txt. it shows stronger signal, but slower speed.

---

### Post by chili555 on 2016-02-05
If you wish to uninstall it, please do:```
cd ~/Desktop/rtlwifi_new
sudo make uninstall
```Reboot.

I doubt, however, that this will be helpful.

---

### Post by Mel_Blakey on 2016-03-03
I did the above and uninstalled and it worked reasonably until a few days ago when I did an update. It went back to being erratic.

I did the driver rebuild and it is sometimes good but most of the time it is very slugish.

The wireless-info was run with the laptop about 3 feet from the MiFi unit.

Thanks!

[ATTACH]267612[/ATTACH]

---

### Post by chili555 on 2016-03-03
I notice this:> wlan0     IEEE 802.11bgn  ESSID:"3MobileWiFi-b1e1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '3MobileWiFi-b1e1' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=**38**/70[/COLOR]  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:0How close to the router or wireless access point are you? I am wondering if this is an antenna wire problem. Can you walk the computer over to the router and let us see, again:```
iwconfig
```

You have, throughout this thread, installed, uninstalled and reinstalled *rtlwifi_new*. Which is this? You may be able to get some clues with the terminal command:```
history
```

---

### Post by Mel_Blakey on 2016-03-03
The first one (in previous post) was taken with the lappy 3 feet from the wifi.

This 2nd one below is with the wifi sat next to the lappy, maybe 3 inches from the card. (antenna wire on connector 1)

[ATTACH]267613[/ATTACH]


On this 3rd one I have moved the antenna wire to connector 2. Wifi still only about 3 inches away.

[ATTACH]267615[/ATTACH]


I had a spare antenna wire and there was a point when I had wires connected to both. But, no luck.

Thanks!

---

### Post by chili555 on 2016-03-03
Your attachment doesn't show up; sorry.

---

### Post by Mel_Blakey on 2016-03-03
oops!

[ATTACH]267618[/ATTACH]

---

### Post by chili555 on 2016-03-03
> [  363.349573] wlan0: deauthenticating from <MAC '3MobileWiFi-b1e1' [AC1]> by local choice (Reason: [COLOR="#FF0000"]2=PREV_AUTH_NOT_VALID[/COLOR])
[  363.360088] wlan0: authenticate with <MAC '3MobileWiFi-b1e1' [AC1]>
[  363.370319] wlan0: send auth to <MAC '3MobileWiFi-b1e1' [AC1]> (try 1/3)
[  363.373715] wlan0: authenticated
[  363.374901] wlan0: associate with <MAC '3MobileWiFi-b1e1' [AC1]> (try 1/3)
[  363.378359] wlan0: RX AssocResp from <MAC '3MobileWiFi-b1e1' [AC1]> (capab=0x431 status=0 aid=1)
[  363.378949] wlan0: associated
That sometimes means that your device is roaming to another ESSID with the same name and a different password. It also sometimes means that the router may have switched channels. 

Let's give your device the best possible chance to connect and stay connected. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by Mel_Blakey on 2016-03-04
> [  363.349573] wlan0: deauthenticating from <MAC '3MobileWiFi-b1e1' [AC1]> by local choice (Reason: [COLOR=#FF0000]2=PREV_AUTH_NOT_VALID[/COLOR])
> **chili555 said:**
> That sometimes means that your device is roaming to another ESSID with the same name and a different password. It also sometimes means that the router may have switched channels

There were 2 instances of the 3mobile connection in Network Manager. I have deleted one of them - to no avail.


With regard to the settings that you list. I have been following some of your other posts and implemented all of those some months ago. I have systematically tried each channel and at the moment it is fixed on ch 11.

.
> You have, throughout this thread, installed, uninstalled and reinstalled *rtlwifi_new*. Which is this? I am a Linux novice and trying the things that I 'think' have made some improvement in a desperate attempt to not have to return to an environment were my wireless 'just works' (without all this fuss and nonsense), because that environment is owned my MS.

I do appreciate the time that you have so freely given me and I sincerely am grateful. But, I think that it is time that I held my hands up and realised that Ubuntu (or its derivatives) is not going to drive this card.

THANK YOU!

---

### Post by Mel_Blakey on 2016-04-01
I solved this problem by buying this:[SIZE=2]

**TP-Link TL-WN725N 150Mbps Wireless N Nano USB Adapter**[/SIZE]
[URL="http://www.tp-link.com/en/products/details/cat-11_TL-WN725N.html"]http://www.tp-link.com/en/products/details/cat-11_TL-WN725N.html

[/URL]
The best price I found in the UK was from DABs Ebay.
[http://www.ebay.co.uk/itm/311202068133?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.co.uk/itm/311202068133?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)


I had difficulty installing the official driver from the TP-Link website
[http://www.tp-link.com/en/download/TL-WN725N.html#Driver](http://www.tp-link.com/en/download/TL-WN725N.html#Driver)

So I installed this one instead and it works fine.
[URL="http://askubuntu.com/questions/381574/drivers-for-tp-link-tl-wn725n-nano-usb-wireless-n-adapter"]http://askubuntu.com/questions/381574/drivers-for-tp-link-tl-wn725n-nano-usb-wireless-n-adapter

[/URL]

Good Luck!

---

