---
title: "Can't Connect To WiFi"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by cagey cretin on 2007-08-30
Hola. :D

First, let me say that both version of Ubuntu I've used recognized my IBM Thinkpad R50's a/b/g mini pci card out of the box. This is just so sweet. :) I used HH a couple of years ago, but then changed to Core 4 last year (bad mistake), and I am on Dapper Drake right now.

I have a home set up with an encrypted key, named ESSID, and this setup works just great. However, I went to my library the other day, and they have an open system. All the windows users were able to connect just fine, but not me. 

My Questions:

1) How can I set up the laptop to connect in one of these WiFi environments? My ath0 config forces me to select a key type (hex or ascii) even if one is not needed. My configuration only allows DHCP or Static, which is set to DHCP.

2) Is there a way to set up my laptop so I can keep my home settings untouched and yet still be able to connect in a secondary environment?

Thank you for reading, and thank you in advance for any help you might offer,

cc

---

### Post by bmartin on 2007-08-30
> **cagey cretin said:**
> 1) How can I set up the laptop to connect in one of these WiFi environments? My ath0 config forces me to select a key type (hex or ascii) even if one is not needed. My configuration only allows DHCP or Static, which is set to DHCP.
If you leave the key blank, it should work the same as having an unencrypted connection.

> **cagey cretin said:**
> 2) Is there a way to set up my laptop so I can keep my home settings untouched and yet still be able to connect in a secondary environment?
I use WICD ([info here]("http://wicd.sourceforge.net/") -- [installation here]("http://blakecmartin.googlepages.com/wicd.html")) to connect to wireless networks. It allows you to select whether networks connect automatically, which kind of encryption they use, etc., and it has a nice tray icon.

Another nice program for wireless connection management is wifi-radar. Some simple installation instructions can be found [here]("http://blakecmartin.googlepages.com/wifi-radar.html"), or if you prefer to use a GUI to install, you can install if from Synaptic by adding the Universe repository and installing the **wifi-radar** package.

The built-in internet connection management programs are very limited.

---

### Post by cagey cretin on 2007-08-30
> **bmartin said:**
> I use WICD ([info here]("http://wicd.sourceforge.net/") -- [installation here]("http://blakecmartin.googlepages.com/wicd.html")) to connect to wireless networks. It allows you to select whether networks connect automatically, which kind of encryption they use, etc., and it has a nice tray icon.

Another nice program for wireless connection management is wifi-radar. Some simple installation instructions can be found [here]("http://blakecmartin.googlepages.com/wifi-radar.html"), or if you prefer to use a GUI to install, you can install if from Synaptic by adding the Universe repository and installing the **wifi-radar** package.

The built-in internet connection management programs are very limited.

Giving WICD a try. Thanks for the install info and the pointer. Off to the library with me. :D

---

### Post by cagey cretin on 2007-08-30
Posting from my library right now. Thank you very much, bmartin!

cc

---

### Post by bmartin on 2007-08-30
You're welcome. I have one other thing to say that might interest you.

You can run the tray program automatically when your computer starts by adding in the appropriate line into the Sessions program. Assuming you're using GNOME, go to System > Preferences > Sessions, then under the **Startup Programs** tab, click **New**. Assuming you installed it using my instructions, you should be able to run it with the Command **wicd-tray**.

To add it to KDE's startup, enter **ln -s /usr/local/bin/wicd-tray $HOME/.kde/Autostart/wicd-tray** in a terminal.

---

### Post by halw on 2007-09-04
Does wicd work with dapper? Noticed it mentions feisty as as repo.

---

### Post by cagey cretin on 2007-09-04
> **halw said:**
> Does wicd work with dapper? Noticed it mentions feisty as as repo.

Works great! I followed bmartin's tips. Fast and easy on Dapper.

---

