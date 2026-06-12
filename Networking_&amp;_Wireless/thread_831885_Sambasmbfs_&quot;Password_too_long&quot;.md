---
title: "Samba/smbfs &quot;Password too long&quot;"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by dickohead on 2008-06-17
Hi all,

I have just finished putting hardy on my desktop (had it on my laptop for months now), and am unable to mount samba shares as I once did.

I am getting the error: "password too long" when either mounting from fstab, smbmount or mount -t smbfs.

Short of changing all my bloody network samba network passwords (major pain) to be shorter in length (current passwords are between 8 and 24 characters), how do I fix this?

Is it just me, or does this seem incredibly counter-intuitive given the security concerns with short passwords?

---

### Post by Anzan on 2008-06-17
I'm not certain or clear on this but there might be a recursive loop going on. Something to do with network manager/gvfs/samba copying something into itself. 

Try just resetting your authorizations (erasing and typing them in again).

---

### Post by jetsam on 2008-06-17
Smbfs support has gone away in Hardy, so even though you are specifying an smbfs type mount, what you are getting is a cifs type mount underneath.

I did some testing, and the password length limit for cifs mounts on Hardy seems to be 16 characters if you put the password directly in the fstab file or on the command line in a **mount** command.  I'm not sure if this is a bug or not: the limit is too restrictive.

I could work around this limit by using a .smbcredentials file in the fstab mount, though.

If you've never used a .smbcredentials file before, see Dmizer's how-to for cifs mounting here:
[Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534&highlight=credentials")
The part you need is the stuff under **Permanent Mount** in the first post.  

It's a bit of a pain, but I think you'll need to do this for every mount with a password longer than 16 characters.  On the plus side, it's better security to use a credentials file.  

You can use a single credentials file for more than one fstab mount if they use the same credentials (same username and password.)  

You have to use a different credentials file for each mount that has different credentials.  You just need to give each file a different name and reference it correctly in the fstab file.

---

### Post by dickohead on 2008-06-18
Perfect! That fixed it right up, cheers mate!

---

