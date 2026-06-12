---
title: "[SOLVED] Desktop icon font overlapping"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by dosterror on 2009-01-07
Hi, im using ubuntu 8.10 and i have a problem with the desktop icon fonts (the text under the desktop icons).
when a file name gets too long, it should normally get abbreviated with a "..." at the end but in ubuntu gnomes desktop, the whole file name is displayed. this results in the icon texts overlapping with the icons beneath it. another problem is the width is too wide and it also overlaps with the icon texts next to it. is there a way to fix this?

---

### Post by iKonaK on 2009-01-07
Why would you keep such a file on your desktop, just rename it or change his location...:)

---

### Post by Michael.Godawski on 2009-01-07
perhaps...
right click Clean up by name
or is this not what you are looking for?

I know what you mean though with the overlapping filenames.

---

### Post by dosterror on 2009-01-07
the file names follows a certain naming scheme that i cant change. i guess i could move them somewhere else but id rather have em on the desktop where its viewable to everyone. so i was just wondering if this was possible with ubuntu

---

### Post by dosterror on 2009-01-07
hmm clean up by name just spaces out the icons and doesnt do anything about the name width. thanks though, i guess ill stick with this for now :)

---

### Post by Doneer on 2009-01-07
Hello! welcome to website; [www.shoes-trader.com](www.shoes-trader.com)

We are a trade and manufacturing company of brand name sport productions in China,Our main productions are:Jordan,Nike shoes;Lv,Prada bags;Jeans(evisu jeans.rmc short.);Sunglasses hat etc 

Here I list some of our products. 
Brand shoes: Nike, Adidas, Bape, BBC, Prada, LV, Timberland, Puma 
Brand clothes: Gucci, Bape, BBC, Rock&republic Seven, Red Monkeys, Diesel, LEE, D&G 
Brand bag: LOUIS VUITTON, GUCCI, CHANEL, CHRISTIAN DIOR, COACH 
Brand Watch: ROLEX, RADO, Omega, Cartier. 
Brand glasses: Chanel, Dior, Gucci, Louis Vuitton, Burberry, Police, Fendy. 

We insists that " SAFETY+ QUALITY+FAST DELIVERY+ GOOD PRICE = PERMANENT CUSTOMER".With high-standard quality, fastest delivery and satisfied service and reasonable price for you. 

Welcome to visit our website [www.shoes-trader.comIf](www.shoes-trader.comIf) you are 
interested in our production pls don't hesitate to contact us. 
Thank you! 
Best regards!

---

### Post by dosterror on 2009-01-07
I think ive found a solution in gconf-editor: apps > nautilus > icon-view, then check default_use_tighter_layout. this solves the horizontal overlap. the vertical overlap problem still remains since the align grid gets smaller, but using Clean up name helps.
ill play about with gconf-editor to see if i can fix this too.
Thanks!

---

### Post by m2xtreme on 2010-12-28
> **dosterror said:**
>  the vertical overlap problem still remains since the align grid gets smaller, but using Clean up name helps.
ill play about with gconf-editor to see if i can fix this too.

Good luck with the vertical grid spacing, it has been driving me nuts!  I've been searching forever for a solution to this and have found nothing!  I'll post back if i find anything but i'm not too hopeful ;)

---

