---
title: "Configuring D-link DI-524 for torrents"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by DavidGX on 2007-12-20
Hi. I seem to be having a bit of difficulty configuring my D-link DI-524 to correctly allow torrent traffic. Instead of explaining exactly how I have my router set up I'll just show you..

[IMG]http://img297.imageshack.us/img297/8050/screenshotfq2.jpg[/IMG]

In BitTornado I have the Port Range set as follows..

From: 10000
To:     10010

Randomize is checked. Encryption is off (as the options to enable it are disabled).


Now, in my limited experience, it seems to me as if I've opened a ten port wide hole in my network that would allow any traffic to or from my system on ports 10000, 10001, 10002, 10003, 10004, 10005, 10006, 10007, 10008, 10009 and 10010 via TCP or UDP. And it also seems as if I've set BitTornado to properly take advantage of this. But the status indicator is always yellow. So, have I gotten this wrong?

---

### Post by DavidGX on 2007-12-20
Going to sleep so.. up. Even if I'm doing this correctly I'd like confirmation of that, have never been 100% sure that I've got things right with this. I thought maybe the applications tab might work but the firewall tab seems to cover pretty much everything so.. bah.

*falls over*

---

### Post by DavidGX on 2007-12-21
No ideas?

---

### Post by DavidGX on 2007-12-22
=/

---

### Post by DavidGX on 2007-12-22
No one here has this router or knows if I'm doing this right or not?

---

### Post by DavidGX on 2007-12-22
...

---

### Post by DavidGX on 2007-12-24
Up we go...

---

### Post by koala114 on 2007-12-24
Well, to open the port BT used is in the Virtual Server page
Just click Virtual Server, enter into the page than add the IP address your PC bounded at the right of Private IP, Protocol is Both.

add the port both TcpIP and UDP

check on the Always and Apply. 
Have fun~

---

### Post by DavidGX on 2007-12-24
> **koala114 said:**
> Well, to open the port BT used is in the Virtual Server page
Just click Virtual Server, enter into the page than add the IP address your PC bounded at the right of Private IP, Protocol is Both.

add the port both TcpIP and UDP

check on the Always and Apply. 
Have fun~

I'll try that, thanks. I thought the firewall tab was pretty much a univseral thing for any kind of traffic coming in or going out. That's been my only issue, knowing when to use the firewall tab, applications tab and virtual server tab for different things.

---

