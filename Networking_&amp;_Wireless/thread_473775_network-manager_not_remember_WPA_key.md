---
title: "network-manager not remember WPA key"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by gnychis on 2007-06-14
Hey all,

I have a WPA2 wireless network at home, i am running network-manager, i click on the wireless symbol and a list of wireless networks come up, then i select mine and type my WPA2 key.  When i reboot, it forgets all about it.  How do i get it to remember?

Thanks!
George

---

### Post by stchman on 2007-06-14
> **gnychis said:**
> Hey all,

I have a WPA2 wireless network at home, i am running network-manager, i click on the wireless symbol and a list of wireless networks come up, then i select mine and type my WPA2 key.  When i reboot, it forgets all about it.  How do i get it to remember?

Thanks!
George

The keyring manager is what remembers WEP and WPA keys.  Keyring manager should have popped up when you first typed in your WPA2 key.

---

### Post by gnychis on 2007-06-14
hmmm... i'm not sure what this is

so I don't run the full desktop install with gnome and such... i run a barebones server install which I've built up to an FVWM desktop that runs nm-applet  ... maybe this is something additional i need to apt-get?

---

### Post by gnychis on 2007-06-14
so i'm gusesing its gnome-keyring and gnome-keyring-manager

networking seems extremely tied in to the desktop manager in ubuntu ... shouldn't networking be enabled at boot?

---

### Post by stchman on 2007-06-14
> **gnychis said:**
> so i'm gusesing its gnome-keyring and gnome-keyring-manager

networking seems extremely tied in to the desktop manager in ubuntu ... shouldn't networking be enabled at boot?

As far as I understand how network manager works it goes like this.

If there is a live connection on your wired ethernet than the connection is enabled.  Else it is disabled.  Same with wireless.

Are you using Edgy or Feisty?  Feisty has Network manager installed by default.

---

### Post by gnychis on 2007-06-14
I'm using feisty

when i boot up and sit at the login screen, which is not gdm... just basic terminal, network is not enabled

as soon as i start fvwm and nm-applet then its enabled

---

