---
title: "WN3100 Wifi Dongle will not work with WPA2 Broadcom (BCM43231)"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by fum on 2014-04-18
[COLOR=#333333][FONT=UbuntuRegular]I can not get my Wireless dongle to work at all with WPA2 encryption. I noticed some people mentioned my same model works with WPA2. It works if I connect via WEP but that reduces my speed by a lot. WPA2 comes back as invalid password even though its correct.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Bus 002 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I followed this guide to enable my dongle to get detected and installed the proper drivers as well. [Could anyone help me get my NETGEAR WNA3100 (Broadcom BCM43231) wireless adapter to work?]("http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter?newreg=afa257173d924dcda056d8b75a8ec63d")



[FONT=Verdana]My SSID is not hidden but it is WPA2 AES encrypted. Right now it detects the network but won't connect even though i put in the correct password. If i switch my wifi router's encryption to WEP it works. Running 14.04 on a 64bit system with the 32bit driver that is known to work. Wifi router is on channel 1 and 54Mbps strength to minimize interference. It is set to WPA2 AES mode only.[/FONT]

[FONT=Verdana]lsusb[/FONT]
[FONT=Verdana]```
Bus 002 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```[/FONT]

[FONT=Verdana]Ndiswrapper is [/FONT]
[FONT=Verdana]```
bcmwlhigh5 : driver installed    device (0846:9020) present
```[/FONT]

[FONT=Verdana]dmseg | grep ndis[/FONT]
[FONT=Verdana]```
fum@FUMPC:~$ dmesg | grep ndis[  112.238595] rndis_host 2-5:1.0 usb0: register 'rndis_host' at usb-0000:00:04.1-5, RNDIS device, 02:50:63:3e:33:6f
```[/FONT]```

[FONT=Verdana][  112.238716] usbcore: registered new interface driver rndis_host[/FONT]
[FONT=Verdana][  513.624863] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)[/FONT]
[FONT=Verdana][  514.170351] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded[/FONT]
[FONT=Verdana][  514.577255] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135a7000, 16000, 4[/FONT]
[FONT=Verdana][  514.577262] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135aae80, 16000, 5[/FONT]
[FONT=Verdana][  514.577266] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135aed00, 16000, 5[/FONT]
[FONT=Verdana][  514.577270] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135b2b80, 16000, 5[/FONT]
[FONT=Verdana][  514.577273] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135b6a00, 16000, 5[/FONT]
[FONT=Verdana][  514.577277] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135ba880, 16000, 5[/FONT]
[FONT=Verdana][  514.577280] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135be700, 16000, 5[/FONT]
[FONT=Verdana][  514.577284] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135c2580, 16000, 5[/FONT]
[FONT=Verdana][  514.577287] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135c6400, 16000, 5[/FONT]
[FONT=Verdana][  514.577290] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135ca280, 16000, 5[/FONT]
[FONT=Verdana][  514.577293] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135ce100, 16000, 4[/FONT]
[FONT=Verdana][  514.577296] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135d1f80, 16000, 5[/FONT]
[FONT=Verdana][  514.577299] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135d5e00, 16000, 5[/FONT]
[FONT=Verdana][  514.577302] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135d9c80, 16000, 5[/FONT]
[FONT=Verdana][  514.577305] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135ddb00, 16000, 5[/FONT]
[FONT=Verdana][  514.577308] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135e1980, 16000, 5[/FONT]
[FONT=Verdana][  514.577311] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135e5800, 16000, 5[/FONT]
[FONT=Verdana][  514.577315] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135e9680, 16000, 5[/FONT]
[FONT=Verdana][  514.577318] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135ed500, 16000, 5[/FONT]
[FONT=Verdana][  514.577321] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135f1380, 16000, 5[/FONT]
[FONT=Verdana][  514.577325] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135f5200, 16000, 5[/FONT]
[FONT=Verdana][  514.577329] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135f9080, 16000, 4[/FONT]
[FONT=Verdana][  514.577336] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900135fcf00, 16000, 5[/FONT]
[FONT=Verdana][  514.577339] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013600d80, 16000, 5[/FONT]
[FONT=Verdana][  514.577342] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013604c00, 16000, 5[/FONT]
[FONT=Verdana][  514.577345] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013608a80, 16000, 5[/FONT]
[FONT=Verdana][  514.577348] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001360c900, 16000, 5[/FONT]
[FONT=Verdana][  514.577351] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013610780, 16000, 5[/FONT]
[FONT=Verdana][  514.577354] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013614600, 16000, 5[/FONT]
[FONT=Verdana][  514.577357] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013618480, 16000, 5[/FONT]
[FONT=Verdana][  514.577360] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001361c300, 16000, 5[/FONT]
[FONT=Verdana][  514.577363] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013620180, 16000, 4[/FONT]
[FONT=Verdana][  514.577366] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013624000, 16000, 4[/FONT]
[FONT=Verdana][  514.577369] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013627e80, 16000, 5[/FONT]
[FONT=Verdana][  514.577372] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001362bd00, 16000, 5[/FONT]
[FONT=Verdana][  514.577375] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001362fb80, 16000, 5[/FONT]
[FONT=Verdana][  514.577378] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013633a00, 16000, 5[/FONT]
[FONT=Verdana][  514.577381] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013637880, 16000, 5[/FONT]
[FONT=Verdana][  514.577385] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001363b700, 16000, 5[/FONT]
[FONT=Verdana][  514.577389] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001363f580, 16000, 5[/FONT]
[FONT=Verdana][  514.577392] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013643400, 16000, 5[/FONT]
[FONT=Verdana][  514.577395] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013647280, 16000, 5[/FONT]
[FONT=Verdana][  514.577398] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001364b100, 16000, 4[/FONT]
[FONT=Verdana][  514.577401] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001364ef80, 16000, 5[/FONT]
[FONT=Verdana][  514.577404] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013652e00, 16000, 5[/FONT]
[FONT=Verdana][  514.577407] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013656c80, 16000, 5[/FONT]
[FONT=Verdana][  514.577410] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001365ab00, 16000, 5[/FONT]
[FONT=Verdana][  514.577413] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001365e980, 16000, 5[/FONT]
[FONT=Verdana][  514.577416] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013662800, 16000, 5[/FONT]
[FONT=Verdana][  514.577419] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013666680, 16000, 5[/FONT]
[FONT=Verdana][  514.594502] ndiswrapper (ndis_encode_setting:383): unknown type: 3[/FONT]
[FONT=Verdana][  514.885468] usbcore: registered new interface driver ndiswrapper[/FONT]
[FONT=Verdana][  514.917425] ndiswrapper: interface renamed to 'wlan1'[/FONT]
[FONT=Verdana][ 1941.727536] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)[/FONT]
[FONT=Verdana][ 4901.591866] rndis_host 2-5:1.0 usb0: unregister 'rndis_host' usb-0000:00:04.1-5, RNDIS device[/FONT]
[FONT=Verdana][25704.604287] rndis_host 2-5:1.0 usb0: register 'rndis_host' at usb-0000:00:04.1-5, RNDIS device, 02:50:63:3e:33:6f[/FONT]



```

[FONT=Verdana]The askubuntu post I put up is this [/FONT][http://askubuntu.com/questions/449849/wn3100-wifi-dongle-will-not-work-with-wpa2-broadcom-bcm43231](http://askubuntu.com/questions/449849/wn3100-wifi-dongle-will-not-work-with-wpa2-broadcom-bcm43231)[/FONT][/COLOR]

---

### Post by fum on 2014-04-18
Wow It just started working on its own now! I switched between 54mbps (B/g) to 144 and rebooted. Then I did 144 to 300 and rebooted one more time and switched back to 54 and it connected perfectly! How would I be able to command it to run automatically at boot up?

---

### Post by chili555 on 2014-04-19
What exactly did you run or do to get it to change speeds? We'll try to automate it.

---

### Post by fum on 2014-04-19
> **chili555 said:**
> What exactly did you run or do to get it to change speeds? We'll try to automate it.

I changed speeds manually with the control panel from my netgear router. I opened up 192.168.1.1 and just switched them around.

---

### Post by chili555 on 2014-04-20
> **fum said:**
> I changed speeds manually with the control panel from my netgear router. I opened up 192.168.1.1 and just switched them around.I am unaware of any method to so so from the computer and from ndiswrapper. If it were me, I'd probably check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

Any improvement?

---

### Post by dvlnchrs on 2014-04-29
Hello all

I'm new to Ubuntu, 3 weeks or so. I've been meaning to do it for some time now and since Windows stopped supporting XP, I took the plunge.

Must say I'm finding the transition fairly easy so far.

I'm also having problems with the netgear wireless router.

Whilst I was updating ubuntu the other day, it was in version 13.10 and  the wireless came up of its own accord. I then updated to 14.04 and it's  not working now. No wireless connections are showing at all.

Whilst reading a thread which suggested typing 'sudo modprobe ndiswrapper'..

I did and returned 'no talloc stackframe at.. /source 3'param/loadparm.c:4864, leaking memory'

Looked this up and came up with 'sudo apt-get remove libpam-smbpass'

Which fixed the 'no talloc...'

As you can see from below (again from reading other threads and trying their remedies), I still appear to be stuck...

cjd@cjd-M68MT-S2:~$ sudo modprobe ndiswrapper
[sudo] password for cjd: 

cjd@cjd-M68MT-S2:~$ dmesg | grep ndis
[  446.712176] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  446.752936] usbcore: registered new interface driver ndiswrapper

cjd@cjd-M68MT-S2:~$ sudo modprobe ndiswrapper
(No response)

cjd@cjd-M68MT-S2:~$ ndiswrapper -l
(No response)

cjd@cjd-M68MT-S2:~$ lsusb

Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cjd@cjd-M68MT-S2:~$ 

Can anyone help me here?

Thank you in advance

---

### Post by dvlnchrs on 2014-04-29
Well, I think I've just cracked it...

[http://ubuntuforums.org/showthread.php?t=2174748](http://ubuntuforums.org/showthread.php?t=2174748)

The above thread gives a link to the drivers for the adapter.

I opened ndiswrapper (windows wireless drivers app),
Clicked on install new driver,
Navigated to the folder where I'd d/l'ed the above mentioned file,
Added [B]bcmn43xx64.inf
[/B]Hey Presto!Now to see if it still works when I reinstall the HDD back onto my desktop PC[B]...

P.S. My inner geek is loving all this ;)
[/B]

---

