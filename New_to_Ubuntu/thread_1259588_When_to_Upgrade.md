---
title: "When to Upgrade?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by stormvinyl on 2009-09-06
Hi everyone.  I have a question about upgrading while using Ubuntu.  I am currently using 8.04 and am very happy with the results.  I am running it on a dell inspiron 6000 and the computer is working great.  There have been several automatic updates that have happened since I installed ubuntu.  My question is, how should I handle the major updates such as going to 8.10, 9.04 or even 9.10.  I realize and understand about the version and how they are constantly updated for so many years and how some others are not really supported.  I guess one thing Im worried about is if I do update to a newer version, do I have to do a clean install or will the operating system simply install over the existing version?  And, should I even worry about it until the formal support for my version expires?  Thanks again for all the help.

---

### Post by scragar on 2009-09-06
It's a good idea to upgrade your operating system around a week to a month after the official release if you want to make sure all the major problems have been fixed(depending on how many problems are reported, and how quickly they are fixed).
Do not wait until your release is no longer supported, this will make upgrading harder than it has to be, and upgrading multiple versions at once is a pain.

If you have a seperate /home partition then by all means install again over the old install and reinstall anything you're missing(slower, but gives cleaner results).
If you don't have a seperate /home partition back-up anything you need, just incase there's a problem, and use the updater to update to the latest release.

---

### Post by Cresho on 2009-09-06
Just 3 letters for you.

LTS

---

### Post by cariboo on 2009-09-06
THe version you are using, 8.04 is a Long Term Support release, it will be supported until 2011, so you have a while before you need to upgrade. If you do decide to update to 9.10 when it is released, you need to do it in stages. 8.04-->8.10-->9.04-->9.10.

I would suggest you read the release note of each version, so you will know what if any problems you will run into after the upgrade.

---

### Post by halitech on 2009-09-06
do any of the updates in the newer versions really give you any benefits? Are there features that you need that are not currently in the version you are using? If the answer to either is no, stick with 8.04 LTS and when the next LTS release comes out, it will prompt you to ugrade at that time. If 8.10 or 9.04 have features or newer software you need, then upgrade now.

---

### Post by konqueror7 on 2009-09-06
my advice would be doing a backup and do a clean install - less headache. i'm not saying that upgrading an existing system to a new version is not possible, but there has been know complication in doing this. so i suggest doing a clean install. =)

---

### Post by RedRat on 2009-09-06
Here I must take a more conservative approach. I would stay with 8.04 (as you can see from my profile that is what I use). A perusal of these forums and a look at the ubuntu newsgroup will show you that many who have a good working version of 8.04 have had difficulties moving up to 8.10 and to 9.04. I fully expect that going to 9.10 will have it sets of problems. Updates for some machines can be a difficult experience.

On the other hand, what is it you want from an operating system? Are you using Ubuntu 8.04 as a functional system that allows you to do everything that you must do? Surf the internet, email, photo or music manipulation, etc? If it is working for you, why change? Don't fix what ain't broken, to quote the old philosopher.

Before you do upgrade, make sure that you are doing so for a very good and strong reason. I feel that upgrading for the sake of upgrading is a dangerous motive. Perhaps you might want to do it for the challenge; well OK, but prepared to spend many hours here in the forum.

---

### Post by misfitpierce on 2009-09-06
I would say go ahead and upgrade to atleast 9.04 now... Everything should be fine in those OS's by now or you can stick with the LTS 8.10 release for awhile till the next LTS release. It's really up to you but 9.04 had all my stuff working instantly which was not like that back on 8.04 and everything is speedy and working great.

---

### Post by halitech on 2009-09-06
1 thing to keep in mind is the hardware. If they have an "older" ati card or an intel onboard graphics card, upgrading to 9.04 will be a headache for them so staying at 8.04 may be a better option unless they want to either spend a fair bit of time fixing things, or buying a new card.

---

### Post by fela on 2009-09-06
No, don't upgrade if your current system is working fine and is supported.

When I was using intrepid ibex I made the mistake of updating to jaunty jackalope and my graphics tablet completely broke, as well as my audio going choppy due to high latencies.

I'm on debian now, I'm a bit sick of Ubuntu. I love Debian's ultra slow release cycle, it makes the OS feel much more stable and mature.

---

### Post by fela on 2009-09-06
> **RedRat said:**
> Before you do upgrade, make sure that you are doing so for a very good and strong reason. I feel that upgrading for the sake of upgrading is a dangerous motive. Perhaps you might want to do it for the challenge; well OK, but prepared to spend many hours here in the forum.

+1, wise words.

My philosophy is to have a stable partition with stable software and a testing partition with bleeding edge software. I'm gonna install debian experimental to the bleeding edge partition.

---

### Post by ugm6hr on 2009-09-06
> **stormvinyl said:**
> I am currently using 8.04 and am very happy with the results.

This is a nice tone of phrase, and tells me all I need to know.

Keep with 8.04LTS until the next LTS reaches a .1 release (i.e. 10.04.1 in July 2010).  You will be able to upgrade directly from 8.04 to 10.04 when the time comes.

As you say, the automatic updates are important for stability and security.

If the quoted section above ever becomes untrue, ask again.

---

### Post by Bölvaður on 2009-09-06
> **konqueror7 said:**
> my advice would be doing a backup and do a clean install - less headache.

But if you do not want to do that and still want to use Long Term Services to avoid constantly upgrading, then the following is your ultimate solution:

**Upgrade via Update Manager to next LTS**

Open the update manager (system &#8594; administration &#8594; update manager) and click the *Settings* button on bottom of the window. There change *Release Upgrade* to *Long Term Support Releases only*.
Then when next LTS comes out it will prompt you to upgrade via update manager by a simple click of the button and entering your password. Then all your repos will be redirected to the next lts release instead of the old one and hence, all software will be updated with ease.

Just wait a month after the release for the bugs that will be found the first week of release and see if they get fixed or if they will affect you.

---

### Post by zhanglini on 2009-09-06
I don't mean to hijack the topic, but this is related to upgrading:
I have deleted some apps such as GIMP cuz I have no use for them and want to keep my system clean.  Would upgrading reinstall these apps automatically, cuz they are by default in the package?
Thanks

---

### Post by scragar on 2009-09-06
In my experiences upgrades wouldn't reinstall anything unless there's a dependency for it that's not met.

---

### Post by halitech on 2009-09-06
if you had removed (k)(x)Ubuntu-desktop then it shouldn't. the ubuntu-desktop is a metapackage that lists all the installed programs so if its gone, only the apps you have installed should be updated.

---

### Post by Wataru8675 on 2009-09-06
Here's another question about upgrading:
 
I just bought a new laptop and would like to dual boot Ubuntu on this guy (I found with my last laptop that having JUST Ubuntu is a pain in the rear if you don't know all of what you're doing).  Should I wait until November (a month after 9.10) to download Karmic, download Jaunty now, or can I go and download 8.04LTS (I think that was the last LTS, at least...)?  My guess is the consensus on the forum would be to download the last LTS because of its ease of upgradability and stableness.  Can I just get the download from Ubuntu.com, if that is the case?

---

### Post by Jimmyfj on 2009-09-06
We are at Alpha 5 right now. And so far I for one have not had any major issues with Karmic. It runs great - But unless you like to live on the edge of a possible system-break-down, you'd better stay safe and not upgrade until absolute necessary. The changes from Jaunty to Karmic are not much for the eye as for the system itself. Karmic sets new boot-speed-record yet again. Other than EXT4 being default FS and a change in boot loader to GRUB 2.0 nothing much is visible for the naked eye.

---

### Post by Garrovick on 2009-09-06
I've upgraded from 8.04 to 8.10 to 9.04 just to update and for some thing to do as soon as they are released. For 9.10, I'll wait for the DVD.

---

### Post by konqueror7 on 2009-09-07
> **Wataru8675 said:**
> Here's another question about upgrading:
 
I just bought a new laptop and would like to dual boot Ubuntu on this guy (I found with my last laptop that having JUST Ubuntu is a pain in the rear if you don't know all of what you're doing).  Should I wait until November (a month after 9.10) to download Karmic, download Jaunty now, or can I go and download 8.04LTS (I think that was the last LTS, at least...)?  My guess is the consensus on the forum would be to download the last LTS because of its ease of upgradability and stableness.  Can I just get the download from Ubuntu.com, if that is the case?

yes, it would be better to get the latest lts version. oh, and don't forget to try it first via liveCD, in case any hardware or driver issues comes up.

---

### Post by louieb on 2009-09-07
lol - Its been my experience the best time to upgrade is right after doing a a full backup. 

Three years of using Ubuntu on desktop and laptop. About 60% of the time upgrades go without a hitch.  About 20% had minor problems easily fixed. The others - well sure glad I took the the time to backup.

---

