---
title: "Wireless networking bug fix."
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by sonasi on 2007-01-12
All,

I have been wrestling with a problem that many of you have also been pulling your hair out over:  wireless networking not working after boot - but works fine if you restart networking (# /etc/init.d/networking restart).

There are two ways (that I know of) to get wpa_supplicant in the loop:
1 - Use pre-up in /etc/network/interfaces and manually spawn daemon
2 - Depend on /etc/wpa_supplicant/ifupdown.sh to do it automatically

Well, I have been relying on the latter and that is where the bug is.  The script spawns wpa_supplicant without the "-w" option - which forces the daemon to wait for the interface to be brought up ($ man wpa_supplicant).  If you check your processes you will see its missing ($ ps aux | grep -i wpa).

So I edited the ifupdown.sh script and added "-w" to the WPA_SUP_OPTIONS variable.  I had to do this in two places in the script.  Do a reboot and all is good in the world!  You can check the process again to verify that now is using "-w" switch.

No longer need to hack networking restart in rc.local or other rc scripts.

---

### Post by mtierney on 2007-01-12
Would you mind elaborating on what you think the source of the problems was? (or, well, point me in the direction of a thread with such info?) Sounds interesting, but I haven't experience it myself :-)

---

### Post by sonasi on 2007-01-12
Read this thread for an example of problems some were/are having:[http://ubuntuforums.org/showthread.php?t=323177]("http://ubuntuforums.org/showthread.php?t=323177")

wpa_supplicant is designed to be a "daemon" program that runs in the background and acts as the backend component controlling the wireless connection.

The problem is regarding the timing related to having the wireless interface brought up and the wpa_supplicant daemon waiting for it.  Without the "-w" switch the daemon would immediately halt in handling the negotiation with the wireless AP.

---

