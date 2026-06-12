---
title: "Broadcom 4312 rev 02 wont get it work"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Fasian on 2008-06-12
Hi, this is my first contribution to the site, must say thanks god that this kind of site exists.

However i've red quite a bit of different articles about getting my broadcom wireless networkcard to work with ubuntu. Iv used fw-cutter but it diddnt work with my bcmwl6.sys file. I tryed with ndiswrapper but it gives me the errormessage "file couldnt be found at line 219 in ndiswrapper-1.9 something" :(
My question is how i go from this, i have a wired network working so i can download files but i would really want getting the wireless working.
any ideas?

---

### Post by Dark_Stang on 2008-06-12
Try the wireless section in the HP Howto in my signature... Although I'm not 100% sure it will work on the 4312. Mind being a guinea pig?

Edit: If you're doing this on Hardy be sure to read the special notes at the end of the post.

---

### Post by Fasian on 2008-06-12
Yes i have ubuntu 8.04 kernel 2.6 something
the only problem im confronting is that when i use ndiswrapper on the .inf file it says cant find file at line 219 in ndiswrapper1.9
why is this happenin, do i have to cd to the desktop where the .inf file is?

---

### Post by Dark_Stang on 2008-06-13
Yes, you have to go to wherever the .inf file is otherwise ndiswrapper doesn't know where to go.

---

