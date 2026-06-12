---
title: "Pop-Up Message on Samba Login"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by i.wanna.corndog on 2008-03-26
Hey everyone,

I have a headless server running Ubuntu Server (Gutsy). I have Samba installed and have set up a number of user accounts for people on my local network to backup their files. What I'd like to do seems simple: send a popup message to each user when they login listing what types/sizes of files they are and are not allowed to upload to the server. All users are running Windows, so I'd think it should be simple, but I'm not sure. (I know that when I disable a user account, a message pops up telling the user that their account has been disabled, so something like that, but a customized message.)

Could anyone help me out? I'd really appreciate a hand!

Thanks!
Dan

---

### Post by Iowan on 2008-03-26
Sort of an MOTD-type message?

---

### Post by Eiríkr on 2008-03-26
Have a look at [this]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PREEXEC") smb.conf option.  It sounds like just what you need.  

Cheers,

Eiríkr

---

### Post by i.wanna.corndog on 2008-03-26
> **Iowan said:**
> Sort of an MOTD-type message?

That's exactly what I'm talking about. :) Any clue?

---

### Post by i.wanna.corndog on 2008-03-26
> **Eiríkr said:**
> Have a look at [this]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PREEXEC") smb.conf option.  It sounds like just what you need.  

Cheers,

Eiríkr

Thanks mate, that's exactly what I'm looking for! I'll check it out!

---

### Post by i.wanna.corndog on 2008-03-26
> **i.wanna.corndog said:**
> Thanks mate, that's exactly what I'm looking for! I'll check it out!

Well, now that I look at it, it would appear that the displayed message would only appear on other Ubuntu systems. :(

Any other ideas?

---

### Post by Eiríkr on 2008-03-26
Doh.  :shock:  Score -1 for reading comprehension -- you'd noted in your first post that this was for Windows clients.  My bad.

Take Two:  
Try [this one]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONSCRIPT") on for size.  Note the following from the man page:
> This option is only useful if Samba is set up as a logon server.

That sounds like maybe what you're doing, no?

Cheers,

Eiríkr

---

### Post by i.wanna.corndog on 2008-03-26
> **Eiríkr said:**
> Doh.  :shock:  Score -1 for reading comprehension -- you'd noted in your first post that this was for Windows clients.  My bad.

Take Two:  
Try [this one]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONSCRIPT") on for size.  Note the following from the man page:


That sounds like maybe what you're doing, no?

Cheers,

Eiríkr

Eiríkr,

No worries. Thanks so much for the help. This appears to be exactly what I'm looking for.

Dan

---

### Post by Eiríkr on 2008-03-26
Cheers, Dan.  Let us know how it goes.  :)

-- Eiríkr

---

