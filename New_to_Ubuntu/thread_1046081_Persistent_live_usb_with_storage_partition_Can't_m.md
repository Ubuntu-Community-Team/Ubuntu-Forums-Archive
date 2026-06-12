---
title: "Persistent live usb with storage partition Can't manage to do it."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by underwhelmed on 2009-01-21
I've been experimenting with the usb stick way for a bit.  I've managed to get an installed version on a stick but windows can't see it so i can't transfer files via it, nor can i get the use of its entirity as I'd hoped to make a subsequent fat 32 partition and so left 4 gb 'spare', which of course you can't re partition without losing the lot, I think?

I've also made a bootable live usb but still can't make it have a windows friendly storage space.
there are loads of posts almost relating to this.
Has anyone actually made a persistent live usb with windows friendly storage.
I would be grateful for a steer in the right direction.
I've formatted the stick so many times that it'll probably melt soon lol!

Oh, and can you make an installed disk into a live disk retrospectively?

---

### Post by Archmage on 2009-01-21
I would suggest using the package usb-creator with a Live-CD-ISO. This way you should have everything that you need.

---

### Post by muteXe on 2009-01-21
I read somewhere that you should create an extra partition for storage (on your ubuntu memory stick), and make this the first partition on the stick. Windows might see it then.
Not tried it myself, but i've read a few pages on it.

---

### Post by theozzlives on 2009-01-21
If you have the 8.10 live CD, boot up with it and go to applications>accessories>terminal. type the following:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
then:
```
chmod +x u810.sh && sh u810.sh
```
Follow the instructions.

It'll create 2 partitions (fat32 & ext3) to access the ext3 install Ext2Fsd-0.46a, don't remember where to get it but you can google it.

---

### Post by muteXe on 2009-01-21
And how does that create an additional partition that windows can read?

---

### Post by theozzlives on 2009-01-21
it'll create a live, persistant, install USB... I edited my other post so you can read and write from Windows. Make sure you can boot USB.

---

### Post by muteXe on 2009-01-21
Ah yeah.  Nice one :)

---

### Post by C.S.Cameron on 2009-01-21
If installing to USB from setup on the the Live CD you can use manual partitioning to leave a FAT32 partition on the left side of the slide bar.
If using usb-creator, Windows can write to the first partition. You can access this in Ubuntu using gksu nautilus and looking in filesystem / cdrom.

---

### Post by underwhelmed on 2009-01-25
I tried the advice in post 4; it did divide the drive into 2 partitions, 1=Fat32, other ext3 BUT the live disk installed onto the 1st partition (Fat32) I had no choice as to where to install - I'd have expected the partition manager to have offerred me a choice, but no.  Therefore the 8.10 eneded up on the bit reserved for windows.  
i tried first to simply make the 2nd partition into fat32 - but windows wouldn't see that so
i tried to get round this by deleting the ext3 partition,( well the 2nd partition, currently in fat 32), shifting the fat32 (with 8.10 installed to the right and then creating a new fat32 to the left.  Result was - nothing seen by windows and 8.10 lost the will to boot.

IS there a trick to make windows see an existing partition?

I've done a fair bit with my installed stick and, as it won't simply copy onto another stick as back up am reluctant to mess it about and risk losing it all.  Incidentaly, why can't I copy it onto another stick?



Putting an o/s onto a usb stick is almost a good idea?

---

### Post by theozzlives on 2009-01-26
you forgot to google for Ext2Fsd-0.46a and install it into Windows so you could give the ext3 side access to Windows.

---

### Post by C.S.Cameron on 2009-01-27
> I've done a fair bit with my installed stick and, as it won't simply copy onto another stick as back up am reluctant to mess it about and risk losing it all. Incidentaly, why can't I copy it onto another stick?

```
sudo dd if=/dev/sda of=/dev/sdb
```

should clone your flash drive sda to a second flash drive sdb.

---

