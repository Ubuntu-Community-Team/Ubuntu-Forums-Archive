---
title: "Ubuntu 14.04 Audio sink problem to Logitech Wireless Adapter"
date: 2014-10-02
forum: Networking &amp; Wireless
---

### Post by jcmoriaud on 2014-10-02
Hello,

Deseperately searching on blogs or forums how to make the Bluetooth of my old but healthy Lenovo T400 work with my Logitech Wireless Adapter which is pluged in my Amp.

Everything is working fine from any other device (iPhone, MacBook, Android, Windows...) but I can't make music sink from my Ubuntu 14.4.

I have tried with Blueman. the Logitech is detected, but I still can't audio sink, with the following error message :  "Connection failed, Stream setup failed" et quand je fais un "connect",  j'ai le message "Device added successfully, but failed to connect".

I am using a Logitech Bluetooth dongle that is also used by my keyboard and mouse.

I have tried this (in french sorry) [http://forum.ubuntu-fr.org/viewtopic.php?id=1323461&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=1323461&p=1) without success.

Thanks for your help in advance. 

Cheers from France !

---

### Post by jcmoriaud on 2014-10-07
Hum, looks like either I am the only one getting this problem... Should I wait for 14.10 ?

---

### Post by Mason_Burton on 2014-12-11
Hello, jcmoriaud.

I had this problem recently as I bought a bluetooth speaker and attempted to connect to it with my laptop. It kept giving me "Connection Failed: Stream setup failed". I eventually figured out how to make it work like this.

You need to have pulseaudio installed, which you can check for in Synaptic Package Manager by typing pulseaudio into the search bar. You can install it from there if it isn't already installed.

Next, you need to install pavucontrol, either in Synaptic Package Manager, or by running this in the terminal.
```
sudo apt-get install pavucontrol
```

This is the unfortunate part. Every time you boot, you need to run this command in the terminal before any bluetooth devices attempt to connect.
```
pactl load-module module-bluetooth-discover
```

You can now go into the bluetooth manager and tell it to connect to the device as an A2DP audio sink.

Now, finally, if you go into the PulseAudio Volume Control, on the Playback tab, you can choose the option to send audio through the bluetooth device.

Good luck with this.

---

