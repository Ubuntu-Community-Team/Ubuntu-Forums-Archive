---
title: "issue with wi-fi connection speeds."
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by wfriedwaldgmail.c on 2016-12-07
My wired (ethernet) connection on the Mac desktop gets 150 MPBS (up & down) via Verizon FIOS.

My non-wired (wi fi) HP Stream laptop (running Ubuntu) connection only gets about 25 MPBS.  Not fast enough to suitably stream live TV.

I've tried placing the laptop directly in front of the router, it doesn't make any difference.

Alas, the HP stream does NOT have an ethernet port - clearly that would be desirable at this point!

I'm fairly certain this is NOT an Ubuntu issue (although I wish I had checked the speed while it was still running windows) but I was wondering if anybody might have a helpful suggestion. I wanted to watch HAIRSPRAY LIVE tonight on the HP stream unit; alas, there's no way to connect my Mac to my video projector.

thanks for any feedback!

w

---

### Post by slickymaster on 2016-12-07
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2016-12-07
What is the wireless driver here? From the terminal:```
lspci -nnk | grep 0280 -A2
```What are the stated capabilities of the hardware/software combination?```
iw list
```Do you have the router set optimally? Here are my suggestions.

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

### Post by TheFu on 2016-12-07
You can also get a USB3 to GigE ethernet adapter for $20 from Amazon. I have one with 3 USB3 ports and 1 GigE port for my chromebook to use. Won't help today, but there will be other shows.

I'm also a projector user - have a wired raspberry pi v2 driving it.

---

### Post by wfriedwaldgmail.c on 2016-12-08
thank you!  I'm going to try all those steps (thanks for those) and also going to order that USB/ethernet adapter - what a great idea!

w

---

### Post by TheFu on 2016-12-08
> **wfriedwaldgmail.c said:**
> thank you!  I'm going to try all those steps (thanks for those) and also going to order that USB/ethernet adapter - what a great idea!

w

Be careful ordering. You want one with chips that are supported directly by the Linux kernel. Also know that "server" versions of Ubuntu don't recognize the USB3 NIC, but the installer does???.!   So look in the reviews/comments for Linux support on whatever device you are pondering.

---

### Post by wfriedwaldgmail.c on 2016-12-09
thanks! I did the first couple of steps, and here is the result:

will@will-HP-Stream-Notebook-PC-11:~$ lspci -nnk | grep 0280 -A2
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]
    Kernel driver in use: rtl8723be
will@will-HP-Stream-Notebook-PC-11:~$ ^C
will@will-HP-Stream-Notebook-PC-11:~$ will@will-HP-Stream-Notebook-PC-11:~$ lspci -nnk | grep 0280 -A2
will@will-HP-Stream-Notebook-PC-11:~$: command not found
will@will-HP-Stream-Notebook-PC-11:~$ 01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
01:00.0: command not found
will@will-HP-Stream-Notebook-PC-11:~$ Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]
Subsystem:: command not found
will@will-HP-Stream-Notebook-PC-11:~$ Kernel driver in use: rtl8723be
Kernel: command not found
will@will-HP-Stream-Notebook-PC-11:~$

I am hesitant to change anything on the router: as of now, it's working fine with my desktop Mac, and my iPad, and other devices ... what do you think?

Thanks!

w

---

### Post by wfriedwaldgmail.c on 2016-12-09
1. one of the reviewers here indicates that this adapter works with Linux:
<https://www.amazon.com/StarTech-Gigabit-Ethernet-Network-Adapter/dp/B0095EFXMC/ref=sr_1_fkmr0_1?ie=UTF8&qid=1481315482&sr=8-1-fkmr0&keywords=USB3+to+GigE+ethernet+adapter+for+%2420+from+Amazon>

2. but this one seems to advertise that it works with Linux:
<https://www.amazon.com/dp/B00AQM8586/ref=psdc_13983791_t3_B0095EFXMC>

any additional feedback / suggestions?

thanks again!

w

---

### Post by chili555 on 2016-12-09
It should work perfectly but check here for a driver parameter that will help: [http://askubuntu.com/questions/752850/hp-stream-11-late-2015-edition-r050sa-wifi-not-working-properly](http://askubuntu.com/questions/752850/hp-stream-11-late-2015-edition-r050sa-wifi-not-working-properly)

---

### Post by TheFu on 2016-12-09
USB Ethernet ... I wouldn't get an adapter that doesn't add more USB3 ports too.  Mine is a Unitek, but it doesn't seem to be available anymore. Something like this: [https://www.amazon.com/Plugable-Gigabit-Ethernet-backwards-compatibility/dp/B00M7MYFAU/](https://www.amazon.com/Plugable-Gigabit-Ethernet-backwards-compatibility/dp/B00M7MYFAU/)
I didn't look at the specifics, but don't waste a USB port without getting some replacements.  Chromebooks only have 1 USB3 port, so wasting it only on a GigE port wouldn't be ideal.

---

### Post by wfriedwaldgmail.c on 2016-12-15
Yes!  

I plugged it in and it worked.  

(I'm not sure if it was plug-and-play or not; I did try installing a driver from the the manufacturer.  However, knowing my skill level at such things, it's highly likely my "installation" didn't do anything at all.)

I just test it before and after: before it was about 25 down / 40 up, with the adapter, it's now 262 down / 145 up.  (Holy guacamole, my ethernet-wired desktop is only 150 up - I'm only paying for 150 either way via FIOS!)

I tried watching something on youTube - it looked great. I have not yet tried live streaming from the networks, but I have every confidence ...

And yes, this is the adapter with three USB3 ports, so I am gaining more USB in the process.

All in all a very worthwhile investment of $23.

thanks so much for the feedback and the suggestions.

Linux rocks!

w

---

### Post by TheFu on 2016-12-15
a) Linux does ROCK!
b) You don't want to buy any devices that require installing a driver.  Always buy devices that have kernel support.
c) Did you want to work on the wifi still?  Wifi troubleshooting is non-trivial. Lots and lots of factors that are nearly impossible to understand remotely.
d) if you are done, please mark this thread as "SOLVED" in the thread tools button near the top. That helps both helpers and people looking for answers.

---

