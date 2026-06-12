---
title: "Idiot bluetooth questions."
date: 2009-05-26
forum: New to Ubuntu
---

### Post by longfeltwant on 2009-05-26
I've been all over the internet looking for instructions on setting up my bluetooth GPS device with Ubuntu. I apologise for the following stupid questions:

80% of the instructions I find tell me to go find and edit /etc/bluetooth/hcid.conf. I do not have this file. Is that a file that Ubuntu had in the past, which is now replaced by something new?

100% of the instructions I find tell me to edit some kind of configuration file. Is it really necessary to do that, just to connect a bluetooth device? Shouldn't the Bluetooth Prefs setup wizard do that for me?

In Bluetooth Prefs there is a little (i) icon. I would normally expect to click that icon and get more information about the thing selected, but in BTPrefs instead it toggles an identical icon alongside the selected item, with no more apparent action. What does the (i) icon do? Why doesn't it show info, which is the universal meaning of the (i) icon?

Specifically I am trying to get a GlobalSat G-SAT BT-359 working on Koala. I can open Bluetooth Prefs and set up the device no problem. Then it shows up in my list. The next thing I'm trying to do is to run gpsd, which requires me to tell it which device to use. On my Mac I do gpsd -p /dev/cu.DEVICENAME, but I can't find any similar names in /dev/ in Ubuntu. That problem led me to the instructions telling me to edit hcid.conf.

All this is step zero in the list of many steps which I hope will take me to successful use of GpsDrive or obdgpslogger. It keeps getting harder and harder to get either of those things to run. Maybe I should state my general purpose, which is to get this darn GPS unit to give location data to my netbook so I can record my path on a road trip this summer.

---

### Post by longfeltwant on 2009-05-26
I answered one question. The deceiving (i) icon means "trust", apparently, and there was a bug filed on it.

[https://bugs.launchpad.net/bluez-gnome/+bug/331224](https://bugs.launchpad.net/bluez-gnome/+bug/331224)

---

### Post by Didius Falco on 2009-05-26
I can't offer any help on setting up the GPS, but I would offer this one piece of advice:

Do not count on Karmic for something like this. It's in Alpha right now and it may break at any time - I'd actually expect it to break a few times. Even when it goes to Beta, it may well hit problems before it gets stabilized and goes to RC.  

Install a stable version to use for your summer trip. If you have room, you can dual boot Jaunty and Karmic, using Jaunty for your GPS data. You can keep on tinkering with the Karmic install to try and get it working as well, but I'd hate to see you lose all your trip data to a Karmic meltdown.

Regards,

Didius

---

### Post by longfeltwant on 2009-05-27
That's good advice, Falco, I'll drop back to 9.04.

In the meantime, I found some good directions for setting up bluetooth GPS devices elsewhere on this website ([http://ubuntuforums.org/archive/index.php/t-200142.html]("http://ubuntuforums.org/archive/index.php/t-200142.html")). With those directions, I did get my computer to connect to my GPS, but I still had to manually edit /etc/bluetooth/rfcomm.conf and I had to manually run rfcomm connect devicename, and I guess I think those steps ought to be handled by one of the other pieces of software I am trying to use. And I'm sure they are, and I'm just Doing It Wrong.

---

### Post by longfeltwant on 2009-05-29
I have found pretty good instructions online for setting up bluetooth GPS devices.

This is the Bluetooth page for the GPSd software. It tells you to define the bluetooth descriptor in /etc/bluetooth/rfcomm.conf, then bind the service to that device, then start gpsd.

[http://gpsd.berlios.de/bt.html]("http://gpsd.berlios.de/bt.html")

So now I know how to set up bluetooth GPS devices on Linux, and I have to say I'm surprised it isn't easier. There is that Bluetooth Preferences pane, but I'm not sure what it's even there for. You go in and set up a bluetooth device, but in the end, what happened? You still have to go edit /etc/bluetooth/rfcomm.conf, still have to bind it to rfcomm, still have to spawn gpsd. I think the Prefs pane should create the device descriptor, and start rfcomm for it. Then maybe gpsd should be smart enough to recognise the new device, or maybe there would be a trigger to roll gpsd. The Bluetooth Prefs pane is a red herring.

---

### Post by t0p on 2009-05-29
> **longfeltwant said:**
> I think the Prefs pane should create the device descriptor, and start rfcomm for it. Then maybe gpsd should be smart enough to recognise the new device, or maybe there would be a trigger to roll gpsd. The Bluetooth Prefs pane is a red herring.

You've found an itch.  Scratch it!

---

