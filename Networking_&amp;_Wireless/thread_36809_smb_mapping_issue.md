---
title: "smb mapping issue"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by andrewsawyer on 2005-05-24
Hiya,

Another question for the Ubuntu Gods if I may...

I have a Win2003 machine that contains all my movies/mp3's etc.  I can access this by  clicking 'Places >> Connect to Server >> Browse Network >> ...' or to get to the movies share for example, I can type smb://mediacentre/Movies in Firefox.  I would however like to map this.

I have created a dir called /mnt/sever, however I am getting the following message (password changed):

root@ubuntu:/ # mount -t smbfs  -o username="Andy",password=something //mediacentre/Movies  /mnt/server
cli_negprot: SMB signing is mandatory and we have disabled it.
9807: protocol negotiation failed
SMB connection failed
root@ubuntu:/ #

Can anyone pls help me with this?  It will make watching movies through gxine much easier, as currently I am having to drag and drop into the gxine window rather than 'File >> Open'.

Many thanks,

Andy

---

### Post by andrewsawyer on 2005-05-26
[QUOTE=][/QUOTE]
 No-one?

---

### Post by trunky on 2005-05-30
Andrew,

I ran into the exact same issue.    The problem is solved by using CIFS to mount SMB shares on W2K3.   Apparently SMB does not support strong signing which is now required by W2K3.

Try:

mount -t [COLOR=Red]**cifs**[/COLOR] -o username="Andy",password=something //mediacentre/Movies /mnt/server

Nigel.

---

### Post by andrewsawyer on 2005-05-30
Fantastic thank you.  Works like a charm!

---

### Post by ndhiet on 2005-06-08
trunky,

Thanks for the hint.
I've try to modify /etc/fstab for mounting my server folder automatically everytime i booting up, but not succesfull.
the entry I've add into /etc/fstab as follow:
//192.168.0.1/my_server_folder /mnt/server cifs username="ndhiet",password=something

can you help me on this??

[QUOTE=trunky]Andrew,

I ran into the exact same issue.    The problem is solved by using CIFS to mount SMB shares on W2K3.   Apparently SMB does not support strong signing which is now required by W2K3.

Try:

mount -t [COLOR=Red]**cifs**[/COLOR] -o username="Andy",password=something //mediacentre/Movies /mnt/server

Nigel.[/QUOTE]

---

