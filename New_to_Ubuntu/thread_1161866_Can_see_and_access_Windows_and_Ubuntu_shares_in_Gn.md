---
title: "Can see and access Windows and Ubuntu shares in Gnome commander but not Nautilus"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by longtom on 2009-05-17
As above.

Get an error message in Nautilus.  All works fine in Gnome commander.  What could be the source of that trouble...?

---

### Post by longtom on 2009-05-18
bump.  Sorry, this is really important for the people working in the network.

Nautilus just freezes or does nothing, when a directory on a network pc is selected.  I can get onto the pc but cannot get into any shared directory.

With Gnome Commander this problem does not exist.

Any clues?

---

### Post by kellemes on 2009-05-18
Start nautilus from a terminal window and post the error you're getting when trying to connect.

---

### Post by longtom on 2009-05-18
> **kellemes said:**
> Start nautilus from a terminal window and post the error you're getting when trying to connect.

I am getting this:

```

Initializing nautilus-open-terminal extension
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6058): WARNING **: Unable to add monitor: Not supported

```

After that nautilus shuts down - or sometimes it just hangs after opening a second window.  This does not only happen on one machine but on all three I have on this network right now.

Hope this helps.

---

### Post by XCan on 2009-05-18
I've noticed that if I use Nautilus to access Windows shares, I never get prompted for password, hence couldn't see much of anything. I had to type in the whole path manually, iirc, smb://name/name/share . Also, if I browsed the network, Nautilus was super slow, as you described, it appears to have hung.

---

### Post by longtom on 2009-05-19
> **XCan said:**
> I've noticed that if I use Nautilus to access Windows shares, I never get prompted for password, hence couldn't see much of anything. I had to type in the whole path manually, iirc, smb://name/name/share . Also, if I browsed the network, Nautilus was super slow, as you described, it appears to have hung.

Starngely enough, this also appears to happen with Ubuntu shares on the network...

---

### Post by timosborn on 2009-05-29
I've got a similar problem.  Nothing shows on my desktop, except the background.  The panels at the top and bottom of the screen show and work.  If I try and open a directory it says it is starting and then I get nothing.  If I use gnome commander it works fine.  If I try to run Nautilus from a terminal, I get this message: "Segmentation fault"

The log file reports:" May 29 09:58:28 big-black kernel: [ 6245.205490] nautilus[5560]: segfault at a110008 ip b5c76dc6 sp b5462fb0 error 4 in libbrasero-media.so.0.1.1[b5c65000+1f000] "

Any Ideas???  Thanks.

---

### Post by maks_zbogar on 2009-07-09
Same here...

From today, after Ubuntu restart, I cant access my windows shares anymore. It used to work perfect for 1 year, but now I don't have any idea why. I didn't install any new software, except Ubuntu updates.

I start Nautilus from Terminal and this is what I get:

** (nautilus:6460): WARNING **: Unable to add monitor: Ni podprto
Nautilus-Share-Message: unknown format for key 'desktop/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'deluge/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'videos/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'pictures/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'the best ever collection/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only

(These are all shortcuts to my network shares on my desktop.)

If then, I try to navigate to my network shares, Nautilus crashes with "Segmentation fault" text in Terminal. After that I can no longer see any item on my desktop. No icons, only background image.

Please, anyone...

---

