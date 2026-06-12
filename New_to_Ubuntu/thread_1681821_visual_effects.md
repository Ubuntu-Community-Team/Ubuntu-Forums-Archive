---
title: "visual effects"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-04
Hi there I am brand new to gnu/linux yes that right fresh fish. Just have installed umbuntu 10.10  on a 30 dollar computer that I bought today on craigslist 30 I know score right. Any way, I can´t for the life of me get my  visual effects to change :(  I looked into it a little and this is what I came up with so far.  I found out what kind of   graphic card I have  
$lspci | grep VGA
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) and 
then I went to look up if it was working 
glxinfo | grep direct
direct rendering: Yes   


So where do I go from here thank you so much for your time

---

### Post by ridin on 2011-02-04
have you tried 

compiz --replace & in the terminal?

---

### Post by josephmills on 2011-02-04
no I haven't, what will that do    

ok so I did it and this is what came up 
 compiz --replace
Blacklisted PCI ID 8086:2562 detected

Launching fallback window manager   
then tryed to change effects after to no luck any other suggestions

---

### Post by ridin on 2011-02-04
check out [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by josephmills on 2011-02-04
not going to take the chance a 30 dollar computer is a 30 computer thanks you guys

---

