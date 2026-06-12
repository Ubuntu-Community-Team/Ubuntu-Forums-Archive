---
title: "Another Duel Booting Question"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by tetherblood on 2009-10-25
Apologies in advance if this has been covered before, please feel free to just direct me elsewhere.

The Question!

I will be getting a new laptop soon and it will come without a preinstalled OS. I will have a copy of Windows 7 Ultimate Edition (32bit) and I am very keen to duel boot it with Ubuntu.

What would be (considering the laptop is a blank canvas) the best order with which to install them. Windows -> Ubuntu or vice versa?

I will no doubt be using Windows more often in the first few months but I am planning to make Ubuntu my primary OS when i feel more comfortable with it. 

I experiemented with Ubuntu about a year back and although I enjoyed it I was always drawn back to Windows because of certain software. WINE seems to have come on alot more since then and I have seen that I can have most of my favorites on Ubuntu now which makes me very excited :)

---

### Post by SkyNet2029 on 2009-10-25
Hi. The installation order is to do windows first (7 and any other variants included) followed by the linux of your choosing. Grub will overwrtie the mbr and allow for booting from your windows. 
Doen in the reverse order (windows after linux) does not allow for dual booting, as windows does not provide the functionality to boot other os's (other than windows).
Hope that helps.

---

### Post by tetherblood on 2009-10-25
Thanks that helps alot. I had to read up about Grub but it all makes a lot more sense to me now. Thanks alot :-D

---

### Post by mapes12 on 2009-10-26
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Bartender on 2009-10-26
Windows "can" be installed second, and some folks claim that it's a breeze to fix GRUB so that it works just fine, but it's easier (and less frightening!) to just stick to the path that's used by most folks and add Ubuntu to the existing Windows installation.

---

