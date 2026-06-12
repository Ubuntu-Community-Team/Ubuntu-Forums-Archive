---
title: "[SOLVED] Appending hostnames and timestamps to folder names"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by wiseguyxp on 2008-10-14
I am trying to set up some bash scripts to upload my Java applications to a central server from different computers with SCP capabilities.  So far, the format of the simple bash script looks like this:
```
#! /bin/bash
scp -r /home/username/NetBeansProjects/* user@remotehost:java/*
```
This uploads my entire development directory to the central server, but I would like the folder names to look like "foldername-[hostname]-[timestamp]".

---

### Post by mssever on 2008-10-15
Your request is a bit ambiguous, but here's what I came up with:```
#! /bin/bash
hostname=user@remotehost
timestamp="$(date '+%s')" # Customize the date command to taste
scp -r "$HOME"/NetBeansProjects/* "$hostname:java-[$hostname]-[$timestamp]"
```

---

### Post by Ayuthia on 2008-10-15
If you are just looking for the hostname, you can also use $HOSTNAME.  The username is $USER.

If you are looking for more information about the formatting for the date command, you can use the man page or the date help:
```
man date
date --help
```

---

### Post by mssever on 2008-10-16
> **Ayuthia said:**
> If you are just looking for the hostname, you can also use $HOSTNAME.  The username is $USER.

If you are looking for more information about the formatting for the date command, you can use the man page or the date help:
```
man date
date --help
```
Note that $HOSTNAME refers to the local host, not the remote host.

---

### Post by wiseguyxp on 2008-10-17
I do labs on multiple computers for my CS classes.  For example, I have a netbeans project folder called "Lab5".  I want to send /home/user/NetBeansProjects/Lab5 to user@remotehost:java/ (java being the folder under the root directory that I store my java projects in).  When I access the remote host, I would like to see the timestamp and hostname in the folder name, ex: /java/Lab5-hostname-timestamp.

I am beginning to wonder if this is possible, as it would end up appending the current timestamp and hostname to anything in my projects directory, so directories would have multiple hostnames and timestamps attached to them after multiple transfers.  I also just realized that the only way to effectively do this would be to somehow download only the latest ones and remove the timestamp and hostname from them.  The entire goal of this was making sure I don't accidentally overwrite a completed project with an incomplete project from other machine.

edit: An even better idea would be to have a script that would scp the files in the remote directory to my local machine when I open up NetBeans, then transfer them to the remote server after I close NetBeans.  If there is a way to do this, I would prefer this option.

---

### Post by mssever on 2008-10-17
> **wiseguyxp said:**
> I do labs on multiple computers for my CS classes.  For example, I have a netbeans project folder called "Lab5".  I want to send /home/user/NetBeansProjects/Lab5 to user@remotehost:java/ (java being the folder under the root directory that I store my java projects in).  When I access the remote host, I would like to see the timestamp and hostname in the folder name, ex: /java/Lab5-hostname-timestamp
I guess I must not really understand what you're asking, because my previous suggestion will do what I think you're asking.

It sounds, though, like a better solution would be to only have a single place to keep your files. Using a source control system such as Bazaar is one option. Another option is to work directly on the server, if possible. For example, Nautilus can the the "Connect to server" option to present files on a remote SSH server as if they were local.

Finally, you could copy the files, work on them, then copy them back. Rsync or Unison would be good tools for this.

---

### Post by mssever on 2008-10-17
> **wiseguyxp said:**
> edit: An even better idea would be to have a script that would scp the files in the remote directory to my local machine when I open up NetBeans, then transfer them to the remote server after I close NetBeans.  If there is a way to do this, I would prefer this option.
A naïve approach: ```
#!/bin/bash

scp user@remotehost:java/whatever destination/directory
netbeans
scp destination/directory user@remotehost:java/whatever
```

---

### Post by wiseguyxp on 2008-10-21
would it execute the 2nd scp after netbeans closes? or does it execute it, then I just put in the password after I close netbeans?

---

### Post by mssever on 2008-10-21
> **wiseguyxp said:**
> would it execute the 2nd scp after netbeans closes? or does it execute it, then I just put in the password after I close netbeans?
That depends on how Netbeans works. I only used Netbeans for a short amount of time, so I don't remember exactly how it works. If it's well-behaved, then the second scp wouldn't run until after it closes. However, if it detaches from the terminal, then the second scp will run right away. And the password prompt might eventually time out.

---

