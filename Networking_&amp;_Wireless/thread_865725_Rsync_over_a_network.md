---
title: "Rsync over a network"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by Tom_ZeCat on 2008-07-20
I have a simple wired network with Ubuntu 8.04 on two PCs and Windows XP on another.  This post only concerns the Ubuntu machines since I'm trying to copy files from one Linux machine to another via rsync and do not need to copy to or from the Windows PC.  

I'm syncing a music collection.  I have 20 gig worth of MP3s that I'm  keeping on both PCs and playing with Amarok.  Rsync seems to be the ideal tool since it's wonderfully fast and has so many useful options.  I've found the perfect GUI to simplify things by storing my frequently used copy operations:  

[http://opbyte.it/]("http://opbyte.it/")

Rsync is the perfect tool ... almost.  Unfortunately, it doesn't support Samba shares.  The author of the GUI tool (Grsync) can't make his utility support Samba shares since rsync itself doesn't support them.  I did a web search and found his comments on how to get around this limitation:  

> if you want to use a windows share, you must mount it using linux filesystems. something like (as root):

smbmount //192.168.0.12/somedir/ /mnt/share

for example see "man mount" about smb or cifs options.
mounting like that will be transparent to all programs, not just gnome or kde ones. it's just a bit more tricky ;-)

So there's a way to do it, but I need to find out the IP address of each machine.  I've looked, and what I found is baffling.  The first machine is named: TOM-FASTJUKE.  On it I went to: 

System ===> Administration ===> Network

The Network Settings menu comes up.  I unlock it with my password.  I click on DNS Servers; it gives me this IP: 192.168.0.1.  I think it must be the IP for this machine, and then go to the other machine, TOMS-JUKEBOX, and do the same thing.  I get the same IP number and therefore know that it's not either machine's IP since it's not unique.  So I go back to the TOM-FASTJUKE machine and do the same thing as before, except this time I click on Hosts.  A list comes up with a column named IP Address and another named Aliases.  The first IP is 127.0.0.1 and its alias is localhost.  The next IP is 127.0.1.1, and its alias is tom-FastJuke.  Bingo, I think.  However, I go do the same thing on the other machine, and I get identical numbers.  The "127.0.1.1" IP is also listed by toms-JukeBox.  

?????????

Shouldn't toms-JukeBox have had a different IP number, the one I should use in Grsync to get around the lack of support for Samba shares?  

And, btw, here's a typical source and destination I would like to copy:

> Source: smb://tom-fastjuke/max120/Data%20Files/amarok/
Destination: /home/tom/.kde/share/apps/amarok/

 It works with Nautilus and Dolphin, but those programs don't have the speed or features that I'd like to use with rsync via the GUI, Grsync:

---

### Post by SpaceTeddy on 2008-07-21
let me get this straight. 

 - You have two linux boxes
 - you want to sync the content of one linux box to the other linux box ? 
 - the stuff you want to sync in on a samba share ? (which really, really does not matter at all... as far as i see it)

So, my question is - what *exactly* do you want to sync ? 
nevertheless, here is a link to a [COLOR="Blue"][tutorial]("http://troy.jdmz.net/rsnapshot/")[/COLOR] how to rsync between two computers which both have ssh and rsync installed.

One final note - as far as i know, rsync is a one sided sync only. Meaning you have a slave and a master. Changes on the master get propagated to the slave - changes on the slave get overwritten and forgotten... at least that is how i understood rsync.

hope it helps :)

---

### Post by Tom_ZeCat on 2008-07-21
It does help, and I very much appreciate the help.

---

