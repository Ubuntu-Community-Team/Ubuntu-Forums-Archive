---
title: "scanning wlan spots and connect to them in aa easy way?"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by freeka on 2007-08-19
hi

i got wlan working on my vaio vgn-a417m with this tutorial:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa)

however, this has the great disadvantage that i just can only connect to this spot.
i can't scan networks, choose one and connect with a pass

wlan is working fine, so it should be possible to realize that in the way i described. but how/with what programs?

kwlan says "cant find a wpa_supplicant configuration"

although i didnt need one for the configuration given in the link above, i created one

```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="wassup"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk="XXX"
}

```

so kwlan isnt workin at all.

---

### Post by Jamie Jackson on 2007-08-19
Are you running Feisty?

---

### Post by freeka on 2007-08-20
ah yeah, forgot to mention that

running feisty, latest version of xubuntu

---

### Post by Jamie Jackson on 2007-08-20
You shouldn't need to go through the hassle of configuring wpa_supplicant*, if you run NetworkManager. NetworkManager is a roaming-capable app that installs with Feisty (on Ubuntu-proper, anyway).

What's the output of:
```
nm-applet --version
```

*Yes, it's a pain that there are 100 different ways to skin a cat in Linux, and that 99 of them are unnecessary and obsolete, but still documented online somewhere.

---

### Post by freeka on 2007-09-10
seems like i didnt got it

freeka@fogel:~$ nm-applet --version
The program 'nm-applet' is currently not installed.  You can install it by typing:
sudo apt-get install network-manager-gnome
bash: nm-applet: command not found

ok so i installed it



freeka@fogel:~$ apt-get install network-manager-gnome

freeka@fogel:~$ nm-applet --version
GNOME nm-applet 0.6

freeka@fogel:~$ nm-applet 
/bin/sh: /usr/bin/esd: not found
<empty prompt here>


i think this isnt still alright? ;)

---

### Post by Jamie Jackson on 2007-09-10
Try this instead: 

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by freeka on 2007-09-10
well..

freeka@fogel:~$ sudo apt-get install network-manager network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager is already the newest version.
network-manager set to manual installed.
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
freeka@fogel:~$

/e iwlist eth1 scan gives me a nice list of networks, so wlan itself is workin fine

---

### Post by Jamie Jackson on 2007-09-10
I'm at a loss as to why nm-applet's not installed or not on the path. Could you try this?

./usr/bin/nm-applet

---

### Post by freeka on 2007-09-12
well nm-applet seems to work now!

so i have a wlan tray in my top bar. i can connect with it to unecrypted wlans, not to encrypted ones (no error message)

i also can use wpa_supplicant to use a non-encrypted wlan. so this program and all the config stuff work. but he cant really connect to a encrypted wlan(at this moment i cant post his error messages)

also, nm-applet tends to crash when i click on it

---

### Post by Jamie Jackson on 2007-09-12
I don't know what's wrong with that configuration or why NM is crashing, but a couple things:

If you're connecting to unencrypted networks, then wpa_supplicant is not involved.
If you're using nm-applet to connect, then it's not any manual configuration that is allowing you to connect, it's just NetworkManager.

---

