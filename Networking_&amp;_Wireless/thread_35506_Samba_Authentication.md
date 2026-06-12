---
title: "Samba Authentication"
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by deception on 2005-05-19
I have searched but didn't think any of the previous topics covered this, I could be wrong so I apologise in advance if I've mucked up. 

I have an ubuntu server install running on a network machine with samba set up. I need to grab files off of it regularly from my Ubuntu lappy (running gnome). The server has authentication set up, which from Windows presents to me a login dialog when I browse to the server in Windows Explorer. But in Nautilus, nothing is shown. Just an empty box as if the server contains no shares. 

Is it possible to mimic windows this way in Nautilus? Or will I have to use CLI ( which I do not mind doing ) ?

Many thanks in advance,
Matt

---

### Post by sfw5000 on 2005-05-19
Hi,

Samba is generally just for network windows machines to linux machines. If you want to network linux machines to linux machines, most people use NFS. On the server you "export" your NFS shares and then they will show up in nataulis when you access the server...

The NFS howto: [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by deception on 2005-05-19
Thanks for your reply. The reason I use Samba is because there is Windows boxes that need access to this server also.

---

### Post by sfw5000 on 2005-05-19
Hey -- you can have both Samba and NFS set up without any problems. You need Samba for the windows shares and NFS for the linux... NFS is extremely easy to set up. The howto is pretty long and exaustive, but the basics are very simple... skim through it and post any questions.

---

### Post by deception on 2005-05-19
OK thanks! I suppose it couldn't hurt to learn something new  :) 

Your help is much appreciated.

---

### Post by deception on 2005-05-19
I'm getting a timeout error but the troubleshooting faq doesn't help :(

rpcinfo -p servername 

shows the services running, Anything else i should try?

---

### Post by lilandra on 2005-05-26
[QUOTE=sfw5000]Hey -- you can have both Samba and NFS set up without any problems. You need Samba for the windows shares and NFS for the linux... NFS is extremely easy to set up. The howto is pretty long and exaustive, but the basics are very simple... skim through it and post any questions.[/QUOTE]
 Hi

I hope you don't mind me asking, but what would I need for Linux/Mac OS X shares?
Right now, I'm using samba to access my windows machines from Mac OS X and Linux.
I'm working on making Linux samba shares (I think I managed it...but I just have to follow instructions to add network users

But...as it is now, I can't create a proper share on Mac OS X to my other machines...and I was wondering if NFS would work between Linux and OS X?

Or should I wander over to the Mac/PPC support

*sigh*

---

