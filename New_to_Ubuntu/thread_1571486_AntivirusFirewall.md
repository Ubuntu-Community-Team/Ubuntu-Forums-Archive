---
title: "Antivirus/Firewall"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by corriepalmer on 2010-09-09
I was just wondering if Ubuntu already came with stuff like this in it and if not, where can I find a decent one?

---

### Post by uRock on 2010-09-09
Welcome to the forums,

There is a built in firewall called IPTables, it is automatically activated.

To learn more about Ubuntu security check out this link [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) by an awesome community leader.

uRock

---

### Post by corriepalmer on 2010-09-09
Thank you :)

---

### Post by mr.xulu on 2010-09-09
To learn more about Ubuntu security check out this link [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) by an awesome community leader.

uRock[/QUOTE]


I'm an absolute beginner at ubuntu. thanks for this link uRock.

Re corriepalmer's question of whether ubuntu comes with firewall and anitvirus packaged there's a basic page I found from my searches for setting this up.

here's the link:

[http://www.johannes-eva.net/index.php?page=2010-04-ubuntu-lucid-useful-guide](http://www.johannes-eva.net/index.php?page=2010-04-ubuntu-lucid-useful-guide)

then go to item 'E. System & administration software'.

---

### Post by uRock on 2010-09-09
> **mr.xulu said:**
> 
I'm an absolute beginner at ubuntu. thanks for this link uRock.

Re corriepalmer's question of whether ubuntu comes with firewall and anitvirus packaged there's a basic page I found from my searches for setting this up.

here's the link:

[http://www.johannes-eva.net/index.php?page=2010-04-ubuntu-lucid-useful-guide](http://www.johannes-eva.net/index.php?page=2010-04-ubuntu-lucid-useful-guide)

then go to item 'E. System & administration software'.

I wouldn't trust anything on that site after the FUD I just read there about MS Hotmail. [http://www.johannes-eva.net/index.php?page=2010-01-ten-reasons-why-not-to-use-hotmail](http://www.johannes-eva.net/index.php?page=2010-01-ten-reasons-why-not-to-use-hotmail)

---

### Post by mr.xulu on 2010-09-09
> **uRock said:**
> I wouldn't trust anything on that site after the FUD I just read there about MS Hotmail. [http://www.johannes-eva.net/index.php?page=2010-01-ten-reasons-why-not-to-use-hotmail](http://www.johannes-eva.net/index.php?page=2010-01-ten-reasons-why-not-to-use-hotmail)

Hi uRock! Checked out your link. I think that article took it quite a bit too far.

Will be more careful.

Thanks :)

---

### Post by Dex73 on 2010-09-09
Firestarter is a good fire wall and Avast makes for a decent antivirus, not that you need antivirus for Ubuntu in my opinion.

---

### Post by seawolf167 on 2010-09-10
You have choices as mentioned above, but here are two that should work straight-away after you install them:

clamtk

[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

gufw

[http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

---

### Post by coffeecat on 2010-09-10
> **Dex73 said:**
> Firestarter is a good fire wall

Sorry to appear pedantic, but this can't be said too many times. The firewall is iptables which comes in a default install. Firestarter is merely one of several GUI configuration tools.

From the link that uRock posted:

> A source of confusion sometimes occurs when users feel the need to be  running firestarter/Guarddog for their firewall to be active. **This is untrue !**  Keep in mind that these applications are not firewalls, but rather  configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*.  firestarter will monitor traffic, but it runs as root and there are  better monitoring programs, so configure you firewall, shut down  firestarter/grauddog, and let IP tables do the restIt's important to make the distinction because newcomers, used to Windows firewalls, worry needlessly when they see that Firestarter doesn't seem to be running immediately after login.

---

### Post by Rubi1200 on 2010-09-10
+1 to what coffeecat says here.

I just want to add that those venturing into Ubuntu for the first time should NOT be using Firestarter at all. It is no longer maintained and there are better alternatives out there. For example, UFW or if you must have a GUI, use GUFW.

You wouldn't use security software on Windows that wasn't actively maintained, so why would you do it on Ubuntu?

---

### Post by coffeecat on 2010-09-10
> **Rubi1200 said:**
> I just want to add that those venturing into Ubuntu for the first time should NOT be using Firestarter at all. It is no longer maintained and there are better alternatives out there. For example, UFW or if you must have a GUI, use GUFW.

I'll return the compliment and +1 that back. :p

If you look at the firestarter webpage...

[http://www.fs-security.com/](http://www.fs-security.com/)

... you'll see it hasn't been updated for three years. Not a good sign. Last time I used it, I had real problems with it, blocking services I had specifically unblocked, so I had no confidence that it would block services that needed to be blocked. Or, more accurately, configuring IPtables to do the correct blocking.

A pity - it's a nice user-friendly interface. A shame that no one picks it up and bugfixes and maintains it once again.

---

