---
title: "how to optimise the wifi for ubuntu 16.04, Intel Dual Band Wireless-AC 72"
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by Hodor on 2016-07-19
Can anyone give me some advice on how to optimise the wifi for my system (ubuntu 16.04, Intel Dual Band Wireless-AC 7260)?
I have an ac adapter / router and yet the wifi connection is very slow (slower than non-ubuntu systems connectiving via wifi to the same network).
Results of wireless-info attached.
As a workaround, I am currently using ethernet and both the ethernet and wifi were connected whilst wireless-info was run, but normally I'll only use the one or the other.

Thanks very much for any help.

---

### Post by chili555 on 2016-07-20
You can do all the usual things.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Finally, you might try the latest firmware file. In a terminal:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot. After the reboot, see what firmware loaded:```
dmesg | grep iwl
```we hope that the -17 loaded.> loaded firmware version [COLOR="#FF0000"]17[/COLOR].265642.0 op_mode iwlmvm
Currently, your system is using -16.

As far as I know, there is no way to tweak or force AC speeds. I'm not at all certain the current best driver and firmware even support it. All we can do is try the latest and hope.

---

### Post by Hodor on 2016-07-20
Thanks very much chilli555 - I seem to have obtained a substantial improvement in wifi performance from the above, I'll just watch to see over the next little while if it continues / is stable.
Not sure what to credit - I'd previously set the router as above (on your advice), country code was updated and I instructed network manager to ignore ipv6, and I've also recently turned off power management.
The attempt to update the firmware appears to have failed (ran twice, no avail):
[COLOR=#000000]```
[/COLOR]
dmesg | grep iwl[    1.653838] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
[    1.662169] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
[    1.679018] iwlwifi 0000:05:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    1.715430] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[COLOR=#000000]
```[/COLOR]

---

### Post by chili555 on 2016-07-21
Oops! Sorry for my mis-step. I was sure the later firmware was included in linux-firmware; I was wrong.

Let's try another location:```
cd /lib/firmware
sudo wget https://github.com/OpenELEC/iwlwifi-firmware/blob/master/firmware/iwlwifi-7260-17.ucode
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
dmesg | grep iwl 
```Any change? It might take a reboot.

---

### Post by Keith_Helms on 2016-07-21
That -17 firmware doesn't "look" right.  Here's what's already on my system:
```
-rw-r--r-- 1 root root  672352 Apr 25 06:55 iwlwifi-7260-10.ucode
-rw-r--r-- 1 root root  782300 Apr 25 06:55 iwlwifi-7260-12.ucode
-rw-r--r-- 1 root root  786920 Apr 25 06:55 iwlwifi-7260-13.ucode
-rw-r--r-- 1 root root 1049284 Apr 25 06:55 iwlwifi-7260-16.ucode
-rw-r--r-- 1 root root  683236 Apr 25 06:55 iwlwifi-7260-7.ucode
-rw-r--r-- 1 root root  679780 Apr 25 06:55 iwlwifi-7260-8.ucode
-rw-r--r-- 1 root root  680508 Apr 25 06:55 iwlwifi-7260-9.ucode
```

Here's the new firmware, which I downloaded using the OpenELEC link:
```
-rw-rw-r-- 1 keith keith   35048 Jul 21 09:20 iwlwifi-7260-17.ucode

```

As you can see, the size of the new file is vastly smaller than the previous versions.

---

### Post by chili555 on 2016-07-21
Let's try again. First, remove the old, possibly defective file:```
cd /lib/firmware
sudo rm iwlwifi-7260-17.ucode
sudo wget https://github.com/OpenELEC/iwlwifi-firmware/raw/master/firmware/iwlwifi-7260-17.ucode
ls -al | grep 7260
```How about now?

---

### Post by Hodor on 2016-07-21
Thanks chii555, but I think I've now gone one step backwards from two steps forwards - it's better than it was when I first posted, but not as good as when I marked 'solved'.
no output from that ls:
```

 ls -al | grep 7260
desktop:~$ 

```[FONT=Verdana]
A reboot after [/FONT][FONT=&amp]sudo wget [https://github.com/OpenELEC/iwlwifi-firmware/raw/master/firmware/iwlwifi-7260-17.ucode](https://github.com/OpenELEC/iwlwifi-firmware/raw/master/firmware/iwlwifi-7260-17.ucode) seemed to be stuck (ubuntu with dots ... endlessly, so I hit a hard reset).
I now can't seem to turn off wifi power management permanently - I've tried a few tips from ubuntu forum posts, none seem to work.
Before I upgraded the firmware, the bit rate was around 500 (clearly an ac connection), now it's back to [/FONT][FONT=Verdana]Bit Rate=144.4 Mb/s, so I'm guessing I'm stuck on an N connection.
Can I revert to the firmware I was using previously?  Can I permanently turn off the wifi power management (it's a desktop).[/FONT]

---

### Post by Keith_Helms on 2016-07-21
That looks better:
```
-rw-r--r-- 1 root root 1049340 Jul 21 17:54 iwlwifi-7260-17.ucode
```

And the driver apparently thinks it's firmware:
```
[    8.241714] iwlwifi 0000:03:00.0: loaded firmware version 17.265642.0 op_mode iwlmvm
```

Now I'll see if it works any better than the -16 version.

---

### Post by chili555 on 2016-07-21
> loaded firmware version [COLOR="#FF0000"]17[/COLOR].265642.0 op_mode iwlmvmBetter!

I look forward to your result.

---

### Post by Keith_Helms on 2016-07-21
Hodor, I also wanted to disable power management as doing so seemed to resolve the problem where the refresh of the wifi network list stopped working and the network manager applet showed an empty or old list of networks.

I found two ways that worked for me.  Both involve waiting for the wifi initialization process to catch up with the boot process.

You can add the following to /etc/rc.local before the exit statement
```
sleep 10
iwconfig wlp3s0 power off
```

Somebody suggested creating the following script as /etc/pm/power.d/wireless and marking it executable

```
#!/bin/bash

/sbin/iwconfig wlp3s0 power off
```

That didn't seem to get executed, but the other method I found was to add a "sleep 20" statement to the script and then change the system crontab to execute it at startup:
```
sudo crontab -u root -e
```
and add an entry
```
@reboot /etc/pm/power.d/wireless

```

---

### Post by Hodor on 2016-07-22
Thanks Keith, I'm in the middle of something just now but I'm thinking that when I have a little more time a clean install might be a better way to go - I'm at a loss to see how a driver that won't connect at AC is an advance on a driver that will.

---

### Post by Keith_Helms on 2016-08-02
> **chili555 said:**
> Better!

I look forward to your result.

Well chili555, I've been running the -17 firmware for a week now and, as far as I can tell, it works the same as the -16 version.  I still get the internet traffic randomly halts problem where I have to reconnect to the SSID/wireless network in order to get it moving again.  For some reason that problem never seems to happen when I'm using my router at home (not complaining!), but only on other networks such as the hotspot on my android tablet.

I've tried setting the regulatory domain, disabling power management for the wifi adapter, setting the 11n_disable=8 option (I hesitate to turn off wireless N completely) and even using wicd instead of network manager.  None of those fixed it.  I've been told it's a "known problem" and that a fix is being worked on, but nobody has provided a link to an actual launchpad bug.  There ARE multiple bugs over the years related to the Intel 7260 adapter, so I guess it's a problem child.

---

### Post by chili555 on 2016-08-02
> There ARE multiple bugs over the years related to the Intel 7260 adapter, so I guess it's a problem child.Not really. Guess what I use with perfect results.```
Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)

```And my firmware is:```
[    4.104323] iwlwifi 0000:03:00.0: loaded [COLOR="#FF0000"]firmware version 17[/COLOR].265642.0 op_mode iwlmvm

```Are there any clues in your dmesg?```
dmesg | grep iwl
```

---

### Post by Keith_Helms on 2016-08-02
I never see any log messages when the traffic halts.  The iwl messages in dmesg don't seem to tell anything interesting:
```
[    8.869402] iwlwifi 0000:03:00.0: loaded firmware version 17.265642.0 op_mode iwlmvm
[    9.160540] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    9.160614] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    9.160869] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    9.449494] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.468166] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   19.655556] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   19.655812] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   19.874089] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   19.874348] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
```

---

### Post by chili555 on 2016-08-02
How about:```
dmesg | grep wlp3s0
cat /var/log/syslog | grep -e wlp -e etwork
```As the outputs may be lengthy, please post them here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by Keith_Helms on 2016-08-02
Here's the dmesg grep
```
[    9.468166] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   19.655463] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   19.895491] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   20.363268] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   26.934632] wlp3s0: authenticate with 58:6d:8f:8d:e5:cb
[   26.937467] wlp3s0: send auth to 58:6d:8f:8d:e5:cb (try 1/3)
[   26.938054] wlp3s0: authenticated
[   26.939932] wlp3s0: associate with 58:6d:8f:8d:e5:cb (try 1/3)
[   26.941104] wlp3s0: RX AssocResp from 58:6d:8f:8d:e5:cb (capab=0x11 status=0 aid=1)
[   26.942406] wlp3s0: associated
[   26.942434] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
```


Here's the link to the syslog grep
[http://paste.ubuntu.com/21959647/](http://paste.ubuntu.com/21959647/)

That syslog should actually cover one or more of the times when I had the problem.

---

### Post by chili555 on 2016-08-03
> Activation: starting connection 'khmifi' And then, later:> Activation: starting connection 'KHWIFI50'I assume, based on the frequencies, that one of these is your 2.4 gHz channel and the other is your 5 gHz channel. We see your device roaming from one to the other, disconnecting, obviously, and reconnecting. I suggest that you bind your wireless to one or the other, like this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)As well, in Network Manager check 'Autmatically connect to this network when it is available' on the preferred network and uncheck the other.

---

### Post by Keith_Helms on 2016-08-03
> **chili555 said:**
> And then, later:I assume, based on the frequencies, that one of these is your 2.4 gHz channel and the other is your 5 gHz channel. We see your device roaming from one to the other, disconnecting, obviously, and reconnecting. I suggest that you bind your wireless to one or the other, like this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)As well, in Network Manager check 'Autmatically connect to this network when it is available' on the preferred network and uncheck the other.

khmifi is my android tablet and KHWIFI50 is my Linksys E4200 router on the 5ghz band.  Both are using wireless N.  Those connections were all done manually by me.  My laptop does not generally disconnect from one network and connect to another on its own.  You'll probably notice the first two "starting connection" messages were for khmifi.  That is because wireless traffic just stopped going through after using the connection for a while and I manually reconnected to that network using the network manager applet in order to "prod" it to start working again.

---

