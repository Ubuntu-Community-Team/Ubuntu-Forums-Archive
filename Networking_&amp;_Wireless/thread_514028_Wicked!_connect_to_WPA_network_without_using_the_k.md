---
title: "Wicked! connect to WPA network without using the keyring"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by janbockaert on 2007-07-31
Network manager is a great program, but it has one big problem, every time i connect to my homenetwork, i have to open my keyring before it can connect with the WPA-key.

I understand, that is a safe place to store the key, but it also means, there is no network at boot, and applets like the weather and the mail notification can not do what i wanted them to do. (i also do not want them to reload every second).

Today there was a post about [wickd]("http://wicd.sourceforge.net/") in [linux.com]("http://www.linux.com/feature/118224"), and the author was very happy with the program. 

So i decided to check it out.

Installing wicked means uninstalling networkmanager, so, if anything goes wrong with the installation, you can have a problem. (safe the nm-deb on your desktop if you want to be safe).

Nothing went wrong with my installation. After installing wickd, all you have to do is adding /opt/wicd/tray.py to your sessions, (and removing nm-applet), so wickd starts when ubuntu starts.

Wickd does not stores the key's in the keyringmanager, so when you boot the next time, you will already be connected to the internet.

I have to say, i actually do prefer the networkmanager pulldown list over the wickd-window (witch looks a bit like the windowsxp networksettings) for managing your networks, and in the wickd-window, you can not see witch network you are connected to. (but you can see that in the systemtray)

I'll update this post as soon as i run into trouble with wickd or if for one reason or another, i change back to networkmanager. If i don't update this post, and you are reading this in a distance future, you can assume, I am still a wicked network user:)

---

### Post by ugm6hr on 2007-07-31
Actually, Wicd does show you which access point you are connected to in the main window (as well as when moving mouse over the system tray icon).

Along the bottom of the window is your IP and connected SSID.

And you will not have any problems with it.  It is actually a lot more stable than Network Manager, especially with atheros and intel chipsets and WPA.  And it allows static IP.

---

### Post by janbockaert on 2007-07-31
indeed, it does, yet, it would be nice you could read connected next to the icon and name of the network. (i guess that is somthing for a next version?)

However, there seems to be a problem with hidden ESSID's. At start, it only finds some of the networks, and only after i add a hidden network (one of mine), it finds all the other networks in the range.

This is not a deal breaker for me, but i guess it could be annoying when you do not know the name of a hidden network that is blocking the other networks to be detected. Is there a place to send bugreports to?

(or maybe this is not a hidden Essid problem reloading the networks gives me everytime a different number of networks. )

---

### Post by ugm6hr on 2007-07-31
I think this is nothing to do with hidden SSID.  It is because the signal strength of your neighbours networks is variable, so they don't always appear.  Obviously, some people actually physically turn their networks off - which removes it from the list.  You will find the same "problem" from running *iwlist scan* from Terminal too.

If you want to communicate directly with developers - the wicd forum has adam and dano on it all the time:
[http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

Actually - I think dano is on these forums a lot too...

---

### Post by janbockaert on 2007-07-31
i'm not sure, i have 3 ssid's myself, of witch two are from the same router (fon). Every time i reload, (within minutes) the networks that appear in the list are different. Adding a hidden ssid to the list, does make wickd find a lot more networks (not only the hidden one).

iwlist scan only finds one network, and swscanner crashes after i start scanning :)

anyway, i only need one network to connect to, and there is no question wickd is better in connecting to it than networkmanager is. I'll checkout the forums, thanks.

---

### Post by imdano on 2007-07-31
> **ugm6hr said:**
> Actually - I think dano is on these forums a lot too...Hi.  Adam actually posts here a decent amount too, his username is compwiz18.

I think that problem you're finding scanning for networks is more of an iwlist scan issue.  I've noticed on my home network iwlist scan finds more networks around if I'm in monitor mode, so when I'm connected to my home network (and in managed mode), it finds less networks (or it least it seems like that's whats happening).  There's not much we can do about that kind of stuff.  When you give wicd a hidden network all that changes in the scanning process is it calls "iwconfig <wireless interface> essid <hidden network's essid> before calling iwlist scan.  So if you're finding a bunch more networks I'm pretty sure that's either a coincidence or a driver/iwlist problem.

---

