---
title: "How can Amarok find music files on a windows machine?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-05
Running Jaunty (32 bit), samba.  Wireless network.  Another machine runs Vista.  From the Linux machine I can see the shared folders on the windows machine so I know sharing is working.  The problem is that when I start up Amarok 2.0.2 or rythmbox, I can't get the list box to show the music files on the windows machine.  In Amarok, I have to use the "playlists" tab and "add media".

In windows there is a feature that is called "mapping a network drive".  Does a similar concept exist in Ubuntu?

Or maybe there is a better way?

---

### Post by logos34 on 2009-06-06
does this help

[http://ubuntuforums.org/showpost.php?p=7342001&postcount=6](http://ubuntuforums.org/showpost.php?p=7342001&postcount=6)

?

maybe then you can add location to amarok collection scan in settings

---

### Post by MrWES on 2009-06-06
> **raymondvillain said:**
> Running Jaunty (32 bit), samba.  Wireless network.  Another machine runs Vista.  From the Linux machine I can see the shared folders on the windows machine so I know sharing is working.  The problem is that when I start up Amarok 2.0.2 or rythmbox, I can't get the list box to show the music files on the windows machine.  In Amarok, I have to use the "playlists" tab and "add media".

In windows there is a feature that is called "mapping a network drive".  Does a similar concept exist in Ubuntu?

Or maybe there is a better way?

If your music library on the Vista machine is using iTunes, you can share the library from iTunes and Rhythmbox will see the shared library. It's actually called mt-daap shares, and Apple developed it.

Bill

Edit: I believe the new version of Amarok supports daap shares now too.

---

### Post by raymondvillain on 2009-06-06
Thanks for all the help.  I was able to have Amarok 2.0.2 find the music files on the other machine using "play media">"network" etc. but sloopveedub says I might use "auto-mount".

What does one do to enable "auto-mount"?  Just point me in the right direction.

---

### Post by logos34 on 2009-06-06
> **raymondvillain said:**
> "play media">"network" etc. but sloopveedub says I might use "auto-mount".

What does one do to enable "auto-mount"?  Just point me in the right direction.

in the main windows try right-clicking on the device/network folder>properties>mounting.  I think there's an automount option but I'm not sure how it all works with amarok

---

### Post by raymondvillain on 2009-06-06
I am confused.  Logos34 says

"In the main windows try right-clicking on the device/network folder>properties>mounting."

Are you speaking of the main window for Amarok?  My version of Amarok (2.0.2) doesn't have anything that jibes with your instructions.

Are you referring to the Nautilus main window?

---

### Post by logos34 on 2009-06-06
well i'm using amarok 1.4.9

I meant this:

[ATTACH]116640[/ATTACH]

maybe you can go into network folder and right-click to bring up properties

dunno exactly how it's supposed to look because I don't have samba or NAS

---

### Post by raymondvillain on 2009-06-06
Thanks for the clarifaction, logos34.  Automount is not an option when I right click on the network or any of it's drives.

---

### Post by logos34 on 2009-06-06
yeah, after fiddling around it seems I can only do it for **Storage Media**>right-click on volume>properties>mounting

---

