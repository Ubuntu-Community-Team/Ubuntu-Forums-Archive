---
title: "Avahi services"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by mrgrapefruit on 2007-01-24
Hi there,

I have netatalk running, but I can't seem to get avahi to display the service. I've added an afpd.service xml doc to /etc/avahi/services and restarted the daemon, but it still doesn't show. I can connect to the AFP share directly. I've installed libnss-mdns too. Any ideas?

[edit:]i should probably also add that i've got this working before on FreeBSD, so i dont see why it shouldnt work now...

---

### Post by spd106 on 2007-01-24
Have you double-checked the .service file for errors? 
Use the man page for information [http://www.die.net/doc/linux/man/man5/avahi.service.5.html](http://www.die.net/doc/linux/man/man5/avahi.service.5.html)

---

### Post by mrgrapefruit on 2007-01-24
yeah everything seems to be ok in it, i added the protocol=ipv4 part, although i dont think that part is necessary, and it still doesnt show.

its pretty annoying, because i just installed mt-daapd and it autoregistered itself and is working great!

---

### Post by mrgrapefruit on 2007-01-24
bugger me

i removed the <!DOCTYPE... on a whim and it started working. i dont know whether to laugh or cry... :confused:

---

### Post by spd106 on 2007-01-24
Does the line look like this```
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

```.
I didn't know it was optional, well you learn something everyday.

I think most apps that support avahi natively use avahi-publish or perhaps dbus to register services directly rather than statically advertise.

---

