---
title: "Acer Aspire One Netbook Wireless is greyed out"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2014-04-22
I have just installed lubuntu 13.10 on my Acer Netbook, but do not know how to set up the wireless networking.

In Network Connections / Wireless tab, it shows "Wireless Connection 1", used Never.

Clicking on Edit, there are several fields:

SSID (is this the name of my Access Point or what?)

BSSID (I don't know what this is. Do I need to fill in anything here?)

Between these two is MODE with a drop down box offering a choice of Infrastucture or Ad Hoc (I don't know which I should use)

Device Mac Address (with an IP# displayed)

Cloned Mac Address (I don't know what this is. Do I need to fill in anything here?)

MTU (with "Automatic" filled in)

Could someone guide me through set up so that I can take the Netbook on a trip with me tomorrow and be able to access WiFi? Thanks.

---

### Post by Old_Grey_Wolf on 2014-04-22
SSID is your Access Point name.
BSSID you do not need.
MODE set to Infrastructure.
Device Mac Address leave it alone.
Cloned Mac Address don't need it most likely.
MTU AAutomatic.

---

### Post by Odyssey1942 on 2014-04-22
Thanks for yours. Before posting, I had experimented and did as you suggested without success.

Have done it again, but with a different access point, but still no cigar, and I can't see that anything has changed anywhere else. The Network Connections icon in the bottom right of the panel still has Wireless Connections grayed out. Do I need to restart or what else can I try?

---

### Post by Old_Grey_Wolf on 2014-04-22
[s]Open Dash Home and[/s] search for Addition Drivers. See if any are offered.

Edit: Never mind I see you are using Lubuntu. I don't know how to find Additional Drivers in Lubuntu.

---

### Post by Rex Bouwense on 2014-04-22
Have you enabled Networking and enabled WiFi?  Right click the icon in the LXPanel to access them.

---

### Post by Odyssey1942 on 2014-04-22
I did right click on the little pie-shaped icon in the bottom right corner of the panel and clicked on Enable Wireless (Enable Wired is already ticked).

Going to the bottom of that popup (from right clicking the icon) and clicking on Edit Connections took me to the screen mentioned in my last 2 posts.

But if I left click the icon, "Wireless Networks" is grayed out.

Have looked at everything I can find, but nothing that gets me past this point.

---

### Post by papibe on 2014-04-22
Thread moved to **Networking & Wireless**.

---

### Post by Odyssey1942 on 2014-04-22
Howdy all,

I hope that someone can move this along for me as we depart early tomorrow for several days in a place with wifi, but no eth. connection and I would like to get this working before we leave as I will not have a connection there to work on this without success tonight. 

I feel like a solution is close but at the moment I am stymied.

Thanks.

---

### Post by Odyssey1942 on 2014-04-28
Am bringing this back to the top in hopes of finding someone who will shed some light on this. Thanks.

---

### Post by wildmanne39 on 2014-05-02
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by Odyssey1942 on 2014-05-03
Thanks for your kind assistance.

Here is the file.

Edit. Please disregard above and upload. Had a brain fart (I did warn that I am both old and a beginner) and uploaded from my desktop. Have to bring netbook here for wired connection. Will do later today if I can pick it up, or tomorrow. Thanks now for your patience.

---

### Post by wildmanne39 on 2014-05-03
Is the file you from your desktop? it does not show an internal wireless card.

---

