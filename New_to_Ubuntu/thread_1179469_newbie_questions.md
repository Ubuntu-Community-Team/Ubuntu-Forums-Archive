---
title: "newbie questions"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by KingJackalope on 2009-06-05
OK These hopefully will be simple and easy to answer.

1. If I open my firefox then I open my e-mail program I see my firefox minimize down but once I close my e-mail I can't find my firefox again without having to reopen another one. I know its still there since one thing I was logged into would not allow multiple log in sessions and it told me to close the other one out first. But where is it? In Windows they go to the task bar and are easy to find here I couldn't find it at all.

2. I got a ran out of disc space message today. I have a 6.8 gig hard drive. I went and removed all the programs I could. I currently have NO music. NO games. NO "Frills" of any kind and my disc space is still 6 gigs, 90% used. Does the OS take up that much room? Is there temp files I should remove from like updates and such? I guess I assumed it would do that once they were installed.

Those seem to be my 2 biggest pressing issues #2 more than #1 actually but #1 is just frustrating you know? Any help somone can provide me with this would be greatly appricated.

Thanks,
Dave

---

### Post by LowSky on 2009-06-05
welcome to the forums


**#1** Applications go to the bottom panel just like in windows, you may have accidentally deleted this feature if they are not showing up, its very easy to re-add, just right click on the panel choose add option and look for application (sorry its name is escaping me, and I'm at work on a wiondows machine)

**#2**  6GB is not that much space, its nearly the basic requirement of this operating system for a normal install. if you need something that takes up less space, I suggest using a distro like Puppy Linux.

run this command from a terminal to remove file no longer needed.
```
sudo apt-get clean
```
that might get you a little more space freed up, but i doubt it.

I dont know much about your computer or where you live but a new hard drive but a new hard drive costs as little as $35 for 80GB, and 500Gb for $50
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+4025&QksAutoSuggestion=&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+4025&QksAutoSuggestion=&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by wpshooter on 2009-06-05
On number 1 are you sure that you are not switching between the mutiple desktops that Ubuntu allows when you are opening these 2 applications.

Look at the number of desktop currently setup/chosen into bottom right hand corner of your desktop/screen.

If this is perhaps the problem, then I would suggestion that you change the number of desktops to just 1 unless there is some compeling reason that you need more than one.

---

### Post by LewRockwell on 2009-06-05
there are quite a few threads discussing hardware. in fact, you might actually find someone else who has the same exact machine(as long as they bothered to post their hardware, software, peripherals, and installed operating system(s) when they started their "help wanted" thread on the Ubuntu Forums)

there is always used stuff around for cheap or free so don't go blowing big bucks til you've done the research and shopping around

---

### Post by mocoloco on 2009-06-05
For #2, the base install of Ubuntu takes up about 2.5 to 3 gigs.  And that's still small compared to say Vista's base install (8-10GB I think).  Add to that any apps you install, and you won't have much space for large media like photos, music etc.
Run the Disk Usage Analyzer (Applications -> Accessories) and scan you home folder to see where your space is going.

---

### Post by KingJackalope on 2009-06-05
First, Thanks for such a fast response! Very cool!!

I got this for Christmas from a friend that bought a Dell and was able to get this very cheap. Its one of those mini computers and this happens to be the OS that is installed on it. I know NOTHING about the OS have tried to read up on it but not very motivated I guess.

I'm pretty sure I am not switching desktops Ive tried to play with that and it doesn't seem to work very well for me It just looks the same. Again, not sure what Im doing wrong if anything. I relly don't work on this computer its mostly for traveling checking email and being able to surf the web for fun. Just surprised me when I tried to do an update and got the hard drive was 100%. 

I'm close to getting an upgrade HD and getting windows installed on it since I already know that and and operate in it. Probably the best bet I'd think for me I guess.

Anyway again thanks for such a prompt reply!!

-Dave

---

### Post by mocoloco on 2009-06-05
Ah, is this a Dell netbook?  That helps.  New info then:

#1 - Dell changes the default panel to minimize everything to the top instead of the bottom.  If you still don't see it, try Alt-Tab when it's running and see if it comes up.

#2 - That low space on netbooks is intentional, they originally weren't meant to have lots of storage and only work as a secondary computer (that changed though and a lot of the newer ones have large hard drives).

You'll want to use what works best for you of course, but if these are the only issues you have I would recommend giving it a little more time to learn the system. Having just for the 3rd time reinstalled my mother-in-laws WinXP due to a nasty virus problem, I've seen how people suffer unnecessarily just to avoid learning a new interface.

---

### Post by KingJackalope on 2009-06-05
OK. Alt-Tab works!! That helps out a lot. Thanks.

 Yeah I want to give it a good college try so I'm hanging with it. 

I pretty much suspected as much with the low disc drive stuff. I also assumed that like a previous poster it only took 2-3 gigs for the os install and when I saw it used the full 6 gigs basically I was kind of shocked. Using the "sudo apt-get clean" did help out quite a bit. Down to only 77% used so thats cool I can live with that for the most part.

I did go to that disc usage area befoe even coming here but being ignorat to the OS I really have no idea what is needed and what is not. There is not a cd drive on it so I really can't install anything. I did have like 5 songs on it (erased this morning). To get it over I had to use my flash drive to transfer but thats cool.

Again, Thanks for the help thing you guys got me pretty much covered.

---

### Post by mocoloco on 2009-06-05
Glad that worked. I'm guessing you're just missing the window list applet.  Quick terminology:

panel - the bar(s) at the top & bottom (or depending on setup just top or bottom) of the screen.  They do nothing themselves without applets.

panel applet - A little program made to run inside a panel. The "Applications" menu for example is just an applet.  You can add and remove or reorder applets all you want.

So knowing those terms, there's an applet that shows the running windows, called "Window List" that I'm guessing just got removed from yours somehow.  Right-click on a blank part in the panel, and do "Add to Panel..."  Then add the "window list" applet.  Once it's there you can right-click on it and move it to any part of the panel you want.

---

### Post by KingJackalope on 2009-06-05
> **mocoloco said:**
> 
panel applet - A little program made to run inside a panel. The "Applications" menu for example is just an applet. You can add and remove or reorder applets all you want.


Dude you rock!! Thanks a million!! 

Side note kind of funny/sad. I had it cleaned up to 77% free space. did the newest updates ate it back up to only 92% free!! haha. oh well.. that will work for what I'm doing. The windows applet was EXACTLY what I wanted!!

---

