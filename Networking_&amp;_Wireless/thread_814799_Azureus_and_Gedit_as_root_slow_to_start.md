---
title: "Azureus and Gedit as root slow to start"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by martinnorth on 2008-06-01
I´ve recently encountered 2 issues, that I can solve at least temporarily, but I´m looking for a permanent solution. The problems are:

-Azureus starting VERY slowly. (3 mins). On starting I see the following message ¨There appears to be another program process already listening on socket [127.0.0.1: 6880]

-Gedit starting and running VERY slowly when run with gksudo. Otherwise running normally.

I found a solution that worked for the Azureus issue here:

[http://ubuntuforums.org/archive/index.php/t-216971.html]("http://ubuntuforums.org/archive/index.php/t-216971.html")

by running


/sbin/ifconfig lo 127.0.0.1
/sbin/route add -net 127.0.0.0 netmask 255.0.0.0 lo

And much to my suprise, the gedit issue was resolved as well.

But can anyone tell me how to modify my settings to apply this solution permanently? I an Ubuntu novice, so forgive me if this is obvious.

Martin

---

### Post by fontenot_1031 on 2008-06-03
woah I wasn't the only one with slow gksudoed gedit

---

### Post by martinnorth on 2008-06-03
Did the commands work for you? Do you know how to make the changes permanent?

---

### Post by sultanoswing on 2008-06-03
> **fontenot_1031 said:**
> woah I wasn't the only one with slow gksudoed gedit

Nope me too. In fact it would take about 30 seconds or ore to open, then would freeze (grey out) - necessitating a 'force quit'.

Running as 'su' from terminal ran into authentication errors, while "gksudo -u username gedit /filename" worked OK, but I didn't have permissions to actually make changes (to system config files, anyway).

I thought it could be due to the theme I'm running (Mac4Lin, emerald theme), or some other odd gnome / gconf settings, as the problem resolved initially by wiping all my .gnome et al folders from my Home directory, but returned as I reinstituted my settings.

FWIW, today's updates seem to have resolved my problem - I note there were a few gedit / gksudo updates in there.

---

### Post by martinnorth on 2008-06-08
This is really annoying. Localhost won resolve properly, and this is affecting Azureus, gedit, and now rdesktop to QEMU. Running the commands in the original post fixes, but only until the next reboot.

Can somebody please help me make this permanent?

Martin

---

