---
title: "Dislplay problems while installing"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by AlbinoGoudvis on 2009-02-26
When trying to install Ubuntu on my new laptop, the screen displays weird patterns of what should be a window.  
At first, everything looks fine.  The orange bar moves as it should, i get the language selection menu.
[http://farm4.static.flickr.com/3605/3312051408_76f84bde4e.jpg](http://farm4.static.flickr.com/3605/3312051408_76f84bde4e.jpg)
[http://farm4.static.flickr.com/3321/3311208907_2361f3da96.jpg](http://farm4.static.flickr.com/3321/3311208907_2361f3da96.jpg)

But then, right when the screen would change to the desktop, it displays distorted patterns of what should be appearing:
[http://farm4.static.flickr.com/3584/3312051414_d4885e58c6.jpg](http://farm4.static.flickr.com/3584/3312051414_d4885e58c6.jpg)
[http://farm4.static.flickr.com/3503/3312051422_a9d672f840.jpg](http://farm4.static.flickr.com/3503/3312051422_a9d672f840.jpg)
[http://farm4.static.flickr.com/3068/3312066280_9ec0ed4a2c.jpg](http://farm4.static.flickr.com/3068/3312066280_9ec0ed4a2c.jpg)
[http://farm4.static.flickr.com/3609/3312066324_5417573198.jpg](http://farm4.static.flickr.com/3609/3312066324_5417573198.jpg)

The patterns change when i move the mouse, or hit enter.

I thought it might be a problem with the ubuntu window manager; but while trying puppy linux, the exact same thing happened:
[http://farm4.static.flickr.com/3527/3311196143_150e7c2566.jpg](http://farm4.static.flickr.com/3527/3311196143_150e7c2566.jpg)
[http://farm4.static.flickr.com/3446/3311208897_7c0b0b8c5b.jpg](http://farm4.static.flickr.com/3446/3311208897_7c0b0b8c5b.jpg)

You can see a little piece of the bottom left menu button is showing.
So I got two linux distribution which I managed to install with xp in dual boot on other computers; and they both have the same problem on this laptop.  (I also checked the ubuntu disk: it was ok)  
But Vista works perfectly (I would much rather use ubuntu)
[http://farm4.static.flickr.com/3301/3312073860_89858abd51.jpg](http://farm4.static.flickr.com/3301/3312073860_89858abd51.jpg)

I'm guessing my screen and drivers are too complicated for linux. Or maybe a hardware defect?  I'm not the biggest expert so I'm clueless.  

Please help...

the system:
[http://www.laptopshop.be/product/64028/toshiba-satellite-u400-136-azerty.html#specificaties](http://www.laptopshop.be/product/64028/toshiba-satellite-u400-136-azerty.html#specificaties)

---

### Post by tarps87 on 2009-03-13
When running Puppy Linux did you try both xorg and xvesa modes?
Have you tried using 'safe graphics mode'? (f4 and select 'safe graphics mode' before you select try/install Ubuntu)
I doubt the driver it to 'complicated' of Linux, it may not be supported or it may be trying to use the wrong driver. Booting using the vesa driver should solve this.

---

