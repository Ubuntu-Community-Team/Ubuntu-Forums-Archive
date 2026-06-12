---
title: "Getting dell laptop wireless to work"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by corbypete on 2007-07-28
Ok so I have a dell D520 laptop and got ubuntu installed on the external usb (so works xp cant spy on my home activities)

I now need to get the wireless working.

I have an internal wireless and a pcmcia D-link AG660 to choose from, but both load in ubuntu with the Restricted Driver Manager

The cards see my local wireless lan, but cant pick up an ip address (i dont know how to force this in ubuntu so i changed the details and reboot). So its kind of working?

How can i troubleshoot further?

My home ip's are distributed by an XP machine running ICS. I tried putting in a manual  ip but still no joy.

---

### Post by nick.inspiron6400 on 2007-07-28
Are you using gnome network-manager?

---

### Post by corbypete on 2007-07-28
yeah, its gnome and the version is the latest ubuntu

---

### Post by corbypete on 2007-07-28
bounce

---

### Post by NilsE on 2007-07-28
In ubuntu 7.04 and Gutsy the following steps worked for me which I culled from a few other posts. This also added the capability to use WPA

```
In Synaptic package manager:

1) Make sure network-manager-gnome  is installed

2) Make sure wpasupplicant is installed

3) Install libpam-keyring


```

```
In System Administration:

Make sure the restricted driver for the chip is there, enabled and in use.
```

```
In terminal:

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring

and not get prompted by the keyring manager every time. This is not mandatory.
```

```
In System/Preferences/Session:

Add gksudo nm-applet (if the network manager is not there) as the command 

line to a new start programs. You can name it whatever you want. It may 

work without the gksudo.
```

```
You may also have to clean out the /etc/network/interfaces file if you have

 configured any devices manually. Just leave these 2 lines. (back it up first)

auto lo

iface lo inet loopback
```

SHUTDOWN AND RESTART

NOTE: The applet may not show up in the upper panel so you can right click 

on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

---

