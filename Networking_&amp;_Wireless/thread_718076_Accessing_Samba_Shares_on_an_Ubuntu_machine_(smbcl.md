---
title: "Accessing Samba Shares on an Ubuntu machine (smbclient)"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by ratvomit on 2008-03-07
Okay, here's the deal:

2 Machines, one is a Gateway Mx6453 laptop, the other is an ASUS eeePC 4GB.  Both multiboot (XPsp2 and Ubuntu - Feisty on the Gateway, Gutsy installed to an SD card on the eeePC).  After setting up Samba shares, the eeePC booted in Windows can access SMB shares normally, prompting for credentials.  However, when booted in Ubuntu, problems arise:

I researched a bit, and tried to use smbclient to access the shares.  Both machines have Samba server/client and smbfs installed.  When attempting to access using smbclient, I'm informed the connection times out, and then receive NT_STATUS_ACCESS_DENIED.

I have the user setup and enabled on both machines, and the local permissions allow read/write access to others.

All of the following actions result in the NT_STATUS_ACCESS_DENIED:

smbclient \\\\hostname -L  (to list shares)
smbclient \\\\hostname\\sharename 
smbclient \\\\hostname\\sharename -U username
smbclient \\\\hostname\\sharename -U username -P password

Additionally, when not specifying a Username/Password, I am NOT prompted for credentials.

I think that about covers it.  Any help would be greatly appreciated.

---

### Post by Iowan on 2008-03-07
Mine works if I use```
smbclient -L //hostname
```

---

### Post by ratvomit on 2008-03-07
No luck, chief, but thanks for the reply.  However, using that context with credentials added in, results in "unable to open secrets database (/var/lib/samba/secrets.tdb)" - graphically browsing to that folder shows all those files/directories with the icon representing 'unreadable'.  I think removing and reinstalling Samba (on the client) may be in my future...

---

### Post by ratvomit on 2008-03-07
OK.  Workaround found.  Ideally I would've liked to do basic networking the oldschool way to save resources on the teeny eeepc (meager 600mhz processor w/1GB ram), but in the meantime, I've installed 'smb4k' - a graphical KDE network management tool.  Works just fine (for now).

---

### Post by Eiríkr on 2008-03-07
Two thoughts --
[list][*]By "have the user setup and enabled on both machines", do you mean via [font=courier]sudo smbpasswd -a USERNAME[/font]?
[*]Do you have guest access configured in your smb.conf file?[/list]

Cheers,

Eiríkr

---

### Post by ratvomit on 2008-03-07
Yes, I added them with smbpasswd -a *username* .

I didn't edit my smb.conf.  All the references to guest (other than the printer section of the file) are commented out.  I wouldn't know what to set them to, however - any suggestions I'm all ears.

---

### Post by Eiríkr on 2008-03-08
One synonym for guest access is [FONT="Courier New"]public = yes[/FONT].  

Personally, I think guest access is a terrible idea if you know who's going to be accessing your shares, *unless* it's not a problem if anyone at all reads / overwrites / deletes the files on your share.  Maybe I'm paranoid, but I always figure that an open door can sometimes be seen as an invitation...  Anyway, in my case, I use [FONT="Courier New"]security = user[/FONT] and username mapping where required, and then a carefully selected set of filesystem permissions for the shared folders, based on the usernames (and attendant groups) on the Samba server side.  

Incidentally, you say you haven't edited your smb.conf file -- do you mind posting it?  

Cheers,

Eiríkr

---

### Post by ratvomit on 2008-03-09
Well, I wouldn't mind posting my server's smb.conf except that I just reinstalled Ubuntu on the server machine (from Feisty to Gutsy).  However, it seems to work as it should now, using:

mount -t smbfs -o username=*username* //server/sharename /mnt/*mountpoint*

to mount/access shares.  Credentials are now asked for as they should be, and I can now thankfully avoid using the hefty KDE client.  Perhaps the default samba config differs between Feisty and Gutsy repos?  Regardless, if you could direct me to a handy guide to editing smb.conf for future reference, t'would be appreciated.

Though my current issue is solved, I'm still obviously familiarizing myself with GNU networking - I'll likely be trying to use NFS at some point, as I understand it performs faster than SMB as far as read/write times.

Thanks for your help!

---

### Post by Eiríkr on 2008-03-09
Glad to hear things are working.  I've read/heard numerous accounts of Feisty smb.conf files no longer working in Gutsy, so I suspect something substantial changed in the Samba package between the two OS releases.  

For Samba, your best bet is really to dig through the smb.conf man page.  There's a somewhat more readable online version [here]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  I'd recommend thinking up what kind of options you're interested in and then reading up on them.  

For sharing files among Unixy machines, I find NFS does work better than Samba.  There are a couple caveats to keep in mind, though (some of which I include more for other readers, as it seems you're happy with the CLI) --
[list][*]Samba has broadcasting built-in, so GUI clients can see the shares even if you don't know the IP address or hostname of the server.  NFS does not broadcast at all, so you need to know where to look.  One option for broadcasting NFS share availability is [Avahi]("http://avahi.org/"), the Linux version of Apple's Bonjour zeroconf implementation.  (This is handy for automounting Ubuntu-served NFS shares on a Mac client with a minimum of fuss, instructions [post=4387032]here[/post].)
[*]Nautilus (the default Ubuntu file browser) doesn't have any NFS browsing capability, whereas Konqueror does.  Nor does Nautilus have any Zeroconf browsing capability, whereas Konqueror does.  
[*]Samba sharing authentication is based on usernames.  NFS sharing authentication is based on user IDs.  The default NFS server package (nfs-kernel-server) in Ubuntu inexplicably has UID mapping capabilities *removed*.  I'm really not sure why; even the exports man page describes how mapping IDs is often desirable, with instructions on how to map.  Anyway. if you need UID / GID mapping, you'll need to install the nfs-user-server instead.  The two are mutually exclusive.  [/list]
UID / GID mapping is probably the biggest NFS bugaboo that I've seen here on the forums, as folks might find access permissions are not what they expect, depending on what their client-side UID equates to on the server machine, and what with the default Ubuntu NFS package not having any mapping.  It took me a while to figure things out myself.  But once you get it set up and running, it should do you pretty well.

And even if you're not setting up Avahi for anything, the first half of the post linked to above should be at least somewhat helpful in getting an NFS server configured.

Cheers,

Eiríkr

---

