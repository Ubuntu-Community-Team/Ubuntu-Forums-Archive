---
title: "ubuntu as nis client with Solaris"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by mathiraj on 2007-04-30
i've been using 6.06.1, 6.10 and recently 7.04 with the following setup.

My NIS and NFS servers are solaris. I configured Ubuntu as NIS/NFS client following this doc [http://lyre.mit.edu/~powell/debian-howto/nis.html](http://lyre.mit.edu/~powell/debian-howto/nis.html)

In addition, I also installed autofs and added the line "automount : nis" to the /etc/nsswitch.conf
My yp.conf points to the correct server.

I noticed 7.04 becomes really really slow with this configuration. I don't seem to recall any performance problems with 6.06.

If I stop nis and autofs ("/etc/init.d/nis stop" & "/etc/init.d/autofs stop") the system becomes responsive. But I need this to be nis client. If i start nis and autofs, the system just comes to its knees. It takes so much time just to login.

I've also verified that there is no network related problems. Other systems in similar configurations run just fine.

Has anyone else faced this? Any tips to fix this?

---

### Post by the_original_billq on 2007-05-02
Same setup, same symptoms.  Interesting to note, following an update to edgy on another workstation, k3b crawls when trying to burn a cd, but everything else seems fine.  Oh, and it *only* crawls if you interrupt the checksum process (which takes forever) and jump right into burning a disc.
The fiesty machine seems to have problems only after enabling NIS/autofs and tweaking nsswitch.conf, then it has issues pretty much across the board.
I need to go back to dapper, I guess:-(

-Bill

---

### Post by the_original_billq on 2007-05-02
I *hate* to followup my own post, but I'll make an exception.

I edited /etc/default/acpid and changed

MODULES="all"

to

MODULES="none"

Everything is FEISTY!!!

It works for me, your milage may vary.

-Bill

---

### Post by jefferybond on 2007-05-09
The above fix didn't work for me, and I had the exact same problem.

Actually, in my case it was nothing to do with NIS (even though I am using it), but the fact that I have an NFS mounted home directory. The problem was that the nfs-common package was not installed, and therefore NFS locking did not work.

Simply installing nfs-common and rebooting solved the issue for me.

Jeff

---

### Post by ethoms on 2008-01-10
Thanks mathiraj for your post which led me to getting my Solaris 10 nis users to work in Ubuntu. I tried my best go fully Solaris but it's just not ready for desktop computing yet, whereas Ubuntu is an awesome desktop environment.

I had a few problems getting automount to work, even after following the guide in your link and installing autofs but eventually solved it. Basicallly, Solaris nis maps are auto_master and auto_home by default, nis converts them to auto.master and auto.home but the syntax within auto_master will allow "/home auto_home" and works on Solaris clients but not linux clients. The solution is to replace the "_" with a "." in the map detail, I have renamed the files to auto.master and auto.home as well.

My next problem was permissions within Ubuntu, I couldn't get audio to work, neither would a terminal session open, window just opened and closes instantly. It seems that in Ubuntu there are access rights to features like cdrom, audio, lpadmin (printer administration), scanner, admin services etc. This is a good thing, makes me wonder how Solaris deals with these access rights, or maybe it doesn't. I'm glad that the access rights where given in the /etc/group file and not through RBAC, that's just because i'm new to unix and don't know RBAC yet. Anyway, to solve the problem I have added my nis users username to the appropriate lines in the /etc/group file on the Ubuntu client machine an dnow I have sound etc.

e.g. sample lines in /etc/group file:

adm:x:4:localuser,nisuser1,nisuser2
floppy:x:24:localuser,nisuser1,nisuser2
audio:x:29:localuser,nisuser1,nisuser2

My question now is, how do I add all nis users to these groups, to allow all nis users to use audio etc. I need a more dynamic method. I tried adding "+" instead of a username, hoping that it would imply all nis users, no luck there.

---

### Post by ethoms on 2008-01-10
Damn those emoticons!

CORRECTION to last post (ignore the quotes):

e.g. sample lines in /etc/group file:

"adm:4:localuser,nisuser1,nisuser2"
"floppy:24:localuser,nisuser1,nisuser2"
"audio:29:localuser,nisuser1,nisuser2"

---

### Post by ethoms on 2008-01-12
I think i was too hasty posting my last post, it hasn't solved all my nis client issues after all. Sound (audio) is now working, definitely due to adding username in /etc/group file, but I still can't get terminal to run, it closes immediately after opening, no error message. Also, cdroms will either not mount, or at least not show on desktop like the local users does. I can't try to diagnose what's going on because I can't get terminal to open. My solaris nis server is setup fine for Solaris clients, no problems logging in or accessing resources like sound, cdrom etc.

Has anybody got nis clients to work from a solaris nis server on Ubuntu 7.10 (Gutsy Gibbon). All the "How to..." articles I have read are minimal, I could do with some more depth, maybe a server-side guide as well.

---

### Post by fmagh on 2008-03-13
Hello

Have you solved your problem ?

I have the same, can't have audio on client with ubuntu 7.1 and solaris server, when I use NIS account.
If I put user on local group audio it's working. But I can't do that on all computer for all user. 

Regards

---

