---
title: "Help this sucks!"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by peachster22 on 2009-01-12
i installed ubuntu on my toshiba laptop running vista not to long ago id say about a month. i use it really only for gimp because the wifi on it really sucks and is quite unreliable. anyway this morning before i went to school i used vista and opera to view some websites ext.. i proceeded to put it into hibernate and evrything was fine. when i got home today from school i went to boot into vista and before i was able to i got a GRUB error which was ERROR number 16. i read into it and alot of people said to pop an ubuntu 8.10 live cd into the machine so i did and i cant run live cds or anything from my USB drive...nothing is working i do not know what to do any suggestions...the laptop is a really Sh**y one but its only a year old so i need to keep it other wise i am F**KED. thanks any help is appreciated

---

### Post by albinootje on 2009-01-12
> **peachster22 said:**
>  i went to boot into vista and before i was able to i got a GRUB error which was ERROR number 16.

Can you still boot into Ubuntu or not ?

If you can, follow the instructions from #2 of this page :
[http://ubuntuforums.org/showthread.php?t=1037876](http://ubuntuforums.org/showthread.php?t=1037876)

And post the output here. Thanks.

---

### Post by Captain_tux on 2009-01-12
And what are you trying to achieve?

Booting into Vista only or Ubuntu only?

---

### Post by Michael.Godawski on 2009-01-12
> 16 : Inconsistent filesystem structureThis error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.       

This is what grub error 16 wants to tell us. So your drive may be corrupt. I am thinking right now how to check it when no CD is working....

---

### Post by deputy on 2009-01-12
Do you have your BIOS setup to boot from CD?

---

### Post by jimv on 2009-01-12
>i use it really only for gimp

You do realize that there is a version of the GIMP for Windows, right?

---

### Post by peachster22 on 2009-01-12
haha yah i realize that gimp is on windows lol... shut up :-p
and my BIOS is set up to boot from hard drive but i bring up the boot menu and try to boot my live cd and it does not work it just loads up and turns off before it fully loads its a pain in the ***.... idk what to do im so like confused lol

---

### Post by peachster22 on 2009-01-12
And what are you trying to achieve?

Booting into Vista only or Ubuntu only?

in response to this question

i just wanna boot into something lol so i have a damn computer to use...im doing all this from my moms comp and i dont want her to find out my laptop is frigged up you know
thanks for the responses so far but im still like screwed so far

---

### Post by albinootje on 2009-01-12
> **peachster22 said:**
> And what are you trying to achieve?

Booting into Vista only or Ubuntu only?

in response to this question

i just wanna boot into something lol so i have a damn computer to use...im doing all this from my moms comp and i dont want her to find out my laptop is frigged up you know
thanks for the responses so far but im still like screwed so far

Please, if you can, boot from "recovery mode" in the Grub boot menu, and choose "drop to root shell prompt".

Report back if that is done successful.

---

### Post by mlentink on 2009-01-12
> **peachster22 said:**
> haha yah i realize that gimp is on windows lol... shut up :-p

You might find that just a bit different attitude might increase the number of helpful responses. This forums consists of users just like you, nobody gets paid for anything and nobody owes you anything.

You might also ask yourself just how you ended your Vista session. Vista can be quite unforgiving if not closed correctly. I'm not saying that's what went wrong, but the GRUB error tends to point in that direction

---

### Post by anewguy on 2009-01-12
> **mlentink said:**
> You might find that just a bit different attitude might increase the number of helpful responses. This forums consists of users just like you, nobody gets paid for anything and nobody owes you anything.

You might also ask yourself just how you ended your Vista session. Vista can be quite unforgiving if not closed correctly. I'm not saying that's what went wrong, but the GRUB error tends to point in that direction

Ditto.  We're just volunteers - but we do expect a professional attitude here.  Obviously you're a kid - we can tell that from your posts - but this is not one of those forums where you say or imply whatever you want to.

If you really want help, remove the quite clear references to bad language and things like "shut up", realize people here are volunteering their time and effort, and by far we are all not kids - so to put it bluntly, please grow up when using the forum.  Others have offered advice - have you tried and replied to those things yet?  Examples - are you trying to boot Windows or Linux?, does Windows boot okay?, and when someone asks if you are aware of gimp for Windows, try saying something like "I've tried it but had xxxx problems" or "no" - otherwise quit trying to tell us you want to just use gimp.

---

### Post by peachster22 on 2009-01-12
i ended it by hibernating it and it shut down fine so im like going nuts here i dont know what to do...can i like buy a new hardrive lol?

---

### Post by albinootje on 2009-01-12
> **peachster22 said:**
> i ended it by hibernating it and it shut down fine so im like going nuts here i dont know what to do...can i like buy a new hardrive lol?

Can you not boot anything at all from the Grub boot menu ?
In other words, do you get the Grub error 16 after you choose to boot MS-Vista ?
If the latter, can you boot with any of the Ubuntu options in the boot menu or not ?

Buying a new hard disk would be the very very last resort in my opinion, but it should be totally unneeded to think about that option right now.

You have friends or relatives who can help you with this ?

---

### Post by peachster22 on 2009-01-12
nah sadley i noe the most about computers of any1 i know but when it comes to the BIOS and boot screen crap im brain dead... i cant even try to boot into Ubuntu or Windows basically this is what i see picture this

Grub Version 1.5 (something like that)

Loading GRUB please wait....(after this i would see the Vista/longhorn loader and also the ubuntu linux options but i dont i just see ERROR 16) 

Error 16

thats it...

---

### Post by peachster22 on 2009-01-12
in response to one guy above me...i said i used it mainly for gimp because once i installed it i realized the wifi sucked. my original plan was a complete conversion from vista to ubuntu because i dont feel totally safe on vista also i just relaly dislike microsoft as a whole... after i culdnt get ubuntu working so i just stayed with vista and used ubuntu for off line programs (gimp, games :-p, minor things like that because i didnt know how to uninstall it.) nice try on being a smart *** and my bad for not totally giving u my reasoning for getting linux in the first place...you guys have been a big help but it appears as if my problem really doesnt make much sence...can anyone give me some alternatives besides the hard disk swap because as one person stated that seems to  be a LAST resort.... thanks

---

### Post by peachster22 on 2009-01-12
haha wow i must really be pissing u guys off but i just went on to my comp and now i am able to ATTEMPT to boot into linux and windows but neither works...i am now recieving an error 18 which says something is to large for the bios... or something of that nature....any ideas now? im sorry this is so confusing for you guys

---

### Post by Terl on 2009-01-12
> **peachster22 said:**
> haha wow i must really be pissing u guys off but i just went on to my comp and now i am able to ATTEMPT to boot into linux and windows but neither works...i am now recieving an error 18 which says something is to large for the bios... or something of that nature....any ideas now? im sorry this is so confusing for you guys

Wow, you really are something.  I doubt anyone is pissed and as for confused it is only because you don't answer questions posed to you.  Oh well, my computer works just fine.  Maybe if you help us help you, yours can as well.

How old is this computer of yours?  How big is the hard drive?

---

### Post by anewguy on 2009-01-13
Leave off the smart remarks, leave off the ha-ha's and anything else you seem to think is clever.  You end up giving the impression you know more than we do with those answers, and until you prove us wrong, try to be nice, polite, and answer the questions directly posed to you.

At this point, I think you'll be lucky to get anyone to post back now because of your attitude and remarks and failure to supply information when requested.

This isn't a kids forum.  Don't act like one.

Continued posts like this will get you banned.

---

### Post by anewguy on 2009-01-13
> **peachster22 said:**
> in response to one guy above me...i said i used it mainly for gimp because once i installed it i realized the wifi sucked. my original plan was a complete conversion from vista to ubuntu because i dont feel totally safe on vista also i just relaly dislike microsoft as a whole... after i culdnt get ubuntu working so i just stayed with vista and used ubuntu for off line programs (gimp, games :-p, minor things like that because i didnt know how to uninstall it.) nice try on being a smart *** and my bad for not totally giving u my reasoning for getting linux in the first place...you guys have been a big help but it appears as if my problem really doesnt make much sence...can anyone give me some alternatives besides the hard disk swap because as one person stated that seems to  be a LAST resort.... thanks

Please read ALL of this kids' replies - he can't give an answer, and he acts like a troublemaker.  I don't think there is room on the forum for someone with this kids' attitude and phrasing and lack of response - please do something like disable him for a few days and let him know why, or just ban him altogether.

He's wasting our time and looking like a jerk.  I've tried to be direct with him in my replies - he may not like it - but everyone here is trying to help him and he just keeps acting like a jerk.

Thanks!
Dave :)

---

### Post by albinootje on 2009-01-13
> **peachster22 said:**
> i just went on to my comp and now i am able to ATTEMPT to boot into linux and windows but neither works...i am now recieving an error 18 which says something is to large for the bios...

I think the most important thing you need to find out first, is how to boot from the Ubuntu installation cdrom again.

From that point on, we can help you further.

---

