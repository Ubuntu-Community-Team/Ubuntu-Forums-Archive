---
title: "Avahi exits on startup because of '.local' domain."
date: 2017-02-07
forum: Networking &amp; Wireless
---

### Post by twb999 on 2017-02-07
This problem appeared after a recent update of Xubuntu.  When the system starts, an error message appears saying that network discovery has been disabled because my computer has a '.local' domain and avahi does not allow this.  This seems strange, since the /etc/avahi/hosts file specifically shows how to set up '.local' static mappings.  However, there are no '.local'. mappings defined in the /etc/avahi/hosts file on my computer.  Anyone else see this and know how it can be fixed?  I have never seen this until a week or so ago and have been using xubuntu on this computer for several years.

---

### Post by wildmanne39 on 2017-02-07
I use to get this message a long time ago and it can be safely ignored, you can read the following link for information on this issue.
[https://ubuntuforums.org/showthread.php?t=2143237](https://ubuntuforums.org/showthread.php?t=2143237)

---

### Post by Morbius1 on 2017-02-07
THe first question I guess is do you use avahi?

If you do then run the following command:
```
host -t SOA local
```
It should come back with this:
> Host local not found: 3(NXDOMAIN)
If instead it comes back with something like this:
> local has SOA record localhost. xxxx.yyyy.zzz. 
Then someone at your ISP is drunk or they fired the only guy who knew how all this works.

You might consider changing your DNS servers from your ISP's to something like Google DNS 8.8.8.8

EDIT: You can verify that the google DNS servver works by running the host command again:
> morbius@mw1865:~$ host -t SOA local 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

Host local not found: 3(NXDOMAIN)

---

### Post by twb999 on 2017-12-08
Thank you Morbius.  This has been driving me nuts for a while.  Now, using the host command you showed,
I see that the AT&T's ISP setup is the problem for this.  I guess the only solution is to find another DNS server.

---

