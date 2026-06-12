---
title: "Browsing Bluetooth Device"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by columbo1977 on 2008-01-03
Hi

Hope someone can help as I have been looking all over the forums to try and sort this??

I have a bluetooth dongle attached, no matter what i try I cannot connect to the phone, if i right click on a file i can send it to the phone and if i send something to the computer it comes up on the desktop.

What i cannot do is browse the phone, when i try it comes up with 

Couldn't display obex check if service is available - on the bottom of the screen a popup tells me the bluetooth is connected then disconnects??????

I have run apt-get to install obex so that isnt the answer??

I have use a few different ways and now have blueman installed at the moment.

Would appreciate help as i need to get the contents off my phone.

Cheers

Columbo1977

---

### Post by pietjanjaap on 2008-01-03
At the moment it's not working for me, but i read a lot, and saved some info, here it is:


hi, im having a problem connecting my mouse to my ubuntu.
heres the comman i used:
rhanex@X-ZODIA:~$ hcitool scan
Scanning ...
00:1B:AF:B4:9E:5A Nokia 6120 classic
00:0E:9B:DA:BB:2E INNKDDAVID
00:50:F2:E8:A3:EA Microsoft Mouse
rhanex@X-ZODIA:~$ hidd --connect 00:50:F2:E8:A3:EA
HID create error 13 (Permission denied)
i keep getting this error when i try to connect my mouse, wats up with this?

Its a guess , try sudo hidd --connect 00:50:F2:E8:A3:EA





sudo hidd --search




hcitool scan


I managed to get my internet over bluetooth, with wm5 and internet sharing. Here is what I did. I'm using t-mobile internet with a T-Mobile MDA that has internet sharing.

Part of this guide is from [http://news.softpedia.com/news/Conne...on-50670.shtml](http://news.softpedia.com/news/Conne...on-50670.shtml)

If your laptop has an incorporated bluetooth adaptor and so does your phone, you could try the following to connect your computer to the Internet through the phone's GPRS connection:

1. Open Synaptic and install the following packages:
&#8226; bluez-utils
&#8226; bluez-passkey-gnome
&#8226; gnome-bluetooth
&#8226; bluez-pin*

2. Turn your phone's BT connection and set its visibility to 'Show to all' or equivalent.

3. Open a terminal and type:

Code:

hcitool scan

You should see something like:

Code:

Scanning ...
00:0E:07:37:7C:BD 6230i

(Your device identification will be different)

4. Open /etc/bluetooth/hcid.conf in a text editor and set:
autoinit yes
security auto
pairing multi
passkey whatever-you-want

5. Press ALT+F2 and run the

Code:

bluetooth-applet

6. On your mobile phone, go to bluetooth settings, search for a new device and add your computer and pair it using the passkey you set up before

7. On your mobile phone to Start->Programs->Internet Sharing, choose Bluetooth PAN, and your NetworkConnection (Mine is T-Mobile GRPS/EDGE), and choose Connect

Open a terminal:

8. sudo modprobe bnep

9. sudo pand --connect 00:0E:07:37:7C:BD

10. sudo ifconfig bnep0

11. sudo ifup bnep0

It should assign you an IP address automatically. And thats it!

I'm actually writing this guide using my internet over bluetooth, so I know it works for sure!

I hope this helps




gnome-phone-manager

---

### Post by columbo1977 on 2008-01-04
Hi

Thanks for the reply but I am not trying to use the Bluetooth dongle for internet all I want is to be able to browse the phone so I can take all the photos and videos off it in bulk to backup.

My phone is bonded with the computer.

Forgot to say before but I am using Gutsy 7.10.

Ta

---

### Post by pat_can_vault on 2008-02-25
bump

---

### Post by columbo1977 on 2008-02-25
Bump??

---

