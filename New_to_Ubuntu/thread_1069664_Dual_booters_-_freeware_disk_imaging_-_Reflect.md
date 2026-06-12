---
title: "Dual booters - freeware disk imaging - Reflect"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-14
Hi all - thought to give a heads up for non-tech individuals who are dual booting Windows and Ubuntu a (or another distro I suppose).

I just set up laptop with Vistax64 & U8.10 - wanted freeware app to replace my incompatible Acronis TI for Vista. Macrium Reflect has issued a free imaging package for 32 & 64 Windows here..

[http://www.macrium.com/ReflectFree.asp](http://www.macrium.com/ReflectFree.asp)

It will find and image your Linux partition from Windows. I have used it twice to restore my Vista install from a linux based rescue disk and it works. I haven't yet had to rescue U8.10...hehehe

The rescue wizard will ask if you want to restore MBR and bootloaders or just the image of the partition you saved. Gives you GUI of the partitions and files and double-checks your choices of image source and destinations.

You should be able to restore the Linux partition direct from Windows or via the rescue disk.

I looked at Partimage and PING and DD (dd?) but I'm not any good with commands and they are scary...especially with a single drive and multiple OS and logical partitions.

Supports BartPE, some other features. A week and I've seen no ill effects from it. By the by, it 'hot-images' the working Windows partition while running Windows so I can image Vista in the background while running Vista and image the inactive U8.10 partition immediately after. 

I like it. Your mileage may vary.

Cheers

dmc

PS - took 10 minutes to image 3GB U8.10 install on 10GB partition and compressed 50%. Took 20 odd minutes for Vista 30BG install on 60 GB partition. Vista recovery took about 30 minutes...

---

