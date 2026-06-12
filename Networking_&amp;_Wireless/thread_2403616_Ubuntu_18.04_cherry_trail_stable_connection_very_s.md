---
title: "Ubuntu 18.04 cherry trail stable connection very slow speed"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by diegogdvu on 2018-10-13
Hi i bought a very cheap laptop and installed Ubuntu on it and i'm using it a lot currently since my desktop is broken, dead Mobo.

Intel cherry trail z8300
4GB RAM
32 GB eMMC

after some tweaking everything works fine except the wifi is very slow i'm getting around 1mbps my normal speed in other devices and the speed i was getting in windows is 15 mbps (third world country), tried a lot of solutions like updating distro, kernel and others but with no luck.

[https://pastebin.com/XAL2aKsS](https://pastebin.com/XAL2aKsS)

Here is the data from the script that the sticky told me to run. 

Hope someone can help me thanks.

---

### Post by Redalien0304 on 2018-10-13
If you have Usb Wifi Dongle try it see if you get the same speeds or faster. Some Cheap Laptops Use Cheap Older Wifi hardware Chips

---

### Post by diegogdvu on 2018-10-13
Hmm ill probably buy one if i cant solve via software tweaks it or a ethernet to usb adapter.

---

### Post by chili555 on 2018-10-13
Please try:```
sudo -i
echo "options r8723bs rtw_ant_num=1"  >  /etc/modprobe.d/r8723bs.conf
exit
```Reboot and run:```
iwconfig
```Is there any improvement from your current reading?> 
wlan0     IEEE 802.11bgn  ESSID:"CASA"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'CASA' [AC1]>  
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=5/100[/COLOR]  Signal level=6/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

More important, is there any improvement in performance? I don't necessarily rule out that the hardware and driver combination may not report signal strength accurately.

If there is no improvement, do the steps again with  "options r8723bs rtw_ant_num=2"  and test again.

Moreover, please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and *certainly not *TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

---

### Post by diegogdvu on 2018-10-13
Thank you for taking the time to respond, did try your first fix with option 1 and 2, option 2 seems to give a small boost in speed, it now seems to oscillate between 2 and 3 mbps, its something :), and running iwconfig link quality also seems to oscillate between 10/100 and 30/100. Will try some of your other fixes and report back, but some will have to wait till monday because it seems i'll have to call my ISP so i can get my router username and password, will report back.

---

### Post by C.S.Cameron on 2018-10-14
Have you looked at Linuxium or Isorespin? 
They were created to supply Atom Cherry Trail computers with the missing drivers for Ubuntu.

---

### Post by diegogdvu on 2018-10-16
Well reporting back i managed to access my router configuration and  changed what i could to the recommended settings, sadly it didnt seem to  make any difference, im still stuck with 2 - 3 mbps tops, guess ill  have to buy an ethernet to usb adapter since i use my laptop mostly in  the same place.

> **C.S.Cameron said:**
> Have you looked at Linuxium or Isorespin? 
They were created to supply Atom Cherry Trail computers with the missing drivers for Ubuntu.

Well i did find that site early, but my laptop worked with Ubuntu since the start, only thing i had no sound, that was fixed with a kernel update. The driver seems to be the correct one r8723bs, could be something else, but im not sure what.

---

### Post by C.S.Cameron on 2018-10-17
The sound drivers from [http://linuxiumcomau.blogspot.com/2018/03/fixing-broken-hdmi-audio-again.html](http://linuxiumcomau.blogspot.com/2018/03/fixing-broken-hdmi-audio-again.html) worked on my compute stick.

---

