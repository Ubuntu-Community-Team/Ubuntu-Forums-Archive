---
title: "Error After Upgrade To 9.10 - &quot;Mount of filesystem failed...&quot;"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by forbidenpasionfruit on 2009-10-29
Hi everyone,

I turned my server computer on after a few weeks of not having time to get back to it (after freshly installing 9.04 and getting some great help on these forums!), and it told me that 9.10 was out, so I upgraded in through the update manager.

It restarted a few times, and then on what was to be the last restart, it came up with the following error message:

```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@server-desktop:"#
```

So I did CONTROL-D and this is what came up on the screen aftewards:

```
root@server-desktop:"# exit
fsck from util-linux-ng 2.16
/dev/sda1: superblock last mount time (sat oct 31 20:09:47 2009,
now=fri oct 30 12:10:06 2009) is in the future

/dev/sda1:UNEXPECTED INCONSISTENCY; RUN FSCK MANUALLY.
(i.e., without -a or -p options) 
swapon: /dev/disk/by-uuid/d5c266b2-fdc9-4417-b537-b4f388cc15c3: swapon failed: Device or resource busy
mountall: swapon/dev/disk/by-uuid/d5c266b2-fdc9-4417-b537-b4f388cc15c3 [910] terminated with status 255
mountall: problem activating swap: /dev/disk/by-uuid/d5c266b2-fdc9-4417-b537-b4f388cc15c3
mountall start/running, process 904
mountall: fsck / [908] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (904) teminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started
CONTROL-D will terminate this shell and retry.
root@server-desktop:"#
```

Restarting doesn't help, and I really don't know where to go from here, and didn't see anything helpful in my searches of the forums before posting here.

Any advice would be great.

Thanks again,
Nicole

---

### Post by ikt on 2009-10-30
> /dev/sda1:UNEXPECTED INCONSISTENCY; RUN FSCK MANUALLY.

in the terminal space below type

```
fsck
```

after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.

---

### Post by ranch hand on 2009-10-30
I have not seen that bug myself but there was quite a bit of it a couple weeks ago.  I would;
```

ubuntu-bug mountall

```
and follow the directions as they come up.

This will end up with you on the launchpad page with the bug and there should be directions for fixing it.

---

### Post by zeilant on 2009-10-30
[user:Dergel:] schrieb:
> falls es jemand interessiert.
> 
> Ich hab am Ende meiner fstab folgende Zeile gefunden:
> /home    /home    dazukofs
> 
> Keine Ahnung wie die dahin kam, hab sie gelöscht und nun gehts.

---

### Post by forbidenpasionfruit on 2009-10-31
Hi guys,

Thanks for the help. 

To ikt - I only know a tiny bit about cmd prompt style things, so even though I saw that and it made sense I didn't want to touch it just in case it made a bigger mess!

And in regards to the suggestions, I haven't had to do any of them as today (about 24 hours since the problem) I switched the computer back on, and it just worked - gotta love computers!

Thanks again,
Nicole

---

### Post by bezt.inc on 2009-11-13
I have same problem, and now it's solved.
Thanks a lot you guys :wink:

---

### Post by toni1963 on 2009-11-15
thanks, it works. You are asked several times to fix and finally the control-d keys restart the computer properly.

---

### Post by doc.ved on 2009-11-16
thanks 
even i had the same problem and din't know what to do

---

### Post by freezerburn666 on 2009-11-18
i got this error but after a fresh install. fsck worked.

---

### Post by RADARB8 on 2009-11-18
> **freezerburn666 said:**
> i got this error but after a fresh install. fsck worked.

+1

useful writeup \\:D/

---

### Post by avatarz on 2009-11-26
the fsck command helped in resolving my problem.. thank you for your all knowledge.

---

### Post by WizardGir1 on 2009-11-28
Thank you, thank you, thank you! :) I'm one happy girl! Problem solved here too. 
...the ASPIRING WizardGir1 ;)

---

### Post by OldGamer on 2009-11-30
Thanks for the excellent advise!  I had this same problem, and after running fsck one time (from the maintenance prompt), my ubuntu boots again.  As always, this forum is great!

---

### Post by Adam Orth on 2009-12-05
Thank you, thank you. I've been stumbling though my first Ubuntu install on an IBM ThinkPad and this thread got me past what I hope will be my final hurdle!

---

### Post by glitch942003 on 2009-12-12
Had the some problem: "mount of filesystem failed..." ran the fsck command and it fixed the problem.

---

### Post by fuchila on 2009-12-19
Thanks a lot guys. This is my first time looking something up to fix it on my own. A buddy usually fixes everything for me but he was all "stop destroying your computer and why are you feeding it sandwiches".

---

### Post by b1lancer on 2010-01-05
Help!

I'm having this exact problem. I had upgraded to 9.10 a few days back and everything was peachy until I decided to start my computer today.

I tired the above: fsck didn't do anything. And ubuntu-bug mountall couldn't send the report.

What's going on? Any suggestions?

I don't want to do a clean install because I have files on it that I was in the process of backing up!!

Thanks guys. I'm confident I'll get this resolved on this forum!! :)

---

### Post by b1lancer on 2010-01-07
Ok. Got it. Fixed it.  Thanks anyway.

---

### Post by kekebay on 2010-01-07
don't want to do a clean install because I have files on it that I was in the process of backing up!!

---

### Post by UAA on 2010-01-13
Same problem here with Netbook Remix. I would report this if I had time. and the fsck then Crtl+D worked for me.

---

### Post by dlowerre on 2010-01-13
This is the second time this has happened to a friend of mine who relies on me for help.  It is VERY disturbing to get a call that 'Ubuntu won't boot'.  

Does anyone know what is causing this problem?  Is it going to be fixed?

---

### Post by freesitebuilder on 2010-01-13
I get that error - but Ubuntu carries on to load normally. fsck is the problem for me - if I let it run, I get "signal out of range" on my monitor. If I hit esc to prevent fsck running it goes on to load.

---

### Post by theboycalcoen on 2010-01-15
I think I would've  given up on Ubuntu without this forum. Fsck then control + d worked for me too. Thanks.

---

### Post by Tachikoma805 on 2010-01-27
So then what is the bottomline cause of this? HDD error or kernel error?
I notice tho that this happened for the first time to me, today, after the machine went to sleep or hibernate w/e. How can I completely turn off hibernate or any powersave util at all?

Much thanks,
Tachi:p

---

### Post by JosephKheir on 2010-01-28
Thank you guys for yuor support.... fsck works !!!!!!=D>

---

### Post by henrywgc on 2010-01-31
Phew, that was a nasty moment! Same thing happened to me, I think after I downloaded a whole lot of system update files and rebooted. The 'fixit' command seemed to do just that, and after that 9.10 booted up OK. A bit worrying though - glad I found this thread by googling from my 'real' computer ;)

---

### Post by fooliot on 2010-02-01
I have a similar problem with my computer and restarting doesn't do anything and I haven't set up my root account yet.  Where is the terminal space where I can run fsck?

---

### Post by freesitebuilder on 2010-02-02
> **fooliot said:**
> I have a similar problem with my computer and restarting doesn't do anything and I haven't set up my root account yet.  Where is the terminal space where I can run fsck?

Applications > Accessories > Terminal

---

### Post by fooliot on 2010-02-02
> **ikt said:**
> in the terminal space below type

```
fsck
```after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.
where can i find the space mentioned here? sorry if i wasn't clear before.

---

### Post by jakare on 2010-02-03
Edit:
I had fixed this problem but it wasn't solved by typing fsck. So when I shut
my computer off the problem returned. I think I should have used the terminal and type
fsck when ubuntu worked. Is the only way to reach terminal by using ubuntu cd or is there
another way, because in this "mount of filesystem failed" page I cannot do
anything else than pressing control D. This seems to be a shell??

---

### Post by pituk on 2010-02-03
i have same problem,after typing fsck then ctrl D worked for me.
thank you very much.

---

### Post by klausdiemaus on 2010-02-06
I've had this happen to me before after I did a large update. I reinstalled Ubuntu, but this time I have a lot of files I cannot recover if I reinstall. I will boot up Ubuntu again and try fsck. 

I'm wondering if this is a kernel issue, or maybe ext4. This last time I was doing some heavy hard drive stuff. I had imported all my music and photos from a flash drive and Banshee was running it's Mirage plugin scanning all my files. I was going to copy some files from a second flash drive but Nautilus kept complaining that my folders were read-only. I angrily tried a reboot and sure enough Ubuntu wouldn't boot up.

Both cases with me were after I did something that used the hard drive alot. Anyone else?

---

### Post by fooliot on 2010-02-10
this is similar with what happened to my computer too.  does anybody know why this happens or how frequently this happens?

---

### Post by WkenCouser on 2010-02-13
Hey Guys,

Thanks. 

I had the same problem and did "fsck" and "reboot".

I am now up and running.

Ken

---

### Post by tb87670 on 2010-02-22
My HDD had a bad sector in it and I tried Ubuntu as a last ditch effort. Worked after typing FSCK into the command prompt after reading about bad filesystem. Thanks guys, revived a dead HDD!

---

### Post by Dougle on 2010-02-27
> **ikt said:**
> in the terminal space below type

```
fsck
```

after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.

Thanks Ikt, i've just put my laptop back together after cleaning it and got this error, an fsck fixed it within 2 mins, cheers.

---

### Post by Alteaz on 2010-02-27
I'm still having trouble, I've tried fsck numerous times with reboots and ctrl+d but I still get the same error. I've been doing it for days now with no success.

Can anyone help?

---

### Post by foogoo on 2010-03-03
Does anyone know why this happens? Is it a software or hardware issue? I have this occur every 2 weeks or so, I'll be doing things as usual then my HD will suddenly be unwritable and Ubuntu will start acting funny. Reboot, and I'd get this error. fsck usually fixes things, but only a matter of time until something important gets corrupted...

---

### Post by thomachan on 2010-03-10
I have the same problem,,.

fsck works once.. But when I reboot the same problem returns.. Please help me.. I am a complete newbie.

---

### Post by ChrisWlinux on 2010-03-19
> **ikt said:**
> in the terminal space below type
 
```
fsck
```
 
after it runs, ctrl+d, and you may have to do it again.
 
It should generally 'fix itself' after running fsck, as many people had this issue.
 
 
Thanks for posting this. I had the problem which, following your advice, I have now rectified.:p

---

### Post by mehmetbaris87 on 2010-03-19
> **ikt said:**
> in the terminal space below type

```
fsck
```after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.

thank you for this solution, it really works :))

---

### Post by fooliot on 2010-03-24
Yeah, it worked for me too, I'm just that smart to realize that you need to type in your root password before doing anything!! :) I'm now fine.  Thanks guys!

---

### Post by fiklein on 2010-03-24
I typed in "fsck", which led me to a bunch of prompts asking me to press "y" to fix things. It then prompted me to reboot, and everything works. Thank you very much. I had tried other things using the live cd and was about to type in another word beginning with f and ending in k. Saved me a reinstall. Thanks again.

---

### Post by b1lancer on 2010-03-24
Oh man, I was just hit by this on my desktop (again). But indeed the fsck works. Just follow the prompts after then.

> I typed in "fsck", which led me to a bunch of prompts asking me to press "y" to fix things. It then prompted me to reboot, and everything works. Thank you very much. I had tried other things using the live cd and was about to type in another word beginning with f and ending in k. Saved me a reinstall. Thanks again.
:p

I've tried that command for other problems and it doesn't work. Maybe one day soon enough it will for something.

---

### Post by JePro on 2010-03-26
> **ikt said:**
> in the terminal space below type

```
fsck
```after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.


hi, i tried the fsck and at the end it ask me to clear HTree index...

should i say yes? is it save to do so?

---

### Post by kakk on 2010-04-03
Well, this problem was announced in oct 2009, I upgraded my system to 9.10 a few weeks ago and know have the same issue. So it has been around for FIVE months and no actual fix? Does anyone know where the actual problem is and whether it will exist in 10.04 as well?

---

### Post by b1lancer on 2010-04-04
Within the past 2 weeks I've had this issue pop up 3 times. I have only seen it so far on my HP desktop. However, I have noticed a very interesting pattern: it seems that this problem correlates with an improper shutdown or if there is a power surge in my house. 

Let me explain. I came home the other day, and I saw that the power had gone out. When it came on, various devices had been turned on, including my desktop computer which had this error showing. On another occasion, the power strip was accidentally turned off and so when I reconnected it, the computer started up straight to the error. 

Mind you, fsck works like a charm. I just answer 'yes' after the command, and then reboot and done. But the time it takes is a bit of a nuisance.

---

### Post by freesitebuilder on 2010-04-04
Mine does it every time, unless I hit ESC at exactly the correct time ... the solution worked after a couple of tries, but it re-appeared almost immediately.

I'm really glad I switched to Ubuntu in 2006 - with the problems I've had on recent releases I wouldn't have stayed.

---

### Post by joepz on 2010-04-13
Worked like a charm for me too!

Thought I was getting crazy and began to sweat.
Using the CD start-up showed me nothing was wrong with HDD's as they existed.
Fortunately I could surf the net from CD.
But still do not believe this can happen.
Well
I survived.
Cheers

---

### Post by joepz on 2010-04-16
Mmmm,
Problem keeps coming back.
During a session it seems the drive is lost/dismounted. At certain point in time programs won't start anymore and files cannot be read.
restarting using the above commands doe shelp for a while, but seems to be something is structurally wrong.
 
I did a memory test, no problem and lately I added a 256MB ATI PCI videocard. Could this make it unstable? Removing it does not solve the problems. 
 
I go for a fresh install with 10.4 when available!
Good luck to you all.

---

### Post by Necoz on 2010-04-19
Thanks! i did really think i had to reinstall ubuntu and lose all my file and then i found fsck command and it fixed the problem, thanks again :D

---

### Post by tastybrains on 2010-05-19
> **ikt said:**
> in the terminal space below type

```
fsck
```

after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.
worked perfectly for me thanks

---

### Post by mark bower on 2010-11-21
fsck on the command line worked for me on first try in 9.10.  probably save about 3dys of reinstall (setting up apps etc) time!

I booted with a book laying on keyboard, and got the blue cmos screen.  i accepted settings (F10) since i had not changed anything, but when the computer continued to boot, stopped at the "Mount of filesystem failed . ." msg.  Ctrl-D did nothing at this point.

mark bower

---

### Post by majedaly on 2010-12-22
> **ikt said:**
> in the terminal space below type

```
fsck
```after it runs, ctrl+d, and you may have to do it again.

It should generally 'fix itself' after running fsck, as many people had this issue.
Thanks, that is a life saver. I encountered this bug after installing firewall starter.. Don't know if it is related

---

### Post by extraordinary_boy08 on 2011-02-04
happened to me too. The suggestion was useful. My pc worked well after doing the step here. Thanks!

---

### Post by link2yasar on 2011-06-14
Thanks fsck work for me.

---

