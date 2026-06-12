---
title: "Lenovo G40. Wifi &quot;Qualcomm Atheros QCA61x4 Wireless Network Adapter&quot; not working"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by mitulsaha on 2015-07-16
Hi,

Can anyone please help me get wifi working in my new Lenovo G40 laptop?
The wifi card is: "Qualcomm Atheros QCA61x4 Wireless Network Adapter"
I have installed Ubuntu 15.04.

Thank you!

---

### Post by chili555 on 2015-07-16
Please give us further details about your device:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mitulsaha on 2015-07-16
Sure. "lspci -nn | grep 0280"
gives:- 03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)

Thank you!

---

### Post by chili555 on 2015-07-16
Please see my posts #2 and #4 here: [http://ubuntuforums.org/showthread.php?t=2282387](http://ubuntuforums.org/showthread.php?t=2282387)

As you can see, you have the same device.

---

### Post by mitulsaha on 2015-07-16
Thanks! I actually have been looking at that thread. Has this issue been resolved as of today?

---

### Post by chili555 on 2015-07-16
Not that I can find. The bug report confirms it is also not supported in Wily, which is the upcoming Ubuntu 15.10: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)

---

### Post by mitulsaha on 2015-07-16
Ok Thank you! ... then I am going to go ahead and buy this USB wifi adapter:-
[[COLOR=#1155CC][FONT=Arial][/FONT][/COLOR]]("http://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/ref=lp_13983791_1_2/184-1611984-0951902?s=pc&ie=UTF8&qid=1437084028&sr=1-2")[COLOR=#1155CC]_[http://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/ref=lp_13983791_1_2/184-1611984-0951902?s=pc&ie=UTF8&qid=1437084028&sr=1-2](http://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/ref=lp_13983791_1_2/184-1611984-0951902?s=pc&ie=UTF8&qid=1437084028&sr=1-2)_[/COLOR]
&#8220;Edimax EW-7811Un 150Mbps 11n Wi-Fi USB Adapter, Nano Size Lets You Plug it and Forget it, Ideal for Raspberry Pi, Supports Windows, Mac OS, Linux&#8220;.
Hope it will work well with ubuntu. 
I could not also make the wifi work with Ndiswrapper.

---

### Post by mitulsaha on 2015-07-16
BTW, i tried using Ndiswrapper by following instructions here:- [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
It did not work. Any ideas why Ndiswrapper will fail to run wifi in this case?

---

### Post by chili555 on 2015-07-17
> **mitulsaha said:**
> BTW, i tried using Ndiswrapper by following instructions here:- [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
It did not work. Any ideas why Ndiswrapper will fail to run wifi in this case?Without a full diagnostic work-up, the Doc hasn't any idea. Did you use XP drivers? Windows 7 or 8 or 3.1 just won't work. Are there clues in the log?```
dmesg | grep ndis
```

---

### Post by mitulsaha on 2015-07-17
Thank you.

Actually i did use the drivers from Windows 8. I think i read somewhere it needed it to be from Windows XP.
So no hope with drivers from Windows 8?

BTW, the doc [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) says to check log at "[COLOR=#333333][FONT=UbuntuMono]/var/log/messages[/FONT][/COLOR]". But this file does not exist in my G40 laptop ubuntu drive. Is there any other place i should be looking for the log?

---

### Post by chili555 on 2015-07-17
> I think i read somewhere it needed it to be from Windows XP.That's what the documentation says, and I've never seen otherwise  except Windows 2000 which is essentially industrial strength XP.> So no hope with drivers from Windows 8?Pilot6 claims to have got ndiswrapper working with 7. I suggest you send him a private message and ask him to help.> Is there any other place i should be looking for the log?I think I already told you:```
dmesg | grep ndis
```However, if you want the in-depth, heavy-duty version, it's in /var/log/syslog. I doubt it gives us anything more informative than dmesg, though.

---

### Post by mitulsaha on 2015-07-19
Thank you!

---

