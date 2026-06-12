---
title: "macchanger installation issues for Ubuntu 10.04"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by SocialNetwork123 on 2010-05-04
I have installed version 10.04 LTS, 

can anyone provide a step by step guide to installing:

        **[SIZE=4] macchanger[/SIZE]**

I have tried various options, downloading packges, using the software centre, apt etc. But I can't figure things out after 1.5 hours!

Any help appreciated. I have tried the help documentation, but struggling to work things out.

**Links:**

[http://packages.ubuntu.com/source/lucid/macchanger](http://packages.ubuntu.com/source/lucid/macchanger)
[http://www.alobbs.com/macchanger](http://www.alobbs.com/macchanger)

---

### Post by cariboo on 2010-05-04
Macchanger is in the repositories, there is even a gui interface, go to System->Administration->Synaptic Packager Manager, and search for macchanger, make sure you select the macchnager-gtk. to use it without rebooting press Alt-F2 and type:

```
gksudo macchanger-gtk
```

then all you have to do is fill in the info.

---

### Post by SocialNetwork123 on 2010-05-05
Thanks, I managed to install macchanger, via you straightforward instructions and the code tip on using it without needing a reboot was very handy. It seems I have to click on more Software Source in the Synaptic Packager Manager for the macchanger-GTK to show up.

Problems changing wlan0 MAC!
----------------------------------------

Though I am having problems getting macchanger to work, I can change the MAC address for eth0 instantly, but I cannot change wlan0 to change and I can't find any 'how to' or help files for macchanger on [http://www.alobbs.com/macchanger](http://www.alobbs.com/macchanger) within the packages.

Thanks for your help

---

### Post by SocialNetwork123 on 2010-05-05
Changing MAC for wlan0 sorted :p

I have worked it out, I had to:

Disable networking
Change MAC
Enable networking
Reconnect to wifi

I am getting more impressed with Ubuntu

> **SocialNetwork123 said:**
> Thanks, I managed to install macchanger, via you straightforward instructions and the code tip on using it without needing a reboot was very handy. It seems I have to click on more Software Source in the Synaptic Packager Manager for the macchanger-GTK to show up.

Problems changing wlan0 MAC!
----------------------------------------

Though I am having problems getting macchanger to work, I can change the MAC address for eth0 instantly, but I cannot change wlan0 to change and I can't find any 'how to' or help files for macchanger on [http://www.alobbs.com/macchanger](http://www.alobbs.com/macchanger) within the packages.

Thanks for your help

---

### Post by KunChan^^ on 2010-05-13
plz help me..i cannot search macchanger using the manager,,when i install it with sudo apt-get install macchanger it says package not founddd,,><:(

---

