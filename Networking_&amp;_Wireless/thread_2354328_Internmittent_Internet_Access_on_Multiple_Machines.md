---
title: "Internmittent Internet Access on Multiple Machines and Versions of Ubuntu"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by garrettives on 2017-03-01
I have tried, on two machines now, Ubuntu 14.04, 15.04, and 16.04.  The internet intermittently disconnects, and requires one of various steps to fix it which are always different.  This includes disconnect/connect, turn Wi-Fi off and on, log out/in, reset the computer, or various methods via the terminal.  On my Core I3 (I am now using a core I5) I even tried re-compiling the Wi-Fi driver and using a proxy server (Ubuntu 14.04), and still only had intermittent internet access.  This new computer has a different wifi driver and is from a different manufacturer.  The old one was an HP and the new one is a Lenovo.  I really like Linux, however I can't use it due to intermittent internet issues.  I am a web developer by trade, with approximately 30 Years of experience with computers.  I would like to use Ubuntu as my primary development environment for web sites, however I can't use it professionally due to the intermittent lack of an internet connection.  Has anyone else struggled with this?  I am thinking about reinstalling Linux, and maybe trying an older and more stable release on my new machine instead of 16.04 maybe 15 or 14, give it a day and see.  If anyone has successfully solved this issue let me know.

---

### Post by chili555 on 2017-03-01
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

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these steps are ineffective, we'll look at the individual drivers' settings.

---

