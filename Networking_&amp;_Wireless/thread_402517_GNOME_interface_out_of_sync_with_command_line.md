---
title: "GNOME interface out of sync with command line?"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by GregNick on 2007-04-05
Hi there.  First of all the disclaimer: I'm another Windows user trying to switch to Ubuntu (Edgy).  While I've got plenty of experience with command line Unix in an academic setting, I have none with a home OS (or any sys admin experience for that matter).

The install went flawlessly except for getting my Linksys WUSB54G to work.  The driver installation actually went fine, I just had trouble connecting when my router had WEP turned on.  I eventually figured out that I had to specify an "open" key on the command line using iwconfig.  Before that I had been relying on the System->Administration->Networking applet.

Now that I've got it up and running, I've got two questions:

1.  Why doesn't the Networking applet seem to be synced up with the settings I specify on the command line?  First of all, typing the WEP key in at the command line won't change anything in the applet.  Also, if I go into the applet to fiddle with the settings, the connection will be gone again (I imagine because it removed the "open" status from the key).  I would think that the applet would just be a graphical interface to ifconfig, but apparently I'm wrong about that.

2.  I have to manually specify the essid and the key at the command line every time I reboot - how do I make these settings permanent?  All the tutorials I've seen set it up in the applet, which I guess isn't going to work with me.

3.  Is there any nice GUI package similar to the Windows Wifi connection applet?  While "iwlist scan" works fine to get a list of access points, a graphical one would be nice.  Furthermore, connecting to the router with iwconfig gives no feedback as to how successful the connection is.  In Windows there's a dialog box that will show the status as it goes from connecting to getting an IP address and so forth... anything similar for Ubuntu?

Thanks so much for any input.

---

### Post by Floppyjoe on 2007-04-05
> 1. Why doesn't the Networking applet seem to be synced up with the settings I specify on the command line? First of all, typing the WEP key in at the command line won't change anything in the applet. Also, if I go into the applet to fiddle with the settings, the connection will be gone again (I imagine because it removed the "open" status from the key). I would think that the applet would just be a graphical interface to ifconfig, but apparently I'm wrong about that.

2. I have to manually specify the essid and the key at the command line every time I reboot - how do I make these settings permanent? All the tutorials I've seen set it up in the applet, which I guess isn't going to work with me.

3. Is there any nice GUI package similar to the Windows Wifi connection applet? While "iwlist scan" works fine to get a list of access points, a graphical one would be nice. Furthermore, connecting to the router with iwconfig gives no feedback as to how successful the connection is. In Windows there's a dialog box that will show the status as it goes from connecting to getting an IP address and so forth... anything similar for Ubuntu?

I'm not sure why the System/Administration/Networking does not sync with command line or config file text. I set up my /etc/network/interfaces file with the neccessary info to make it boot properly every time. IF you are using ndiswrapper to make your wireless card work you need to add the word ndiswrapper to the file /etc/modules to get it to load at boot time. I have these attributes in my /etc/network/interfaces file to be able to connect using WPA encryption.
```
auto rausb0
iface rausb0 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
```
Hopefully some of this info will help you.

---

### Post by dbott67 on 2007-04-05
You can install NetworkManager, which is quite nice.
[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]
More info here:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

To install:

```
sudo apt-get install network-manager-gnome
```

-Dave

---

### Post by GregNick on 2007-04-05
> **Floppyjoe said:**
> I set up my /etc/network/interfaces file with the neccessary info to make it boot properly every time.

Any idea about how to specify an **open **WEP key in the interfaces file?  I can't see to find anything on the web that spells out all of the various options you can set in this file.

... I really should use WPA, but I've got a few devices that only support WEP.

---

### Post by Floppyjoe on 2007-04-05
If you go to System/Administration/Networking and enter a Essid and Password it will be written to the /etc/network/interfaces file. If you do this though it will erase any other information you may have entered before in that file like wireless-essid and wireless-mode , etc for that interface. So only enter information after you have done that. Or you can just add wireless-key followed by the key to the file but I'm not positive about the syntax. 
sometimes it can be "wireless-key s:secretpassword" and sometimes its just "wireless-key sdfsfsfsf"

---

### Post by GregNick on 2007-04-05
EDIT: Deleted this post - I figured out how to specify an **open** key in my interface file making this post obsolete.

Any input on my following post though?

---

### Post by GregNick on 2007-04-05
> **dbott67 said:**
> You can install NetworkManager, which is quite nice.

I installed NetworkManager, but it doesn't seem to notice my wireless setup.  The icon has a little orange warning sign and clicking on it just brings up a dimmed "Wired Network" button (my ethernet isn't connected).  

Sorry I couldn't provide a screen shot, I wasn't sure how to do that without clicking the application menu and thereby closing the little popup from NetworkManager.

... I'll learn the UI basics once I can actually look them up.  Unfortunately I need a reliable web connection for that :) 

Thanks so much again for all the help everyone.

---

### Post by Floppyjoe on 2007-04-05
> **GregNick said:**
> I installed NetworkManager, but it doesn't seem to notice my wireless setup.  The icon has a little orange warning sign and clicking on it just brings up a dimmed "Wired Network" button (my ethernet isn't connected).  

Sorry I couldn't provide a screen shot, I wasn't sure how to do that without clicking the application menu and thereby closing the little popup from NetworkManager.

... I'll learn the UI basics once I can actually look them up.  Unfortunately I need a reliable web connection for that :) 

Thanks so much again for all the help everyone.

I'm curious how you got the open setting in there.

When using network-manager in 6.10 or lower you need to disable all the network interfaces in System/Administration/Networking.

---

### Post by GregNick on 2007-04-06
I got the open specifier into /etc/network/interfaces by just using this syntax:

```
wireless-key open XXXXXXXXXX
```

Pretty straightforward, eh?

I disabled all my devices in the networking applet, this got NetworkManager to talk to my adapter and let in scan for SSIDs, but I couldn't connect to my router.  I tried it with the WEP key (NM lets you specify "open"), and I also tried unsecuring the router - no luck either time.

Here's an excerpt from the syslog (I chopped out the redundant "computer-name NetwrokManager" prefix for most of the lines):

_**[ATTACH]29126[/ATTACH]**_

FYI: In the "..." there was a bunch of "Iwpa_supplicant" activity despite the fact that there's no WPA on my router.

I admit I haven't searched the forums too much about this problem... I can connect by editing the /etc/network/interfaces now, so I'm not in a hurry to figure this one out.  I'm just asking in case there's a common solution to this problem that someone could share real quick.  Again, thanks so much.

---

