---
title: "WiFi File Transfer"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by Chip88 on 2013-09-22
Hi there!

Yesterday, I saw for the first time that it's possible to transfer files from your Android - Smartphone to your PC (and the other way around).
Obviously, this seems to be very useful. Especially, if you don't have to search for an USB - cable all the time.

The app "ES File Datei Explorer" ([https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en](https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en)) comes with an integrated *Remote - Manager*.
If you activate it, you'll get a FTP - address like [ftp://192.168.178.XX:XXXX](ftp://192.168.178.XX:XXXX) .
You've to enter it into your browser or any FTP - programme and then you'll have access to all the files on your Android via WiFi.
&#8594; Unfortunately, the access to the FTP wasn't successful and canceled every time I tried it.

I tried then another app ("WiFi File Transfer", [https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer&hl=en).Here](https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer&hl=en).Here) you get a HTTP - address like [http://192.168.178.XX:XXXX](http://192.168.178.XX:XXXX) .
&#8594; Unfortunately, I couldn't get any access neither.

Today I tried both addresses in Dolphin on a computer, which is connected via a LAN - cable to the internet - and voilà:
Both addresses did work and showed me all the files on my Android.

[B]So, I'd like to know how it happens that I can't access to my Android with my notebook, which is connect via WiFi with the internet;
but a computer, which is connected via a LAN - cable to the internet, can do?![/B]

As router we use a Fritzbox.

Thanks in advance for your help & your timely answers.

Mark

---

### Post by SeijiSensei on 2013-09-23
Are all the machines including the phone in the 192.168.178.0/24 network?  Can you ping the phone from the laptop?  If you install a [Terminal]("https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en") application on the phone, can you ping the laptop?

I've used Wifi File Manager (although I bought the Pro version to remove the filesize limitation of the free version).  It worked as advertised for me, though all my machines are on the same subnet.  FTP is a pain in the neck to set up, so I avoid those kinds of apps entirely.

I have no idea what a "Fritzbox" is, so I can't help you there.

---

### Post by houstonbofh on 2013-09-23
Do you have user mode isolation enabled on the wireless?

---

### Post by Chip88 on 2013-09-24
SeijiSensei & houstonbofh:
Thank you very much for your answers.

Great to hear, everything works fine with the app *Wifi File Manager*.

*Fritz!Box* is a router (very common here in Germany).
And in the WiFi settings, all the time the option that all the devices within the same net can actually communicate with each other.

Well, this evening I remembered we have an Android - tablet here at home.
And I tried to communicate my smartphone via the app *Wifi File Transfer* (IP [http://192.168.178.26:1234](http://192.168.178.26:1234)) and even via the *FS File Manager* (IP [ftp://192.168.178.26:3721](ftp://192.168.178.26:3721)).

**Both ways worked like a charm!!! Without any troubles.**

This means to me, the issues has to be on the notebook's side, i. e. Kubuntu.

Now, it's your turn again, please:
What should I then change in my system to get the wifi file transfer to work???

I don't know exactly, what do you mean with ***user mode isolation***, houstonbofh.

Thanks to everybody in advance!
Mark

_**EDIT:**_
@ houstonbofh: The user mode isolation forbid devices to communicate with each other, right?!
So, no, this option is disabled. Wireless devices CAN communicate with each other (as seen above: the communication between my Android Smartphone and the Android Tablet worked well!).

---

### Post by SeijiSensei on 2013-09-24
I'm assuming your Kubuntu laptop is set up to use DHCP to get an address from the wireless router, which is the default.  If you entered a static IP address, switch to DHCP instead.

In KDE, click on the little transmitter icon in the panel's System Tray, then click on the WLAN Interface panel to bring up its details.  What IP address does it have?  Is it in the same subnet as the other devices?

One useful diagnostic tool is **nmap** which you can install from the repositories.  On the laptop, use the command:

```
$ nmap -sP 192.168.178.0/24
```

That will run a "ping scan" of the entire subnet and show you which devices the laptop can see.

---

### Post by Chip88 on 2013-09-24
Hi SeijiSensei!

Thanks again for your answer.

First of all the results of the *ping scan*:
```
Starting Nmap 6.00 ( http://nmap.org ) at 2013-09-25 01:07 CEST
Nmap scan report for fritz.box (192.168.178.1)
Host is up (0.0049s latency).
Nmap scan report for chip.fritz.box (192.168.178.24)
Host is up (0.00089s latency).
Nmap done: 256 IP addresses (2 hosts up) scanned in 2.62 seconds
```

So, obviously, my laptop can only see the router (named *fritz.box*).
Otherwise I already had been able to connect my Smartphone or Tablet to my Laptop.

Well, for sure, all devices here are in one and the same WiFi network.

I didn't enter a static IP address, as far as I know.
And in the settings of the WLAN Interface panel there is also anywhere a static IP address.
It only says: [I]Method: Automatic (DHCP)

[/I]That's all.
Do I maybe have to changed anything there?
Maybe I have to change *mode *to *Ad-Hoc *or *AP-Modus*. This function is set by default to *infrastructre*.

I added two screenshots and although they're in German, I'm sure you'll understand them:
- [http://imageshack.us/photo/my-images/571/5xdj.png](http://imageshack.us/photo/my-images/571/5xdj.png)
- [http://imageshack.us/photo/my-images/593/jzcg.png](http://imageshack.us/photo/my-images/593/jzcg.png)
 
Thank you in advance!!!

---

### Post by SeijiSensei on 2013-09-25
I'm guessing there's some setting in the router that needs to be changed, but I can't help with that.  I'd see what kinds of help you might get at [http://www.fritzbox.eu/en/index.php](http://www.fritzbox.eu/en/index.php).

---

### Post by kurt18947 on 2013-09-25
I don't know if this will help but I had a similar problem to Chip88 trying to connect to an FTP server integrated into a router.  I messed about then installed "filezilla" from the repositories.  Problem solved!

---

### Post by Chip88 on 2013-09-25
Well, kurt18947, I don't think your solution will work for me.
My problem is that I don't have any connection between my Android and my notebook **in a protected WiFi network (WPA2 - PSK)**.
In an open network, i. e. withouth protection at all, everything just works like a charm.

Apparently, this is caused by a misconfiguration within my router - not the settings I made there!

In the [German Ubuntu Forum]("http://forum.ubuntuusers.de/topic/dateiuebertragung-via-wlan/10/#post-5967357") someone worked with me for two days now to find a solution and finally, some minutes ago, we succeeded to build up a connection.

By generating static ARPs on both devices, I'm able to connect my Android and my notebook.

This is how we did:
1. Open the terminal on your notebook and type in:
```
sudo arp -i eth1 -s **THE.IP.ADDRESS.OF.YOUR.ANDROID ****THE:MAC:ADDRESS:OF:YOUR:ANDROID**
```

2. Typing in ```
arp -av
``` now finally recognizes the Android device.

3. Open a terminal emulator on your Android device and type in:
```
sudo arp -i wlan0 -s **THE.IP.ADDRESS.OF.YOUR.NOTEBOOK ****THE:MAC:ADDRESS:OF:YOUR:NOTEBOOK**
```

4. Typing in the terminal emulator ```
arp -av
``` now finally recognizes the notebook.

You're able to connect your Android and your notebook now and access your files with the help of apps like *WiFi File Transfer* or *ES File Manager*.

**&#8594; BUT:** I think, it's impossible that this is the solution of the problem, i. e., connecting Kubuntu with Android in a protected WiFi Network.

First of all, what do you think about that solution?!

Is there maybe a possibility to make a script or something similar, so I don't have to type in every time the codes above?!

Thanks in advance!
Mark

---

