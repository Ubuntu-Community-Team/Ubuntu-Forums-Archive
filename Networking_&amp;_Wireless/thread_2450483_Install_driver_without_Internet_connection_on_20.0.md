---
title: "Install driver without Internet connection on 20.04?"
date: 2020-09-14
forum: Networking &amp; Wireless
---

### Post by astronomy1986 on 2020-09-14
hi all,

I just downloaded ubuntu 20.04 to finally move on from Windows 7. Problem is I don't have a wired Internet connection, I use my phone as a hotspot then connect my pc using a tp-link ac600 archer t2u wireless usb adaptor. Ubuntu doesn't  allow me to connect to Internet using my wireless adaptor so while using ubuntu im cut off from the Internet  on my pc. 

I have read some fixes for getting the wireless  adaptor to possibly work with ubuntu but I think they require my pc to be connected to the Internet, a bit of a catch 22 situation. I still have windows 7 so can i download driver to a USB drive then load ubuntu and install said driver???

Im literally a noob with Linux and ubuntu so could use some help please 

Thank you

---

### Post by morrownr on 2020-09-14
I think this can be solved. Many of the solutions do seem to make it look like you have to have internet to install wifi adapters but if that adapter is your internet access, what do you do?

First and foremost, we need to identify exactly what chipset that adapter is using. Since it is an AC600 adapter, my guesses would include rtl8811au or rtl8811cu but my guesses don't matter.

The TP-Link web site shows 3 versions of this adapter have been sold. Do you know if this is v1, v2 or v3?

Open a terminal and run the follow code with the adapter plugged in so maybe we can see the device ID:

```
lsusb
```

---

### Post by CelticWarrior on 2020-09-14
Welcome.

You can use USB tethering (shows up as "USB Ethernet" in Ubuntu 20.049) instead of WiFi's.
Once connected you may want to try this: [https://askubuntu.com/a/1191835](https://askubuntu.com/a/1191835)

Please note the driver above is for the[COLOR=#242729][FONT=Arial] T2U with ID** 2357:011e**&#8203; only.[/FONT][/COLOR]

---

### Post by astronomy1986 on 2020-09-14
[ATTACH=CONFIG]286959[/ATTACH]

Im sorry, I can't get picture the right way up, don't know why :(

The packaging says its ver.3.0.

I downloaded a driver file from github but the readme file makes no sense to me.
[https://github.com/gordboy/rtl8812au-5.6.4.2](https://github.com/gordboy/rtl8812au-5.6.4.2)

---

### Post by astronomy1986 on 2020-09-14
I think that link shows the driver I downloaded, no idea what to next though

---

### Post by CelticWarrior on 2020-09-14
1. Please do not post code as images. Select it, right-click > copy (or CTRL+SHIFT+C) and then paste it here inside code tags ("Go Advanced", press "#" and past inside). If anything, your pictures show you have additional problems, a likely wrong resolution for starters.

2. Please do not ignore links posted. I know I've said "[COLOR=#000000]for the[/COLOR][COLOR=#242729][FONT=Arial] T2U with ID** 2357:011e**&#8203; only" but your [/FONT][/COLOR][COLOR=#242729][FONT=Arial]**2357:011f **is the same chipset and supported by the same driver. 

3. Do NOT download things willy nilly especially when you evidently don't know what to do with it. The post at AU I linked above has the full instructions and it just requires a working internet connection (again, USB tethering):
[/FONT][/COLOR]```

[FONT=Consolas]sudo apt install git dkms
[/FONT][FONT=Consolas]git clone https://github.com/aircrack-ng/rtl8812au.git
[/FONT][FONT=Consolas]cd rtl8812au[/FONT][FONT=Consolas]
[/FONT][FONT=Consolas]sudo ./dkms-install.sh
[/FONT]
```[COLOR=#242729][FONT=Arial]

where each line represents one single command to be entered one at the time.

[/FONT][/COLOR]

---

### Post by astronomy1986 on 2020-09-14
> **CelticWarrior said:**
> 1. Please do not post code as images. Select it, right-click > copy (or CTRL+SHIFT+C) and then paste it here inside code tags ("Go Advanced", press "#" and past inside). If anything, your pictures show you have additional problems, a likely wrong resolution for starters.

2. Please do not ignore links posted. I know I've said "[COLOR=#000000]for the[/COLOR][COLOR=#242729][FONT=Arial] T2U with ID** 2357:011e**&#8203; only" but your [/FONT][/COLOR][COLOR=#242729][FONT=Arial]**2357:011f **is the same chipset and supported by the same driver. 

3. Do NOT download things willy nilly especially when you evidently don't know what to do with it. The post at AU I linked above has the full instructions and it just requires a working internet connection (again, USB tethering):
[/FONT][/COLOR]```

[FONT=Consolas]sudo apt install git dkms
[/FONT][FONT=Consolas]git clone https://github.com/aircrack-ng/rtl8812au.git
[/FONT][FONT=Consolas]cd rtl8812au[/FONT][FONT=Consolas]
[/FONT][FONT=Consolas]sudo ./dkms-install.sh
[/FONT]
```[COLOR=#242729][FONT=Arial]

where each line represents one single command to be entered one at the time.

[/FONT][/COLOR]

im posting from my pc which is connected to the internet via wifi :guitar:

i apologise. i didnt ignore the link you posted, i just didnt know what to do with that information.

the info you posted in the quoted post above worked for me, i got wifi working, thanks a million :mrgreen::mrgreen::mrgreen:

---

