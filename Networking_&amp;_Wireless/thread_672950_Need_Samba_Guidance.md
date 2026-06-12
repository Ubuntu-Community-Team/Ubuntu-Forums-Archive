---
title: "Need Samba Guidance"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by crossedout on 2008-01-20
Hello folks,
Recently I added a laptop to my network.  I want to be able to share files with it obviously, but this particular laptop has Vista on it.  So after some investigating I decided I need Samba to share the files.

The Problem:
Samba installs fine but when I navigate to Places->Network->Windows Network there is nothing displayed.  I have installed & reinstalled samba several times as well as run through the configuration each time and each time I end up with nothing.
I am at a total loss on why and what may be causing that.  Frankly, I've read SO many posts, threads, install guides, etc. from UbuntuForums, Google, etc. that my head is spinning trying to solve this problem and to list all variations of what I've tried would be lunacy.
I had read somewhere that this situation may be a bug but I have been unable to confirm such a thing.

Technical Details:
Wired Network = Dual Boot Ubuntu 7.04/WinXP
Wireless Laptop = Vista
Ping = Successful
Firewall = Not an issue
Internet Access = Successful
Network Printer = Successful
Samba Install = 0 Errors
Samba Config = Successful, although unable to confirm since there is nothing to connect to
Win Network between XP & Vista = Successful
Win Network Vista to Ubuntu = Properly setup if Ubuntu were visible

Any help towards this problem is appreciated, the only solution that isn't an option is wiping out Vista completely (at least for now).  Thanks in advance.

-Xout

---

### Post by b0rka7a on 2008-01-20
Take a look at Stormbringer's tutorial:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by blueridgedog on 2008-01-20
The HOWTO mentioned above will get you going, remember that samba has to be configured and users have to be added to the samba user file.  Out of the box, there will be very little functionality without some setup.

---

### Post by crossedout on 2008-01-22
@ b0rka7a:
Thanks for the link.  I actually used that HowTo the first time I attempted to setup Samba.  However, I followed your advice anyhow and tried it again.  At first it appeared to be the same result.  Turns out I had to have more patience as both the Vista and Ubuntu side needed some time to acknowledge to setup or refresh or whatever.  I waited about 15-20min before both machines actually showed the connection visibly.

@blueridgedog:
Absolutely.  Configured and good to go, even added some hosts allow/deny to tighten it up.

Thanks,
-Xout

---

