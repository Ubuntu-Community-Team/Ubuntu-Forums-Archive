---
title: "Edimax EW-7612Pln V2 PCI Wifi Adapter"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by RealisticDave on 2015-01-17
Purchased this earlier---while running 12.04---and it operated great. A couple of months ago, I upgraded to 14.04, and now this either doesn't connect to router at all, or if it does, shortly afterwards (time span varies) it stops working (even though it still shows "Connected").

I've done searches and can find almost no information about EW-7612Pln V2.  On the Edimax site, they have a Linux driver that says it was updated recently, but nowhere can I find instructions about the step-by-step procedure to install the driver. All of the info I can find is for other models of Edimax adapters, mostly USB. I've tried to follow some of these instructions, but the examples have much different terminology and I can't 'convert' the information shown in the examples into the files that I have.

Can someone either point me to specific instructions for the EW-7612Pln V2 driver installation---or give me a definitive answer that this hardware does _not_ work with 12.04? (FYI, this computer has 3 HDD [Win7, Win XP, and Ubuntu]; Edimax works great with both Win drives, and I can plug in a TP-Link USB wifi adapter while in Ubuntu to acess wifi---but my first choice would be to use the Edimax for whatever operating system I'm using at the time. I also have an Acer laptop with Ubuntu. I was using a NetGear WNA3100 USB wifi adapter when I had 12.04, but as soon as I upgraded to 14.04---the NetGear adapter stopped working correctly. I've just purchased a Belkin USB adapter, and---thus far---it's working great with 14.04.)

Thanks.

---

### Post by chili555 on 2015-01-17
First, please let's not get confused switching from among 3-4 different adapters; let's get the 7612Pln working.

What does the terminal report about it?```
lspci -nn | grep 0280
```

---

### Post by RealisticDave on 2015-01-17
Chili555, here's the report from the command you provided:

realisticdave@Bonjour:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)

At present, the Edimax adapter seems to be working fine. However this afternoon---as often happens---the Edimax simply stopped working, I tried repeatedly to go back online with it (disconnect and reconnect), but it simply wouldn't do so.  That's when I plugged in the (USB) TP-Link adapter and started my thread.  (FYI, looking at the list of available networks, it showed both the Realtek Edimax that wouldn't work, as well as the Atheros TP-Link that was working.)

Thanks

---

### Post by chili555 on 2015-01-18
> That's when I plugged in the (USB) TP-Link adapter and started my thread. (FYI, looking at the list of available networks, it showed both the Realtek Edimax that wouldn't work, as well as the Atheros TP-Link that was working.)It is not at all helpful to have two or three possibly (probably!) conflicting driver suites loaded. Please report your results with one and only one device running. If it is the Edimax you'd like to fix, then the Edimax.

Let's try a driver parameter. From a terminal:```
sudo -i
echo "options rtl8192ce swenc=1"  >  /etc/modprobe.d/rtl8192ce.conf
exit
```Reboot with only the Edimax active and let us hear your report.

---

### Post by RealisticDave on 2015-01-18
I'm sorry about using my other adapter, but that's the problem: if I either don't have the Edimax connected at bootup, or if it stops working while I'm doing something, I either have to lose everything I've done and keep rebooting until the Edimax decides to reconnect, or try Plan B (the USB adapter). 

So, I booted up today, the Edimax was working. I pulled up this thread, saw your message, opened a terminal and inputed your commands. (The results are pasted below.  I didn't receive any other output.) I rebooted, and when Ubuntu opened, the Edimax adapter tried to connect, but after it reached the threshold for attempts (I think it's 5 or 6 times it tries, with the wifi symbol flashing?), it stopped and gave me the "Disconnected" message. Even though I wasn't connected, I opened a terminal and inputed the command again, and received the same output as shown below. I then rebooted again...and again...and finally this time the Edimax connected automatically---and I'm able to post this reply. Still working as I compose this message.

I'm not certain what you were looking for when you used the term "report." If it was just my 'reporting' whether or not the Edimax was operating, then you have my report.  But---if there was supposed to be some more verbose output after I inputed the command you gave, I didn't receive them.  If so, perhaps I did something incorrect when I inputed them?  

Here's the pasted info from the terminal:

realisticdave@Bonjour:~$ sudo -i
[sudo] password for realisticdave: 
root@Bonjour:~# echo "options rtl8192ce swenc=1" > /etc/modprobe.d/rtl8192ce.conf
root@Bonjour:~# exit
logout
realisticdave@Bonjour:~$

---

### Post by chili555 on 2015-01-18
> If it was just my 'reporting' whether or not the Edimax was operating, then you have my report. Exactly that. Thanks.

It does nothing whatever to input the code repeatedly; once the parameter is set, it's set.

If the Edimax stops working again, let's see some diagnostics:```
dmesg | grep -e wlan -e rtl  >  wifi.txt
cat /var/log/syslog | grep etwork | tail -n25  >>  wifi.txt
```Then use the USB to connect to the internet, find the file wifi.txt in your user directory and paste it here: [http://paste.ubuntu.com](http://paste.ubuntu.com). Give us the link in your reply.

---

### Post by praseodym on 2015-01-18
Tried to update the driver?

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/3/#post-6439727](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/3/#post-6439727)

---

### Post by RealisticDave on 2015-01-18
Chili555, I've left Ubuntu running for a while, and then tried doing a reboot, and the Edimax has connected and stayed connected---for now. I'm going to let it ride while I do some other things, and whenever it decides to disconnect, I'll run the commands and post them on PasteBin.  Tonight or tomorrow, or whenever it happens?

Praseodym, the link that you referred me to is exactly why I opened this thread (see my first message).  I can find many links to instructions for _other_ drivers, but I don't understand enough to be able to use them. For instance, I don't have RTL8188ce, I have RTL8192ce.  And, I don't know what the "FreedomBen" refers to, nor if I would use the same numbers for other entries or not.  Simply don't understand enough. Thanks for your help, though.
[h=2][/h]

---

### Post by chili555 on 2015-01-18
We look forward to your good results! If not, post back and we'll help.

---

### Post by RealisticDave on 2015-01-18
While I was waiting, I did a system software update download and install---all while it was connected via the Edimax!---and when it came back after the reboot, it wouldn't connect. So, I ran your command, then plugged in my USB and here it is.  
The paste link is [http://paste.ubuntu.com/9780010/](http://paste.ubuntu.com/9780010/)

Thanks.

---

### Post by chili555 on 2015-01-18
I suggest you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

If these changes are not helpful, let's try a different driver parameter:```
sudo -i 
echo "options rtl8192ce ips=0 fwlps=0 swlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo reboot
```

---

### Post by RealisticDave on 2015-01-19
i went through your list. Set my domain to US, and verified after doing so. Set IPv6 to ignore, in the Edit Connections tab. Router security was already set to WPA2-AES, and it was set at 2.4 Ghz for all speeds (B, G, & N). My router doesn't have a choice for channel width (been all through the manual for my Netgear model). I don't live in an apartment, and the houses are a bit apart. When I do a scan for available wireless networks, I normally only see my router and the wifi extender that I have in the other end of my house.  Once in a while, I get a very weak signal from the neighbors, but it's intermittent. I doubt that I'm getting channel interference from someone, but I will download some free software from CNET (available only for Windows) and check my channels. 

But after running through the above items last evening, I left my computer on until late at night, and it stayed connected the whole time. This morning, I've tried to get it to fail, but the Edimax seems to stay online. So, I'm going to mark this solved. I appreciate all your assistance over the past couple of days.  I see that you're from SC, if I lived closer (I'm in Arkansas) I'd treat you to a Calabash supper on the Strand---but I'm not, so I guess you'll just have to accept my "thanks!"

---

### Post by chili555 on 2015-01-19
Thank you so much for your kind words. I'm glad it's working!

---

