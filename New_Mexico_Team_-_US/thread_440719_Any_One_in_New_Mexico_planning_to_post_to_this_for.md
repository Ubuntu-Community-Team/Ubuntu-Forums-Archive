---
title: "Any One in New Mexico planning to post to this forum?"
date: 2007-05-11
forum: New Mexico Team - US
---

### Post by dthomasdigital on 2007-05-11
So let's post.

---

### Post by merlinus on 2007-05-12
OK.  I am posting.

If anyone lives near Santa Fe and is of a mind to help, I can sure use some assistance with getting Ubuntu to recognize and load my cd-burner.

I would also be interested in meeting local Ubuntu users in-person.

Many thanks!

-merlin

---

### Post by dthomasdigital on 2007-05-12
Were working on having in person meetings but right now were having trouble getting people juts to commit to signing up for the New Mexico Team.

I'd be glad to help with your cd-burner problem, can I get some details like make and model?

---

### Post by merlinus on 2007-05-12
Hi, and thanks for your response.  I posted this problem on the Ubuntu hardware forum and also at Launchpad, but no solutions so far.

I have a Plextor Plexwriter 24/10/40A, which is listed as being compliant with Ubuntu.

Feisty recognizes my DVD-ROM player, but not the cd burner, which is a separate drive.

The only entry in etc/fstab for this kind of device is:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

I have tried adding similar lines such as /dev/scd and dev/scd1, but get error messages that there are no such devices. 

In /media there is cdrom listed, but it is only a link to folder cdrom0.  /dev/cdrom properties says link to block device scd0.

I would be most grateful for any assistance.

Also, perhaps you can give me some details about what is involved in signing up for the NM team.

Many thanks!

-merlin

---

### Post by dthomasdigital on 2007-05-13
Well, I'm glad to try and help, after all that is what Ubuntu is all about.
I'm currently looking into your problem and your right Ubuntu should be compatible with your burner. Have you ever updated the firm ware on this device? I'll keep looking until we get it going.

The best way to join the team is.


Next go here [https://wiki.ubuntu.com/NewMexicoTeam]("https://wiki.ubuntu.com/NewMexicoTeam") follow the link to the mailing list and add yourself to the mailing list.

The next thing to do is register at Launchpad [https://launchpad.net/]("https://launchpad.net/") once you have registered go here to join Team New Mexico [https://launchpad.net/~ubuntu-newmexico]("https://launchpad.net/~ubuntu-newmexico")

Go to [http://myweb.cableone.net/dthomas]("http://myweb.cableone.net/dthomas") check out the links and contact section for other places to go.

Hope you join, and like I said if we can get the membership and interest up we will have in-person meetings.

---

### Post by merlinus on 2007-05-13
Hi, and thanks very, very much for your assistance.  I have not upgraded any firmware for the cd-burner.  

Sad to say, it works perfectly with Windows 2000, which is the only reason I have kept a dual-boot with Ubuntu.

Is there a terminal command that might give more information on whether it is a master or slave, or its own device entirely?

I have already signed up at launchpad, and am on the nm ubuntu mailing list, although I have not received anything other than the welcome message.

Anything else?

-merlin

---

### Post by dthomasdigital on 2007-05-15
Have you thought about a clean install of Ubuntu?

---

### Post by merlinus on 2007-05-15
After all my customizations, etc.?  No thanks!

Besides, there are a number of other forum members who are experiencing the same problem, with a variety of cd drives.

Interestingly, though, booting from the Knoppix live cd finds and mounts everything correctly, even my now never-used zipdrive.  Booting from the Ubuntu live cd does not.  So if that does not find and load my burner, why would a fresh install do anything different?

And the fact that the forum moderators have not responded to anyone posting about this issue makes me think it is a known bug in Feisty that will hopefully be fixed in Gutsy.

But perhaps there is some CLI command that will force Feisty to look for and mount drives?

Thanks anyway.

-merlin

---

### Post by dthomasdigital on 2007-05-15
Well I will not give up on your issue, I'm going to keep looking and looking. A fix is out there.

---

### Post by cmprather on 2007-05-15
YOOOOOOOOOOOOOo!!!!!!!!!!!!!!

nice to see some peeps in NM using Ubuntu.  i just upgraded from 6.10 to 7.04 today; kinda HAD to, as i got 6.10 out of whack while trying to update my Intel i915 video display.  7.04 doesn't do much better of a job with the graphics (trying to get 1440x900 out of it) but it's still better than using Windoze.

i'm gonna go post a question on Automatix on why my upgrade won't work ([www.getautomatix.com)](www.getautomatix.com)), just wanted to say hello all since the subject line asked for it!

*YAY* Linux!!!  i look forward to a Santa Fe Users Group sometime in the near future!!!

c-

---

### Post by dthomasdigital on 2007-05-15
fantastic, you got to join team New Mexico...come one come all

---

### Post by dthomasdigital on 2007-06-08
This is sad, you mean I'm the only person in New Mexico using Ubuntu?

---

### Post by Roger Gundberg on 2007-11-27
No. me too !
Roger-Socorro

---

### Post by dthomasdigital on 2007-11-27
Glad to see others on the forums

---

### Post by GrammatonCleric on 2007-11-27
It is alive!!!  =)

-GC

---

### Post by jimrz on 2007-11-28
Hi all ... still here, guess I don't check this section often enough, though I am on the forums pretty regularly.

@merlinus -

Have you tried copying the fstab line for your burner from knoppix and adding it to your feisty fstab? Probaby a long long shot, but forcing it to at least look for it could produce something. If yo give it a try, make CERTAIN that you backup your current fstab BEFORE attempting to edit. 
```
sudo cp /etc/fstab /etc/fstab-bak
```
That way, if it makes a mess you can boot recovery mode and reverse the process to get your current fstab back ... no harm, no foul

---

### Post by chrinabuntu on 2009-07-10
Hey everyone! I live in Alabama at the moment, and have been a member of the Alabama group for some time, but I am about to make a move to Albuquerque, NM, and would like to know if there is anyone in the ABQ area? It would be cool to meet some other Ubuntu folks...but I think it will be sometime in August before I get out there. 

I started out in Ubuntu when Gutsy was the new thing...and now I've been running with Hardy for a while.  I never did make the move to Intrepid for some reason, but I am about to jump to Jaunty. I tried it out on the live CD and it was awesome...and finally my wireless 'just worked' on my laptop! 

Also...I have found that Ubuntu/Linux is more 'guy world', but I am a chick. Just wanted to point that out in case there are any other female Ubuntu users out there. That would be cool too!  ;O)

I look forward to chatting with and possibly meeting some of y'all!  

Chris

---

### Post by chrinabuntu on 2009-07-10
Wow...I didn't realize no one has posted since '07!  Now I'm sad! 

Come on folks...wake up!  ;O)

---

### Post by dthomasdigital on 2009-07-10
Don't be to sad, we have a very robust Ubuntu group in New Mexico and LUG's all over the place. Your right are biggest fault is the forum. We have so much going on everywhere but here.

here is our wiki
[https://wiki.ubuntu.com/NewMexicoTeam](https://wiki.ubuntu.com/NewMexicoTeam)

We meet every Tuesday on IRC so come by.

Also we will be having a convention and expo in December, hope you can make it.

[http://www.newmexicognulinuxfest.org/](http://www.newmexicognulinuxfest.org/)

Talk at you soon....David

---

### Post by KegHead on 2009-07-10
Hi!

I'm not from NM, but it's one of the coolest places Ive visited.

I've been to ABQ and Santa Fe.

I missed the tram in ABQ-maybe next time.

If I ever move from the Land Of Lincoln-NM would be on my list.

KegHead

---

### Post by GrammatonCleric on 2009-07-11
damn that identi.ca and twitter!  =) 

Howdy and welcome!  

> **chrinabuntu said:**
> Wow...I didn't realize no one has posted since '07!  Now I'm sad! 

Come on folks...wake up!  ;O)

---

### Post by maskanh on 2010-01-06
I have a Plextor Plexwriter 24/10/40A, which is listed as being compliant with Ubuntu.

Feisty recognizes my DVD-ROM player, but not the cd burner, which is a separate drive.

The only entry in etc/fstab for this kind of device is:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

I have tried adding similar lines such as /dev/scd and dev/scd1, but get error messages that there are no such devices.

---

### Post by Objekt on 2010-03-09
Yes, I post often.  

Naturally, I cannot get to the NM LUG website at work.  They block just about anything useful.  From that I expect a lot of your can guess where I work.

---

### Post by vrkalak on 2010-05-11
I'm here.

Been using Ubuntu/Xubuntu/LinuxMint/Crunchbang for over a year now.

I'm an Xfce fanatic.

Live in Santa Fe and work in Albuquerque.

---

### Post by Nxion on 2010-05-13
Ill post as much as possible. Had some external issues that took up a lot of my time lol butI'm back now!

---

### Post by GrammatonCleric on 2010-05-13
I'd post to this more... but I have a job...and a twitter account.

=P

-GC

---

### Post by Objekt on 2010-05-13
I'm amazed this forum is even accessible where I work.  They like to block most things that are even remotely interesting.

---

### Post by GrammatonCleric on 2010-05-13
> **Objekt said:**
> I'm amazed this forum is even accessible where I work.  They like to block most things that are even remotely interesting.

Damn those IT people, like me!  =)

Or better, damn those auditors that make us filter.

-GC

---

### Post by Objekt on 2010-05-13
Don't misunderstand, I have NO problem with blocking stupid crap like Facebook, MySpace (the seedy boardwalk of the Internet), and other "social networking" (read: timewasting).  Or bandwidth-eating things like YouTube and Flash video in general.  And I wish I had such good antispam/phishing protection at home.  Our office Exchange server blocks or strips just about anything that could possibly be dangerous.  If it were my network, I sure wouldn't want people clogging the tubes with that stuff.

It does get a bit tiresome when I'm trying to research something for work, and find half the Google results blocked for no particular reason.  99% of the blocked site pages give no reason for blocking.  We're almost operating on a whitelist model here.

---

### Post by corvus85 on 2010-05-24
guess i'm way late to the party

---

### Post by GrammatonCleric on 2010-05-26
Better late then never.  =)

---

### Post by corvus85 on 2010-05-27
very true

---

### Post by chrinabuntu on 2011-03-11
> **dthomasdigital said:**
> Don't be to sad, we have a very robust Ubuntu group in New Mexico and LUG's all over the place. Your right are biggest fault is the forum. We have so much going on everywhere but here.

here is our wiki
[https://wiki.ubuntu.com/NewMexicoTeam](https://wiki.ubuntu.com/NewMexicoTeam)

We meet every Tuesday on IRC so come by.

Also we will be having a convention and expo in December, hope you can make it.

[http://www.newmexicognulinuxfest.org/](http://www.newmexicognulinuxfest.org/)

Talk at you soon....David

Gosh David...thanks for the reply! Now I'm the one who waited forever between posts! I'm here now but kind of forgot about the forum and never followed thru. But I'm back in the swing of things now. It would be cool to meet some folks! Are y'all still having meetings and stuff? I noticed some of the folks are pretty spread out. It would be hard to meet somewhere accessible to all in person. 

And vrkalak, do you really commute from SF to the Q every day? Yikes! I couldn't do that! 

Hey, are any of y'all using Maverick? I just posted under another thread about it so I don't want to post it all over the place, but was wondering what other folks' opinions are. I usually end up having issues after upgrading, so I was resisting this one, but was kind of reading around the internet to see what folks were saying, and then I just decided I might as well do it. I haven't had time to really see many differences, but in my case that's good...means nothing seems to be broken! *so far!*  I know the photo viewer app is different...but I don't know what else really. 

Chris

---

