---
title: "mount.nfs: Permission denied"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by ear9mrn on 2008-03-11
Hi,

I have an nfs mount on my Ubuntu 7.1 box which is working fine. The problem I have is if the machine the nfs drive is on goes down or is rebooted I cannot simply remount it on my Ubuntu box. I get the following error.

mount.nfs: Permission denied


Is there a way to resolve this. The only solution I have is a reboot my Ubuntu box!

Thanks,

Pete.

---

### Post by itix on 2008-03-11
Not NTFS??
post the output of ```
fdisk -l
```

---

### Post by Eiríkr on 2008-03-12
Nope, this definitely sounds like NFS, as in **_N_**etwork **_F_**ile **_S_**ystem, *the* main means on Unixy systems of setting up networked shares, originally developed by Sun and IBM way back in 1984.  Still going strong, and still quite useful.  I've personally found it very effective for sharing from Linux to Mac clients.  (More NFS history [here]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29") if you're interested.)

As an alternative to rebooting the NFS client machine that's having trouble connecting, try manually restarting the nfs-common service on the client:
```
sudo /etc/init.d/nfs-common restart
```
When attempting to mount, you might also be able to glean more of a clue as to what's wrong by using the [font=courier]mount.nfs[/font] command's [font=courier]-v[/font] flag for verbose messages.  I think you can have up to three of them in a row for the most verbosity.  

HTH,

Eiríkr

---

### Post by itix on 2008-03-12
I had no idea. Every day you learn something new. Thank you :)

---

### Post by Eiríkr on 2008-03-12
You're most welcome.  :)  I'm a translator myself, and am constantly having to learn new stuff in the process of doing my job.  Not a day goes by when I don't find myself running into something I had no clue about before.  Doh!  :shock:

And in case anyone reading this thread winds up wondering, "just how do I use NFS to share to MacOS clients?" -- [post=4387032]here's a bit of a HOWTO[/post].  :D

Cheers,

Eiríkr

---

### Post by ear9mrn on 2008-03-25
restarting the nfs-common daemon did not help. Neither did I get any more info using the -v flag.

I did get an extra peice of info when I did 

sudo umount -v /data
Could not find /data in mtab
umount: /data: device is busy

when I do an ls -lrt the mount point is highlited in red and looks like this.

?---------   ? ?    ?         ?                ? /data

Does this mean anything to anyone ?


Thanks,

Pete.

---

### Post by Eiríkr on 2008-03-25
I've seen this happen before when testing mount / umount, and saw it when trying to use the smbfs file type (which has been deprecated for some time now).  I saw the same "device is busy" errors, and the same question marks and red highlighting, and all I could find to fix the situation was a reboot, just as you describe.  I interpreted this to mean that the kernel's understanding of the filesystem was in trouble, and thus thought a reboot was actually a very good idea, but if anyone has any ideas how to fix or reset such filesystem problems *without* rebooting, I'm all ears.

Cheers,

Eiríkr

---

