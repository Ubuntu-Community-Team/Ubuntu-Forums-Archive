---
title: "Installing ACX100 Driver DWL-G520+"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Ian505 on 2008-03-05
Please note that I have already looked in the forums but cant seem to find anything posted after Sept. 2005 that had an answer to it- so I am reposting as this seems to be a relatively common problem.

I have a DWL-G520+ PCI wireless card with the ACX100 chipset. I have downloaded the tarball from the ACX100 driver project website ([http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)-Official Wiki Howto (complicated...)[http://acx100.sourceforge.net/wiki/ACX]("http://acx100.sourceforge.net/wiki/ACX")) but the instructions are too complicated for me and they aren't specific to any Linux distro- just distros in general.

For example, the README file in the tarball said to go to a folder like /usr/lib/hotplug/firmware "in your kernal folder" and copy drivers in there... but I can't find that in Ubunutu.

Could somebody please help me? 

Thanks,
Ian

PS- If the download on the ACX100 website is too slow for your liking, I would be happy to host the file for you on my US server- though I will take it off after the problem is resolved.

EDIT- I posted here ([http://ubuntuforums.org/showthread.php?t=641707&page=3](http://ubuntuforums.org/showthread.php?t=641707&page=3)) earlier and there was a reply... but they said that they were a noob to linux so I don't know if I want to trust their advice and blindly copy and paste.

---

### Post by NullHead on 2008-03-11
His commands seem to do nothing that would be destructive. I would follow 'em.

---

### Post by Ian505 on 2008-03-14
Thanks, but I would like it if someone could make it so I didn't have to type that in at every boot. Remember, I am still a noob.

-Ian

---

### Post by NullHead on 2008-03-14
You need what made into what? The guide made into a script? Please be more informative.

---

### Post by potrick on 2008-03-25
Reading through your request earlier brought me to a workable solution, so I thought I'd share. 

So first I followed our good friend's instructions as given, first disabling Network Manager:

```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
```

And then we disable the service from starting at startup, running as root:

```

sudo bash
echo "exit" > /etc/dbus-1/event.d/25NetworkManager
echo "exit" > /etc/dbus-1/event.d/25NetworkManagerDispatcher
```

Close this terminal window and open a new one so we're not running as root anymore. (note: if someone thinks it's not safe or necessary to run as root here let me know and I'll update. I'm just following the suggestions I found elsewhere)

And then we have the series of commands our friend ran every time at startup. I altered them to work well as a script:

```
#!/bin/sh

ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid "network name in brackets"
iwconfig wlan0 key HEXCODEHERE
iwconfig wlan0 mode Managed
dhclient wlan0
```

As before you'll have to configure this to fit your network, with the network name in the brackets and the Hexcode where it says HEXCODEHERE. If you want you can save this script where you want, set the permissions to allow it to execute and run it with sudo whenever you want to connect to your network. 

Or, if you only use wireless in one location, you may simply want this script to open when your computer boots. No problem. Open a text editor to write a new script in your /etc/init.d folder (note, if you don't use gnome replace "gedit" with your preferred text editor.)

```
sudo gedit /etc/init.d/startwireless

```


Copy and past the script above in the text editor that opens and save. Then make the script executable:

```
sudo chmod +x /etc/init.d/ startwireless defaults
```

And then run this command to ad it to startup:

```
sudo update-rc.d startwireless defaults
```

This worked for me. Let me know if it works for you.

---

### Post by jimelb on 2008-04-11
Thank you
it help me..good work!!

---

