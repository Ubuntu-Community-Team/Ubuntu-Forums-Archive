---
title: "NFS - Moving files bogs down all network apps."
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by notwen on 2008-03-26
I have a media server setup running NFS(for my laptop) and a uPnP server(for my Xbox 360).  I primarily download my media via my laptop and then transfer it(wirelessly) over to my media server via NFS.  However when I do this, most network related applications(FireFox, Filezilla) will grey out until the transfer is finished.  Depending on how big the transfer is this may take a while, is there anyway to prevent this from happening?  My laptop has the Intel 3945 wireless card running the iwl3945 module.  Any ideas and/or recommendations welcome.  =]

---

### Post by Eiríkr on 2008-03-26
I'm no NFS guru, but a quick look at [the man page]("http://linux.die.net/man/5/nfs") shows options like [font=courier]rsize[/font] and [font=courier]wsize[/font] that appear to be related to transfers.  I've also read somewhere in this Forum that forcing UDP might sometimes work better than TCP.  What options have you used in your fstab for mounting the NFS share?

Cheers,

Eiríkr

---

### Post by notwen on 2008-03-26
I mount my storage drives manually w/ the basic command as follows:

```
sudo mount 192.168.1.1XX:/media/sdaX /nfs/sdaX
```



How would I implement the wsize option to declare the maximum block sizeif I do not use fstab?

---

### Post by Eiríkr on 2008-03-26
Provided you've found a reasonable value for the parameter (something I'm personally not sure how to find), you'd specify it as an option at mount time using the [font=courier]-o[/font] flag, like so:
```
sudo mount -o wsize=XXXX 192.168.1.1XX:/media/sdaX /nfs/sdaX
```

HTH,

Eiríkr

PS -- Go Cinci!  :D  I did some housing restoration work in OTR years ago; how's that part of the city coming along?

---

### Post by notwen on 2008-03-26
Reading over this [site]("http://www.linuxselfhelp.com/HOWTO/NFS-HOWTO/performance.html") will help me determine my optimal block size, but if anything it looks as if I can set it to the nfsv3 block max of 32768 and it will use the max of my server/client machine's ability.  Thanks for all your input.  =]

Not really around Over the Rhine too much, never downtown too much either, I work more up in the Blue Ash/Mason areas.  They are planning to revamp the riverside of downtown Cinci though in the coming years.  =]

---

### Post by Eiríkr on 2008-03-26
Thanks for the link, that looks like a useful resource.  And cheers too about town.  Though I must admit I'd heard about those riverside revamping ideas back in '94 too, don't know if much has come of it...  ;)

Cheers,

Eiríkr

---

