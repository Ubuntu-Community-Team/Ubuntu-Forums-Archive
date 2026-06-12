---
title: "[HOWTO] Generate a WPA2 (HEX) passphrase from a wired, Windows connection?"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by TBerk on 2008-11-14
I am setting up a wireless connection on a newly installed system running 8.10. 
It has not had any updates as of yet, hasn't been on any network yet either.

I have been following (successfully so far...) this thread:

Walkthrough - Installing Ralink 2860 Based Wireless Adapters
[http://ubuntuforums.org/showthread.php?t=966185](http://ubuntuforums.org/showthread.php?t=966185)

And I get to the point where I am to edit the RT2860STA.dat file to specify my Router's SSID, encryption type, and passphrase.

There are instructions to get the hex version of the passphrase by running a Linux based command but the horse is before the cart on that one; in my case I can't yet log onto the network w/ the system in question, so running a command against the router from there is moot.

What I CAN do is run a command from the Windows based system I am posting from, (but it is wired, not wireless).

My question then becomes; How do I generate the version of my known passphrase that the settings in Ubuntu can understand, from a Windows based PC?


Thx,
TBerk

---

### Post by flyguy97 on 2008-11-14
There should be no need to log into the network to run the wpa_passphrase command. When I went through the process of setting up my wireless connection the network was completely down. I guess I am not sure what you want to do here. Can you explain what happends when you issue the wpa_passphrase command?

---

