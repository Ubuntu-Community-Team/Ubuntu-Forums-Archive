---
title: "Hp Printer Laser 1300 very slow to print from Vista"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-02
Any one else encounter this trouble? 

I have Ubuntu 8.10 as my file and print Hub. My HP Laserjet 1300 is connected to the ubuntu box and I have several computers networked to the Ubuntu box. 

I can print seamlessly from a Ubuntu Box or from XP or from windows 7 but just installed Vista on a couple boxes and they are all part of the same network but for some reason when printing from the new vista boxes using either MS Word or open office writer it is very slow to connect to printer and spool. about 5 min to print one doc and hangs the word processor in the mean time.

Any help is appreciated.

Also;
Using Samba and it is set as a share and everyone has rights to print from within the network.

Powel

---

### Post by powel212 on 2009-06-02
I think it might have something to do with the fact that vista is 64bit and my Ubuntu sever is 32bit. I have been getting an intermittent error saying there is a problem with the 64 bit to 32 bit clunking spooler.

So I am going to try it with 32 bit vista tomorrow and see if that makes any difference. 

I am thinking that the HP driver is not well equipped to handle what I am asking of it.

Powel

---

### Post by powel212 on 2009-06-03
Well it is better with 32bit vista but still very slow. I have 4 vista boxes networked to the ubuntu server. None of these four vista boxes are dealing with the print server well but if i print from one vista box to another vista box shared network printer, (the Ubuntu server), the transaction happens lightning fast. What the heck???

So now i have 3 vista x64 boxes sending their print jobs to the 32bit vista where the job is bounced to the ubuntu server and this seems to work flawlessly. But, why can't i just print directly to the ubuntu box???

Powel

---

### Post by MrWES on 2009-06-03
> **powel212 said:**
> Well it is better with 32bit vista but still very slow. I have 4 vista boxes networked to the ubuntu server. None of these four vista boxes are dealing with the print server well but if i print from one vista box to another vista box shared network printer, (the Ubuntu server), the transaction happens lightning fast. What the heck???

So now i have 3 vista x64 boxes sending their print jobs to the 32bit vista where the job is bounced to the ubuntu server and this seems to work flawlessly. But, why can't i just print directly to the ubuntu box???

Powel

Try changing the printing protocol from smb to ipp - internet printing protocol. I've preferred ipp over smb and it seems faster too.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

Bill

---

### Post by powel212 on 2009-06-03
Thank you.

I'll give it a try.

Powel

---

### Post by powel212 on 2009-06-04
I tried ipp// it was faster but still intolerably slow. Thanks for your suggestion. I am going to the store to see if I can get a print server Ethernet adapter to do the job.

Powel

---

### Post by feistybird on 2010-12-30
I've having the same problems with my HP-1200 and 1300 printers since Ubuntu 6.10,  finally I've found a solution, FYR. :

[http://ubuntuforums.org/showpost.php?p=9984757&postcount=2](http://ubuntuforums.org/showpost.php?p=9984757&postcount=2)

Just changed the driver to be **generic**, and then [COLOR="Red"]**PCL 5e Foomatic/hpijs-pcl5e **[/COLOR]

---

