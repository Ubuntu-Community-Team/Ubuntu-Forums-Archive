---
title: "Setting up a Mustek 600 III EP Plus Scanner"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by jgreensail on 2010-01-05
Hi all, I'm setting up my computer using Ubuntu 9.10 (karmic), Kernel Linux 2.6.31-16-generic GNOME 2.28.1; Hardware: Memory 1002.5 MiB, Processor AMD Athlon XP 1700+

I have already successfully gotten my Canon PIXMA iP2600 working, etc. Now I'm trying to get my old but trusty Mustek 600 III EP Plus scanner to work. Here's what I've done so far:

Installed the libsane-extras package.

In Terminal I edited the SANE driver file:
gksudo gedit /etc/sane.d/dll.conf

I removed the # in front of mustek_pp
Saved and Closed the file dll.conf

Then ran XSANE

The scanner was not detected

Then I edited the mustek_pp.conf file

1st I tried removing the # from in front of this line:
# scanner Mustek-600-IIIEP 0x378 ccd300

Saved/Closed and tried to detect it with XSANE again, No luck.

Then I re-edited the  mustek_pp.conf file
and changed the same line to be like this:
scanner Mustek-600-IIIEP parport0 ccd300

That didn't help either.

Then I tried this: commented out the line again like this:
# scanner Mustek-600-IIIEP 0x378 ccd300

Then under (# auto probing:) I un-commented this line:
# scanner mustek-ccd300 * ccd300 like this:
scanner mustek-ccd300 * ccd300

Still not detected.

Any suggestions would be very appreciated.
Capt. Jim in NC USA

---

### Post by sandyd on 2010-01-05
i ##used
to have that scanner
and i needed to use....although this is dangerous....
gksudo xsane
seems like theirs a permissions problem on /var/parport0

---

### Post by jgreensail on 2010-01-05
That worked! Why is this dangerous?

---

### Post by jgreensail on 2010-01-06
Here's what I tried next: I thought that if I added "lp" to my group memberships that would cure the permission problem since group "lp" has rw- permission just like root. So, I added lp to my groups.

That had no effect. So I removed lp from my groups.

Last I used chmod to change the permissions from 660 to 666.

sudo chmod -v 0666 /dev/parport0

Now I can run the XSANE and it finds my scanner without my having to run it as root.

I would love to hear any good reasons not to do it this way. It seems to work perfectly well now.

---

### Post by jgreensail on 2010-01-07
I found out now that using chmod as above only works for the duration of the login. That's ok for me, I guess. Its not too much trouble to do the chmod command whenever I want to do scanning.

---

### Post by jgreensail on 2010-01-07
This should be the final post on this subject.

I found out in my reading today that for a new group membership to take effect you have to logout and log back in. I didn't do that after I made myself a member of the "lp" group last time.

Today I made myself a member of the "lp" group for /dev/parport0 and rebooted.

Now XSANE works without me having to put in any special commands.

Hurrah!

---

### Post by Methuselah on 2010-01-07
Great work figuring this out :)

---

