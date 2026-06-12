---
title: "Newbie backup question"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by inigopete on 2011-02-21
Hi, I'm sorry if the answer to this can already be found elsewhere; I had a search but couldn't find what I was looking for.

I've got a netbook with an 8GB hard drive (SSD, and yes I know that's tiny but really that's all I need for my netbook). I would like to back it up to an 8GB USB stick that I've got. Ideally I'd like to make this USB stick bootable so that if there's any problem, I can boot from the USB and restore my HD without having to reconfigure anything.

Is there a simple way to do this?

I'd appreciate any help you guys could offer.  Thanks.

---

### Post by maqtanim on 2011-02-21
I think you can do that with the Remastersys.
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by seawolf167 on 2011-02-21
Its not exactly what you asked (since the backup image isn't bootable) - but here are my $.02

Burn a [clonezilla]("http://clonezilla.org/") cd or make a bootable usb of it, then have clonezilla backup (image the entire disk) to your 8 GB flash drive (you'll have the option to mount it when running through the clonezilla dialogs). Clonezilla only takes used space, so you won't have any issues storing it on a drive of the same size.

If anything ever goes wrong, simply boot off the clonezilla cd/usb, and tell it to restore from your flash drive (the backup is simply an image of your entire disk). Everything will restore and you won't be able to tell any difference from when you originally made the backup.

---

### Post by inigopete on 2011-02-23
Thanks seawolf167, that's a nice straightforward idea! maqtanim, I'll look into that one too.

Thanks both!

---

