---
title: "KDE has mucked up Gnome!!"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by migs73 on 2010-06-12
Have been using plain Ubuntu for a while and thought I would give KDE a whirl. Went to software centre and downloaded Kubuntu Plasma Desktop. Logged out, selected KDE from the options on login and hey presto, Kubuntu.
Great, played around finding out how the menus worked etc, but no changes to system or the like. Logged out and changed back to gnome (wasn't that keen on KDE), now some of my panel applets disappear on occasion, my pointer is the fat looking KDE one along with the KDE spinning circles when working, and also when I shutdown I get the Kubuntu splash screen and the same splash screen on boot.:confused:

Please help me get my Gnome back!!!

I have uninstalled Kubuntu Plasma (still no change), but I believe this is really just a pointer to lots of other files, etc which make up Kubuntu.

---

### Post by cuberts on 2010-06-12
> **migs73 said:**
> Have been using plain Ubuntu for a while and thought I would give KDE a whirl. Went to software centre and downloaded Kubuntu Plasma Desktop. Logged out, selected KDE from the options on login and hey presto, Kubuntu.
Great, played around finding out how the menus worked etc, but no changes to system or the like. Logged out and changed back to gnome (wasn't that keen on KDE), now some of my panel applets disappear on occasion, my pointer is the fat looking KDE one along with the KDE spinning circles when working, and also when I shutdown I get the Kubuntu splash screen and the same splash screen on boot.:confused:

Please help me get my Gnome back!!!

I have uninstalled Kubuntu Plasma (still no change), but I believe this is really just a pointer to lots of other files, etc which make up Kubuntu.I am not aware of the problem that you are having right now, but perhaps this link will help. [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Elfy on 2010-06-12
+1 to the psychocat link.

Also check this for the splash - this assumes you're using 10.04.

```
sudo update-alternatives --config default.plymouth
```

I'd bet it is set to kubuntu - change it there.

---

### Post by migs73 on 2010-06-12
Cuberts; tried your suggestion but made no difference, still KDE pointer etc. Probably uninstalled all the other stuff that comes with Kubuntu though, thanks.

forestpiskie; Yes it was set to Kubuntu; have just changed to Ubuntu so assume this will be ok. Many thanks.

Anybody any ideas how to get rid of my fat pointer, I really hate it!! I have changed themes and back again, but no joy. :confused:

Just logged out and back in and have my Ubuntu splash back. Not far to go now!

Another edit; oddly the pointer is only the 'oxy-white' KDE one when I am in the panels, desktop or other open window? But when I go onto the Firefox window it changes to the DMZ white. DMZ white is on my Appearances> Customize> Pointer as the selected pointer.

---

### Post by Elfy on 2010-06-13
I would check in synaptic for any installed kde packages.

---

### Post by migs73 on 2010-06-13
Forestpiskie

There are hundreds of KDE packages installed. Had a look through them and found one package called oxygen-cursor-theme (obvious now, but wouldn't have meant much till I found out what the cursor theme was called!). Completely removed and rebooted. I now have DMZ back. 

The Gnome has returned :p.

Many thanks to you all.

---

### Post by Elfy on 2010-06-13
well if you have no kde apps installed then you shouldn't have any kde packages I thought - I know after a visit to amarok I removed all the kde stuff manually.

But that's another story I guess

---

