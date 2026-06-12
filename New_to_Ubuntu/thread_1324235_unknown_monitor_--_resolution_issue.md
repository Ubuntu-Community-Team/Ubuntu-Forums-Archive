---
title: "unknown monitor -- resolution issue"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by estephens25 on 2009-11-12
Hi,
 
I'm new to the Linux world and recently installed Ubuntu 9.10. Everything is working fine except that the resolution is set to 800x600. I've been doing some research online and have found SEVERAL cases of this problem but so far I haven't had any luck with getting the resolution set to something higher. I have a 17" monitor so I'm just trying to bump the resolution to 1024x768. It appears that my problem is occurring because my monitor isn't getting detected. It's showing up as "Unknown Monitor". From everything I've read it seems like I have to modify the xorg.conf file -- but if I open that file mine is completely blank (or I should say that the file just doesn't exist as it doesn't show up if I search for it under the X11 directory). I've tried creating it and entering information into it but after a reboot it goes to the tty prompt and won't load into the GUI until I remove the xorg.conf file.
 
I have an Intel graphics card that appears to be properly detected by Ubuntu -- so again -- it looks like the problem is with the monitor not being detected.
 
The monitor is a Eizo FlexScan L767. Is there anyone that can tell me how to get this detected? Or how to properly create the xorg.conf file (if that's what I need to use)?
 
Thanks!

---

### Post by Janus82 on 2011-03-02
Hi estephens25,

Did you resolve your issue ? I'm in the same situation.

Thanks.

Best Regards,

---

### Post by Mariane on 2011-03-02
I had this issue and solved it by upgrading to Ubuntu 10.04. There the problem just went away. 

On that computer I stayed with 8.04 until 10.04 appeared, because of this. 

Mariane

---

### Post by Mark Phelps on 2011-03-02
Unless you have a very old CRT-style monitor that is really limited to 800x600 (and, we're talking 10 years ago!), the monitor is not what is limiting your display resolution.

It's the display driver that's at fault.

You need to tell us the make and model of your video card.  Older ATI cards (and SiS cards) can force you into using drivers that don't give you very good resolutions.

---

### Post by Uhura on 2011-03-02
I'm having a similar problem. I installed ubuntu 10.04 on a new system last week and all worked fine. Then I upgraded the drivers, kernels etc as per the instructions on this website: [http://www.contentwhores.com/wordpress/?page_id=484](http://www.contentwhores.com/wordpress/?page_id=484) and ever since then have been stuck in low res graphics mode. You can check the thread I started to see what's been tried so far (title; ubuntu stuck in low res mode since messing with nvidia drivers) Will be interested to know if you find a solution!

---

