---
title: "getting slower &amp; slower"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-17
i have been using ubuntu for over a month now , and have been trying to learn by installing different softwares and exploring , but i have noticed that my system is getting slower day by day , i-e  taking more time to boot , taking more time to open any folder. 

i have already tried removing softwares i installed like google earth  but no difference ,

is this because of some type of virus ?

is there an option to restore my system to a previous time ?

---

### Post by mrcollinz on 2011-04-17
Hmmm interesting, it is not very likely that is being caused by some type of virus, although all things are possible download ClamAV and give you're system a scan.

From the terminal:

sudo apt-get install clamav

From Ubuntu Software Center:

search "ClamAV"

Also you may want to try running the system monitor in the background and check and see if there are any processes running that shouldn't be. You can access it from [COLOR=#008000]System->Administration->System Monitor.[/COLOR]

You may also want to use the clean up janitor to delete and old unused files from you're system. You can access it from [COLOR=#008000]System->Administration->Computer Janitor.[/COLOR]

Other then that you may want to have a look at you're specs and maybe check you're graphics settings etc.

P.S there is _[COLOR=Red]NO[/COLOR]_ utility in Ubuntu to create or return to previous restore points as there is in windows, sorry about that. I forgot to notice this was a beginners post so I edited my instructions to make them easier for you I hope this information helps.

---

### Post by zaafar on 2011-04-17
thanks Ryan,
i checked system monitor , i didnt see any process that were not supposed to be running but the odd thing is that  processer shows 80%-100% usage even if i just open an application like software centre,  is it normal ?
 i will try klamav , if it doesnt work , do you think i should re-install meerkat  or try 10.04 LTS ( if it is more stable than meerkat ? )
regards
zaafar

---

### Post by mrcollinz on 2011-04-17
Hmm, that is extremely high load for such a simple process. What kind of system are you running?. Dependent on you're system specs you may want to downgrade, but to be honest Linux is generally stable even on older pc systems.

If I may make a suggestion, run a scan it will likely return null (nothing). But for good measure run a scan anyway. If you're running 10.10 you may want to try downgrading to 10.4. But to be honest I think this may be a hardware issue unless my assumption is wrong and you're running an i3 with 4gb of ram lol.

---

### Post by zaafar on 2011-04-17
:D no , this is not a 4g ram system ,,, its an old one , a Dell Latitude D610 with 1.2 G Ram and 1.8 G processor with 80 GB hard disk. 

i am confused that if it is a hardware problem . it should have behaved this way from the first day .. but it worked well initially.

i guess i did something wrong with installing some softwares , because i am new at ubuntu and was trying to play with it...:(

---

### Post by Paqman on 2011-04-17
> **zaafar said:**
> 
i guess i did something wrong with installing some softwares , because i am new at ubuntu and was trying to play with it...:(

Maybe. What have you been installing? Did you get everything from Ubuntu Software Centre, or have you been installing things manually?

---

### Post by crispy_420 on 2011-04-17
Possible some where along the line you added software that acts likes services (apache, ftp, etc.) that could be running and using resources?

---

### Post by zaafar on 2011-04-17
tried to install google earth, scanner drivers , printer drivers and  some other applications like GNOME DO , GIMP , themes etc . 

by using synaptic , terminal and software centre

---

### Post by zaafar on 2011-04-17
@ crispy , i dont remember installing such programs ,

i did follow instructions(from a website) which run in terminal and automatically install different programs and update some..

---

### Post by Paqman on 2011-04-17
Well, your hardware should be fine to run any version of Ubuntu. I use it on a netbook with lower specs and it runs fine. Without knowing exactly where the problem is it's a bit hard to advise any kind of solution. It might just be easier to do a reinstall just in case something has got a bit messed up. One of the nice things about Linux when you're starting out is that reinstalling is pretty quick and painless if you break your system somehow.

---

### Post by zaafar on 2011-04-17
should i re-installl it with that iso image cd . or is there a better option ?

---

### Post by weedeater64 on 2011-04-17
You should probably do a clean install, and take more care with future software installation.

---

### Post by racie on 2011-04-17
My install has gotten slow as well.  This is the longest I've ever used Ubuntu, and I'm a little surprised that it has followed the path of Windows.  It started out lightning fast, but has become slower and slower.

Perhaps the hard disk has just become old.

---

### Post by weedeater64 on 2011-04-17
> **racie said:**
> My install has gotten slow as well.  This is the longest I've ever used Ubuntu, and I'm a little surprised that it has followed the path of Windows.  It started out lightning fast, but has become slower and slower.

Perhaps the hard disk has just become old.

 Ubuntu seems to resemble winblows more and and more with each release.. sad.  Ultimately though, it's up to you. I like this guys aproach,  [http://www.youtube.com/watch?v=PuGVz15Pe5Y](http://www.youtube.com/watch?v=PuGVz15Pe5Y)  and am adopting it for myself.

---

### Post by kaldor on 2011-04-17
Nobody bothered to ask an obvious question; Did you install Ubuntu on a partition or did you use the WUBI method by installing it inside of Windows like any other Windows program? If you installed it inside Windows, it will suffer from the same problems that happen such as slow downs.

Also, to the above post: Ubuntu isn't resembling Windows. Try any other distro and they're all essentially the same.

Edit: Also, the Windows mentality of "reinstall your OS to fix issues" is just silly.

---

### Post by mrcollinz on 2011-04-17
I agree it would be best just do a fresh installation and see if that works, it's hard to diagnose cause there could be some service in the background using resources. Best to get a trial UbuntuOne account, come with 2gb of free storage, save you're necessary items there do a fresh install and restore you're data.

Hope everything works out,

---

### Post by Falcon1002 on 2011-04-17
Hello! Sorry to hear you system is slowing down. :( If you do end up reinstalling Ubuntu you also may want to write down any programs you use frequently. Doing so could help you get up and running again faster because you won't have to remember what that really great program was. :D Also you might find it a good time to put your home on separate partition (maybe you did this already???) that way in the future if you need to do a reinstall again you don't have to wipe all your personal files off the hard drive. :D I have reinstalled linux a lot (more times than necessary) :D

---

### Post by DrSeemann on 2011-04-17
I'm not having that problem ATM, but I know it's possible to have this kind of problems using ANY OS if you don't pay attention and take care of it.
I think that the OS is like any other "product", like a car or a motorcycle. When it's brand new it will run as fast as it can, but as time goes by it will get slower more and more.
So what we do when our "products" start working wrongly, simply repair them.
I.E On windows I was used to monitor what processes where running at start up, how much do they load memory, and how much CPU they consume. Disk framentarion and some other stuff.

It's not hard to do this, you must know a bit of how does PC and OS works.
I'm running Ubuntu 10.10 maverick, and ATM i'm running jDownloader and Firefox. Using 52% of RAM (872 MiB), 0.6% of SWAP (4 GB) and 25% of CPU (Dual 1.7). 

And I've been installing a lot of software (without really watching what I was doing), 1 month "old" OS.

I hope this helps you.

---

### Post by mörgæs on 2011-04-18
Poor original poster. Must be confusing to read all this.

Assuming this is a true Ubuntu installation and not Wubi:

You should not reinstall until diagnosing the problem. Run **top** while doing your normal work will tell you which application is causing the processor load. Press q for quitting top.

ClamAV searches for Windows vira in an Ubuntu installation. They have no significance for Ubuntu and its speed, but they could spread to a Windows machine. 

10.04 and 10.10 are similar with regards to system load. Downgrading does not change anything.

In general: Some of the posters in this thread should pay more attention to the exact details and only write what they are absolutely sure about. While we appreciate people giving advice, an ill-founded advice is worse than nothing.

---

### Post by Rasa1111 on 2011-04-18
I find that very interesting...
I have been using Ubuntu for a year and have not had any of my systems slow down yet!

 They all run pretty much as fast as the day i installed them. 

Not sure what's going on over there.

---

### Post by mörgæs on 2011-04-18
By the way, this is the exact same computer I am using. Runs Ubuntu with no problems.

---

### Post by K_45 on 2011-04-18
I can't see this as happening. Even if you install a lot of programs with daemon's that startup the "rot" the OP is mentioning shouldn't happen to that degree. There is no real fragmentation, nothing sapping resources unless its a running process *cough Firefox cough*, no registry (well, there is gconf-editor), and downloaded packages may takeup space but that would be it; maybe this is a hardware problem?

---

### Post by mörgæs on 2011-04-18
The only certain thing is that it is not a hardware problem. Hardware does not gradually get slower and slower - unless the machine is running on battery, but I guess this option is too obvious.

Please don't confuse original poster more than has already been done in this thread.

Everything points to the direction that there has been installed one particular application which is too heavy. As stated above, **top** will show that. Firefox has been on the system from first day, so it is unlikely to be the explanation.

Let's stop the random guessing and get some facts on the table.

---

### Post by DrSeemann on 2011-04-18
> **zaafar said:**
> thanks Ryan,
i checked system monitor , i didnt see any process that were not supposed to be running but the odd thing is that  processer shows 80%-100% usage even if i just open an application like software centre,  is it normal ?
 i will try klamav , if it doesnt work , do you think i should re-install meerkat  or try 10.04 LTS ( if it is more stable than meerkat ? )
regards
zaafar
Can you post a list of the processes shown on system monitor in order to see the software using such a high amount CPU?

[ATTACH]189390[/ATTACH]

Something like this :P

---

### Post by Falcon1002 on 2011-04-18
So sorry for adding to the confusion. :oops:

---

### Post by BrandonC19 on 2011-04-18
> **mörgæs said:**
> The only certain thing is that it is not a hardware problem. Hardware does not gradually get slower and slower - unless the machine is running on battery, but I guess this option is too obvious.

Please don't confuse original poster more than has already been done in this thread.

Everything points to the direction that there has been installed one particular application which is too heavy. As stated above, **top** will show that. Firefox has been on the system from first day, so it is unlikely to be the explanation.

Let's stop the random guessing and get some facts on the table.

While I certainly do agree that it IS probably one heavy app causing all the trouble, to say that hardware is **certainly** **not_**_ the issue is a bit much. Taken from personal experience I can assure that it very well could be the case. Best to rule out everything before putting all of the grunt into solution.

---

