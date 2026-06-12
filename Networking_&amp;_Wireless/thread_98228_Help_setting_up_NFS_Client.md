---
title: "Help setting up NFS Client"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by jbraum on 2005-12-02
I have setup NFS on my Mandrake machine and want to share the export with my laptop (Ubuntu).  How would I go about setting the client side up?

Thanks

---

### Post by emperor on 2005-12-02
[quote=jbraum]I have setup NFS on my Mandrake machine and want to share the export with my laptop (Ubuntu). How would I go about setting the client side up?Thanks[/quote] 
On Mandrake, create an NFS "/etc/exports" file:
[http://www.faqs.org/docs/linux_network/x-087-2-nfs.exports.html]("http://www.faqs.org/docs/linux_network/x-087-2-nfs.exports.html")

Also edit "hosts.allow" on Mandrake so your laptop can access Mandrake. 

Then on your laptop, you will need to install the nfs client. Then you should be able to mount the remote drive from Mandrake manually or directly via an fstab entry. However, the fstab auto mount will probably fail due to the late startup of the wireless link.

[http://www.die.net/doc/linux/man/man5/nfs.5.html]("http://www.die.net/doc/linux/man/man5/nfs.5.html")

On my wireless laptop, I have a fstab entry and then manually mount the nfs drive if necessary with say:

sudo mount /media/data

fstab entry: (all one line)
NFServer:/mnt/data    /media/data    nfs tcp,rsize=8192,wsize=8192,timeo=14,intr   0   0

where "NFServer" is the host name of the Mandrake NFS server.
where "/mnt/data" is the entry in exports that is being "exported".

---

### Post by jbraum on 2005-12-02
Ok would I need to edit the fstab on mandrake or the laptop (unbuntu)?  And where the fstab file located.

Thanks

---

### Post by jbraum on 2005-12-02
Ok I found the fstab file but do I make and entry in the laptop to mount or mandrake.  I have an idea but just need some confirmation.

---

### Post by emperor on 2005-12-02
[quote=jbraum]Ok I found the fstab file but do I make and entry in the laptop to mount or mandrake. I have an idea but just need some confirmation.[/quote]

laptop.

Mandrake is exporting the nfs mnt point to the laptop which needs to mount it under /media (recommended).

---

