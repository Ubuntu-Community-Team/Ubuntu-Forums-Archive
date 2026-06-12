---
title: "Strange problem with Google ater long uptime"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by Konfuz on 2015-05-29
Hi yall, I'm currently running Ubuntu 15.04, but this problem was happening with 14.04 too.

My internet connection, for some reason, stops being able to access Google, Gmail, Youtube, Google Maps and pretty much everything Google related after I've been using my computer for a long time (more than 24 hours without rebooting). I still can search on Yahoo when this happens, and pretty much every other non-Google related sites are available (Bing being an exception, it also gets inaccessible along with Google).

At first I thought this was a problem with my ISP, but then I noticed that this did not happen with Windows 7, only started after I migrated to Ubuntu. I tried restarting my TP-Link router, as well as going into the configuration interface to get a new IP, but it never helps. Still I thought it was just a coincidence, until I decided to just reboot the computer, and voilà, I'm immediately capable of accessing Google related sites right afterwards.

This has been happening every couple of days for a month or so now. As soon as I notice this, I don't even mess with my router or anything, I just reboot the PC immediately. 

Still, it's pretty annoying, and I'd like to know a solution for this, or at least, what kind of commands I can do to avoid having to reboot? I tried "ifconfig eth0 off" and "ifconfig eth0 on" but it didn't help.

Some details: 
Internet is fiber with pppoe authentication.
I leave qBittorrent on pretty much 24/7 and I do a lot of seeding.
When Google goes dark for me, usually my torrent upload speed gets much slower as well, but the download continues to work fine.
Restarting the router and getting a new IP do not help.
Restarting the PC helps immediately.
The problem happens both on Firefox and Chromium.
Pinging google.com from the Terminal works.

Any ideas?

---

### Post by tgalati4 on 2015-05-29
Welcome to the forums.

Google applications are all linked, so if you have a problem with google-chrome, then it will affect other google apps.  It's possible that there is a bug which needs fixing.  

Try using another browser in linux and see if the behavior is similar.

---

### Post by Konfuz on 2015-05-29
Thank you @tgalati4 !

My main browser is Firefox and I noticed the problem while trying to access Google sites with it. I occasionally use Chromium and the issue affects both browsers equally, I suspect it has nothing to do with these applications.

---

### Post by Konfuz on 2015-05-30
little bump in case someone figures this mystery out

---

### Post by Konfuz on 2015-05-31
It just happened again and I had to reboot. 
Tried to access Google and Youtube without success from Firefox and from Chromium.
Strangely, pinging google.com from the terminal worked.

---

