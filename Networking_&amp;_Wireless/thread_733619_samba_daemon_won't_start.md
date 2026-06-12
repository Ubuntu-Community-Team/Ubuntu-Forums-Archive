---
title: "samba daemon won't start"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by hatdragon on 2008-03-24
I've been trying to get samba working for a long time, and I've been having no luck. I think I just realized that the samba daemon might not be starting up.

Here's what's happening.  (I'm running Hardy, btw)

```

hatdragon@guildenstern:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                [ OK ] 
hatdragon@guildenstern:~$ pgrep smbd
hatdragon@guildenstern:~$ sudo /etc/init.d/samba stop
* Stopping Samba daemons                                                       
start-stop-daemon: warning: failed to kill 11685: No such process
                                                                         [ OK ]

```

The pgrep at the end (I've also used "ps - e | grep smb" and looked through the process table) indicates that as far as I can tell the samba daemon isn't running. Any ideas how this can happen, or how can I fix it? I've already reinstalled samba a few times, but I don't know enough about samba or the daemon system to try anything else.

---

### Post by Eiríkr on 2008-03-24
I'd suggest looking into your smbd and nmbd logs, located at [font=courier]/var/log/samba/log.Xmbd[/font] (replace the "X" with "s" or "n" as appropriate, without the quotes).  These should give you some clue as to what's going on.  It might be a badly borked smb.conf file, or maybe something else.  If it's your conf file and you can't see how to fix it ([refer here for the online man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), most useful), post it here and we'll pitch in.  

If these logs provide no clues, I'd try fully removing the Samba packages, rebooting, reinstalling, and rebooting, then checking to see if the processes run properly.  I've had odd situations in the past where too much mucking about resulted in packages that wouldn't properly reinstall, and this was what I figured out would fix the problem.  

Cheers,

Eiríkr

---

### Post by hatdragon on 2008-03-24
Eiríkr, thanks for the post. In my log.smbd, I found that it was searching for a guest user, and commenting out "guest account = yes" seemed to make it work. It at least let the daemon start. I've only tested between two Ubuntu computers, so the real trial is whether my fiancée will able to connect to my computer (she runs OSX).

---

### Post by Eiríkr on 2008-03-24
Aha!  The global [font=courier]guest account[/font] option actually isn't a boolean -- it takes the name of the user account that should be used for guest connections.  Have a look [here at the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT").

Incidentally, if you're only sharing between Unixy computers and you don't need all the Windows-related cruft, I'd suggest you try NFS instead of Samba.  Samba's got lots of stuff that can get in the way of clean Unixy sharing.  I wrote a HOWTO a while back specifically for Lin -> Mac sharing over NFS, but it also works for Lin -> Lin.  [post=4387032]Have a look[/post], and let me know if you have any questions.  

Cheers,

Eiríkr

---

