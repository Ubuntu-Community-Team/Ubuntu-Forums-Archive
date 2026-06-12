---
title: "[SOLVED] Remote Access for Xubuntu"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by CaesarLike on 2008-03-22
Hi There,

Ok, so I have just installed Xubuntu 7.10 and find there is no remote access to it.

Am I correct in thinking that I need to install vnc4server to allow remote access, including for SSH etc?
Is there anything else I need to install or change to allow access the same as with Ubuntu?

---

### Post by Eiríkr on 2008-03-22
If all you need is ssh, then install ssh.  VNC is only needed for VNC.  

What exactly do you mean by "remote access"?  CLI?  GUI?  FTP?  NFS?  Samba?  SSH?  SFTP?  etc. etc...

---

### Post by CaesarLike on 2008-03-22
Hi Eiríkr, thanks for the reply.

I want to be able to access the pc to download files from it, say using scp.  I have an app called WinScp that I run on an xp box to access files remotely on the Ubuntu machine.

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

The pc running Ubuntu is an old pc, so using Xubuntu would be better for it.  This machine is mainly used for downloading torrents, hence the need to also remotely downlod from it, so I can access the downloded torrents remotely.  While having VNC might be usefull, for now I think just SSh, SCP, & SFTP would be sufficient.

---

### Post by Eiríkr on 2008-03-22
Okay, thank you for the more detailed description.  Within these operating parameters, I'd recommend two possible courses.  

SFTP can be used very easily once you install the [font=courier]ssh[/font] package, just by typing [font=courier]sftp://IP.ADD.RE.SS[/font] in the Nautilus location bar, replacing the caps with your Xubuntu machine's IP.  This has the added benefit of enabling normal CLI-based SSH access, which can be quite useful for remote server admin purposes.  

The other option is NFS, which (as far as I've read) has only limited overhead.  This requires that the numeric user and group IDs be either identical or mapped between server and client, or you get very weird permissions behaviour.  A while back, [post=4387032]I wrote a HOWTO for Lin -> Mac NFS sharing[/post], but it's applicable to Lin -> Lin as well.  

HTH,

Eiríkr

---

### Post by CaesarLike on 2008-03-22
Thanks Eiríkr,

I think that SSH is the way I will go for now.

If I also install VNC, will I get the setup dialog for remote access like Ubuntu has?

---

### Post by Eiríkr on 2008-03-22
No idea, I'm afraid, as I haven't installed VNC myself.  

Anyone else know?

Cheers,

Eiríkr

---

### Post by CaesarLike on 2008-03-23
OH well never mind about VNC, I will just install it and see what happens.

As for SSH, its installed and running perfectly :)

---

### Post by Eiríkr on 2008-03-23
Great!  :D  If that does it for this thread, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.

Cheers,

Eiríkr

---

