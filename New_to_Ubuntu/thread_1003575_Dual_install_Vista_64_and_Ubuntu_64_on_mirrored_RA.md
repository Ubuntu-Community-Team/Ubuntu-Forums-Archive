---
title: "Dual install Vista 64 and Ubuntu 64 on mirrored RAID ... Ubuntu missing..."
date: 2008-12-06
forum: New to Ubuntu
---

### Post by pablolie on 2008-12-06
Obviously I did not install something the right way...

I used the alternate 8.10 CD because it will (unike the standard CD) discover the mirrored RAID drive and the partition I had ready for Ubuntu. Installation works. But then there's a hitch when it comes to the final dialogue around Grub instalation. I want to use EasyBCD as an OS selector. When trying to follow this piece of advice
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

they say to *not* install Grub to the MBR. But rather to the bootsector. Well, there is no such choice in the Ubuntu instalation process, it is either MBR or nothing from what I saw on the alternate CD install. So I finish the installation with an incomplete Grub installation, I gather, and now Ubuntu will not start. When I select Ubuntu from my OS choice it simply stops with

grub>

I guess I need to reinstall, but I am truly worried about damaging Vista 64 if I go for the "install Grub on MBR" option...
Suggestions?

---

### Post by stefangr1 on 2008-12-12
> **pablolie said:**
> Obviously I did not install something the right way...

I used the alternate 8.10 CD because it will (unike the standard CD) discover the mirrored RAID drive and the partition I had ready for Ubuntu. Installation works. But then there's a hitch when it comes to the final dialogue around Grub instalation. I want to use EasyBCD as an OS selector. When trying to follow this piece of advice
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

they say to *not* install Grub to the MBR. But rather to the bootsector. Well, there is no such choice in the Ubuntu instalation process, it is either MBR or nothing from what I saw on the alternate CD install. So I finish the installation with an incomplete Grub installation, I gather, and now Ubuntu will not start. When I select Ubuntu from my OS choice it simply stops with

grub>

I guess I need to reinstall, but I am truly worried about damaging Vista 64 if I go for the "install Grub on MBR" option...
Suggestions?

The article says not to just install grub on the mbr, since "that would leave you with Linux and nothing else". However, I don't think thats really true. Grub will look for existing operating systems, and add an option to select them.

---

