---
title: "Freezing after login"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by PhilJames on 2008-12-11
Sorry, I was an enthusiastic noob but now my ardor has been dampened.

I had Hardy working ok ish for a while, then updated to Intrepid. 
The system freezes to a brown screen just after I've logged in. The cursor sticks and there's nothing to do but hard reboot.
I've tried safe mode and all the options. Fix packages, fix x server, check file system, clean. Sometimes it works, sometimes not.

I have a dual boot, I'm using xp to write this because the last time just now the system **froze in the safe mode** menu screen.

Hardware: Intel Pentium d 2.66ghz x 2 1gbRAM, nvidia geforce 7300 le, canon printer, logitech fusion webcam.

It might be relevant or not. I've found it beyond my capability to follow the workaround to get the webcam working.  And if I try to plug it in while ubuntu is booted up, that also will freeze the system, but will _not_ freze the system if it is already plugged in.

thanks, if you've got anything to renew my enthusiasm

---

### Post by Michael.Godawski on 2008-12-11
Since you tried out much already... I would save the time and do a fresh install. Sometimes things gets very confused when you upgrade. So I always recommend a fresh install.

Do you have done a back-up of your important data? If yes download Intrepid and begin from scratch. If no, you can use the Live CD to access your drives and copy everything which is important to you. 


[LIST]
[*][http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)
[/LIST]
But perhaps someone has a divine inspiration...

---

### Post by PhilJames on 2008-12-11
Thanks for your quick response.
I'll try a reinstall.
There is just something I need to check before I start. I told you I was a noob :rolleyes:
When I load the live cd do I choose the normal install and does it re repartition the drive or does it just install into dva5 partition over the top of my existing install?

---

### Post by PhilJames on 2008-12-11
and btw I'm not going to bother about saving any data from this install.

---

### Post by PhilJames on 2009-01-07
Follow up- 3 weeks later-
I reinstalled and had no problems for 3 weeks until it just started behaving the same way [freezing after logging in]
I just did another reinstall but i hope this won't be a regular occurrence. 

For anyone who had the same questions I had, here is how to reinstall with a dual-boot with windows.
[LIST=1]
[*](always have windows data backed up first, just in case)
[*]Boot from live cd-> choose, try demo and install
[*]Choose location and keyboard layout
[*]then it says "starting partitioner" but don't worry as I did because the next option is -> choose manual
[*]click on the partition which has linux ubuntu, which should be obvious from the size.
[*]click edit partition-> choose to format -> choose the same file system as your original ubuntu( in my case ext3)
[*]Don't worry about the linux swap partition that will be automatically included, and windows won't be touched.
[*]also the grub dual-boot system will be the same
[/LIST]

 
Hope this will be of some help to others in a similar situation. More experienced users... If I've made any mistakes in my instructions, please add any corrections.

---

### Post by namdung on 2009-01-07
I've seen/heard/experienced too many issues with Intrepid that I strongly recommend the much stable Hardy Heron 8.04 LTS with 3 yrs support. Intrepid may have more features but also has more bugs.

Hardy 8.04.2 is out anytime now.

---

