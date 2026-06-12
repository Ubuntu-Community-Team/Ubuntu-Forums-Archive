---
title: "Bluetooth service enabled but not functioning properly."
date: 2021-09-22
forum: Networking &amp; Wireless
---

### Post by flapanther33781 on 2021-09-22
Hi there.  Decided to give linux a try, installed 20.04.3 on an older HP laptop I had laying around.  Not dual booting.  Had many issues getting it to work with a number of different things I wanted to do with it so I set it aside.  Revisiting this now to see if I can use it as a sort of MP3 jukebox.  I bought a bluetooth speaker, confirmed it works with a Windows 10 PC I have that has Bluetooth on its motherboard.  Bought a Bluetooth USB dongle for the laptop.  Ubuntu seems to see the dongle, as in the GUI when I go to Bluetooth settings the on/off switch grays out if the dongle is not inserted.

Turning on the toggle in the settings window does nothing.  The screen still says Bluetooth is turned off.  I found this thread: [https://askubuntu.com/questions/1231074/ubuntu-20-04-bluetooth-not-working](https://askubuntu.com/questions/1231074/ubuntu-20-04-bluetooth-not-working)

Walking through that thread:

The "rmmod btusb" command is not available on my laptop.
The command "service bluetooth status" shows the service is running.  I have updated all packages on this laptop.  

I did not install blueman.
I  do have Python installed on this laptop but have not messed with it as  suggested in that thread.
I was putting the laptop in hibernate, so I rebooted, that didn't help.
I tried disconnecting/reconnecting the power cable, didn't help.
I shut down the PC, removed both the power cable and the battery for 10 minutes, didn't help.

I tried using the dongle in a Windows 7 laptop that doesn't have Bluetooth onboard to see if it would work there.  Windows did recognize the dongle but I couldn't pair the speaker with it.  Can't remember why not, but I already know the speaker is good so I didn't worry about that.

What else can I try?

---

