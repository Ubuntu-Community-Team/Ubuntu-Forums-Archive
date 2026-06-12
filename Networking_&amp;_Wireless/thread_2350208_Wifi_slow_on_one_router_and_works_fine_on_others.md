---
title: "Wifi slow on one router and works fine on others"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by shubham0108 on 2017-01-22
So I recently started using Ubuntu and I am not sure why but when I connect my laptop to my home wifi it is very slow. Whereas when I connect to my workplace wifi I have no problem whatsoever. I even tried connecting to my friends Hotspot from his mobile data it worked fine there as well. Other devices connected to my home wifi work fine. 
Please help. Thanks :)

---

### Post by chili555 on 2017-01-22
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

---

### Post by bushugger on 2017-02-27
Hi chili555, just wanted to say I had a similar problem, very slow wifi after installing 16.04.
After searching the forums for solutions I found this thread with your suggestion to set the channel width on the 2.4GHz band to 20MHz rather than the default automatic 20/40MHz.
It's worked an absolute charm, wifi is full speed again!
Many thanks! (& apologies if it's rude for jumping on someone else's thread)

---

