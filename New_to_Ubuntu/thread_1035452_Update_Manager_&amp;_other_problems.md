---
title: "Update Manager &amp; other problems"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Sound_B on 2009-01-09
Hey guys, I'm new here (and to Ubuntu) so please cut me some slack.

I'm running Hardy Heron, and after booting for the first time I tried to run update-manager.  However, after hitting the "install" button, it froze before it got to the administrator password prompt.
I tried ```
sudo update-manager
``` but that (along with any other sudo command) gave me:
```
sudo: unable to resolve host anthony-desktop
```

cat /etc/hosts give me:

```
127.0.0.1 localhost
127.0.1.1 anthony-desktop.anthony-desktop

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I found a thread of a similar problem, and on it's advice I tried to change the /etc/hosts file with 
```
gksudo gedit /etc/hosts
```

Which causes terminal to just freeze. One the advice on [http://ubuntuforums.org/showthread.php?t=783734]("this") thread, I tried to reboot in recovery mode so I can edit the file, but even that doesn't work on me.  When I try, it runs through a lot of lines before finally looping through the following:
```
[   ] ata2: soft resetting link
[   ] ata2.00: configured for UDMA/33
[   ] ata2: EH complete
[   ] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   ] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
[   ]          cbs 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00 
[   ]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   ] ata2.00: status: {DRDY}
[   ] ata2: soft resetting link
[   ] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[   ] ata2.00: revalidation failed (errno=-5)
[   ] ata2: failed to recover some devices, retrying in 5 secs
```
and it just keeps repeating. 

Any thoughts?

---

### Post by Lisa Y on 2009-01-10
Hi there,

Can you try this command in terminal...

```
 sudo apt-get update 
```

---

### Post by Biggy on 2009-01-10
> sudo aptitude update
and
> sudo aptitude safe-upgrade

---

