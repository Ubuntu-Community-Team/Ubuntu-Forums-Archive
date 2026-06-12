---
title: "NFS:Internal error on bootup"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by BillDozer on 2008-05-19
I recently upgraded to 8.04 (both my server and clients) and have a problem with nfs when booting my clients.

I have three nfs shares to the same server and they all hang for about 30 seconds in the boot process, 1½ minute is a loooong time :-(. But after I log on, I have access to the shares. :-)

When I look in the message log (on the client) I can see the following message: 
```
May 19 17:13:03 optiplex kernel: [  106.969000] rpcbind: server 172.16.1.1 not responding, timed out
```

I cannot see a message on the server, but it can be I am looking in the wrong place.

---

### Post by BillDozer on 2008-05-22
No one has a clue about this??

---

### Post by Silby on 2008-05-22
Do your clients connect wireless or wired ? Are you using networkmanager or have you configured network settings on each client manually ? Do all clients show the exact same error ?

---

### Post by BillDozer on 2008-05-22
Thanks for the reply.

To answer your questions:
[LIST]
[*]All clients are wired, they get the IP from the server that should also serve the shares.
[*]I guess I use networkmanager, I have not configured clients manually
[*]Only ubuntu 8.04 clients have problems (I have three, and they all have the same errors), I have one 7.04 which does not seem to have this problem.
[*]The server is also 8.04
[/LIST]

I recall to have had a similair problem in 7.10 when connecting to 7.04, I solved it that time by upgrading my server to 7.10. But that does not sound like the solution now ;-)

---

### Post by [Psyduck] on 2008-06-26
I have exactly the same issue...someone must know how to fix this?

---

### Post by BillDozer on 2008-08-28
Update:

I still have the problem. In the mean time I also have installed a fresh 8.04 on another machine and on this machine there are no problems. That made me wonder, what is the difference between those machines...

The difference is that the two machines which have the error on bootup are upgrades from previous versions of Ubuntu, the "new" machine is a fresh install.

The problem is that the network hasn't been initialized when the client tries to connect to the nfs server. I know it has something to do with runlevels but am not completely sure what I have to do there.

---

### Post by redmk2 on 2008-08-28
How about trying static IP addressing to confirm your thoughts.  I hear there are differences between Gutsy and Hardy that cause "timing" problems on booting.  I still use Gutsy for that reason.

---

