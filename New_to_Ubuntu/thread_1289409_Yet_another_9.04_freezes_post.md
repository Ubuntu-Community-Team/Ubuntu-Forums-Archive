---
title: "Yet another 9.04 freezes post"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by barbapapa1 on 2009-10-12
Hi,
  I apologize for being yet another person to post on this subject, but I seem unable to fix this one no matter how many posts I read.  This is becoming too much, and will either need to roll back to 8.04 or switch to win7 coming up.  So my last cry for help.

Bottom line:
   Ever since I upgraded to 9.04(from 8.04) my machine locks up at least once per day.  I can still move my mouse, but cannot do anything with it, nor launch a terminal. The only way out is REISUB.  I never had this problem with 8.04.  I believe this is just the GUI locking up because when I am streaming music it continues to stream after the screen freeze has occured. I have a hp dv1300 with 2gb and 100gb.  I use wubi.  All was rosy on 8.04.

  I have read endless posts on how to deal with this, but nothing was clear.  I switched off all visual effects.  It feels like this problem is reasonably widespread, can someone provide a clear trouble shooting guide?

  Please...

---

### Post by coldReactive on 2009-10-12
Canonical wouldn't post support because they make you pay for support, hence why they don't post anything.

Patience is a virtue.

---

### Post by barbapapa1 on 2009-10-12
> **coldReactive said:**
> Canonical wouldn't post support because they make you pay for support, hence why they don't post anything.

Patience is a virtue.

--------------------------------


Good point, I changed the post to reflect your comment.  I am really just looking for the answer.  Thx.

---

### Post by Hated On Mostly on 2009-10-12
You can try following this guide:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

It may or may not work for you. Jaunty didn't work on my system either (I didn't try that guide). The 9.10 Karmic Koala beta is working fine on my system so I would recommend waiting for the final release and seeing if that solves the problem.

---

### Post by sydbat on 2009-10-12
You also mention that you are running it through wubi. That could be the source of all your problems. Because Windows file systems fragment horribly, it likely corrupted your Ubuntu wubi install.

---

### Post by barbapapa1 on 2009-10-12
Thanks for the link to the guide, but it did a pretty good job of scaring me off!  Did you also have the same problem as me with the screen freeze or just performance issues.  If it was the same I have hope for the new release, although I wonder why they wouldn't have fixed 9.04 considering how popular this problems seems.

---

### Post by barbapapa1 on 2009-10-12
I guess it is possible that wubi could be the problem, but it wouldn't be my first thought as I hardly run windows(important to have it occassionally), and problem started straight away when I upgraded.  Would rather chase down a few other paths before the full reinstallment effort as you could imagine.

---

### Post by DrDevice on 2009-10-12
Have you tried a clean install of 9.04?  From Windows to Linux, I find that upgrading instead of a clean install usually gives me issues.  Back up your home directory (if possible) and try a clean install instead.  (my 2 cents)

---

### Post by Hated On Mostly on 2009-10-12
> **barbapapa1 said:**
> Thanks for the link to the guide, but it did a pretty good job of scaring me off!  Did you also have the same problem as me with the screen freeze or just performance issues.  If it was the same I have hope for the new release, although I wonder why they wouldn't have fixed 9.04 considering how popular this problems seems.


I had a less severe freezing issue which was helped but not alleviated by disabling desktop effects and using Metacity. However, I was more concerned about the data corruption bug in Jaunty which I think my system was prone to as programs started crashing with segmentation faults which never happened in Hardy, Intrepid, or now in Karmic Koala. Luckily, the bug didn't fully effect me as I had no data loss, but I didn't use Jaunty for more than a week anytime I did a full install of it, so I didn't get a chance to fully see the extent of the problem.

Keep in mind I didn't try Jaunty until June/July so there were plenty of updates and none of them resolved the problems I and others were seeing. Jaunty was a very buggy and bad release for a lot of people.

---

### Post by barbapapa1 on 2009-10-12
> **Hated On Mostly said:**
> I had a less severe freezing issue which was helped but not alleviated by disabling desktop effects and using Metacity. However, I was more concerned about the data corruption bug in Jaunty which I think my system was prone to as programs started crashing with segmentation faults which never happened in Hardy, Intrepid, or now in Karmic Koala. Luckily, the bug didn't fully effect me as I had no data loss, but I didn't use Jaunty for more than a week anytime I did a full install of it, so I didn't get a chance to fully see the extent of the problem.

Keep in mind I didn't try Jaunty until June/July so there were plenty of updates and none of them resolved the problems I and others were seeing. Jaunty was a very buggy and bad release for a lot of people.

Thanks for the info.  I am not sure the best course of action to take.  I did see that 9.10 has some updates for intel which may be the answer.  Realistically I probably have to roll back, but I have been hoping for a fix as opposed to the hassle of a wiping the slate clean and starting over.

---

### Post by deancasino on 2009-10-12
> **barbapapa1 said:**
> Hi,
  I apologize for being yet another person to post on this subject, but I seem unable to fix this one no matter how many posts I read.  This is becoming too much, and will either need to roll back to 8.04 or switch to win7 coming up.  So my last cry for help.

Bottom line:
   Ever since I upgraded to 9.04(from 8.04) my machine locks up at least once per day.  I can still move my mouse, but cannot do anything with it, nor launch a terminal. The only way out is REISUB.  I never had this problem with 8.04.  I believe this is just the GUI locking up because when I am streaming music it continues to stream after the screen freeze has occured. I have a hp dv1300 with 2gb and 100gb.  I use wubi.  All was rosy on 8.04.

  I have read endless posts on how to deal with this, but nothing was clear.  I switched off all visual effects.  It feels like this problem is reasonably widespread, can someone provide a clear trouble shooting guide?

  Please...


Alright dude, I was you a week ago, I upgraded to Karmic beta and I haven't had one single lock up since. They seem to have done A LOT of work in this area.

---

### Post by ConXtionS on 2009-10-12
Never give up

never surrender

---

### Post by Hated On Mostly on 2009-10-13
> **barbapapa1 said:**
> Thanks for the info.  I am not sure the best course of action to take.  I did see that 9.10 has some updates for intel which may be the answer.  Realistically I probably have to roll back, but I have been hoping for a fix as opposed to the hassle of a wiping the slate clean and starting over.

I would have stayed with Intrepid if it wasn't for certain updated software that only worked with Jaunty/Karmic packages. Karmic and the 2.6.31 kernel have some other fixes that I want as well so going back to an older release is not an option for me anymore.

If the stable release of 9.10 Karmic Koala doesn't work for me I would switch to openSUSE 11.2 which comes out next month. I tried the milestone 8 release and it worked great. A lot of the other non-Debian/Ubuntu distributions did not display the problems that appeared in Jaunty. You just need to weigh your needs and wants and pick which solution is best for you. I prefer Ubuntu, but I most prefer a stable, working computer  that I am not constantly figuring out how to workaround bugs, so I will switch if need-be. Hopefully Karmic and the next LTS release will end any consideration of using another distribution for me.

Good Luck

---

### Post by anewguy on 2009-10-13
> **ConXtionS said:**
> Never give up

never surrender

And always carry a space gun that looks like a big submarine sandwich!

(sorry, I couldn't resist!)

dave :)

---

### Post by barbapapa1 on 2009-10-13
> **deancasino said:**
> Alright dude, I was you a week ago, I upgraded to Karmic beta and I haven't had one single lock up since. They seem to have done A LOT of work in this area.

Mr Dc,  Very interesting that 9.10 could solve my lock up problems.  Were you locking up daily as well?

---

### Post by ububaba on 2009-10-14
> **barbapapa1 said:**
> Mr Dc,  Very interesting that 9.10 could solve my lock up problems.  Were you locking up daily as well?

I get every imaginable lockup problem. If salvation is in the installation 
of 9.10, so be it. You wouldn't be lying. Drinks will be on the house.

---

### Post by deancasino on 2009-10-16
> **barbapapa1 said:**
> Mr Dc,  Very interesting that 9.10 could solve my lock up problems.  Were you locking up daily as well?

Daily? No, 3-4 times a day, I'm going on week 2 with Karmic and still no lockups.

---

### Post by kgarbutt on 2009-10-16
As for my system, I am using 9.10 Karmic and it freezes my display while the computer is idle. Interesting, 9.04 on the same computer never did this. I am waiting to see how the final release of 9.10 will perform.

---

### Post by frank002 on 2009-10-16
You say you upgraded from 8.04 to 9.04.  You have to go from 8.04 to 8.10 to 9.04 if I am not mistaken.  Also, I think a clean install will be much better. Just my 2 cents worth. Good luck.

---

### Post by youthforlinux on 2009-10-16
Jaunty's Intel Driver has been giving a lot of people I know problems.  Some downgraded to Intrepid, and one tried the 2.6.29 kernel, but using karmic seems to have solved the Intel video card driver much better.

---

### Post by barbapapa1 on 2009-10-18
> **frank002 said:**
> You say you upgraded from 8.04 to 9.04.  You have to go from 8.04 to 8.10 to 9.04 if I am not mistaken.  Also, I think a clean install will be much better. Just my 2 cents worth. Good luck.

Yes, I did the serial upgrade, but never really ran on 8.10.  Was going with the 8.04 is a LTS and it is working so I should just leave it alone, but my inner geek got the best of me and next thing you know I was up to 9.04.  I will give 9.10 a try otherwise roll back to 8.04.  However, I am not really holding my breath as this trouble with intel video seems fairly well known so wouldn't they release the fix in 9.04??

---

### Post by igknighted on 2009-10-18
> **barbapapa1 said:**
> Yes, I did the serial upgrade, but never really ran on 8.10.  Was going with the 8.04 is a LTS and it is working so I should just leave it alone, but my inner geek got the best of me and next thing you know I was up to 9.04.  I will give 9.10 a try otherwise roll back to 8.04.  However, I am not really holding my breath as this trouble with intel video seems fairly well known so wouldn't they release the fix in 9.04??

They can't.  When that version was released, the current intel driver was in transition, so they had to make a choice.  Either use an old driver, which would preclude many from using Ubuntu at all due to a lack of support for modern cards with the older driver, or use a driver known to have issues.  There was no god answer.  The problem is, to fix the problem and get a more stable driver into 9.04, you would need to upgrade a significant portion of x.org, as the driver is tied to that.  This would require a ton of testing to ensure that there weren't more regressions than you were fixing, as that is a major change, and affects far more than just intel users.

There are PPA's (xorg-edgers for example) that allow you to make this change yourself, unofficially.  But anytime you upgrade major system components, be careful, because things can break if you make a mistake.

EDIT:  While Wubi is great for trialing ubuntu, it isn't a good long term solution.  Performance is poor, and it is subject to file corruption.  Also, while upgrading is certainly possible, many experienced users back-up and do a fresh install because there are often mistakes in the upgrade.  This is the case with any OS really, very few Windows or OSX users will use the "upgrade" feature instead of a clean install for the same reason.  Usually best to start fresh whenever possible.

---

### Post by barbapapa1 on 2009-10-19
> **igknighted said:**
> They can't.  When that version was released, the current intel driver was in transition, so they had to make a choice.  Either use an old driver, which would preclude many from using Ubuntu at all due to a lack of support for modern cards with the older driver, or use a driver known to have issues.  There was no god answer.  The problem is, to fix the problem and get a more stable driver into 9.04, you would need to upgrade a significant portion of x.org, as the driver is tied to that.  This would require a ton of testing to ensure that there weren't more regressions than you were fixing, as that is a major change, and affects far more than just intel users.

There are PPA's (xorg-edgers for example) that allow you to make this change yourself, unofficially.  But anytime you upgrade major system components, be careful, because things can break if you make a mistake.

EDIT:  While Wubi is great for trialing ubuntu, it isn't a good long term solution.  Performance is poor, and it is subject to file corruption.  Also, while upgrading is certainly possible, many experienced users back-up and do a fresh install because there are often mistakes in the upgrade.  This is the case with any OS really, very few Windows or OSX users will use the "upgrade" feature instead of a clean install for the same reason.  Usually best to start fresh whenever possible.

Thanks for the explanation.  That was what I was trying to get to the bottom of.  Also, your points are well noted regarding clean installs, back-ups, etc.  Truth is that I originally loaded up 8.04 with WUBI one day, and it seemed to work so I didn't touch it.  My better judgement told me not to move to 9.04 like that, but I was on a hot streak so I pushed it.  Also, I only ever backed up my personal files, and figured one day I would have to sort it all out.  Looks like that day has arrived.  Thanks again.

---

