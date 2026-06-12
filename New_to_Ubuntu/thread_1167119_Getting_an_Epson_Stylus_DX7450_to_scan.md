---
title: "Getting an Epson Stylus DX7450 to scan"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by annamoo on 2009-05-22
Hi,

The auto driver works for printing on my Epson Stylus DX7450 all-in-one, but I can't scan.

I found this website: [http://ubuntuforums.org/archive/index.php/t-631781.html](http://ubuntuforums.org/archive/index.php/t-631781.html) and have been trying it but am finding it much too complicated.  Could anyone help me?  I have downloaded the two drivers mentioned.  Can't get past the alien/compiley bit.

Thanks you in advance I am so stuck!

---

### Post by htrufan on 2010-08-31
I am experiencing the same thing with Ubuntu 10.4 + Epson Stylus SX115.  Prints, but doesn't scan.

---

### Post by robert shearer on 2010-08-31
> **htrufan said:**
> I am experiencing the same thing with Ubuntu 10.4 + Epson Stylus SX115.  Prints, but doesn't scan.

go to this page...
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

and scroll down to > **Scanner driver**.  Download for Epson Stylus NX115/SX110/SX115/TX110/TX111/TX112/TX113/TX115/TX117/TX119 **data package**
and select this option...
> deb package  	iscan-data_1.0.1-1_all.deb 	22,296 bytes 
then download it.

Now, scroll down further to..
> Download for Epson Stylus NX115/SX110/SX115/TX110/TX111/TX112/TX113/TX115/TX117/TX119 **Latest Version**

and select this option..
> DEB 32bit package [libltdl7] **(for Ubuntu 8.10 or later)  	**
iscan_2.25.0-1.ltdl7_i386.deb 	349,476 bytes 

and download that.

Then go to where you downloaded them and double click on the first one and it will install. You will have to give your password etc and be patient as it does it.

Then next double click on the second file you downloaded and install that. Takes a while, be patient.

Afterwards logout and back in ( or reboot if needed) and look for
'Image scan for linux" in Apps > Graphics.


(Note that if you are using Ubuntu Lucid 10.04 **64bit** then you would download the 64bit packages and not the 32bit versions.)

---

### Post by robert shearer on 2010-08-31
deleted double post.

---

### Post by htrufan on 2010-08-31
Thank you very much for the detail and quickness of the reply.  Now it works.

A note for others who may come to this post: when I clicked on the 
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
link, it redirected me to the home page.  From there I clicked English > Linux Drivers > The All-In-One graphic (per SX115)
Then the word "here" in this sentence:
A scanner utility [here]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo") is necessary to use the [B]scanner function
[/B]Scrolled down to "Form for download" and filled it out and clicked Next.  That should get you to the .../DL2.do page.
From there Robert's instructions take you the rest of the way.

---

