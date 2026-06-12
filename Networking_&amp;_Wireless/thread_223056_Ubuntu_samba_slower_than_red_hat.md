---
title: "Ubuntu samba slower than red hat??"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by dgermann on 2006-07-25
Hi--

About 10 days ago I switched from a Red Hat 9.0 machine as my Samba server to Ubuntu. Ever since, things have been slow.

How do I mean, slow?

1st clue: previously, when I saved docs in OOo Writer, I would go ctrl-S and once every 4th or 5th time it would say it couldn't create a backup; now it is every time. So to save I have to go ctrl-S esc esc ctrl-S.

2nd clue: WinXP on login to the server times out before connecting the three drives it tries to connect--never before.

3rd clue: WinXp used to load directories instantly; now it takes 4-5 seconds.

There is some other weirdness too: when logged in to the server it reports the file owner and group as dean:1005. dean is the name of another user on this client machine, but rarely used. It should see it as doug:data, which is how the server sees it. 

Also it used to see the files as 
```
-rwxrwSrwt  1 root root 4.0K 2003-01-25 03:18 wgetrc
```

Now it sees them as
```
-rwxrwxrwx  1 dean data   99 1993-09-28 22:07 TEST.SDW
```


The new server: Ubuntu 6.06, Celeron D 2.53Ghz, one 200GB HDD, 6 months old.
The old server: RedHat 9.0, Celeron 2Ghz, one 80GB HDD with OS on it, one 120GB HDD with only data on it, at least 3 years old. Samba is at least that old.

So the question is, how can I speed up the Ubuntu samba? How would you troubleshoot this?

Some ideas I have not yet tried:

1. Remove all the commented lines from the smb.conf file.

2. Perhaps older versions of samba are just faster than the newer ones, and I should learn to live with it.

3. Perhaps there are some tweaks in samba that I need to learn about.

4. Copy over the old smb.conf file to the new system.

Where should I start? What is most likely to have a good payoff for time invested?

Thanks!

---

### Post by dgermann on 2006-07-30
Hi--

I checked the logs at /var/log/samba/smbd.log and have in there 
a long series of these messages:

====clip

[2006/07/25 17:36:14, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2006/07/25 17:36:14, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2006/07/25 19:12:17, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2006/07/25 19:12:17, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
====end clip

Does that provide a clue?

---

