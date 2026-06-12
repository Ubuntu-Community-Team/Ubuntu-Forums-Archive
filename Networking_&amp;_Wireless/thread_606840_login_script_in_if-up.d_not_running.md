---
title: "login script in if-up.d not running"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by bfkeats on 2007-11-08
I've got a little perl script that logs into my school's wireless network. I want to run it when networking is turned on, so I put it in if-up.d. For some reason, it's not running even when I reboot. The permissions are the same as the other scripts in that directory.

Anyone know how I can get this to run for me?

---

### Post by Ehtetur on 2007-11-08
You just need to edit  /etc/network/interfaces and add a  link to your script.
Place this entry below the eth0 or wlan0 entry you want:

post-up /etc/network/if-up.d/<name of your script>

I've only added bash scripts, never perl.. Let me know how that works for you...

side note: You can configure nm-applet to remember multiple wireless and wired connections.. That way, you can have not just your school's wireless settings avail at a click, but also the settings at your friends', at starbucks. and even some of the posher car washes.

---

### Post by bfkeats on 2007-11-15
Hmm, Would there be a way to do this without disabling roaming mode?

---

