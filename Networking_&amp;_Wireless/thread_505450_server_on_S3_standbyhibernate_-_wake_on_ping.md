---
title: "server on S3 standby/hibernate - wake on ping?"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by kacheng on 2007-07-20
I've been looking into trying to achieve the following behaviour:

- server running fileshare
- server uses CPU frequency scaling to minimize power usage while running

- server to go to standby(s3)/hibernate mode when not in use to save energy and reduce heat output
- when server is pinged, server should awaken and resume as normal after a short delay, there should be no need for a 'magic packet' as typically required by Wake on LAN (WOL)


I've been able to get WOL functionality working by enabling WOL in the BIOS and that seems to work if I send a 'magic packet' to the MAC address of server to awaken it.

However, I've seen some Windows XP tutorials to enable a 'wake on ping' type functionality that would not require a 'magic packet'.  Typically this is chosen in the network card configuration dialog.

Is there a way to do this in Ubuntu?

---

### Post by kacheng on 2007-07-23
bump

---

### Post by kacheng on 2007-07-28
bump

---

### Post by lowf on 2008-01-17
If anyone has any ideas please answer, I am looking for the same thing.

---

### Post by icemanxp on 2008-02-10
bump

---

### Post by abbyzcool on 2008-04-10
You could possibly patch your ping program to automatically send magic packets whenever you ping the remote host.

This might help --

[http://www.math.kobe-u.ac.jp/~kodama/tips-WakeOnLAN-C.html]("http://www.math.kobe-u.ac.jp/~kodama/tips-WakeOnLAN-C.html")

---

### Post by kacheng on 2008-04-24
Isn´t that just the same as sending a magic packet?

I would prefer if you could just get the server to wake itself up from standby/hibernation on ANY request.

As I mentioned, in Windows this appears to be a setting on the network adapter configuration.  Is this more of a network adapter driver issue?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-02
bum

---

### Post by al_mckin on 2008-05-03
Bump! This would be awesome, and would lessen my guilt about leaving my desktop on when i'm not there....

---

### Post by vashwood on 2008-05-27
Bump.  I'd rather have this instead of using WOL.

---

### Post by Aearenda on 2008-07-19
Maybe you could use one of the non-magic-packet modes for Wake on Lan - see [http://www.lesswatts.org/tips/ethernet.php](http://www.lesswatts.org/tips/ethernet.php)

---

