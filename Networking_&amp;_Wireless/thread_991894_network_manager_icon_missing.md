---
title: "network manager icon missing"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by ejohn on 2008-11-24
i recently updated ubuntu intrepid beta release to 8.10 main. After the updating got over my menu icons were missing and so was the networkmanager applet icon. Restart fixed the menu problem but i am still missing the Network Manager. I rely heavily on that for wireless connections. Please can somebody tell me what to do or is there any command line alternative to invoke that NM? i tried reinstalling NM too.

thanks 
John

---

### Post by caleb12 on 2008-11-24
nm-applet 

is the command line, type that into a terminal... nm-applet also relies on the Network Manager service to be started:

sudo /etc/init.d/NetworkManager restart

Run the above command first, then type nm-applet - see where that gets you...

---

### Post by ejohn on 2008-11-24
** (nm-applet:10164): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10164): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

this is the result that i get. i am assuming an instance of nm-applet is working just that its not showing up in the top taskbar. 

btw i tried killing that process and restart nm-applet which just showed a no connections warning in the terminal but nothing in the taskbar.

thnx for the prompt reply
john

---

### Post by caleb12 on 2008-11-24
Try killing everything NM related... I usually do:

ps aux |grep nm

which will show something like this: 

root      **5303 ** 0.0  0.1   6848  3016 ?        S    07:24   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
users    **5735**  0.0  0.4  45612 11008 ?        S    07:24   0:00 nm-applet --sm-disable

You should kill nm-applet first, if it is running... then the one above. The first number in the line after the user name is the PID, so use a command like: 

sudo kill **5303** 
sudo kill **5735**

Then start over with the: 

sudo /etc/init.d/NetworkManager start

then nm-applet. 

You could also try opening Synaptic, do a complete removal of NM and then reinstall.. I know they just did a recent release of NM 0.7 - so perhaps something was funky in the upgrade... Personally I user the direct repos instead of the Ubuntu ones, I guess it's personal choice but everything has always worked fine for me... Here's the repos:

deb [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) intrepid main
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

---

### Post by ejohn on 2008-11-24
i had tried everything that u mentioned in the last post. It still does no show up.

---

### Post by caleb12 on 2008-11-24
So, next let's try... 

cat /etc/network/interfaces 

If you have any static entries, then this is what NM is failing over... Try commenting out everything except for these lines:

# The loopback network interface
auto lo
iface lo inet loopback

Then do the same as in the last post, although add a full network restart as well:

sudo /etc/init.d/networking restart

---

### Post by ramblin' wreck on 2008-11-24
I recently had a similar problem (last night). Network manager icon was missing in the sys tray. So, I did the common windows solution (dumb), reinstall through synaptic.

Still not in sys tray. So I read through interfaces manual (man 5 interfaces). commented out my wlan instructions (I needed ethernet, not wireless) and used the ifdown/up instructions. I guess you would need to adjust your wlan or comment out other instructions to test first, like the prev poster wrote down.

I still did not have a tray icon BUT ethernet was running. Then I realized that network manager was slightly different than 8.04, so all I did was right click on the panel to add network-manager to the panel, then moved it to the sys tray. Works fine on reboot.

Hope this helps.

---

### Post by caleb12 on 2008-11-24
Apparently, it's a bug and been notated... only effects existing users of NM, who have upgraded... lol...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466)

The listed fix is to comment out all entries in the interfaces file, hopefully NM will build in support for pre-configured devices eventually. Right now it's more of a replacement to other networking options...

---

### Post by ejohn on 2008-11-25
there are no static entries only one for loopback. 

tried restarting again. still nothing.
tried right clicking on the panel and trying to add icons but network manager is missing. 

<Caleb12> thanks for the bug link..

---

### Post by ejohn on 2008-11-25
creating a new user seems to solve the problems. its pretty lame but seems to be the only way out till the bug is fixed. 

how do i import all the settings(except the broken ones of course!) and files to new user?

---

### Post by NIT006.5 on 2008-11-25
Ok this may seem like a silly suggestion, but have you checked that Network Manager is enabled in Preferences > Sessions? When it runs from there it will add itself to the system tray.

---

### Post by caleb12 on 2008-11-25
That is really odd... a new user solves the issue. The only config files that NM puts into your profile is part of .gconf for the wireless passcode and connection information. And if I recall correctly that changed in 0.7... I think there was an issue with storing passcode information in user profiles. I just went through my home directory and couldn't find anything NM related. 

At any rate, it sounds like this may be completely unrelated to NM afterall. You can always go through your home directory and pull config files, a couple at a time until the problem re-introduces itself. Tedious... I know, but at least you'd know where the problem is.

There may be some documentation on launchpad (from the bug link) that relates to where NM stores settings and thing... and if all else fails, there's always the mailing list. Questions get answered really quickly there...

---

