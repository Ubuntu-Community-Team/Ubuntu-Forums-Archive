---
title: "Pidgin and Gfire Plug in question"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by adventure man on 2009-05-04
Hey guys trying to install gfire plug in into Pidgin.  I downloaded the DEB, installed it, but the xfire IM client doesn't appear in the manage list of chat clients for Pidgin.  At gfire's website I saw "exe", "SRC" and "DEB", not exactly sure if I am doing this properly as I'm totally new to Xubuntu. I downloaded the src and exe both of which ask for a program to open it with :confused:

   I would like to use xfire though to chat with some friends on there.  Any ideas how to install a chat client plug in into pidgin?  :confused:
I'm an ex windows xp user converted to Xubuntu.  I'm using a Gateway 1450 solo laptop.  Xubuntu 9.  Pidgin 2.4.1.  I have MSN,google chat and yahoo chat working on Pidgin.:guitar:

thanks.:)

---

### Post by inobe on 2009-05-04
gfire

[http://www.youtube.com/watch?v=82zeK321b_w](http://www.youtube.com/watch?v=82zeK321b_w)

---

### Post by adventure man on 2009-05-04
> **inobe said:**
> gfire

[http://www.youtube.com/watch?v=82zeK321b_w](http://www.youtube.com/watch?v=82zeK321b_w)


That shows you mostly how to configure your games in gfire.  I can't even get the basics of actually installing gfire into pidgin, I don't know what to do with it :confused:

---

### Post by inobe on 2009-05-04
heres the gfire site loaded with information

[http://gfire.site40.net/?page_id=22](http://gfire.site40.net/?page_id=22)

you may find lot's of howto's at there forum

here's something else 

[http://ubuntuforums.org/showthread.php?t=720375](http://ubuntuforums.org/showthread.php?t=720375)

---

### Post by adventure man on 2009-05-04
> **inobe said:**
> heres the gfire site loaded with information

[http://gfire.site40.net/?page_id=22](http://gfire.site40.net/?page_id=22)

you may find lot's of howto's at there forum

here's something else 

[http://ubuntuforums.org/showthread.php?t=720375](http://ubuntuforums.org/showthread.php?t=720375)


thanks for all the help inobe:)

the first link didn't have much.  The second link was really interesting.  In it user "tinivole" in his 4th post mentions this:

"you could try manually installing it in on your filesystem.

If you right click the .deb file and click "Extract Here".
Enter the newly created folder and extract the "data.tar.gz" file.

Then become root in nautilus
 	Code:
 	 sudo nautilus 
and copy the extracted "usr" folder into your "/" filesystem. Just click "Replace all".
If you feel unnerving doing this, you can always examine the contents throughly before you do. Just to be sure."

ok now I get the extract part.  BUT once he mentions "become root in nautilus" I am lost.  This screenshot shows where I have reached lol  I figured I would have to find a pidgin directory with a plug in folder a la windows style lol.  :confused:

Sorry for my newbness fellas.

oh the screenie:
 [[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/th_Screenshot2.png[/IMG]](http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot2.png)

---

### Post by adventure man on 2009-05-27
i never got gfire to work with pidgin :(

even after switching from Xubuntu to Ubuntu 8.04.2, still I get the same thing after installing it.  Xfire simply will not show up in my list of Instant message clients :(

[[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/th_Screenshot-AddAccount.png[/IMG]]("http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot-AddAccount.png")

---

### Post by Bigbob22 on 2009-06-08
> **adventure man said:**
> i never got gfire to work with pidgin :(

even after switching from Xubuntu to Ubuntu 8.04.2, still I get the same thing after installing it.  Xfire simply will not show up in my list of Instant message clients :(

[[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/th_Screenshot-AddAccount.png[/IMG]]("http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot-AddAccount.png")

I had the same problem adventure man. I never got it fixed though.

---

### Post by philinux on 2009-06-08
[http://ubuntuforums.org/showthread.php?t=1181110](http://ubuntuforums.org/showthread.php?t=1181110)

See post #7 and #8

---

### Post by adventure man on 2009-06-08
Thanks for the updates/help guys.  Phil I followed your posts from that thread.  Installed the pidgin deb then reinstalled gfire.  Still nothing.  I then installed every synaptic pidgin extra I saw, still nothing again LOL

I am using 32bit ubuntu 8.04.2, noticed you were using 64bit.  Think this may be an issue?  I haven't given up yet! :D

---

### Post by philinux on 2009-06-08
If you're using 8.04 what version of pidgin you running. Gfire needs 2.5 or later I think.

---

### Post by adventure man on 2009-06-08
> **philinux said:**
> If you're using 8.04 what version of pidgin you running. Gfire needs 2.5 or later I think.
I'm using 2.4.1, apparently ubuntu won't update pidgin, only security updates?

Well I found this when searching for Pidgin 2.5:

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Followed their instructions with the terminal commands, then went to update manager where 2.5.6 was promptly downloaded and installed on my machine.  Restarted pidgin and it worked, I put xfire as one of my accounts and can chat with my friends.  THANKS PHIL!!! :D

---

