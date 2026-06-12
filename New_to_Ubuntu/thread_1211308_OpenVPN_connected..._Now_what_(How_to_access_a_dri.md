---
title: "OpenVPN connected... Now what? (How to access a drive)"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-07-12
I want my wife to be able to use her laptop to access a specific directory (say, /home/paddy/ourdata) on my machine, even when she's travelling.

I installed OpenVPN and followed [the instructions]("http://openvpn.net/index.php/open-source/documentation/howto.html") -- successfully. My wife's machine successfully pings my machine.

But... now what?

How do I get my wife's machine to see my directory /home/paddy/ourdata?

My machine: Ubuntu Hardy 8.04
My wife's machine: Ubuntu Jaunty Remix 9.04

---

### Post by cariboo on 2009-07-12
If your wife can connect to your computer, then she should be able to use sftp to access files from nautilus. If she is running windows, give [winscp]("http://winscp.net/eng/index.php") a try.

---

### Post by Paddy Landau on 2009-07-12
> **cariboo907 said:**
> If your wife can connect to your computer, then she should be able to use sftp to access files from nautilus. If she is running windows, give [winscp]("http://winscp.net/eng/index.php") a try.
Thanks for the idea. Both computers are Ubuntu (see first post).

I should have explained myself more clearly; I'd like her machine to access my directory as a directory. That way, her program will access the data rather than having to transfer files using FTP.

Looking for answers, I think that NFS may be the solution. I will try it tomorrow, unless you have any easier or better ideas.

---

### Post by Paddy Landau on 2009-07-13
Well, I've tried NFS but without success.

Here's what I did on my machine:

[LIST]
[*]Created a directory /srv/access and gave read-write permission to all.
[*]Added a line to /etc/exports: "/srv/access *(rw,sync,no_root_squash)".
[*]Started NFS: "sudo /etc/init.d/nfs-kernel-server start".
[/LIST]
Here's what I did on my wife's machine:

[LIST]
[*]ping 10.8.0.1 (to double-check that I have OpenVPN access). It succeeded.
[*]Created a directory /mnt/access on her machine and gave read-write access to all.
[*]Tried to mount my directory on her machine. It gave the error message, "mount: wrong fs type, bad option, bad superblock on 10.8.0.1:/srv/access, missing codepage or helper program, or other error". I've tried the following commands:
[LIST]
[*]mount 10.8.0.1:/srv/access /mnt/access
[*]mount -t nfs 10.8.0.1:/srv/access /mnt/access
[/LIST]
 
[/LIST]
Now I'm stumped.

Can anyone help me here? Perhaps I have the wrong end of the stick, or perhaps there's a much easier way?

---

### Post by WakkiTabakki on 2009-07-13
Just checking... Is nfs-client installed on the wifes computer?

/N

---

### Post by Paddy Landau on 2009-07-13
> **WakkiTabakki said:**
> Just checking... Is nfs-client installed on the wifes computer?
Good question!

I've just installed nfs-common from Synaptic...

... And it works! (At least on my network. Now I have to take the machine to a Starbucks or whatever and test it there.)

Thanks very much.

---

