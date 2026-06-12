---
title: "I want to back up my linux install"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by nynoah on 2009-01-20
I lost my windows vista to a total virus wipe.  I want to somehow burn off my linux system as it is to a DVD to I can reinstall that.  I just don't want to wait the hours that needed to reconfigure my system to what I have now.  Is there a program that can make an iso of my system so I can just reinstall real quick?

---

### Post by Dumbestcrayon on 2009-01-20
The absolute best way I have found is


[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Once you tar up the files move them to another partition on its own.

(thats what I did)

More information on the link.

---

### Post by hyperyoda on 2009-01-20
> **nynoah said:**
> I lost my windows vista to a total virus wipe.  I want to somehow burn off my linux system as it is to a DVD to I can reinstall that.  I just don't want to wait the hours that needed to reconfigure my system to what I have now.  Is there a program that can make an iso of my system so I can just reinstall real quick?

Hello,

Do this:

$mkisofs -o /tmp/system.iso /

You can now burn this image file to CD/DVD.

If you get mkisofs not found error you need to do:

$ sudo apt-get install mkisofs

Zach

---

### Post by nynoah on 2009-01-20
Zach will this make a DVD that I can install like the stock Ubuntu install CD?  That is what I was hoping to get.  Kinda how people make a custom cd such as Ultimate edition Ubuntu

---

### Post by nynoah on 2009-01-20
When I looked for that program, it said it was a dummy transitional program that pointed to another program called Genisoimage.  Do you anything about that program.

---

### Post by Cypher on 2009-01-20
There are probably ways of making copies of your configuration and then should you need to re-install you can always bring back the configuration files to restore your system.

At the least, backing up your home directory will likely bring back most of your customization.

The other option is to use a cloning program like [Clonezilla]("http://www.clonezilla.org/") to make an exact copy of your HD to a separate device and then restore your intact image should anything happen to your installation..

---

### Post by geoffjay on 2009-01-20
full hard disk backup:
$ dd if=/dev/sdx of=/path/to/image.iso

restore:
$ dd if=/path/to/image.iso of=/dev/sdx

to back up the MBR:
$ dd if=/dev/sdx of=/path/to/mbr.iso count=1 bs=512

restore MBR:
$ dd if=/path/to/mbr.iso of=/dev/sdx

---

### Post by nynoah on 2009-01-20
If I back up my MBR can I use that to rewrite my grub.  I was also thinking about installing vista and then trying to bring my grub back from the dead.  But I was worried that since I had 2 different Kernals on here that that might be more complicated than I could handle.

---

### Post by geoffjay on 2009-01-20
The MBR contains the partition table and the master boot code, which (correct me if I'm wrong) contains grub. If not, restoring grub using a live/rescue cd is pretty painless. See [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/) for a good place to start.

---

### Post by theozzlives on 2009-01-20
Remastersys will make a live CD/DVD that installs like the original live CD.

---

