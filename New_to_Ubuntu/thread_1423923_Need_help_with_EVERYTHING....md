---
title: "Need help with EVERYTHING..."
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Tiala on 2010-03-07
Ok, so here is the basics. I'm a noob. I'm willing to admit it. I know little to nothing about Linux. I would rather windows for the simple plug and play aspect, but that isn't really an option right now because my Husband wishes to have an OS on his PS3. Please don't brush me off, this is my first try with Linux and I'm begging...

I helped him install it and thought I was doing ok because I was able to figure a lot of this stuff out. Yay me, right? No... I'm so far in over my head that the pain killers aren't working anymore and it's only been 2 days. 

As of now, I've TRIED... and failed, and now need any and all help to figure this out. If people reply to this, I feel that this thread may become my best friend and main time consumer for the next couple of weeks as I learn what I'm doing. 

Now that I've bored you, I'll move on. I'm installing Xubuntu 9.10 on his PS3 and after the install, he attempted to go online. that was great until the flash player became an issue. I followed every install guide I could find, but firefox just ignored my attempts. Nothing shows up after installing the 64bit version of flash. I know I'm doing something wrong, but I don't have a clue as to what. 
I found a site, thought it was helpful, but now I'm not so sure. it had me run some code to be able to install the "extras" for the system, but now, every application on the system is locked up. I read the thing from top to bottom, read the comments on the  post and everything seemed great. I'm not sure if my flash attempts were what got me or the extras. firefox loads, the terminal works, but I can't load any application otherwise. Games and such fail. They load up and then close out in seconds. 

Does anyone have a big enough heart to help me out? I need to know how to fix this and how to get this system up and running doing the basics. Youtube, facebook, etc without having things missing. I'll worry about the rest of his wants after I am able to figure this out and hopefully learn enough along the way to be able to attempt the next steps without failing so badly. 
(Also, I'm sorry if this is in the wrong section. I really wan't sure since this seems to fit in more than one place.)

---

### Post by lacs on 2010-03-07
wow i would say install it again maby with 32 bit and try again 

or if you can get teminal then run " sudo apt/get install (name of program) " command replace (name of program) with the name of the program like " sudo apt/get install cheese " that would install cheese a webcam software

---

### Post by trorion on 2010-03-07
Sounds like you're doing great so far.  You got the OS running, internet, video and all.  Well done.  Flash is unfortunately a non-free program which (even in OS's like windows) has very poorly written web code and causes problems.  Don't feel bad.

OK, so nothing is working now?  You boot up to a locked up system?  Or is it just some things aren't working?  Is your system 64 or 32 bit; I'm not familiar with the ps3.

---

### Post by Sef on 2010-03-07
> Does anyone have a big enough heart to help me out? I need to know how  to fix this and how to get this system up and running doing the basics.  Youtube, facebook, etc without having things missing. I'll worry about  the rest of his wants after I am able to figure this out and hopefully  learn enough along the way to be able to attempt the next steps without  failing so badly. 
(Also, I'm sorry if this is in the wrong section. I really wan't sure  since this seems to fit in more than one place.)     1) If anyone is impolite, please click the report button on the bottom left.

2) I moved your thread to the Absolute Beginners Section.

> I'm installing Xubuntu 9.10 on his PS3 and after the install, he  attempted to go online. that was great until the flash player became an  issue. I followed every install guide I could find, but firefox just  ignored my attempts. Nothing shows up after installing the 64bit version  of flash. I know I'm doing something wrong, but I don't have a clue as  to what. 

I found a site, thought it was helpful, but now I'm not so sure. it had  me run some code to be able to install the "extras" for the system, but  now, every application on the system is locked up. I read the thing from  top to bottom, read the comments on the  post and everything seemed  great. I'm not sure if my flash attempts were what got me or the extras.  firefox loads, the terminal works, but I can't load any application  otherwise. Games and such fail. They load up and then close out in  seconds. 
3) What site did you use to install?

4) The easy way to install would be through the Xubuntu repositories.  (Note: Not sure what it is called in Xubuntu; In Ubuntu, they are located in the Ubuntu Software Center.)

---

### Post by Tiala on 2010-03-07
Thank you so much for your replies thus far. I almost didn't expect anything! 
Ok, on to the responses in order.

> wow i would say install it again maby with 32 bit and try again 

or if you can get teminal then run " sudo apt/get install (name of program) " command replace (name of program) with the name of the program like " sudo apt/get install cheese " that would install cheese a webcam software

I can't install 32bit, apparently, and sadly, only 64bit works on a PS3. I found this out after about 6 hours of trying and failing. I have already found out that it's a little easier and wish I could just use it.

as for the installing, i hate to say... I am lost... When I say noob, I mean I have absolutely no clue. which program should I try to install? as of this moment, nothing is installed except that extras thing, so I need everything that the basic install is missing for normal operation.

> OK, so nothing is working now? You boot up to a locked up system? Or is it just some things aren't working? Is your system 64 or 32 bit; I'm not familiar with the ps3.

system is running and basic functions work. It's not locked up so that's great. it's the programs that would be more... optional. Games and the web messenger are the ones that we tried and they never loaded. the bar popped up on the task manager, then went away. Even the "install and uninstall programs" thing won't load
PS3 only loads 64 bit (that's what I understand at least)

> 3) What site did you use to install?

4) The easy way to install would be through the Xubuntu repositories. (Note: Not sure what it is called in Xubuntu; In Ubuntu, they are located in the Ubuntu Software Center.)

I installed the package from this site:
[http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html)

by typing in "sudo apt-get install ubuntu-restricted-extras"
then tried to give gnash a chance as per the advice on the site. I had hoped that it would bypass flash and give me the result I needed. Now I have white boxes on my flash objects instead of the program I am supposed to see.
I don't see anything like Ubuntu Software Center. Closest I found was software source. where is it found on ubuntu and what does it look like so that maybe i can do a better search?

Hope that helps... I'm not sure what other information to give.

---

### Post by Barriehie on 2010-03-07
Welcome to Ubuntu 8)

Ubuntu Software Center is going to be:
```

System > Administration > Synaptic Package Manager
```
It should/might ask you for your root password in a dialog box before launching.  Once launched you'll be presented with a pane on the left listing categories and a package listing kind of in the middle.  The toolbar will have some binoculars on it to search by keyword(s) in teh title and description.  You're best bet for an app rather than blindly installing is ask, we'll help! :)

HTH,
Barrie

---

### Post by asmoore82 on 2010-03-07
An OS on the PS3 is a dead end road.

PowerPC architecture in general may be great for servers, but it is not a fun place
to be for a Desktop System. IMHO, Responsiveness in GUI's is always underwhelming,
even on Apple's PPC efforts.

As I understand it, the PS3 "slim" re-design doesn't support Linux installs at all.

Build a real PC with DVI output, buy a DVI-HDMI cable and you'll have a drop-in
replacement(in relation to Desktop OS - not gaming) for that PS that'll run circles around it.

I have a similar set up with 5+ year old "off-the-shelf" PC hardware
that doubles as the ultimate Free Software DVR.

---

### Post by egalvan on 2010-03-07
Found this on the web...

[http://psubuntu.com/](http://psubuntu.com/)

the home page states 

[I]psubuntu.com shows you how to **install and run the Ubuntu Linux** operating system on a Playstation 3.
 Read the installation instructions, or join the discussions in our forums.[/I]

--------------

another site...

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)


these may be of help...


Don't mind the doomsayers... :)


And pay close attention to anything sef (post #4) says
he's one of the "gurus" around here... :)

---

### Post by Tiala on 2010-03-07
so far i've been looking at this site today and i want to follow the directions because it looks like a cure all answer, but i am unsure. before i go and screw something up, i figure i'll ask here.
[http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/](http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/)
what do you think? should i do this or should i go a little slower?

---

### Post by egalvan on 2010-03-07
I would go slower (much slower)

To start, this guy (person) wants you to delete Canonical's sources list and  use his "personal" sources list...
do you trust him that much?

The second site I cite at least is related to Canonical (Community) and is (in *my opinion*) a bit more trustworthy.

And both are PlayStation oriented... you may have better luck with others trying to do the exact same thing you are attempting.

---

### Post by Tiala on 2010-03-07
you're right. that whole list thing did scare me a little bit, but i didn't really understand what he was talking about. remember, i'm a windows user by default so this open source stuff is over my head. i am just not used to being able to change everything by editing a file like that. lol
i'm going to go slow. first thing i did was uninstall anything i've done so far. (or at least that was my inderstanding) by following the directions here
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
my applications now run perfectly. well... as perfect as a new install. so i'm back at square 1 instead of having the problems listed above. from what i can tell, it was gnome that messed me up. after uninstalling it, things run again. *sigh* still so lost in how this all works.
the PSUmbutu site seems to have little to no activity in the forums and seems to read that 9.04 is the newest version of ubuntu. so heart breaking. i know i need 9.10 info... but i'll use it as a reference :)

---

### Post by GameOverDood on 2010-03-07
> **Tiala said:**
> Ok, so here is the basics. I'm a noob. I'm willing to admit it. I know little to nothing about Linux. I would rather windows for the simple plug and play aspect, but that isn't really an option right now because my Husband wishes to have an OS on his PS3. Please don't brush me off, this is my first try with Linux and I'm begging...

I helped him install it and thought I was doing ok because I was able to figure a lot of this stuff out. Yay me, right? No... I'm so far in over my head that the pain killers aren't working anymore and it's only been 2 days. 

As of now, I've TRIED... and failed, and now need any and all help to figure this out. If people reply to this, I feel that this thread may become my best friend and main time consumer for the next couple of weeks as I learn what I'm doing. 

Now that I've bored you, I'll move on. I'm installing Xubuntu 9.10 on his PS3 and after the install, he attempted to go online. that was great until the flash player became an issue. I followed every install guide I could find, but firefox just ignored my attempts. Nothing shows up after installing the 64bit version of flash. I know I'm doing something wrong, but I don't have a clue as to what. 
I found a site, thought it was helpful, but now I'm not so sure. it had me run some code to be able to install the "extras" for the system, but now, every application on the system is locked up. I read the thing from top to bottom, read the comments on the  post and everything seemed great. I'm not sure if my flash attempts were what got me or the extras. firefox loads, the terminal works, but I can't load any application otherwise. Games and such fail. They load up and then close out in seconds. 

Does anyone have a big enough heart to help me out? I need to know how to fix this and how to get this system up and running doing the basics. Youtube, facebook, etc without having things missing. I'll worry about the rest of his wants after I am able to figure this out and hopefully learn enough along the way to be able to attempt the next steps without failing so badly. 
(Also, I'm sorry if this is in the wrong section. I really wan't sure since this seems to fit in more than one place.)

Hi! I'm new to linux as well and although I own a PS3 I've never bothered installing an OS on it so I can't help you at all from personal (or lack of) experience.


But, I did manage to find this webpage that might be able to help you out:
>>[http://joepcremers.nl/wordpress/?p=1595](http://joepcremers.nl/wordpress/?p=1595)


If you'd rather try an older version of Ubuntu, which seems to be the tried-and-true method thus far, then here's another link with instructions:
>>[http://psubuntu.com/wiki/InstallUbuntu](http://psubuntu.com/wiki/InstallUbuntu)
...Although I would think egalvan's link is probably better since it's an official Ubuntu documentation.


**Edit**: Oh I should point out that I did notice you already had Xubuntu running and such but at this point since almost everything has locked up I think you're better off reinstalling. Might as well retry with a different installation method and with some version of Ubuntu instead. A "correct" installation may resolve the Flash issue as well as other problems.

---

### Post by Tiala on 2010-03-08
the first site just gives me what i've already done and my apps aren't locked up anymore. but thank you for trying.

newest updates... i went rogue last night. upset that flash won't work, i toyed with some things. i went to that install programs thingie that you sent me to before (excuse my lack of big words, it's early and i'm already starting this... tired) system => sympatic? something or another. then installed a smf thing and now i get no white box for flash objects, now it's a dark grey box with a play button. i was excited to see a response to my efforts... BUT... clicking the play button seems to just upset me. it will play flash objects, like graphics and now flash ads work wonderfully (grr) but youtube and any other flash object i'm expected to interact with fails. fun right? i tried following some directions i found to install flash, only to find myself unable to follow them. 
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)
now, if you look at the top instructions, i follow those and nothing happens. i tweak it to fit my file system instead of gerry's, and everything seems to be fine, but firefox ignores me and nothing happens.
if you scroll down, to the last comment, the guy says that he tried something different. adding the flash file into 2 different files for mozilla
> Hi all there. I have Ubuntu 9.10 64bit and this did not work for me, but this helped me a lot. I did the same “hawk” says but in my case, the folder where firefox links is “/usr/lib/firefox-3.5.8/plugins”. So, copy your new “libflashplayer.so” in that folder too.
My final solution was:
-Paste libflashplayer.so in “/usr/lib/mozilla/plugins”
-Paste libflashplayer.so in “/usr/lib/firefox-3.5.8/plugins”
*Instead of 3.5.8, you may write your own firefox version.
but i can't find those files... at all. my firefox is located at .mozilla not just mozilla. i copied the file there (in plugins) and like i said, firefox pretends that i did nothing. i check my plugins and it won't show adobe. any clues on that?

---

### Post by Revo99 on 2010-03-08
Hello Tiala,

Once you do get your linux running correctly see below link on Flash Player for 64bit Operating Systems. It may shed some light.

[http://labs.adobe.com/technologies/flashplayer10/faq.html#flashplayer10FAQ_64-bit03](http://labs.adobe.com/technologies/flashplayer10/faq.html#flashplayer10FAQ_64-bit03)

I am a noob as well and can't get flash to work on firefox either.

By the way on a PS3 you can backup its data, reformat internal drive and it will reinstall Playstation's software I am very sure. If worst comes to worst. I am sure Playstation can help you with this. 

Good luck!!! I am sure you will work it out! These forums are excellent. step by step.

Cheers,

Revo

---

### Post by Dayofswords on 2010-03-08
take a look into yellow dog linux

the makers apparently sell ps3 with it installed already on it

i hear(hear!!) it works good on the ps3

---

### Post by Tiala on 2010-03-08
no, yelow dog sucks when compared to ubuntu. i did my homework and ubuntu is the way to go. i'm not looking to replace my software, only to improve upon it and get some things working.

anyways, i found the files i was talking about earlier this morning, i just can't do anything to them. could this be part of my problem? the .so files are there, i just can't move, add or delete them. 
also, i read that to make flash work, i need to enable 3rd party repositories. umm... how? when i googled it, i just got a bunch of stuff that wasn't flash or it just said "if you haven't done it, do it now" but doesn't say how.
it seems that i don't have admin ability in those folders. i was watching a "how to" vid that seemed really helpful, until i found that i couldn't "open as admin" and place a file in the mozilla/plugins folder. how do i fix that?

---

