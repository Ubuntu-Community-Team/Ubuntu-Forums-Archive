---
title: "1TB External Hard Drive support?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-29
Hey everyone,

I am thinking about buying a 1tb hdd so i can finally have all of the storage space that i need. I was wondering (as a relatively new linux user), will any old external drive support files from ubuntu and will intrepid ibex be able to recognise any drive i plug in via USB? 

Thanks a bunch everyone in advance!

also as a side topic, does anyone have a 1tb hdd or know one that they would recomend in the range of $150? 

Thanks again!

EDIT: I decided it may be smart to link one im thinking about.... it doesnt specifically list linux as a supported system hence the confusion. Thanks again


[http://www.compusa.com/applications/searchtools/item-details.asp?EdpNo=4148839&SRCCODE=CNETCMPUSA&cm_mmc_o=2mHCjC2WHaCjCVqHCjCdwwp](http://www.compusa.com/applications/searchtools/item-details.asp?EdpNo=4148839&SRCCODE=CNETCMPUSA&cm_mmc_o=2mHCjC2WHaCjCVqHCjCdwwp)

---

### Post by hardyn on 2008-12-29
1) yes, files are files the drive does not care what they are; depending on file system there may be some file size limitations

2) yes, unless you want to use a really bizzare file system.


you must however have make sure that your external enclosure will support a 1tb drive; not all will.

---

### Post by Michael.Godawski on 2008-12-29
> **11010110 said:**
> Hey everyone,

I am thinking about buying a 1tb hdd so i can finally have all of the storage space that i need. I was wondering (as a relatively new linux user), will any old external drive support files from ubuntu and will intrepid ibex be able to recognise any drive i plug in via USB? 

Thanks a bunch everyone in advance!

also as a side topic, does anyone have a 1tb hdd or know one that they would recomend in the range of $150? 

Thanks again!

It should work without issues. 
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

I have seen some ext drivers which were also explicitly labeled as compatible with Linux. So perhaps you search for them.

---

### Post by 11010110 on 2008-12-29
thanks everyone for the quick replies! i think ill go with a nice seagate for the 5 year warranty in case i do have probelms lol.

---

### Post by hardyn on 2008-12-29
if you format the drive fat32 (yes it will be less efficient) you will have no cross platform compatibility issues; but you will be limited to max file size of 4gb.

---

### Post by ShadowfoxXXX on 2008-12-29
Yes.
/thread

---

### Post by ShadowfoxXXX on 2008-12-29
fat32 has a max functional size of 32 GB not 4. i have 3 8GB memory sticks that are fat32 and all work fine.
just use NTFS. My external HDD is

---

### Post by 11010110 on 2008-12-29
well i have read around and it seems that some people have a problem with the auto off feature on seagate products. Should i worry about this or not?

this is one of the drives that i am considering...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148332&nm_mc=OTC-pr1c3grabb3r&cm_mmc=OTC-pr1c3grabb3r-_-Hard+Drives+-+External-_-Seagate-_-22148332](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148332&nm_mc=OTC-pr1c3grabb3r&cm_mmc=OTC-pr1c3grabb3r-_-Hard+Drives+-+External-_-Seagate-_-22148332)

---

### Post by nhasian on 2008-12-29
I have this 1TB western digital usb2.0 drive and it works great with linux/xp/vista.  I even have the entire drive encrypted with truecrypt with NTFS partition.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136186](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136186)

---

### Post by Greyed on 2008-12-29
> **ShadowfoxXXX said:**
> fat32 has a max functional size of 32 GB not 4. i have 3 8GB memory sticks that are fat32 and all work fine.

He said **file** size, not partition size.

---

### Post by RichardLinx on 2008-12-29
I'm not very knowledgable in this area but I'll give you some input. I received a 120GB Maxtor portable hard drive for Christmas and It works perfectly on Ubuntu 8.10, It was detected instantly. My friend who owns a 1TB external hard drive similar to the one you are considering used it on my computer (Ubuntu) and it worked fine.

---

### Post by hardyn on 2008-12-29
> **ShadowfoxXXX said:**
> fat32 has a max functional size of 32 GB not 4. i have 3 8GB memory sticks that are fat32 and all work fine.
just use NTFS. My external HDD is

32GB is faux-limitation imposed MS to persuade those into NTFS... there is nothing about the specification of FAT32 that limits it to 32GB.  I have several external drives formatted FAT32, largest of which is 500GB

---

### Post by crjackson on 2008-12-29
Sorry... Disregard this post...

---

### Post by 11010110 on 2008-12-30
thanks for all of the replies everyone i ended up getting a deal on a western digital 1tb hdd, It should arrive within a few days. Lets hope all goes smoothly!

---

