---
title: "Requires installation of untrusted packages"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by corncob on 2011-05-03
When I run update manager on my 32 bit eeebox running Natty beta2 it says I have 249 updates (I haven't used it for a couple weeks).  When I go to install them I get the above message.  It gives me no way to bypass it.  I can close the window and try again but it just goes round and round.  When I click on 'Details' I get this:
```
apt apt-transport-https apt-utils bamfdaemon evince evince-common file-roller gir1.2-panelapplet-3.0 gnome-panel gnome-panel-bonobo gnome-panel-data gnome-session gnome-session-bin gnome-session-common gnome-user-guide gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter libbamf0 libevdocument3 libevview3 liblircclient0 libnux-0.9-0 libnux-0.9-common liboverlay-scrollbar-0.1-0 libpanel-applet-3-0 libpanel-applet2-0 libpoppler-glib6 libpoppler13 libsmbclient libsyncdaemon-1.0-1 libwbclient0 nux-tools overlay-scrollbar poppler-utils python-ubuntuone-client python-ubuntuone-storageprotocol samba-common samba-common-bin smbclient tzdata tzdata-java ubuntuone-client ubuntuone-client-gnome unity unity-common xserver-xorg-video-intel
```
Any ideas?  There doesn't appear to be anything unusual in my software sources.

---

### Post by Gone fishing on 2011-05-03
I guess that for one of the repositories you haven't got the authorization key. If you remove that repository or add the missing key all will be fine.

Have you got any non standard repository?

---

### Post by josephmills on 2011-05-03
> **corncob said:**
> When I run update manager on my 32 bit eeebox running Natty beta2 it says I have 249 updates (I haven't used it for a couple weeks).  When I go to install them I get the above message.  It gives me no way to bypass it.  I can close the window and try again but it just goes round and round.  When I click on 'Details' I get this:
```
apt apt-transport-https apt-utils bamfdaemon evince evince-common file-roller gir1.2-panelapplet-3.0 gnome-panel gnome-panel-bonobo gnome-panel-data gnome-session gnome-session-bin gnome-session-common gnome-user-guide gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter libbamf0 libevdocument3 libevview3 liblircclient0 libnux-0.9-0 libnux-0.9-common liboverlay-scrollbar-0.1-0 libpanel-applet-3-0 libpanel-applet2-0 libpoppler-glib6 libpoppler13 libsmbclient libsyncdaemon-1.0-1 libwbclient0 nux-tools overlay-scrollbar poppler-utils python-ubuntuone-client python-ubuntuone-storageprotocol samba-common samba-common-bin smbclient tzdata tzdata-java ubuntuone-client ubuntuone-client-gnome unity unity-common xserver-xorg-video-intel
```
Any ideas?  There doesn't appear to be anything unusual in my software sources.
I see alot of gnome things in there for a unity system but do you get the errors when trying to update from the cli if so please post 
```
sudo apt-get update
```

---

### Post by corncob on 2011-05-04
I didn't see any errors running
```
sudo apt-get update
```
but
```
sudo apt-get upgrade
```
 didn't work.  I'll do it again and post the output if it would be helpful.  It seemed to be unhelpful things like 'failed'.  I had unchecked everything in the 'Other Software tab.  I switched to the Unity desktop just to try something different but couldn't even get online.  I went back to Gnome, went online fine, and tried update manager again.  (In spite of removing the other software sources the updates were up to 527)  It appeared to be working with no error messages.  I sat here and watched it till it was about 1/4 downloaded but, since it was taking forever, I went about other things.  When I came back it was as if nothing happened -- Update manager still said I had 527 updates to install.

Maybe there's another thing I should mention:  A window had popped up earlier saying
> Sorry, PolicyKit Authorization Agent closed unexpectedly
I tried to report it as a bug but it said that I couldn't because my files were out of date.  I'm wondering if its a case of PolicyKit not letting me upgrade because I need an upgrade (I know, it doesn't make sense).  I'll reboot and try again.

---

### Post by wolfen69 on 2011-05-04
Try
```
sudo apt-get dist-upgrade
```

---

### Post by corncob on 2011-05-04
> **wolfen69 said:**
> Try
```
sudo apt-get dist-upgrade
```

Getting failure to resolve all kinds of things there too.  I had installed Natty Beta alongside of 10.10 and still have that partition.  I booted into it and get the same kind of problems so I've started to think its something else like the internet connection.  Its in a trailer 300 feet from the house with a repeater in the window.  I'm often amazed at how good the wifi is at that distance but it has acted up. Also, it is my old computer connected to old peripherals. I'll bring it up to the house tomorrow and see how it does on a wired connection.  I just wanted to get it fixed up for the kids.

---

