---
title: "SSH connection"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by nickcollie2 on 2014-08-25
I have just moved from Ubuntu to Lubuntu

Connection to a remote server is very slow.  It takes approximately a minute to open a directory.

When I connect through terminal the connection is as fast as normal, in other words pretty instantaneous.    I am using gigolo to initiate the connection.  When I do this the connection speeds drop.

Not sure what other information might be required but will supply anything that might help.  I have not experienced this with Ubuntu.

Thanks for any help.

---

### Post by SeijiSensei on 2014-08-25
What if you just run "ssh hostname" at a terminal prompt?  Same issues?

If SSH takes a long time to start up, it's almost always a DNS problem.  Both machines want to run "forward" (name->IP) and "reverse" (IP->name) resolution for both ends of the connection.  The timeout period for these requests is quite long, like half a minute or more.   If you don't have a DNS server, add entries in each machine's /etc/hosts file with the IP of the machine at the other end.

---

### Post by nickcollie2 on 2014-08-25
thanks a lot for you time.  I suspected a DNS issue.  

The answer is that from terminal prompt as mentioned the connection is fast.  And as a work around the connection using Thunar is fast.  It is just the connection from the default file manager that is painfully slow.  So,  really,  I would guess that it is more than simple DNS issues.  But I will certainly give your suggestion a go :-) 

And actually the initial connection is not so much of a problem.  Subsequent navigation through the directory structure is more of a problem.  Once connected,  waiting a minute or two for a directory listing is just agonising ...

Thanks again

---

### Post by SeijiSensei on 2014-08-25
If connecting from the command prompt is quick, it's not a DNS problem.

I've installed Dolphin as my file manager in Lubuntu when I last used it.  You'll get a lot of KDE dependencies along the way, but on any modern machine with a decently large hard drive that's not a big deal. Dolphin supports the "fish" protocol which uses SFTP to connect to remote shares on machines that support SSH connections.  You can just enter "fish://user@server/" then navigate around the remote file system.  

Usually I just export the file systems with NFS and mount them on my client.

---

### Post by slickymaster on 2014-08-25
Moved to the **Networking & Wireless** sub-forum.

---

### Post by nickcollie2 on 2014-08-25
OK thanks.  

Using thunar seems like a perfectly fine work around too.  Or anyway it does what I need and I'll play with making it fully default at some point when I run out of other things to do!  But dolphin looks interesting.

Thanks for your time.

---

### Post by nickcollie2 on 2014-09-12
As a final note to this.  In lubuntu using gigolo works fine.  But once the connection is made one can create a shortcut in Thunar to the server.  In future, clicking the link will open the connection ( and request login credentials ).  That seems to operate faster than using gigolo to create the connection and then using Thunar.  Why?  Got no idea.

---

