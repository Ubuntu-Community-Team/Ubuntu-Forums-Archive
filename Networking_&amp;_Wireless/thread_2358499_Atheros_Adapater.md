---
title: "Atheros Adapater"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by terryhe on 2017-04-14
Hi Guys,

Hopefully somebody can help with this. I was running Ubuntu and Windows 10 on my laptop. I have now changed it so my laptop is no longer dual boot and only Ubuntu 17.

My Atheros USB wireless adapter worked fine with Ubuntu 16 but since I made the change above it now does the following:

Sees the wireless networks but will not connect when I enter the wifi code.

I also have an onboard card. This works fine but I need my wireless adapter working.

Any ideas?

---

### Post by ajgreeny on 2017-04-14
See Wireless-info in my signature and follow the instructions there to run the script and post results back here.

Users who know much more about wifi than me will be able to help you more than I can.

---

### Post by Autodave on 2017-04-14
Couple of things come to mind.  I have several laptops, but one in particular gives me fits anytime I try to enter a wireless password: it will take me 20-40 times before it actually accepts it. Why? No idea.

Another is this: on any laptop, when something that used to work suddenly quits working for no apparent reason, try this.....and don't laugh.....I have "fixed" many laptops this way: shut down, disconnect AC power, remove battery. Wait 10 minutes, reinstall battery and power up. See if wireless works now.

---

### Post by terryhe on 2017-04-14
Well the thing is that it seems to take the password. When I enter it I'm given the option to disconnect however its not really connected. The WI-fi icon flashes like it is still trying to connect. Very frustrating!

---

### Post by terryhe on 2017-04-14
Also I cant remove the battery. Its a Dell laptop but a new'ish model cant remove it.

---

### Post by wildmanne39 on 2017-04-14
This is an issue with 17.04 and several adapters, this fix works for certain issues, that have been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

---

### Post by terryhe on 2017-04-14
Thank you so much this worked. I was losing hope.



> **wildmanne39 said:**
> This is an issue with 17.04 and several adapters, this fix works for certain issues, that have been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

---

### Post by wildmanne39 on 2017-04-14
Your very welcome!
Enjoy!

---

