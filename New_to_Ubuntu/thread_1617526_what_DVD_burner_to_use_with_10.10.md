---
title: "what DVD burner to use with 10.10?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by alpinescrambler on 2010-11-09
I used to use Braserro, and it worked great, but when I upgraded to 10.10 it stopped working.
 
:mad:
 
Any suggestions?
 
Any other software for copying DVDs with 10.10?  Any ways to make Braserro work with 10.10?
 
Thanks!

---

### Post by janpol on 2010-11-09
I use Brasero, and it works right out of the box in maverick. Try to open it from a terminal (just open a terminal, type **brasero **and hit enter) and see if it gives you any output and post it here.

Another great dvd burning tool is K3b, but Brasero should work fine in 10.10.

---

### Post by redbook4574 on 2010-11-09
> **alpinescrambler said:**
> I used to use Braserro, and it worked great, but when I upgraded to 10.10 it stopped working.
 
:mad:
 
Any suggestions?
 
Any other software for copying DVDs with 10.10?  Any ways to make Braserro work with 10.10?
 
Thanks!

My personal favourite is K3b, K9copy to copy DVD's (for backup purposes only ofcourse).

---

### Post by sidzen on 2010-11-09
> **janpol said:**
> I use Brasero, and it works right out of the box in maverick. Try to open it from a terminal (just open a terminal, type **brasero **and hit enter) and see if it gives you any output and post it here.

Another great dvd burning tool is K3b, but Brasero should work fine in 10.10.

*****************************************************************
XXXXX@my-desktop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-----------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'HL-DT-ST' 'BD-RE  UH10LS20'
-----------------------------------------------------------------


XXXXX@my-desktop:~$ wodim -sao dev=/dev/scd0 speed=4 -eject absolute/path/to/file.iso

*****************************************************************

The above is an example of how to use wodim to burn an ISO.  This is from the command line in terminal, of course.  Default speed of burner varies, but state no more than speed=8 to be safe.

One can always fall back on this in Debian-based distros.  For others, one must use *cdrecord*
------------------------------------------------------------------

edit:
Otherwise use K3B, but dependencies list is large (*i*.*e*. KDE core)
And, if you are going to install K3b, you may as well get K9copy

sudo apt-get -f install k3b && sudo apt-get build-dep k9copy

then

sudo apt-get install k9copy

worked for me

-----------------------------
The real power of linux lies in the command line!

---

### Post by amjjawad on 2010-11-09
K3b.

---

### Post by alpinescrambler on 2010-11-09
> **janpol said:**
> 

 Try to open it from a terminal (just open a terminal, type **brasero **and hit enter) and see if it gives you any output and post it here.




** (brasero:12538): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory

---

### Post by ezsit on 2010-11-09
I too have dumped Brasero in 10.10. Brasero produces only corrupted coasters for me in Maverick. I installed GnomeBaker and Xfburn and both work very well for me in 10.10.

---

### Post by janpol on 2010-11-10
> **alpinescrambler said:**
> ** (brasero:12538): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory
Does **/usr/share/brasero/logo.png** exist?

Try to remove brasero, and then install it again. If it's still not working, download the tarball from [http://projects.gnome.org/brasero/]("http://projects.gnome.org/brasero/") and get the missing file from there.

Also, I saw a similar thread were people recommended to use **gnomebaker**. I have never used it so I can't recommend it, but you could give it a shot.

Good luck!

---

