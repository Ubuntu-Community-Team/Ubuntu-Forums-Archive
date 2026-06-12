---
title: "Lubuntu 17.10.1 installed to Hp Pavilion - no wireless"
date: 2018-02-12
forum: Networking &amp; Wireless
---

### Post by miker1 on 2018-02-12
I'm new to Ubuntu and have little knowledge of the Terminal.
With the exception of the wireless, Lubuntu loaded ok to my Hp Pavilion dv4200EA.
 I've tried:
- The switch on the keyboard.
-Rebooting.
-Shutting down, removing the battery and power cable, holding the power button for 20 seconds. Then retrying.
- Checking the bios.
All to no avail.

In the Terminal I've tried various commands collected from various sources. With no success.

The result of       rfkill list all

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I would appreciate any help you can offer.
Thanks

---

### Post by chili555 on 2018-02-12
Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by miker1 on 2018-02-12
thanks for responding.
tried the first two commands, no change.
The 'wireless info script' do I copy and paste it into the Terminal. Then copy the Run command also into the Terminal.
Thanks

---

### Post by chili555 on 2018-02-12
Copy and paste this entire sequence into the terminal:```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```Press Enter. It will output something like this:```

--2018-02-12 10:25:33--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2018-02-12 10:25:33--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.192.133, 151.101.128.133, 151.101.64.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.192.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17021 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  16.62K  --.-KB/s    in 0.008s  

Last-modified header missing -- time-stamps turned off.
2018-02-12 10:25:33 (1.93 MB/s) - ‘wireless-info’ saved [17021/17021]

[sudo] password for chili: 

[COLOR="#FF0000"]Results saved in "/home/chili/wireless-info.txt".[/COLOR]

Results also archived in "/home/chili/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

```Where is says that the results were saved as wireless-info.txt, find that rather big text file and post it at pastebin or here [http://paste.ubuntu.com](http://paste.ubuntu.com) and give us the link. That way, we can review all the relevant data and propose a solution.

---

### Post by miker1 on 2018-02-12
hope I've done this correctly
[URL="https://paste.ubuntu.com/=73JXpWKMkQ/plain/"]

[https://paste.ubuntu.com/=8NnznWgW6k/](https://paste.ubuntu.com/=8NnznWgW6k/)
[/URL]

---

### Post by chili555 on 2018-02-12
> **miker1 said:**
> hope I've done this correctly
[URL="https://paste.ubuntu.com/=73JXpWKMkQ/plain/"]

[https://paste.ubuntu.com/=8NnznWgW6k/](https://paste.ubuntu.com/=8NnznWgW6k/)
[/URL]You gave us the terminal output. We want the wireless-info.txt that the script generated.

---

### Post by miker1 on 2018-02-12
Sorry, try this


[https://paste.ubuntu.com/=dKSb5CRk9d/](https://paste.ubuntu.com/=dKSb5CRk9d/)

---

### Post by chili555 on 2018-02-12
> Network controller [0280]: Broadcom Limited BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [[COLOR="#FF0000"]14e4:4318[/COLOR]] (rev 02)Some old guy wrote up a whole big post about Broadcoms. Please wander over there and check it out: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Post back if you get stuck.

---

### Post by miker1 on 2018-02-13
Hi, I tried to follow the thread you suggested but only got so far before the ouputs where very different from those expected.
Thanks for your persistence.


[https://paste.ubuntu.com/p/DsJVc5WT5B/](https://paste.ubuntu.com/p/DsJVc5WT5B/)

---

### Post by chili555 on 2018-02-13
On the look-up list, opposite your pci.id of 14e4:4318, it says that the package to install is firmware-b43-installer. Please try:```
sudo apt-get install firmware-b43-installer
```Reboot.

---

### Post by miker1 on 2018-02-13
I did as you said and I now have wireless.
Thank very very much for your help.
I need to learn a lot more about the Terminal.
Mike

---

