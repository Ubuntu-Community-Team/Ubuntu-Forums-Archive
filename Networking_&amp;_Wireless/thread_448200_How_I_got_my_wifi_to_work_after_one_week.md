---
title: "How I got my wifi to work after one week"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by robucf on 2007-05-18
After 1 week of absolute frustration I finally got my wifi to work consistently, and even at boot-up.  All I can say is WOW stuff should not be this hard.

I'll give you the jist of it and if you need details let me know.

I used wicd, I uninstalled knetwork and gnome network manager as they would not work with a hidden ssid for whatever reason and not connect at boot.

WIcd is here [http://wicd.sourceforge.net/pages/about.php](http://wicd.sourceforge.net/pages/about.php) (there's a deb package, just double click to install once downloaded)

At first I could not get wicd to work either, I was like great another dead end.  So I started messing with the templates in /opt/wicd/encryption/templates/  I changed the wpa one to look like this:

name = WPA 1/2
author = Adam Blackburn
version = 1
require key *Key
-----
network={
       ssid="yourssid"
       scan_ssid=1
       proto=RSN
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk=yourkey
}

This, I think, will force these values if in the GUI you choose WPA 1/2.  

Background:
I saw every time I clicked connect a new file would get created in /opt/wicd/encryption/configurations and it followed the same pattern as the one in the template folder.  Please excuse me if at this point you are like duh, I had to figure all this stuff out on my own.

After I hardcoded my values in the template file, the newly created config file matched it.  From the gui I guess it associated the ssid I entered with the correct template (WPA), then config file.  In any case, to much suprise, when I clicked connect it joined!!!  Now I had gotten this far with the knetworkmanager and gnome but only when I broadcasted my ssid or restarting the the network many times I would get a connection finally.  Even with that it would never connect at boot.  In wicd gui, it has a checkbox to auto connect to a given network at startup.  I was skeptical, but I rebooted 3x and everytime it connected at startup!!

YMMV, my wifi setup is hidden ssid, wpa2, tkip, dhcp.

wicd has some easy quirks to deal with, for one it does not auto start, so you need to add it to the startup menu if you will.  In KDE, .kde/Autostart, Gnome->sessions menu.  I got it  to work in both.  I use /opt/wicd/tray-edgy.py  

All of the above work is just a patchwork from reading what seems like a hundred posts and a lot of trial and error.  I am just happy I got it to work finally.  It would have been nice if wicd worked out of the box, but I do not know why I had to manually edit the wpa file, all I know is that it worked.  Prior to editing the file, I could not connect.

I know I am all over the place here with this post, just wanted to give a braindump of what I did to get my wifi to work correctly.  If you have been messing with it like I have for over a week, I am sure you can make some sense of my post :)

/goodnight

---

### Post by teachop on 2007-05-23
Just wanted to say good job.  That helped me out.  I had WEP working, but this is a much more functional setup for me (Acer Aspire 3100 w. Atheros, hidden SSID and WPA).  By the way, it is easy to edit the .py file to "calibrate" the wireless level meter in the tray.  For some reason that was wacky for my Atheros, so I rescaled it to match reality of the signal.

Thank you!

---

### Post by BroadArrow on 2007-05-23
Thanks for posting this!

Like you I tried pretty much every wireless networking "solution" in the Ubuntu repository without success. 

I hope this gets added to the distribution -- it works a charm!

---

