---
title: "Ok some simple things but yet so confusing in ubuntu."
date: 2009-12-08
forum: New to Ubuntu
---

### Post by aklo on 2009-12-08
Total noob here. I install ubuntu because of the interface and want to try something that belongs to the geek community and i think i am not "geek" enough.

Some simple things which i can't figure out.


1. My nvidia 8800gt fan speed in ubuntu, is it dynamic speed or is it manual speed? In windows mine is set to dynamic so it speed up the rpm when i play graphic intensive games...but what about ubuntu? Does it run on dynamic or manual by default? Any ways i can change them? Heck i don't want it to spin at 30% when my gpu temp is like 70 degree when it could be much lower if it is at 100%.

2. Are there any GRAPHICAL monitoring widgets/softwares in ubuntu?
Seems to me almost everything runs in the command line or terminal. Even simply checking my hard disk temp(using hddtemp) needs me to type a command.

3. Are the temp monitors available out there accurate especially the default installed nvidia x server ? I just checked the temperature and it is 52 degrees celcius while in windows normally it is 54-55...well it could be due to the fact ubuntu is cooler or something but i wouldn't take any chance if the temperature is not accurate.

4. Ok so i read the documentation (like real) nah, i just found a link which says there are problems with the ext4 format with files larger than 512MB(from the official ubuntu bugs)...can someone confirm this? Or whether any of you are using the ext4 format and have files which are few gigs in size and still doing good? damn i have a ton of files larger than 512mb each and waiting in my winxp hard disk can't wait to bring them over to ubuntu.


edit: Lastly how do i disable ubuntu for asking me for my password everytime i make changes? 


Ps: after my long post i did a search and finally found 2 links to "widgets" in ubuntu.

[http://screenlets.org/index.php/Home](http://screenlets.org/index.php/Home)
[http://www.gdesklets.de/](http://www.gdesklets.de/)

Have no idea if they work yet as i'm not on the comp with ubuntu now.

---

### Post by zkriesse on 2009-12-08
> 
Lastly how do i disable ubuntu for asking me for my password everytime i make changes? The first thing I'm going to bring your attention to is this comment. Even if it's possible (I don't believe it though I could be wrong.) to disable the password that would be a most terrible error on your part. The reason why Ubuntu asks for a password in types of situations such as those is to protect your system. If it didn't that would basically give someone such as a hacker pretty much unlimited access to your system so keep that in mind. Ok...that's all I'm going to say on that point.


> 1. My nvidia 8800gt fan speed in ubuntu, is it dynamic speed or is it manual speed? In windows mine is set to dynamic so it speed up the rpm when i play graphic intensive games...but what about ubuntu? Does it run on dynamic or manual by default? Any ways i can change them? Heck i don't want it to spin at 30% when my gpu temp is like 70 degree when it could be much lower if it is at 100%.For this question please look at this Ubuntu Forums post. [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)
     
>  3. Are the temp monitors available out there accurate especially the default installed nvidia x server ? I just checked the temperature and it is 52 degrees celcius while in windows normally it is 54-55...well it could be due to the fact ubuntu is cooler or something but i wouldn't take any chance if the temperature is not accurate.Again, for this question look at this Ubuntu Forums post. [http://ubuntuforums.org/showthread.php?t=325244](http://ubuntuforums.org/showthread.php?t=325244)

> 4. Ok so i read the documentation (like real) nah, i just found a link which says there are problems with the ext4 format with files larger than 512MB(from the official ubuntu bugs)...can someone confirm this? Or whether any of you are using the ext4 format and have files which are few gigs in size and still doing good? damn i have a ton of files larger than 512mb each and waiting in my winxp hard disk can't wait to bring them over to ubuntu.As for this several friends are currently using ext4 with files 1GB and larger and currently are not experiencing no errors or bugs. Well, that's all I got for you for now...will research your questions and get back to you...** [COLOR=Red]P.S. Get back to me and let me know if this helped you![/COLOR]**

---

### Post by diablo75 on 2009-12-08
> **aklo said:**
> 
1. My nvidia 8800gt fan speed in ubuntu, is it dynamic speed or is it manual speed? In windows mine is set to dynamic so it speed up the rpm when i play graphic intensive games...but what about ubuntu? Does it run on dynamic or manual by default? Any ways i can change them? Heck i don't want it to spin at 30% when my gpu temp is like 70 degree when it could be much lower if it is at 100%.

I can't say for sure, but my suspicion is that the fan manages itself dynamically all on it's own without the aid of software drivers.  Kind of how the BIOS on all modern PCs handle the speed of CPU fans.
> 
2. Are there any GRAPHICAL monitoring widgets/softwares in ubuntu?
Seems to me almost everything runs in the command line or terminal. Even simply checking my hard disk temp(using hddtemp) needs me to type a command.

Not sure what you're wanting to monitor exactly, but a lot of people here like to use a little program called "conky" which is a programmable system monitor widget of sorts you can have on your desktop.  I've never used it, but it has a huge following.  Start a seperate thread about it and ask others to help you get started with it.
> 
3. Are the temp monitors available out there accurate especially the default installed nvidia x server ? I just checked the temperature and it is 52 degrees celcius while in windows normally it is 54-55...well it could be due to the fact ubuntu is cooler or something but i wouldn't take any chance if the temperature is not accurate.

I would have to say they are accurate as the actual temperature sensing is done by the exact same hardware-based sensor regardless of what OS you are using.  > 
4. Ok so i read the documentation (like real) nah, i just found a link which says there are problems with the ext4 format with files larger than 512MB(from the official ubuntu bugs)...can someone confirm this? Or whether any of you are using the ext4 format and have files which are few gigs in size and still doing good? damn i have a ton of files larger than 512mb each and waiting in my winxp hard disk can't wait to bring them over to ubuntu.

I use ext4 and have never had such a problem.  Could you provide a link to the bug report you saw?> 
edit: Lastly how do i disable ubuntu for asking me for my password everytime i make changes? 

You can't.  Linux is designed with strict security in mind and restricts global configuration settings from being changed without authorization.  You might think that is a real pain in the neck but it will only bother you while you're in the process of setting up all your hardware and software.  Once everything is the way you like it, you'll appreciate the peace of mind knowing that no software (like a virus) or setting change (like someone accidentally doing something to your setup) could ever take place without your say so.
[/quote]
Ps: after my long post i did a search and finally found 2 links to "widgets" in ubuntu.

[http://screenlets.org/index.php/Home](http://screenlets.org/index.php/Home)
[http://www.gdesklets.de/](http://www.gdesklets.de/)

Have no idea if they work yet as i'm not on the comp with ubuntu now.[/QUOTE]

These widgets might not have exactly what you are looking for but keep searching; I'm sure you'll find what you want eventually.  Again, check out conky.  It can be setup to monitor all kinds of things for you.

---

### Post by JamesParnell on 2009-12-08
Yes gdesklets and screenlets work, i have them myself, although there is not much to choose from, Gdesklets come with the gadget designer, to make your own

---

### Post by aklo on 2009-12-08
I guess i'll have to try the various programs out to see which one works for me. 

As for the password prompt thing, i agree with you but isn't this is what the vista community complained about; the UAC. Well anyway not much of a big deal.

thanks for the inputs

---

