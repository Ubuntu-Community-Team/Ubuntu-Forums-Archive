---
title: "defaulting to network settings location"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Hamdoon on 2008-02-07
Hi, I am new to Ubuntu and sort of Linux in general so please forgive me if this question is extremely basic.

I need to specify a particular set of DNS servers for my internet connection to work properly.  To do this, I went in to the network settings dialog, entered my DNS servers, and clicked "save current network configuration as location" and saved a new network location.

While that did work, I soon found that whenever I log in (or after I have been AFK for a good while), I need to go back into the network settings dialog and select the saved network location.  The default (blank named) location seems to hold the original settings.  I would like to avoid doing this manually, and to have my user account default to use the new network location that I have saved.  

I am probably missing something fundamental here but I have not been able to figure out how to do this.  If someone could clue me in as to how this is done, or how I am barking up the wrong tree, it would be much appreciated.  Thanks!

BTW I am using gutsy and a wired ethernet connection.

---

### Post by Iowan on 2008-02-07
If you use DHCP for IP addresses, you may need to edit the client file.  [This]("http://ubuntuforums.org/showthread.php?t=543659") thread has more details (enable/modify prepend line).

---

### Post by Hamdoon on 2008-02-07
> **Iowan said:**
> If you use DHCP for IP addresses, you may need to edit the client file.  [This]("http://ubuntuforums.org/showthread.php?t=543659") thread has more details (enable/modify prepend line).

That is just what I needed, thank you!

---

