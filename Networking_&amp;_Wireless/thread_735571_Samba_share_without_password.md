---
title: "Samba share without password"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by flip79 on 2008-03-25
Hello,

I have to excuse me for a question that was asked more than one time, but I didn't find an answer that worked for me.

This is my situation: a LAN with my desktop (Ubuntu), my girlfriend's Desktop (Win XP) and my notebook (Ubuntu). I want to share files from my desktop (a folder in my home directory) with the two other PCs in the network **without asking them a password**. And they all have to be **in the same workgroup**.

I tried many... MANY tutorials, but nothing worked. Can you suggest me a smb.conf that MUST work? Or a step-by-step procedure to have it work with Ubuntu GUI configuration?

I spent more than three hours on this problem without finding a solution, while on Windows I simply have to right-click a folder and activate sharing (I know, there are a lot of security issues with this, but... this is too much for me :confused: )

Thank you in advance!

---

### Post by Iowan on 2008-03-25
I presume you've tried the **security=share** option...

---

### Post by Eiríkr on 2008-03-26
Hey there Iowan, flip79 --

I've actually been working quite a lot on Samba issues lately ;), and it looks like the other key components here are the [font=courier]guest ok = yes[/font] share definition option, and the [font=courier]guest account[/font] global option.  

Looking more closely at [the man page section regarding share-level security]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITYEQUALSSHARE") (for when [font=courier]security = share[/font]), I noted the following:
> When clients connect to a share level security server they need not log onto the server with a valid username and password before attempting to connect to a shared resource (although modern clients such as Windows 95/98 and Windows NT will send a logon request with a username but no password when talking to a [font=courier]security = share[/font] server). Instead, the clients send authentication information (passwords) on a per-share basis, at the time they attempt to connect to that share.

Note that smbd *ALWAYS* uses a valid UNIX user to act on behalf of the client, even in [font=courier]security = share[/font] level security.

That last part is very important.  For no-authentication (i.e. no password, no login requested) connections, you need to use the [font=courier]guest ok = yes[/font] share definition option.  As described above, Samba ***must*** use a valid username for access, even with guest connections.  Unless otherwise specified by the [font=courier]guest account = [/font] option in the [font=courier][global][/font] section, this guest user account defaults to the "nobody" username.  This user is generally *very* restricted in what it can do, so chances are high that you (flip79) will want to specify a different user.  

Once you've done this in the smb.conf file, you'll also need to make sure that the user account you specify for guest access also has the needed permissions on the underlying filesystem (i.e. the files / directories being shared).  Have a look at [post=4496702]this post[/post] and scroll down to the "Multi-user" section for details on how to set this up.

HTH,

Eiríkr

---

