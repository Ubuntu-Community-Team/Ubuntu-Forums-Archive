---
title: "No wifi connection with 32 bit?"
date: 2016-07-30
forum: Networking &amp; Wireless
---

### Post by cowboyjane on 2016-07-30
Hi

Uber-noob is having another problem.  &#55357;&#56838;

I've booted Ubuntu 16.04 (64bit) fine now on a new Windows 10 machine, from USB.  Also booted the 32 bit version up fine on my older Dell Inspiron with Vista.  But I can't get the Dell machine to connect to wifi.  In fact I can't find any wifi connection there at all.  

I used this bit from the help pages "

[LIST]
[*=left][FONT=inherit]Click the [COLOR=#808080][FONT=inherit]network menu[/FONT][/COLOR] on the menu bar and make sure that the [COLOR=#808080][FONT=inherit]Enable Wireless[/FONT][/COLOR] setting is checked."
[/FONT]
[/LIST]

 But I can't see that anywhere.  I can only find a network menu with an ethernet option.  Or an option to create a wifi connection, but I have no idea how to do that, or if that's the right thing if no wifi is showing anywhere?

Can anyone help?

---

### Post by mook765 on 2016-07-30
It seems you started a Live-session.
In that case, you will not be able to connect internet using wifi, you would need third party drivers, which are not included in the DVD-ISO.
You should connect to Lan, which will be detected automatically.
In the Notification area of the panel ( taskbar ) you should find an icon for the connection, even if no connection is established.

---

### Post by jeremy31 on 2016-07-30
*Thread moved to **Networking & Wireless**.*
Please visit the wireless script link in my signature and post your results

---

### Post by cowboyjane on 2016-07-30
I have only downloaded Ubuntu for the first time today and have no previous knowledge of Linux. I'm not entirely sure what you mean by "post my results".

I don't have a wired internet line, and can only access the internet via wifi in Windows Vista on the machine I'm trying to use Ubuntu on.  The instructions on the link on your signature for no internet connection doesn't seem to work for me/my old computer.  Can't get the text file to run when I've copied it over from Vista to Ubunto desktop.

---

### Post by grahammechanical on 2016-07-30
But you do see a Network Manager icon in the top panel on the right. Without either a wired or a wireless connection it should look like an Inverted cone. Another way to come at this is to open System settings>Network. That should open a dialog box and in the left pane there should be listed your network adapters, both wired and wireless. In the right pane there should be a list of the wireless access points. Including your wireless router.

If no wireless access points are listed it could (a) the WiFi adapter is switched off. (b) the WiFI adapter is disabled. (c) Networking is disabled. (d) the WiFi adapter needs a driver. To help track this down run this command:

```
rfkill list
```

This is what I see

> graham@sdb1-16:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Soft blocked: yes = WiFi disabled in Ubuntu. Hard blocked: yes = Wifi adapter switched off in hardware. It is possible that the WiFi adapter needs switching on in the BIOS settings utility. Or a key combination needs to be pressed to switch the WiFi adapter on. Another possibility is that the WiFi adapter has been switched off in Vista. In this case Ubuntu will not be able to switch the WiFi on once Ubuntu has loaded.

Depending on the actual situation there are another couple of commands that could be used. Let us see how it goes before we get to the point of needing to install a driver without a wired connection.

Regards

---

### Post by cowboyjane on 2016-07-30
> **grahammechanical said:**
> But you do see a Network Manager icon in the top panel on the right. Without either a wired or a wireless connection it should look like an Inverted cone. Another way to come at this is to open System settings>Network. That should open a dialog box and in the left pane there should be listed your network adapters, both wired and wireless. In the right pane there should be a list of the wireless access points. Including your wireless router.

If no wireless access points are listed it could (a) the WiFi adapter is switched off. (b) the WiFI adapter is disabled. (c) Networking is disabled. (d) the WiFi adapter needs a driver. To help track this down run this command:

```
rfkill list
```

This is what I see



Soft blocked: yes = WiFi disabled in Ubuntu. Hard blocked: yes = Wifi adapter switched off in hardware. It is possible that the WiFi adapter needs switching on in the BIOS settings utility. Or a key combination needs to be pressed to switch the WiFi adapter on. Another possibility is that the WiFi adapter has been switched off in Vista. In this case Ubuntu will not be able to switch the WiFi on once Ubuntu has loaded.

Depending on the actual situation there are another couple of commands that could be used. Let us see how it goes before we get to the point of needing to install a driver without a wired connection.

Regards


Thanks.  As I said in the original post, there are no wifi access points showing in the "inverted cone".  Just an option for Ethernet and a tab to create a wifi connection (no access points or wifi places detected which are there when I run the 64 version on my Windows 10 machine).

I've tried the command in the terminal prompt, and it doesn't give me any answer.  It just keeps returning me to the same command prompt cursor:

sjw@sjw-MM061:~$ rfkill list
sjw@sjw-MM061:~$

---

### Post by chili555 on 2016-07-30
> **mook765 said:**
> It seems you started a Live-session.
In that case, you will not be able to connect internet using wifi, you would need third party drivers, which are not included in the DVD-ISO.
You should connect to Lan, which will be detected automatically.
In the Notification area of the panel ( taskbar ) you should find an icon for the connection, even if no connection is established.
I see no evidence that s/he started a live session. However, even if s/he did, a great many wireless drivers are included by default and a wireless connection is quite possible.

I suggest that @cowboyjane ignore this mostly faulty information.

---

### Post by cowboyjane on 2016-07-31
On the old Vista machine, I used a USB boot at first.  But the same thing was happening after I installed Ubuntu.  It made no difference.  Whereas the Lenovo Windows 10 machine the wifi connects fine on a USB boot.

---

### Post by chili555 on 2016-07-31
On the Dell with Ubuntu booted up, please run, from a terminal:```
rfkill list all
lspci -nnk | grep 0280 -A2
```Post the result and we'll crack this case!

---

### Post by cowboyjane on 2016-07-31
It gives this: 

Kernal driver in use : r852
Kernal modules: r852
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [
14e4:4311] (rev 01)
   Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
   Kernal driver in use: wl

---

### Post by chili555 on 2016-07-31
```
rfkill list all
```Gives this?> Kernal driver in use : r852
Kernal modules: r852I doubt it. Would you please try again?> 0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [
14e4:4311] (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
Kernal driver in use: wlThat is the incorrect driver for this device. With a temporary internet connection, by ethernet, tethered or whatever means possible:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Reboot and your wireless should be working.

---

### Post by cowboyjane on 2016-07-31
I already said, the rfkill and rfkill list all commands on their own just return me to the flashing cursor.  There is nothing there.  

When added all together, what I get is what I typed out. If I could post a screen shot I would.

(Please see earlier post.)

And as I also said in an earlier post, I don't have any means of non-wifi internet access. And I have no exoerience of Linux, this was originally posted in the new to Ubuntu forum, but was moved.

---

### Post by chili555 on 2016-07-31
> **cowboyjane said:**
> I already said, the rfkill and rfkill list all commands on their own just return me to the flashing cursor.  There is nothing there.  

When added all together, what I get is what I typed out. If I could post a screen shot I would.

(Please see earlier post.)Did you change the driver as I suggested?

---

### Post by cowboyjane on 2016-07-31
Does it have to be done while in Ubuntu - or can I go back and do that in Vista?

---

### Post by chili555 on 2016-07-31
> **cowboyjane said:**
> Does it have to be done while in Ubuntu - or can I go back and do that in Vista?In Ubuntu is the only way it will work.

---

