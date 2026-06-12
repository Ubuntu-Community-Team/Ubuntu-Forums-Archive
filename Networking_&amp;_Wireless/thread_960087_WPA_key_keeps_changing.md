---
title: "WPA key keeps changing?"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by fongandrew on 2008-10-27
Having a mixed success rate in connecting to my home 802.11g network. The default Ubuntu wireless manager sees the network and prompts me for my WPA key when I try to connect.

I enter the key, which looks something like 'abc00abc'. It fails and I get another request for my WPA key. When I check the "Show Password" box however, the key in the box looks like this:

c2870c1fd49a5d3b878ad7d9d29a8534dc9bd32626551ed6a8d647caead0b7e4

I keep entering in the same WPA key and getting back the same long string of alphanumerics. Any idea why that happens?

NB: After connecting with a wired connection first, the wireless starts working and continues so after disconnecting with the wired connection. Not sure what's going on. Thoughts?

---

### Post by fongandrew on 2008-10-27
Bump

---

### Post by hewhowatches on 2008-10-31
I also have a problem with the key asking me to re-enter it after starting up (this started happening after I upgraded to 8.10 yesterday). However, I believe I've solved the mystery as to why the key stored in the connection info looks different from the wireless key.

I did some searching and found this page that makes reference to wpa_passphrase:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

```
wpa_passphrase WORKGROUP gsc2F5XrpVswiW6XoooipALuh7dxmZnmeNN49rfob4eYvdYvQqbgvHRPNUppM3Z
```

Which will bring back:

```
network={
	ssid="WORKGROUP"
	#psk="gsc2F5XrpVswiW6XoooipALuh7dxmZnmeNN49rfob4eYvdYvQqbgvHRPNUppM3Z"
	psk=535ee2dce3a0a4293e937bfe6ff2e50b8b33805265f46143a7567fcfb2674f7c
}
```

Obviously this isn't my real network name and key (key was auto-generated from [https://www.grc.com/passwords.htm]("https://www.grc.com/passwords.htm")) so you'll need to add your own details here.

The generated code should match what is being stored.

Something worth mentioning too... once you've exited the terminal, you'll probably want to delete the command you entered from the .bash_history text file stored under /home/USERNAME and resave the text file. This will stop anyone from looking at the key you just typed in later.

If I work out why the prompt for the key keeps appearing I'll post the workaround here.

---

### Post by hewhowatches on 2008-11-04
Ok, only decent workaround I've found for now is to configure the settings manually which is surprisingly easy... but you lose the Network Manager applet doing it this way...

I simply followed the instructions on the page mentioned in my last post:
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

My /etc/network/interfaces file contained:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address <snip>
netmask <snip>
gateway <snip>
```


To which I added:

```
auto ath0
iface ath0 inet dhcp
wpa-ssid <snip>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <snip>
```

...and rebooted. You'd need to read the tutorial yourself and configure the interfaces file to suit your network, but it's certainly improved matters for me. I could barely connect at all tonight, so I've really been forced to do it this way. Here's hoping that a new version of Network Manager is released in the meantime.

This meant I logged into the system and had my network connection, but no Network Manager icon in the top right. Trying to start this from a terminal gives:

```
nm-applet

** (nm-applet:7277): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7277): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

Sigh. See the bug for it here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466")

---

### Post by jimv on 2008-11-04
The NM for NetworkManager should be NightMare.  Try using WICD instead for managing your connections.  I almost guarantee that you will like it more.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by hewhowatches on 2008-11-04
I've just tried wicd and I have to say you're right. Good program, plenty of options, etc. However in my very limited test I couldn't get it to connect to the wired AND wireless networks at the same time, which is unfortunately something I need to do... Connecting one disconnected the other, so I'll stick with the manually configured interfaces file for now - thanks for the reply though! :)

---

### Post by Sephen on 2008-11-10
I'm having the same problem on a machine I upgraded from Hardy, and its driving me insane. Its an Intel Centrino-based laptop from about 3 years ago with very commonplace hardware, namely an Intel 2915ABG wifi chipset. It worked absolutely flawlessly in Hardy, but its terrible in Intrepid. Any time I do a large file transfer over the wireless link, it drops out and Intrepid pops up the WPA authentication dialog. It doesn't matter how many times I enter the correct key, it won't work unless I reboot the machine and let it connect automatically after I log in. Then a few hundred megabytes later it will drop again. Restarting X is not enough. This sucks.

Also, I can leave this machine sitting in the corner on bit torrent 24/7 and it won't drop - it only seems to do this when I copy stuff to local machines on my LAN. Wireless signal strength is also much poorer than it was under hardy.

---

### Post by SparkyStormanvil on 2008-11-10
> **jimv said:**
> The NM for NetworkManager should be NightMare.  Try using WICD instead for managing your connections.  I almost guarantee that you will like it more.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

I started using WICD, but it does not like hidden SSIDs. I couldn't get it to connect to my network unless I broadcast the SSID. It saw that a hidden network was there, but I could not easily find the place to put in the SSID, and it would not connect, even with the WPA password information keyed in.

---

### Post by Sephen on 2008-12-16
*bump* anyone? :/

---

### Post by Favux on 2008-12-22
Hi folks,

You might want to check out:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

