---
title: "How to get a Brother DCP-195c working over the internet?"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by exsencon on 2014-12-26
OK, I installed the new Ubuntu 14.10, and it is working, slowly and sluggishly, but it is working. 
Had big problems to get it connected wireless to my Desktop PC but solved.
Had big problems to get the samba working (as always) but solved more or less.
Now, in my old Ubuntu 10.10 I had no problem connecting to my WinXP printer wireless and in no time at all. But in this new Ubuntu 14.10,well...so much better but a simple wireless printer connection he can't find. Poor thing!
Now if anybody on this forum can explain me what I have to do to get it working I would be very gratefull.
I went to the Brothers site, downloaded the drivers dcp195clpr-1.1.3-1.386.deb and dcp195ccupswrapper-1.1.3-.1.386.deb without any problems (meaning no errors) and installed them, again no problems. The only thing I can do now is to connect the printer to my laptop via usb and that works of course (what a relief)!but how do I go about connecting the *****printer wireless to the Desktop?
My systems: Dell Dimension 520 Desktop, 2HDD, 3GBRAM, and yes the Brother DCP-195c connected to it with USB. 1HDD is WInXP, 2nd HDD has 12 linuxes all working very well.
Dell Inspiron Laptop HDD 120GB HDD, 2GBRAM and dualboot between Ubuntu 14.10 (I think I'will regret it) and WinXP.
Simple question: Has anybody any idea how I should this network printer get to work in Ubuntu? It did without any problems for 4 years in Ubuntu 10.10. It can't surely be that hard to get it working in 14.10 which is so much better?
Brother multifunctional DCP-195C

---

### Post by Mark_in_Hollywood on 2014-12-26
Did you use the Brother install program? You wrote you d/l'd and installed the packages. Brother, after a long while has written an installer. Did you use it? And in your post title you say: "... over the internet", by which I assume you mean via wifi, 'cause of the rest of your post, but I'm double checking you don't mean, for example, Google Cloud Print.

Also, there are a bunch of Pre-Requisites. See here:

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp585cw_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp585cw_all&os=128)

I have a MFC-240C and have to install some apparmor stuff. Or at least I did in the past.

Did you get the packages from this page at BrotherUSA?

[http://support.brother.com/g/b/producttop.aspx?c=eu_ot&lang=en&prod=dcp195c_all](http://support.brother.com/g/b/producttop.aspx?c=eu_ot&lang=en&prod=dcp195c_all)

I'm trying to find an easy solve 4 you, but gotta ask some questions along the way. Sorry I don't have an exact solution.

---

### Post by exsencon on 2014-12-27
Let me clarify: I would indeed have that printer working wireless. The printer is usb-connected to my desktop and I want it to print wireless from my laptop.
And yes, I used the Brother installer and then could install both dcp195clpr and dcp195ccupswrapper, it went fine-no errors reported. THe only thing I had to do was to make a directory in /var/spool/lpr which I did. 
For me it seems the thing just can't connect to the printer on my desktop. Now I used the same URI I had on my Ubuntu 10.10 (and that worked perfectly) so maybe I am using the wrong URI,I don't know.
One last thing: When I connect the printer directly to my laptop (usb) it works perfectly.It's the wireless that's giving me trouble.

---

### Post by exsencon on 2014-12-29
I did another test. Since I have a WinXP on my laptop as well,I booted that and then tried to wireless printing on my DCP-195C USB-connected to my Desktop-well no problem there. He printed whatever I wanted wireless, so the problem for me is that my brand-new Ubuntu 14.10 is not capable of finding a simple connection. Well, my old Ubuntu 10.10 could do it. So...

---

