---
title: "Rhythmbox tease"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by nnjond on 2010-01-16
Have pasted a new radio station into Rhytmbox but
Rhythmbox wont tell me which gstreamer plugin is missing

---

### Post by warfacegod on 2010-01-16
Assuming you are using Ubuntu go to: System> Admin.> Software Sources and enable the multiverse source. Click reload when it asks. Then open a terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by nnjond on 2010-01-16
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-assistant libdmraid1.0.0.rc15 librsvg2-2.18-cil libqt4-test
  libgdata1.4-cil libboost-program-options1.38.0 libakonadiprivate1
  libqt4-xmlpatterns libqt4-help python-qt4 python-sip4 libpolkit-dbus2
  libwnck2.20-cil kdepimlibs5 libpolkit-qt0 libqt4-scripttools kdepimlibs-data
  libpolkit-grant2 libnotify0.4-cil python-kde4 libgnomedesktop2.20-cil
  libpolkit2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nnjond@den-desktop:~$ 

?

---

### Post by warfacegod on 2010-01-16
> **nnjond said:**
> sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-assistant libdmraid1.0.0.rc15 librsvg2-2.18-cil libqt4-test
  libgdata1.4-cil libboost-program-options1.38.0 libakonadiprivate1
  libqt4-xmlpatterns libqt4-help python-qt4 python-sip4 libpolkit-dbus2
  libwnck2.20-cil kdepimlibs5 libpolkit-qt0 libqt4-scripttools kdepimlibs-data
  libpolkit-grant2 libnotify0.4-cil python-kde4 libgnomedesktop2.20-cil
  libpolkit2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nnjond@den-desktop:~$ 

?

It means you already have it. Use the auto remove to get rid of the packages you just downloaded, they're just cluttering things up.

---

### Post by warfacegod on 2010-01-16
> **nnjond said:**
> Have pasted a new radio station into Rhytmbox but
Rhythmbox wont tell me which gstreamer plugin is missing

I assume by this that it is telling that something is missing?

---

### Post by nnjond on 2010-01-16
Rhythmbox wont play new station :

"Couldn't start playback"

"Your GStreamer installation is missing a plug-in."

"The requested plugins are:

text/html decoder"

---

### Post by warfacegod on 2010-01-16
Check Synaptic to see if you have all of these packages exept the one on the bottom of the list.

---

### Post by nnjond on 2010-01-16
Their all there

---

### Post by warfacegod on 2010-01-16
Then I'm out of ideas at the moment. I'll check back in later if I think of anything.

---

### Post by arnab_das on 2010-01-16
u could try purging and reinstalling the gstreamer plugin.

---

### Post by warfacegod on 2010-01-16
> **arnab_das said:**
> u could try purging and reinstalling the gstreamer plugin.

There are several gstreamer plugins, doing them one at a time would be tedious. A more elegant approach would be:

```
sudo apt-get purge ubuntu-restricted-extras

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by twipley on 2012-08-28
Sorry to revive such an old thread.

I have suffered from the following problem:

"Python (v2.7) requires to install plugins to play media files of the following type: text/html decoder"

Under every fresh Ubuntu installs. I have just found a working solution. Right-click on one of the default radio stations, select properties, and then copy and paste the url into a browser. It then makes you download a playlist file, which you can then open back using Rhythmbox.

Then you obtain a new radio station, through which you can (for example for the Broadband Classic Rock) get the url again through properties:

[http://ogg2.as34763.net/vc160.ogg](http://ogg2.as34763.net/vc160.ogg)

Just entering the latter works as great as the default station!

---

### Post by sffvba[e0rt on 2012-08-28
*Back to **sleep **old thread.*


404

---

