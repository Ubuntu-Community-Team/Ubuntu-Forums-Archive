---
title: "WPA and keyring manager"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by stchman on 2007-03-29
Hello all, well I succeeded in getting my built in Atheros wireless card up and running.  I followed the procedure listed below to get WEP and WPA working:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

I logged back in and was able to left mouse clickon the network manager.  **My network did not appear as I don't broadcast my SSID (is this a problem?).  I also use MAC filtering as well.**  No problem I figure I will just type it in and away I will go.

There are some that say that WPA does not like to play well with WPA and hidden SSIDs.  Is this true?  Moving right along.

I first went to my router (Linksys WRT54G) and enabled WPA Personal.  I want to use WPA as everything I have been read and told is that is is stronger than WEP.  I put in my passphrase and saved the settings.  I then went back to my laptop and left clicked on the network manager, typed in the SSID, selected the WPA Personal, and entered in the passphrase.  After that was all done Keyring manager popped up a window asking me to create a password to store the passphrase for the WPA settings for my wireless connection.  OK.  After that a few moments later I get the circling round logo in the network manager and then the I am greeted with a message that I am connected to my router.  YAY

After, that I reboot and when I get back into the desktop I am not able to connect back into my router.  I have to go connect to the wireless network again.  I assume that the network manager will access what is in the keyring manager to connect to the encrypted wireless network.

I went into the keyring manager and said Always Allow for the network manager, so does anyone here have an idea what is going on?

Thanks

---

