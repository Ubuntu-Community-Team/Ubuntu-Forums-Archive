---
title: "Rsync option &quot;stuck&quot;"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by mrebus on 2008-11-11
I use rsync to download from a server I have access to.  however when I 

matthew@MatthewPC:~/Videos$ rsync -avP [EMAIL="admin@*****.*****.com"]admin@*****.*****.com[/EMAIL]:temp/* ./
[EMAIL="admin@****.*****.com"]admin@****.*****.com[/EMAIL]'s password: 

insecure -e option not allowed.
This account is restricted by rssh.
Allowed commands: scp sftp rsync

If you believe this is in error, please contact your system administrator.

rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [receiver=3.0.3]
matthew@MatthewPC:~/Videos$ 


Why does it say -e option i didn't use -e option.  when I use another computer.  I don't get this.  what conf file do I look at. I tryed reinstalling rsync.  and nothing.  it looks like this happened after 8.10 update.

---

### Post by pdwerryhouse on 2008-11-11
The error about "-e" is coming from the remote end of your connection, due to restrictions that they have placed on the ssh key or server.

I suspect they might have misconfigured something.

---

### Post by mrebus on 2008-11-12
I am not allow to use the remote shell version(-e).  on another computer i have no problem on a different computer.

reading on the rsync FAQ page 

"
**is your shell clean**

  The "is your shell clean" message and the "protocol mismatch" message are usually caused by having some sort of program in your .cshrc, .profile, .bashrc or equivalent file that writes a message every time you connect using a remote-shell program (such as ssh or rsh).  Data written in this way corrupts the rsync data stream. rsync detects this at startup and produces those error messages.  However, if you are using rsync-daemon syntax (host::path or rsync://) without using a remote-shell program (no --rsh or -e option), there is not remote-shell program involved, and the problem is probably caused by an error on the daemon side (so check the daemon logs). 



How do I make my shell clean. if i am not allow remote shell.

---

### Post by vroetman on 2008-11-26
"insecure -e option not allowed" is a problem with your version of rsync (3.0.3) sending the -e option to the remote server

You can work-around by adding --protocol=29 to your rsync command, or upgrading rsync to version 3.0.4 or later.

---

