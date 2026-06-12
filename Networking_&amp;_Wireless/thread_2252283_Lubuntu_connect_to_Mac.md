---
title: "Lubuntu connect to Mac"
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by Peter_Matthew_Mier on 2014-11-10
I am looking for a way to temporarily connect my lubuntu computer to my Mac computer.

My mac computer is Mac os X Version 10.4.11

I need to connect to transfer over large amounts of data. Memory sticks will not work that well as my Mac is very slow at transferring data. I would prefer  to use remote connect. Is there a remote connect that can connect to a mac this old.

How do you do remote connect?

Need much help...

Sincerely,
Peter M. Mierau

---

### Post by TheFu on 2014-11-10
Use ssh.
and use rsync to transfer data.  These are generic UNIX tools and work on **every** platform.  Both are on the order of importance as the "wheel" and "fire" to humankind.  There are lots and lots and lots of guides for both of these.  rsync will use ssh by default for network transfers.

Setup the openssh-server on either side, then use the other, client-side, to push or pull the data.

Oh - and ssh is secure enough to use over the internet, though firewalls will get in the way and router ports will need to be open on the server-side (not the client).

---

### Post by Lars Noodén on 2014-11-10
Depending on the version of OS X you will find it something like this:

  ‘System Preferences’ -> ‘Internet & Networking’ -> ‘Sharing’ -> ‘Remote Login’

Checking the box there will turn on OpenSSH server and you can then log in or use rsync.

---

### Post by TheFu on 2014-11-11
> **Lars Noodén said:**
> Depending on the version of OS X you will find it something like this:

  ‘System Preferences’ -> ‘Internet & Networking’ -> ‘Sharing’ -> ‘Remote Login’

Checking the box there will turn on OpenSSH server and you can then log in or use rsync.

This is 1 thing I've always disliked about Apple. They don't use normal, expected, names for things the rest of the world has agreed on - ssh.

We should probably point out that there are many other solutions to this problem.  If the machine running the ssh-server is where the files are stored and already working then using sftp from the client machine might be easier.  See the ssh-server includes sftp, scp, and ssh services by default, all secure (with some reasonable caveats).

---

### Post by Lars Noodén on 2014-11-11
> **TheFu said:**
> This is 1 thing I've always disliked about Apple. They don't use normal, expected, names for things the rest of the world has agreed on - ssh.

We should probably point out that there are many other solutions to this problem.  If the machine running the ssh-server is where the files are stored and already working then using sftp from the client machine might be easier.  See the ssh-server includes sftp, scp, and ssh services by default, all secure (with some reasonable caveats).

Ah, but to add to the difficulty, OS X's file manager does not support SFTP, so if you connect that direction, it will be using shell-based utilities.  I prefer those myself, but they might not be familiar to less cross-platform folks.  I used to like OS X quite a bit, but it peaked with Tiger and is downright annoying now.  I still have some hardware in use but no OS X even as dualboot.  Also, the new hardware is not so good, IMHO, except for the screens.  

But, the point is a good one.  @Peter_Matthew_Mier you could log into your Ubuntu box probably just as easily from the OS X machine and do the rsync transfer that direction.

---

### Post by TheFu on 2014-11-11
Filezilla on OSX?  That has an sftp client.
From Windows, I use WinSCP - nice drag-n-drop interface. Of course, both of these are free.

Looks like the files are all on the Mac, not Linux machine.  I'd just push the files from the Mac to Linux.

---

### Post by Lars Noodén on 2014-11-11
> **TheFu said:**
> Filezilla on OSX?  That has an sftp client.
From Windows, I use WinSCP - nice drag-n-drop interface. Of course, both of these are free.

Looks like the files are all on the Mac, not Linux machine.  I'd just push the files from the Mac to Linux.

There are cyberduck, fugu and filezilla for OS X. The last one only is for 10.7 and later though.

---

### Post by Morbius1 on 2014-11-11
> I need to connect to transfer over large amounts of data.
You didn't specify the from and to so I'm going to asume you want to transfer data from OSX to Linux although it works exactly the same way with the same exact command in reverse:

On the mac open a terminal and run:
```
python -m SimpleHTTPServer
```
The output should be something like this:
> Serving HTTP on 0.0.0.0 port 8000
On the Linux machine open your favorite browser and point it to:
```
 [http://192.168.0.100:8000](http://192.168.0.100:8000)
```
[COLOR=#0000cd]*Change 192.168.0.100 to the correct ip address of the mac.*[/COLOR]

The contents of your "home" directory will be seen as downloadable objects.

Notes:

*** Directories are not downloadable they simply open to reveal what's inside. If you want to transfer an entire directory you will have to create an archive of it first.
[COLOR=#0000ff]In OSX just select the folder > right click > Compress and it creates a folder.zip file alongside the original folder.[/COLOR]

*** After transfer is complete kill the server: Control - C

---

### Post by Peter_Matthew_Mier on 2014-11-11
Thank you so much for your help. Very much appreciated.

Sincerely,
Peter M. Mierau

---

