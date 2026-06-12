---
title: "Wifi goes out often w/ Intel Centrino 6235, happens on 16.04, 17.04, 17.10"
date: 2017-11-13
forum: Networking &amp; Wireless
---

### Post by potion on 2017-11-13
Hi, I hope someone can help. I keep losing my wifi connection. The icon in the top bar will show me as connected, but no sites load and I can't ping Google from the terminal. After "sudo service network-manager restart" or disabling/re-enabling wifi or rebooting, it'll start working again, but it sometimes takes quite a few tries.

When this started, I was on 17.04. I upgraded to 17.10, but that didn't help. Then I reinstalled 16.04 (just because I decided I wanted to stick with Unity for as long as possible), and that didn't help either.

So then I found some threads here recommending installing the 8168 driver from Realtek and blacklisting the 8169 driver that was being used. I did that, but no improvement. [Edit: This is irrelevant. I was confusing ethernet and wifi!]

Ran the wireless-info script. Here are two outputs, first from a time [when I couldn't connect]("https://pastebin.ubuntu.com/25957926/"), and second from a time [when I could]("https://paste.ubuntu.com/25957928/").

One last thing is that we have two of the exact same computer in the house, and the same problem occurs on the other one (same ethernet controller, RTL8111/8168/8411 [Edit: Again, irrelevant], and running Ubuntu 17.04). But other devices can connect to the wifi no problem.

Thank you for any help you can give me!

---

### Post by chili555 on 2017-11-14
First of all, the Realtek 8168 is an ethernet adapter, not wifi. From the wireless script, we see:```
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [144d:c0d3]
	Kernel modules: r8168
```Your wireless is the Intel, driven by the aptly named driver iwl[COLOR="#FF0000"]wifi[/COLOR]. You may wish to edit the title of your post to reflect this. I am certain it will draw better attention if it is accurately titled.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred.

We also notice that the 2.4 gHz and 5 gHz segments on your router are named the same:```
RJJCEJhome     <MAC 'RJJCEJhome' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
RJJCEJhome     <MAC 'RJJCEJhome' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2         yes     * 
```I am quite confident that at least part of your issue is that the wireless leaves one and tries to find a better connection on the other. I suggest that you rename them; something like RJJCEJhome2.4 and RJJCEJhome5 or similar. Then ask the wireless to connect to just one. 

 After making these changes, reboot the router. 

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

Finally, let's turn off the sometimes disruptive power management in Network Manager. Again, from the terminal:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Restart Network Manager:```
sudo service network-manager restart
```Any improvement?

---

### Post by potion on 2017-11-14
Thank you so much, chili555! I did everything you suggested. Was kind of funny seeing how my existing settings differed at every step from the ones you recommend. :) Started by renaming the 2.4 GHz and 5 GHz segments, and that did seem to make a difference right away.

Everything's very much improved now. One computer has a nice, fast connection at either 2.4 GHz or 5 GHz. The other computer (the one running Ubuntu 17.04) can't connect at 5 GHz and gives this error: "Connection activation failed. (0) Active connection could not be attached to the device." Thought I'd mention it in case you know of an easy solution, but it's also no big deal at all, because that computer's connection at 2.4 GHz is working great. Other devices in the house can connect to either.

Embarrassed about confusing the wifi and ethernet. #-o Will edit the thread title and also mark this as solved.

Can't thank you enough for all your help!

---

### Post by chili555 on 2017-11-14
> The other computer (the one running Ubuntu 17.04) can't connect at 5 GHz and gives this error: "Connection activation failed. (0) Active connection could not be attached to the device." Thought I'd mention it in case you know of an easy solution,I'd be happy to help if you'd care to start a new question and include the results of the wireless script.

---

### Post by potion on 2017-11-14
> I'd be happy to help if you'd care to start a new question and include the results of the wireless script. 

I really appreciate it! It looks like I spoke too soon. Got on the other computer to run the wireless script, and it's now able to connect at 5 GHz as well. Not sure why it wasn't working at first, but everything seems to be working great now.

Thank you so much for all your help! :)

---

