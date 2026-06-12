---
title: "thinkpad t420 - kubuntu 17.04 keeps disconnecting"
date: 2017-09-22
forum: Networking &amp; Wireless
---

### Post by oother on 2017-09-22
I've been having regular problems with wireless connections on my lenovo thinkpad t420 for several months. When I power on my laptop it works fine but after an hour or so, it will suddenly disconnect and refuse to work after that. I have to reboot to get it working again. My Mac and Windows machines do not have this problem. There are two routers in my house that work fine normally, but after this problem happens it refuses to work with either of them.

Last week I disabled power saving and changed from hardware to software encryption (among some other settings, but I can't remember what else I changed) but this hasn't worked. However, it did slightly change the nature of the problem - before it would disconnect and refuse to reconnect to wifi, now it stays connected but just suddenly stops all communication to the internet. 

[I've pasted my details in pastebin]("http://paste.ubuntu.com/25591068/")

Do I need to change my drivers? My laptop has the [COLOR=#000000]Intel Corporation Centrino Advanced-N 6205 card, and [/COLOR]I just used the default drivers that came with my Kubuntu installation. I'm new-ish to Linux so if you need more info please let me know

---

### Post by jeremy31 on 2017-09-22
Some advice from chili555

There are several steps that I recommend. First, disable power saving in Network Manager; from the terminal:```
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager

---

