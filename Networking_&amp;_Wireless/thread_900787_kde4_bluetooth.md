---
title: "kde4 bluetooth"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by wpiter on 2008-08-25
I have hardy with kde4. kdebluetooth is installed however a tray icon does not seem to appear. Any help is appreciated...

---

### Post by Crafty Kisses on 2008-08-26
> **wpiter said:**
> I have hardy with kde4. kdebluetooth is installed however a tray icon does not seem to appear. Any help is appreciated...

Have you tried running kdebluetooth in Terminal?

---

### Post by wpiter on 2008-08-26
I am able to connect my bluetooth mouse using sudo hidd --search (after previously allowing the connection)

are hidd and hcitool part of kdebluetooth?

---

### Post by lodp on 2008-10-13
i have the same problem -- no tray icon for bluetooth, even though my bluetooth adapter and mouse worked out-of-the box after installing kde4 in addition to my previous 3.5 installation.

i fixed it by starting kbluetooth from the terminal, and had it auto-started in the system settings. can't file-browse devices tho.

---

### Post by nrwilk on 2008-11-06
I'm having this same problem as well.

Using KDE 4 on 8.10.

Anyone else have any ideas?

---

### Post by jmeyerdo on 2008-11-15
Hi!

Same for me: I can get information from Handy without problems ("hcitool scan").

So I would suggest the bluetooth-USB-adaptor is working fine. But there is no icon in taskbar when starting kdebluetooth4 manually:
```

kbluetooth4(6255) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "BlueZ"                                                                     
kbluetooth4(6255) KBlueTray::offlineMode: offline Mode   

```
How can I move to online-mode - and get the application visible/loaded?

Best regards, Jens

---

### Post by arizonagroovejet on 2008-11-25
I just tried to transfer some pictures of my phone via bluetooth for the first time since updating to 8.10 and found bluetooth doesn't work. Turns out it's a known problem.

> Bluetooth is not supported in Kubuntu 8.10 because KDE does not yet support the bluez 4.x stack required for compatibility with the kernel used in 8.10. A fix for this is being evaluated as a post-release update. (Bug 280997)


[https://wiki.ubuntu.com/IntrepidReleaseNotes#Kubuntu Bluetooth support](https://wiki.ubuntu.com/IntrepidReleaseNotes#Kubuntu Bluetooth support)

---

### Post by jbernardo on 2008-11-25
The workaround (extremely limited) is to use gnome's bluetooth applet. At least allows pairing, but other than that, you have to script around the limitations.

---

### Post by theZoid on 2008-12-08
> **jbernardo said:**
> The workaround (extremely limited) is to use gnome's bluetooth applet. At least allows pairing, but other than that, you have to script around the limitations.

How can we autostart, exactly, bluetooth in KDE4 Kubuntu 8.10...now I'm doing it manually everytime after I installed HIDD...thanks

---

### Post by jbernardo on 2008-12-09
I am also starting the bluetooth applet manually every time I want to use bluetooth. I assume it won't autostart as it is a gnome applet.

---

### Post by JunCTionS on 2008-12-13
thanks for pushing me to this option :P
I was reluctant to do this... but I guess it seems the only reasonable option now (and I'm tired of debugging this laptop for now).
As for running the app at startup, go to System Settings>Advanced>Autostart>Add Program and just type "bluetooth-applet" and press Ok (and I think ok again).

---

### Post by theZoid on 2008-12-13
> **JunCTionS said:**
> thanks for pushing me to this option :P
I was reluctant to do this... but I guess it seems the only reasonable option now (and I'm tired of debugging this laptop for now).
As for running the app at startup, go to System Settings>Advanced>Autostart>Add Program and just type "bluetooth-applet" and press Ok (and I think ok again).

That's after installing the gnome bluetooth applet, right?  thanks

---

### Post by JunCTionS on 2009-02-01
yeah... that's after installing the bluez-gnome package.

(I just realized noone here has said that the terminal command is: 'sudo apt-get install bluez-gnome' )

I subscribed to a bug report on this and it has recently been marked as solved as it appears to be fixed for the next kubuntu version (Jaunty Jackalope, 9.04)

I imagine an update for the older versions might come out someday soon.

---

### Post by theZoid on 2009-03-28
I'm still having BT problems in 9.04 Kubuntu...anyone have success?  I can connect manually, but can't keep it connected for some reason.

---

### Post by lebrun on 2009-04-25
I have a similar problem. kbluetooth4 will show devices to connect, but sending files with it doesn't work. No errors, nothing. The window closes, but no transfer is made. I tested this with the livecd, to check before upgrading. Now it seems I won't upgrade at all, at least not to another kubuntu release.

---

### Post by SteveMcQwark on 2009-04-25
Yeah, for some reason kdebluetooth sets the mouse to "not trusted". Using bluetooth-applet sets it to "always trust" which is what seems to let it work. 

Anyone know why:
1) kdebluetooth sets it to "not trusted"?
2) there is no way to change the trust setting?

---

