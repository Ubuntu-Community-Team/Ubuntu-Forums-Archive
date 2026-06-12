---
title: "no sudo"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by SkimWear on 2006-12-28
I know what the problem is...my hostname is out of whack...I need to reset it back to how it was or change it to what I orginally wanted to change it to.

The problem that really boggles my mind is that I can't sudo. I can't login as root. And I can't edit /etc/hostname or /etc/hosts because the permissions are set for root.

I can't vi either because that needs sudo.

the story is mainly: I tried to change my hostname, I changed it, I borked it somehow, and 3 days later my internet stopped working and I couldn't putty into my box from work...

When I got home I ran ifconfig to check what was up...everything seemed fine so I did a sudo dhclient and I got the error message...and everytime I tried running anything with sudo I got the same error message:

sudo: unable to get hostname via getbyhostname()

err so I try su - root
enter in my root password which I thought it was...
Authentication failed.

and now I'm seriously wondering if theres a gnome inside my box just screwing with me. :(

I've done a couple google searches and searched the forum with no luck. Anyone got any ideas?

edit: I'm using Dapper Drake

---

### Post by dbott67 on 2006-12-28
You can boot into 'safe mode terminal' or use the Live CD to get access.  Then fix the hosts file.

As for a gnome screwing with you, nope.  It happened to me before also when I was setting up a server... missed adding the computer name to the hosts file... et voila, no sudo! :)

-Dave

---

### Post by amo-ej1 on 2006-12-28
just to check if your post is correct. You post mentions sudo, while in you message you use su. If you are using sudo enter your _own_ password. If you are using su you have to enter the root password (as you said).

Anyhow if you've forgotten your root password, simply reboot the machine, boot it into single mode (append single to the list of kernel parameters). Make sure your filesystem is mounted read/writable and type passwd root and reset your root password. Once that's done you can continue to play around ;)

Edit: you should also be able to change your hostname file from that single mode prompt, it'll save you the hassle of locating a cd ;)

---

### Post by Rippey on 2006-12-28
have you tried editing /etc/hosts and /etc/hostname from a live cd?
if you can that might get things back the way they were.
if that doesn't do it for your password problem but you can edit your hosts & hostname files make an other post here.
:)

---

### Post by bapoumba on 2006-12-28
From a liveCD or from recovery mode ;)
In recovery mode, you'll be root, so be careful.

```
:~ # cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       [COLOR="Red"]<here should be your hostname>[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

```
~ $ cat /etc/hostname
[COLOR="Red"]<here should be your hostname>[/COLOR]

```

In recovery mode, you can edit those files with nano, a text editor. CTRL O to write the file, CTRL X to exit. The -B option makes a backup copy of your original file with ~ extension :
```
~# nano -B /path/file_to_edit
```

When you're done :
```
~# reboot
```

---

### Post by SkimWear on 2006-12-28
i actually found a bunch of google results after re-wording my query.

sudo getbyhostname usually finds the better hits.

these two links help if you're having the same problem:

[http://lists.netisland.net/archives/plug/plug-2005-09/msg00122.html](http://lists.netisland.net/archives/plug/plug-2005-09/msg00122.html)
[http://ubuntuforums.org/showthread.php?t=196607&page=2](http://ubuntuforums.org/showthread.php?t=196607&page=2)

err I still haven't tried anything on my box, still at work but I will use a live cd when I get back...or start failsafe mode.

I have like 389274cd's laying around my room with all different flavours of Ubuntu :)

---

