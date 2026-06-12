---
title: "ubuntu 9.04 resalution problem"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by mevan_snp on 2009-06-02
[SIZE="4"]i have totally new to linux. i have instlled 9.04 yester day , i have problme with resulation i can't increse resalution more that 800*600. can enyone help me?[/SIZE]

---

### Post by pspsampsp on 2009-06-02
could you please run  the comman "lspci" (no quotes) in terminal and post the output back here.

---

### Post by mal1958 on 2009-06-02
> **mevan_snp said:**
> [SIZE=4]i have totally new to linux. i have instlled 9.04 yester day , i have problme with resulation i can't increse resalution more that 800*600. can enyone help me?[/SIZE]


It would help us, help you, if you could tell us a bit about your system.


[LIST=1]
[*]Processor (Type, Model, speed)
[*]Memory (meg or gig)
[*]Video card used  and vid ram***  (somewhat important for this question)
[*]and what level of competence you have with Linux (again somewhat important here)
[/LIST]
  If you can answer these questions we might be able to help you.

Mike

---

### Post by mevan_snp on 2009-06-02
I'm using

AMD Athlon 2.4 GHz
4GB RAM
Nvidia 6100 on board vga 512 sharing from ram
using Gigabyte motherboard

i'm totally new to linux so plz expalin little bit more

---

### Post by pspsampsp on 2009-06-02
have you tried going into | system -> administration -> hardware drivers | and installing the nvidia drivers.  before you do that make sure you install all the updates | system -> administration -> Update Manager |

---

### Post by mal1958 on 2009-06-02
> **mevan_snp said:**
> I'm using

AMD Athlon 2.4 GHz
4GB RAM
Nvidia 6100 on board vga 512 sharing from ram
using Gigabyte motherboard

i'm totally new to linux so plz expalin little bit more


  OK, this gives us something to work with.  I would suggest that you follow pspsampsp's advice, and install the video drivers.  I know I had to.  That should get your system to work nicely with your vid card.  (FYI I have an Nvidia GeForce 6400 and installed the drivers, Now I can go upto 1600 x omething res).

Qoted from pspsampsp:
> have you tried going into | system -> administration -> hardware drivers | and installing the nvidia drivers. before you do that make sure you install all the updates | system -> administration -> Update Manager |

This should get you up and running with the drivers.  As a side effect you may have to use the Nvidia tool for setting your screen res.  If that is the case then here is a little trick that you can use.  


Quote from nandemonai (to me actually when I had a problem with default screen res.)
> hit alt-F2 to bring up a run prompt in Gnome and enter:

 	Code:
 	gksudo nvidia-settings 
You can only save the configuration as root. I could be way off but this seems to be a common problem for nvidia users.

I hope this helps you.

Mike

---

