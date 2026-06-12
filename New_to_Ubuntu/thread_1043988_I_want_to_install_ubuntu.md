---
title: "I want to install ubuntu"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by glennlad on 2009-01-19
I have downloaded the ubuntu iso, burnt it to disc and it dont work, i get a blank screen then text will appear, i dunno what it says but it starts with numbers. After 10 mins it will finish, at the bottom of the page it will say Terminate Trace or something like that, there is no option for the text installation either!! 

I have tried the Alternative CD which i burnt to disc also and tried booting my pc via the cd drive first, guess what it didnt work, all it said was "boot from cd".

So Ive tried the server ISO aswell, and even that doesn't work, any ideas?? I really dont want to stick with windows.

---

### Post by glennlad on 2009-01-19
Never mind i will find another OS to use instead of windows and ubuntu.

---

### Post by blackened on 2009-01-19
Bad media is likely the culprit. I've always found that my burners prefer certain brands of media and coaster everything else.

Try a different brand of media maybe?

---

### Post by cacycleworks on 2009-01-19
Good times.

I had similar issues with the laptop I'm typing on now. And it HATED 7.04. I put it in a drawer and by the time I was able to actually spend time on it, 7.10 came around and it worked.

You didn't say what your computer is or anything other info to help anyone help you... 

Anyhow, for the best luck with things like this, try googling for "ubuntu [your computer make and model] boot problem" or some such.

There have been times I've been mad at *buntu, but it really is the best/easiest to get along with, imho. I was able to get SLAX, knoppix, vectorlinux, and SuSe working. Other ones have been really vexing to me.

Good luck - no matter the distro you use! 
Chris
:)

---

### Post by glennlad on 2009-01-19
> **cacycleworks said:**
> Good times.

I had similar issues with the laptop I'm typing on now. And it HATED 7.04. I put it in a drawer and by the time I was able to actually spend time on it, 7.10 came around and it worked.

You didn't say what your computer is or anything other info to help anyone help you... 

Anyhow, for the best luck with things like this, try googling for "ubuntu [your computer make and model] boot problem" or some such.

There have been times I've been mad at *buntu, but it really is the best/easiest to get along with, imho. I was able to get SLAX, knoppix, vectorlinux, and SuSe working. Other ones have been really vexing to me.

Good luck - no matter the distro you use! 
Chris
:)


Amd Sempron 2400...

---

### Post by jimmy the saint on 2009-01-19
I had to add a boot option in order to have ubutnu load on my server for some reason.  Pay attention to the first few things that come up in the text.  Often, it will be an error and a possible solution.  My box said that there was an issue with IRQ 18 and that I should add the irqpoll option.  That is not to say that will solve your problem, it is just an example.  If there is an error/suggestion, and you need help understanding it, post back so we can try to help

---

### Post by meatlegs on 2009-01-19
Try Wubi!
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by glennlad on 2009-01-19
it was error messages yes but no solution to be seen, it was like [208.7545.66 error retrieving ... 
it went all the way up till it hit the first number turned a 4 then it said "terminate trace" then i was presented with a blank black screen. 



Oh and Wubi or what ever it is; i dont want that as i want to get rid of windows all together.

---

### Post by ubersolid on 2009-01-19
Try burning the ISO again, sounds like a bad burn to me.

---

### Post by efexD on 2009-01-19
ISO was giving me problems also, just get wubi.

---

### Post by 3rdalbum on 2009-01-19
Try some of the "cheat codes" on the live disc. You know when you start up Ubuntu and you get presented with the menu ("Install Ubuntu", "Check the CD for errors", "Boot off the first hard disk" etc), look down the bottom of the screen and you'll see something like "F4: Alternate boot options". Pressing the key will tell you various things to add to the boot parameters that can sometimes get Ubuntu to not crash on startup.

Otherwise, you could try a distribution that is not related to Ubuntu; for instance, you could try Mandriva or OpenSUSE.

---

### Post by cacycleworks on 2009-01-19
> **glennlad said:**
> it was error messages yes but no solution to be seen, it was like [208.7545.66 error retrieving ... 
it went all the way up till it hit the first number turned a 4 then it said "terminate trace" then i was presented with a blank black screen. 


Yes, what we mean by finding a solution is that you use google:
1) Type in your error's relevant text and your motherboard or brand of computer
2) press enter
3) read the first 3 pages of replies
4) take notes
5) implement solutions on your computer
6) solutions make ubuntu finish loading

I just tried googling for [ubuntu "error retrieving" install]("http://www.google.com/search?q=ubuntu+"error+retrieving"+install&btnG=Search") just now and got a handful of promising looking replies. Unfortunately, it would seem the most important word is the one following retrieving.

I'm not being a smartazz with the above info... it's really not that difficult to work around the initial bit of problems when trying a fresh install. The two areas where I run into issues are:
1) Really new computers... might have issues for 1 to 3 releases. (my dell laptop for example)
2) Really old computers... The newest releases might not work well. So I start trying older releases of ubuntu. My tattooist has an ancient pentium laptop that he uses solely for presentations. It finally succumbed to malware and he asked me to do anything -- I ended up installing ubuntu 6.04 or something on his laptop and it worked perfectly.

:) Chris

---

### Post by boof1988 on 2009-01-20
When you tried the Alternate Install CD, did you try hitting the <enter> key when the monitor displayed "boot from CD"?  I don't know if this helps or not but there was a time when I had to do that to boot from the CD.

Hope this helps.

---

