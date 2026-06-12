---
title: "[SOLVED] do I have spyware installed?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by amanda hill on 2009-01-06
I am having problems with"firefox" it keeps saying there is a problem with it.Is Firefox antivirus,spyware?how do I check it is working properly?If this is not an antivirus software how can I get this for ubuntu 8.o4.I cannot web browse at all because there is apparently a problem with firefox.I,m worried the computer has a virus how do I check this????:confused::confused::confused::confused::confused::confused::confused:

---

### Post by jrusso2 on 2009-01-06
We need more information on whats wrong but a virus is unlikely.

---

### Post by Paqman on 2009-01-06
Firefox is your web browser. What exactly is the error message that you're getting?

Don't worry too much, it's extremely unlikely that you have any kind of virus or spyware on your system.

---

### Post by BoneSaw on 2009-01-06
firefox is most definitely not a virus or spyware. firefox is a part of the ubuntu suite of programs. imagine it to be an open source internet explorer.

---

### Post by amanda hill on 2009-01-06
Let me first explain,my daughter downloaded limewire and a load of photos on this computer which she got for christmas.I thought this may have caused the problems so I deleted all those files.
I go to web browser.then i click on yahoo this is what comes up.
Alert
could not initialize the applications security component.The most likely cause is problems with you applications profile directory.Please check that this directory has no read/write restrictions and your hard disk is not full or close to fall.It is recommende that you exit the application and fix the problem.If you continue to use this session you might see incorrect application behaviour when accessing security features.

Incidently why is it so unlikely to have got a virus.my windows vista computer hasd norton antivirus loaded.Does ubuntu not need this kind of program also????

---

### Post by amanda hill on 2009-01-06
I can get to a page that lists the option for yahoo when I click on it it goes back to the home page.

nowe there is another alert which says

firefox is already running,but not responding.To open a new window,you must first close the existing Firefux process,or restart your system.

---

### Post by jerome1232 on 2009-01-06
> **amanda hill said:**
> 
Alert
could not initialize the applications security component.The most likely cause is problems with you applications profile directory.Please check that this directory has no read/write restrictions and your hard disk is not full or close to fall.It is recommende that you exit the application and fix the problem.

Well why don't we start off by checking the things mentioned in the error that could be the cause of this issue, permissions and/or a full disk.

Open a teminal and type the following commands, Applications->Acessories->Terminal

to check permissions
```
ls -ld .mozilla
ls -ld .mozilla/firefox
ls -l .mozilla/firefox
```

To check if your disk is full
```
df -h
```

If you could post the output of those commands we can start figuring this out. To make them readable wrap them in [noparse]```
code tags
```[/noparse] To copy text from a terminal press ctrl+shift+c

---

### Post by Tony Flury on 2009-01-06
> **amanda hill said:**
> 
Incidently why is it so unlikely to have got a virus.my windows vista computer hasd norton antivirus loaded.Does ubuntu not need this kind of program also????

Ubuntu does not need Antivirus software esentially becuase it does not have the same virus threat that Windows does. This is for a number of reasons, but mainly : 
[LIST]
[*] Ubuntu has been designed with security and permissions built in from the 1st day (rather than added as an after thought like in Windows). To install anything you need to provide a password - and there is no way round that - so any virus that did try to attack would need to prompt you for your password.
[*] far fewer people run Ubuntu (or any other linux variant) than run Windows, and therefore the target audience for a virus writer is therefore much smaller. 
[/LIST]

---

### Post by Sef on 2009-01-06
> far fewer people run Ubuntu (or any other linux variant) than run Windows, and therefore the target audience for a virus writer is therefore much smaller.

Not true.  GNU/Linux has a majority of the server market (at least 60%), and yet there still aren't any viruses for them.

---

### Post by Paqman on 2009-01-06
**Amanda Hill:** One thing you could try is to export your bookmarks (Bookmarks > Organise > Import/Backup > Export to html) then delete your /home/username/.mozilla folder. Then restart Firefox, import your bookmarks back in and reinstall any extensions you use.

This trashes your Firefox config and sets it back up from scratch.

> **Sef said:**
> Not true.  GNU/Linux has a majority of the server market (at least 60%), and yet there still aren't any viruses for them.

The threat to servers is mostly from hacking, not the trojans and such that the problem on desktops.

However, I agree that the small install base is not the main reason that we don't have a virus problem on desktop Linux. To my mind the main reasons are:

[LIST=1]
[*]The inherently better security model
[*]The superior responsiveness of Open Source
[*]The centralised, trustworthy source of software (ie: the repos)
[/LIST]

---

### Post by amanda hill on 2009-01-06
Ok i will try and type what I see on the terminal I am going to do the disk space first as I  have a sneaky suspicion that is the problem.

filesystem        size   USED   Avail  Use% mounted on
/dev/sda2         3.4G   3.2G     42M   99% /
varrun            247M   100k    247M    1% /var/run 
varlock           247M     0     247M    0% /var/lock
udev              247M    36k    247M    1% /dev
devshm            247M   12k     247M    1% /dev/shm
gvfs-fuse-daemon  3.4G   3.2G     42M    99%/home/lily/.gvfs

---

### Post by amanda hill on 2009-01-06
answers to other codes

ls-ld .mozilla =mozilla

ls-ld .mozilla/firefox =mozilla/firefox

ls-l .mozilla/firefox  =ef137cb5.default

if it is that the disk is too full,please walk me through how to clear it

---

### Post by donkyhotay on 2009-01-06
> **amanda hill said:**
> Ok i will try and type what I see on the terminal I am going to do the disk space first as I  have a sneaky suspicion that is the problem.

filesystem        size   USED   Avail  Use% mounted on
/dev/sda2         3.4G   3.2G     42M   99% /
varrun            247M   100k    247M    1% /var/run 
varlock           247M     0     247M    0% /var/lock
udev              247M    36k    247M    1% /dev
devshm            247M   12k     247M    1% /dev/shm
gvfs-fuse-daemon  3.4G   3.2G     42M    99%/home/lily/.gvfs

Wow, you only have 42mb of hard drive space left. I would recommend cleaning up your drive. Clearing out your hard drive is a simple matter of figuring out whats on your system, what you don't need, then deleting it. If your daughter was using limewire then chances are you probably have a ton of music/movies floating around that you don't need. Find out where she downloaded these too, delete as many as you need (just select the icon and press delete), then empty your trash (right-click on the trash icon in the lower right-hand corner and select empty trash).

//edit: Kind of sad that only having 42mb of hard drive space results in system errors. My first computer only had one 170kb floppy disk drive (a c64) and when I finally did upgrade to *a* hard drive, I don't remember the size but I know it was less then 42mb.

---

### Post by The Cog on 2009-01-06
Oh-oh. Your / partition (/dev/sda2) is 99% full. You need to either enlarge the partition or delete some files. You can use the partition editor on the live CD to enlarge the partition (if there is free space to expand into). The error message did mention disk space and I think it was right.

---

### Post by amanda hill on 2009-01-06
i'll give this a try and let you know.Darn Kids:KS:KS:KS

---

### Post by Paqman on 2009-01-06
> **amanda hill said:**
> Darn Kids:KS:KS:KS

Well to be fair you have got the system installed on an absolutely minute amount of space. It was only a matter of time before you had trouble with it.

---

### Post by donkyhotay on 2009-01-06
I misread your total file size, thats 3.4gb not 34gb, makes sense whey you're out of space. With 3.4gb of hard drive space you might be better off using a lighter distro. I've never used it myself but I've heard good things about puppy linux and it's pretty lightweight compared to ubuntu.
[http://www.puppylinux.org/wiki/hardware/general/minreq](http://www.puppylinux.org/wiki/hardware/general/minreq)

---

### Post by LowSky on 2009-01-06
Could you giver more info on how Ubuntu was installed? Maybe even the computer make and model?

Is this a Dell Inspiron Mini 9?
They are not made for extreme use like downloading with clients like limewire. Also may I suggest getting a usb flash drive to store files on, a 8GB model cost about $20 on Newegg.com

---

### Post by amanda hill on 2009-01-06
the disk is now 84% full and the same message and proble with firefox is present.I am going to attempt the bookmark thing.ahhhh.

---

### Post by amanda hill on 2009-01-06
ubuntu was factory installed.it is an inspiron mini

---

### Post by LowSky on 2009-01-06
I thought so, yea don't listen to **donkyhotay **you dont need a new distro of linux. But you need to know that thoses small notebooks, called netbooks, are not made for "normal" computer use. In normal I mean storing files, playing games or movies, or writing long term papers. They are meant for casual internet use and simple note taking. These smaller computers are meant to be used as secondary machines for most people.

The best suggestion I can make is getting a flash drive or a SD card for extra storage. If you need alot of space maybe invest in a external hard drive. If you do pick one of those up we can explain how to set up the SD card for use as your /home partion so you dont runito these problems later.

I know you thought this cheap computer would be a great gift for your child, but in all honesty  you could have gotten a normal laptop for maybe a few bucks more that is more capable then the Inspiron Mini

---

### Post by donkyhotay on 2009-01-06
If your still having problems with 84% free can you once again do
```
ls -ld .mozilla
ls -ld .mozilla/firefox
ls -l .mozilla/firefox
```
and when you post your responses copy and paste *everything* that appears there. We're wanting to check your file permissions so we need all the sections that will show. Also make certain you copy the command exactly as shown, spacing and caps do matter.

---

### Post by JoshuaRL on 2009-01-06
> **Paqman said:**
> 
The threat to servers is mostly from hacking, not the trojans and such that the problem on desktops.


Well, it has to be.  If Linux had as bad a problem with remote exploits as another well-known OS, then dictionary attacks would be ridiculous.  And the reason malware of the sort you're talking about is so prevalent on desktops is because that's almost all they're good for.  Most people don't keep all their important personal info on the computer.  So malware writers are left with organizing botnets.

But the real power and money is in information, so if Linux was exploitable, you'd see much less of an attack on the desktop space.  But then you'd also have e-anarchy.

---

### Post by amanda hill on 2009-01-06
oh my gosh i have no idea how to do this bookmark thing.We are talking very VERY basic here please.

---

### Post by LowSky on 2009-01-06
> **amanda hill said:**
> oh my gosh i have no idea how to do this bookmark thing.We are talking very VERY basic here please.

very easy, goo to bookmarks (with firefox open of course), then organize bookmarks, look for import backup at the top click on it, the click on back up and save the file to somewhere you will remember it


when you want to add them do the same thing, except at the last step click restore and choose the save file you made

---

### Post by amanda hill on 2009-01-06
OK guys how am i supposed to gooooo tooooo bookmark when evry time i click webbrowser that alert message comes up???also I cannot copy an paste I am on a different computer i am not able to do anything on the web with the computer in question....

---

### Post by JoshuaRL on 2009-01-06
To:  Amanda Hill

Go ahead and try donkyhotay's suggestion below and post exactly what the output is.  Just wrap it in code tags like this:

[noparse]```
stuff from terminal
```[/noparse]

> **donkyhotay said:**
> If your still having problems with 84% free can you once again do
```
ls -ld .mozilla
ls -ld .mozilla/firefox
ls -l .mozilla/firefox
```
and when you post your responses copy and paste *everything* that appears there. We're wanting to check your file permissions so we need all the sections that will show. Also make certain you copy the command exactly as shown, spacing and caps do matter.

---

### Post by amanda hill on 2009-01-06
ok here goes ```
ls -ld .mozilla =drwxr-xr-x 4 lily lily 4096 2008-12-25 02:48 .mozilla

ls ld .mozilla/firefox  drwxr-xr-x 3 lily lily 4096 2008-12-25 02:47 .mozilla/firefox

ls -l .mozilla/firefox
total 8
drwxr-xr-x 6 lily lily 4096 2009 01 06 17:43   ef137cb5.default
-rw-r--r-- 1 root root  93 2008-12-25 02:47 profiles.ini
```

---

### Post by donkyhotay on 2009-01-06
> **LowSky said:**
> I thought so, yea don't listen to **donkyhotay **you dont need a new distro of linux. But you need to know that thoses small notebooks, called netbooks, are not made for "normal" computer use. In normal I mean storing files, playing games or movies, or writing long term papers. They are meant for casual internet use and simple note taking. These smaller computers are meant to be used as secondary machines for most people.

Depends what amandahill wants to do, if you want to browse the web and maybe do some word processing like the computer is designed to do then definitely keep ubuntu and be careful about what gets downloaded in the future. On the other hand if you really *want* to download a bunch of extra stuff then you will either need a new computer or a lighter distro (though even with another distro you are limited by the system itself). Linux is all about choice, it's your computer, you can do whatever you want to do with it. Personally, if I was in your situation I would install another distro, but thats because I wouldn't be content with just browsing the web.

---

### Post by kramer65 on 2009-01-06
I don't want to interupt in this discussion but I was just reading your conversation. I had a look at the inspiron mini [here]("http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?cs=19&s=dhs&ref=homepg"), and in the tech-specs I see that the hard drive is 32GB with the ubuntu install.

Isn't there a different problem then? I mean, is the hard drive correctly partitioned or are there maybe more partitions or something? Also, have you emptied the trashcan (this was a problem with me once..)?

ps. I am not so technical so I'll leave the rest of the answers up to the other guys here, but I thought this maybe could help..:D

---

### Post by karlr42 on 2009-01-06
Dell don't offer all the variants in all regions. Here in Ireland there is only one model, the Ubuntu 4GB version, with no options or customisation possible.

---

### Post by amanda hill on 2009-01-06
oh F*********k I just want the darn thing to work.i do not want to add anything extra.the kids have been told to not use it to download anything.(bumma oh well).yeah I did empty the trash

---

### Post by dynathi on 2009-01-06
I have encountered this problem in the past, and it seemed like the simplest solution was just starting from scratch. At least for me, just entering:

```

rm -rf ~/.mozilla

```

into the terminal solved the problem. When you start up Firefox again, everything will be reset to default settings, including what's causing the problem (which is probably a corrupt file named cert8.db). You will, however, lose all your bookmarks.

Someone else here mentioned this here, but only briefly and sort of got caught up in telling you how to back up your bookmarks.

Hope it helps :D

---

### Post by donkyhotay on 2009-01-06
If you don't care about saving your bookmarks and want to 'just get the @#$%ing thing to work' then follow dynathi's instructions posted above. If you care about your bookmarks then let us know and we'll *try* to help you salvage them.

---

### Post by Temposs on 2009-01-06
To summarize what you should know succinctly:

1) Yes, just follow dynathi's instructions. That's the best way to go :-)

Type in the terminal:
```
rm -rf ~/.mozilla
```

2) Ubuntu will not get viruses or spyware. (as far as we know, at the present time)

All that's necessary right now to have the best security in Ubuntu is to install the automatic updates.(They appear as a little orange gear or red arrow icon occasionally in the top right of the screen)

3) This computer has very little space. Tell your children to not download music or movies onto it. If you'd like, teach them to delete things they download from the computer so it doesn't fill up.

---

### Post by dynathi on 2009-01-06
> **donkyhotay said:**
> If you don't care about saving your bookmarks and want to 'just get the @#$%ing thing to work' then follow dynathi's instructions posted above. If you care about your bookmarks then let us know and we'll *try* to help you salvage them.

I'm sorry if I offended you, I just thought it might be easier to start from scratch rather than bothering going through the extra steps of backing up bookmarks (then again, I usually don't use bookmarks so I'm a little biased ;)

---

### Post by donkyhotay on 2009-01-06
> **dynathi said:**
> I'm sorry if I offended you, I just thought it might be easier to start from scratch rather than bothering going through the extra steps of backing up bookmarks (then again, I usually don't use bookmarks so I'm a little biased ;)

 So yes, if you do care about your bookmarks go ahead and follow donkyhotay's instructions :)

You didn't offend me, I just posted that way because many times people don't care *how* the computer works so long as it *does* work. Also after enough time people get frustrated enough with a system they are willing to start over from scratch just to get on with life (something similar is what got me started with linux BTW). My recommendation is to fix the file permissions (if you notice they're set to root). It may not work but according to amandahill's previous post typing:
```
sudo chown -R username:username ~/.mozilla
```
should work since her profile.ini file is owned by root. Oh and BTW amandahill for my posted code above you will want to replace username with the username of your user account so theoretically if *I* was to type this command it would be
```
sudo chown -R donkyhotay:donkyhotay ~/.mozilla
```
but as I mentioned before if you're confused, uncertain, and don't care so long as it works, use dynathi's instructions.

---

### Post by JoshuaRL on 2009-01-06
> **Temposs said:**
> 
Type in the terminal:
```
rm -rf ~/.mozilla
```



Actually it would be:
```
sudo rm -rf ~/.mozilla
```

Just please be careful with that command.  Altering what comes after the "sudo rm -rf" can possibly delete Ubuntu.  So paste that carefully into the terminal.

---

### Post by the.phantom on 2009-01-06
i might be wrong ( good chance)
but thought i would mention this
i worked on a friend's computer and she had att/yahoo as her isp and they offer a/v firewall and a few other things
and i was thinking they work windows only 
so maybe it is trying to change the firewall or block something and just can't talk to ubuntu?
and if they go into the att/yahoo page and disable that just to see?

sorry probably out of place with the post but thought i would mention it

---

### Post by jolx on 2009-01-06
> **JoshuaRL said:**
> Actually it would be:
```
sudo rm -rf ~/.mozilla
```

Just please be careful with that command.  Altering what comes after the "sudo rm -rf" can possibly delete Ubuntu.  So paste that carefully into the terminal.

temposs should be correct because ~/.mozilla is in the home directory and therefore wouldn't require sudo permissions. right? i havn't got an ubuntu partition atm :S

---

### Post by JoshuaRL on 2009-01-06
> **jolx said:**
> temposs should be correct because ~/.mozilla is in the home directory and therefore wouldn't require sudo permissions. right? i havn't got an ubuntu partition atm :S

Actually, now that you mention it, yeah.  I can't believe I missed that.  I'm just so used to only using that command in root owned folders it was force of habit.  Man.

To Amanda:  Use the command as posted by Temposs.  Another way to do it is to go to your Home Folder, hit Ctrl+H (to unhide hidden folders) and delete the .mozilla folder.  That is, if you don't feel like you want to use the command line.

---

### Post by donkyhotay on 2009-01-06
> **JoshuaRL said:**
> Actually, now that you mention it, yeah.  I can't believe I missed that.  I'm just so used to only using that command in root owned folders it was force of habit.  Man.

To Amanda:  Use the command as posted by Temposs.  Another way to do it is to go to your Home Folder, hit Ctrl+H (to unhide hidden folders) and delete the .mozilla folder.  That is, if you don't feel like you want to use the command line.

No, it won't work, look at my last post and amandahill's ls results. The problem is the fact one of her mozilla files is owned by root. She needs root access to modify/delete it.

---

### Post by amanda hill on 2009-01-06
Thankyou all so much for your patience i am up and running and talking to you from that darn computer.The rm rf thingy worked Hooray!!!!!!!!:D:D:D:D:D:D

---

### Post by oilchangeguy on 2009-01-06
> **amanda hill said:**
> Thankyou all so much for your patience i am up and running and talking to you from that darn computer.The rm rf thingy worked Hooray!!!!!!!!:D:D:D:D:D:D

great! now please use the thread tools, and mark your post solved.

---

### Post by amanda hill on 2009-01-06
where are they?????

i got it.Thanks

---

### Post by JoshuaRL on 2009-01-06
> **donkyhotay said:**
> No, it won't work, look at my last post and amandahill's ls results. The problem is the fact one of her mozilla files is owned by root. She needs root access to modify/delete it.

Man, I am double dumb.  That's what comes from focusing on too many threads at a time.  I suggested the sudo because of the root ownership and forgot why I did that when questioned.

Wow.  Dinner and a show.  :popcorn:

Glad to hear you're up and running again Amanda Hill.

---

### Post by jerome1232 on 2009-01-06
--edit---  ooops I just saw that discrenpency and replied didn't notice there were already replies, well you could've just changed the ownership instead of removing the directory, but glad you got it sorted

If everything is fixed don't forget to mark your thread as solved under thread tools.

> **amanda hill said:**
> ok here goes ```
ls -ld .mozilla =drwxr-xr-x 4 lily lily 4096 2008-12-25 02:48 .mozilla

ls ld .mozilla/firefox  drwxr-xr-x 3 lily lily 4096 2008-12-25 02:47 .mozilla/firefox

ls -l .mozilla/firefox
total 8
drwxr-xr-x 6 lily lily 4096 2009 01 06 17:43   ef137cb5.default
-rw-r--r-- 1 root root  93 2008-12-25 02:47 profiles.ini
```

Ok I see one problem here, profiles.ini is owned by root, on my system it's owned by my user.

Change the ownership back to "lily" see if that remedies it.

```
sudo chown lily:lily ~/.mozilla/firefox/profiles.ini
```

---

