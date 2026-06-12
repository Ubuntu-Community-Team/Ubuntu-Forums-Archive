---
title: "data retrieval from infected Vista laptop"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by beginner's love on 2009-09-01
I have a Sony Vaio laptop with Vista ultimate, the problem is:
- first, I forgot the administrator account password;
- and later on, it seems that my laptop has been infected by a virus, which was detected and put in quarantaine (instead of being suppresed, my mistake) and when I closed the computer, the laptop said updates being installed (which I think was in fact the virus). When I tried to acces my laptop again the next day, it did not recognized my user account password preventing me to access my laptop 

I want first to retrieve my data from the laptop before adressing the virus issue and the lost administrator password issue

So I tried a live Ubuntu CD for Vista but it does not see my windows partition. What should I do next????

Help please:confused:

---

### Post by egalvan on 2009-09-01
> **beginner's love said:**
> 

So I tried a live Ubuntu CD for Vista but it does not see my windows partition. What should I do next????

:confused:

Well, I'm also confused...
The LiveCDs I have used have been able to see NTFS partitions...

Ubuntu LiveCD (Hardy, Intrepid, Jaunty)
PartedMagic LiveCD (several versions)

All worked.

---

### Post by LewRockwell on 2009-09-01
> **egalvan said:**
> Well, I'm also confused...
The LiveCDs I have used have been able to see NTFS partitions...

Ubuntu LiveCD (Hardy, Intrepid, Jaunty)
PartedMagic LiveCD (several versions)

All worked.

It's possible the partition information MBR/EFI(whatever windoze is using with vistaplague) has been corrupted

in which case Ubuntu isn't going to "see" it/them

.

---

### Post by egalvan on 2009-09-01
> **LewRockwell said:**
> It's possible the partition information MBR/EFI(whatever windoze is using with vistaplague) has been corrupted

in which case Ubuntu isn't going to "see" it/them

.

I've never had a drive so munged up (software-wise) that *nix refused to 'see' it... :)
Which is one reason I use *nix-oriented software in fixing software/hardware problems. :)

Bad hardware is of course another kettle of fish.

---

### Post by LewRockwell on 2009-09-01
in any case, if OP isn't comfortable with investigating the ease of hard drive removal and replacement(saving the original for forensic data retrieval later) then an external hard drive will be necessary(and also checking the BIOS to make sure the machine is booting from USB first, optical drive second, and internal hard drive third)

we've repeatedly encouraged others to purchase one of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

[http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

as it is useful for the various types of hard drives and also optical drives as well!

.

---

### Post by LewRockwell on 2009-09-01
> **egalvan said:**
> I've never had a drive so munged up (software-wise) that *nix refused to 'see' it... :)
Which is one reason I use *nix-oriented software in fixing software/hardware problems. :)

Bad hardware is of course another kettle of fish.

probably this:```
sudo fdisk -l
```would show the drive and possibly the goofed up partition(s) information

.

---

### Post by egalvan on 2009-09-01
> **LewRockwell said:**
> 
we've repeatedly **encouraged others to purchase one of these**:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

[http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter)

as it is useful for the various types of hard drives and also optical drives as well!
.

Absolutley...

And Newegg also has these, which i have used...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_sp=DailyDeal-_-12-156-102-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_sp=DailyDeal-_-12-156-102-_-Product)

---

### Post by LewRockwell on 2009-09-01
> **egalvan said:**
> Absolutely...

And Newegg also has these, which i have used...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_sp=DailyDeal-_-12-156-102-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_sp=DailyDeal-_-12-156-102-_-Product)

looks very similar to the coolmax unit(probably made by the same people and just sold via different companies)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

looks like both of these units have a design flaw as Newegg reviewers report BOTH of these units are frying equipment
.

---

### Post by beginner's love on 2009-09-08
> **LewRockwell said:**
> It's possible the partition information MBR/EFI(whatever windoze is using with vistaplague) has been corrupted

in which case Ubuntu isn't going to "see" it/them

.
Hi Lew, if the MBR/EFI is corrupted what can be done? 
and how to know first of all is MBR/EFI is corrupted or not???
Richard

---

### Post by beginner's love on 2009-09-08
> **LewRockwell said:**
> probably this:```
sudo fdisk -l
```would show the drive and possibly the goofed up partition(s) information

.

Hi,
I tried with a friend to retrieve the windows Vista partition using live CD Ubuntu but this is what happened...
- I dont see the windows partition initially but after some obscure commands on the terminal written by my friend we detect a partition NTFS in dev/sda2
- we try to mount it but there a message like this:
a NTFS signature is missing. Failed to mount dev/sda2: Invalid argument. The device doesnt have a valid NTFS. May be you selected the wrong device ? or the whole disk instead of a partition...
:confused::confused::confused: :guitar:

---

### Post by LewRockwell on 2009-09-08
boot up a Puppy Linux LiveCD and see what you can do with it(we have had better luck with puppy versus ubuntu for data recovery)

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

.

---

### Post by LewRockwell on 2009-09-08
we'd rescue the valuable data and then just do a fresh install of whatever you're going to use

we're still boycotting the purchase and usage of Sony products and don't see that changing...ever

.

---

### Post by beginner's love on 2009-09-10
I will try to make a live CD from puppy linux and ask directions later on how to use it... thanks for your help!

---

### Post by LewRockwell on 2009-09-11
just some additional information that might be helpful to someone visiting this thread:

[http://ubuntuforums.org/showthread.php?t=1263773](http://ubuntuforums.org/showthread.php?t=1263773)

.

---

