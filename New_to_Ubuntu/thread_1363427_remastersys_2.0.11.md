---
title: "remastersys 2.0.11"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-24
can some one please explain the difference between...
these options:
Dist 
Distcdfs
Distiso
I can't find a decent explanation at the site.
thanks

---

### Post by bodhi.zazen on 2009-12-24
I believe you get a nice description of these options when you run remastersys as a gui application.

Dist - This is "ons stop shopping" and makes a custom iso you can distribute. It removes all users above 999 (thus any data in your $HOME is not on the iso) and runs both of the below options.

Distcdfs - Makes a copy of your file system in /home/remastersys Peopel use this optino if they want a backup or to make furteher customizations.

Distiso - Uses the above file system to make an iso. Use this option once you have made any customizations to the "cdfs"

See also :

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by DarinB on 2009-12-24
now where near as clear as what you just gave thanks this helps,,,,any way to get the add-ons for firefox and thunderbird that would be a total home run for my flock the people i have converted to the one true god ubuntu....lol

---

### Post by bodhi.zazen on 2009-12-24
You can.

Make a user with a UID of 999

Set up that user with a user name of Ubuntu =)

It will then work when running live.

If you want all users to have the same profile, I put it in /etc/skel

If you want to see one method, you can download Zenix =)

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

If you look at the config I used you can probably set you iso up as well =)

---

### Post by DarinB on 2009-12-24
Make a user with a UID of 999   **Done**

Set up that user with a user name of Ubuntu =) **Done**


It will then work when running live.

If you want all users to have the same profile, I put it in /etc/skel                     **how do i do this?**

Not sure that all of this stuff will do?
will this cause all the extensions to end up on the distro and what else will be on it?

---

### Post by bodhi.zazen on 2009-12-24
You basically have to either go through it with a fine tooth an comb.

If you put .mozilla in /etc/skel , .mozilla will be copied from /etc/skel to /home/new_user when you make a new user.

Some stuff will break, some stuff belongs in /etc and there is no on line tutorial that I know of =)

The Zenix iso will probably help you as again you can look at what was included and how it was included =)

---

### Post by DarinB on 2009-12-24
sounds kind of hairy...I will look up some more stuff thanks.... can you recommend a good book, i remember how great Minasi's book was for windows. Do we have anything that comprehensive for us? I Also remember how good the MCSE cert books were. Do we have those kind of texts? with labs and things to practice with?

---

### Post by bodhi.zazen on 2009-12-24
There are no books on how to do this.

Use google, lol

[http://geekconnection.org/remastersys/capink.html](http://geekconnection.org/remastersys/capink.html)

[http://crunchbanglinux.org/forums/topic/2859/remastersys-guide-create-your-own-ubuntubased-distro/](http://crunchbanglinux.org/forums/topic/2859/remastersys-guide-create-your-own-ubuntubased-distro/)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

No link is complete, you will have to learn as you go.

---

### Post by DarinB on 2009-12-24
one day we will have good text books like M$ does. thanks

---

