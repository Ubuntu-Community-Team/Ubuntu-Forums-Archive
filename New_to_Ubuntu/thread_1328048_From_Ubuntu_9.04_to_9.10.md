---
title: "From Ubuntu 9.04 to 9.10"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by halovivek on 2009-11-16
Hi
This really a big problem for me from ubuntu 9.04 to 9.10.
In one of my system i tried with new installation of 9.04 and i have updated the ubuntu to 9.10.
Then it asked for upgrade. I checked whether all the updates has done successfully. It is done .
Then i gave to upgrade from ubuntu 9.04 to 9.10. 
I have downloaded the image 9.10 from ubuntu and i have burned it.
I checked the CD by running live. It went fine.
But when i insert the CD for upgrade it did not took it. 
So i done through internet.
It gave me the grub 2 Error 15. I tried to fix the grub by getting help from internet but went in vain. So i reinstalled the ubuntu 9.04 and i am using that one.
Now i am having the same ubuntu 9.04 in laptop.
Could you please help me fix this problem without getting error Grub 2.

In laptop i am having windows vista is another OS. I am using for official purpose. I don't want to lose ubuntu 9.04 because i am using that for most purpose of my personal work and i do have my mails.

can you please tell me how to fix this problem or action to be taken so that i cannot get the Grub 2 error in my laptop.

My data is valuable in ubuntu 9.04 because i have installed most precious software in ubuntu.

---

### Post by skymera on 2009-11-16
Try doing a fresh install from the LiveCD. Bit of a pain yes, but i always advise fresh install.

Download in Vista and burn using IMGBurn at 4x speed, then reinstall.

---

### Post by bernardfrancois on 2009-11-16
If you don't want to loose all your data, you could run a live session and copy your files to an external hard disk (or other medium).

Before reinstalling everything, you could try to fix the problem. Maybe the following thread will help:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by halovivek on 2009-11-16
HI all,
In my laptop ubuntu 9.04 is used from the release date.
Can I upgrade the GRUB 2 from GRUB 1 and try to upgrade.
Will this help me to solve the problem?
Thanks

---

### Post by theozzlives on 2009-11-16
Although 9.10 looks nice, it's very buggy. If computing is that important, I'd stick with 9.04 for now. I went back and am waiting for 10.04.

---

### Post by t0p on 2009-11-16
> **theozzlives said:**
> Although 9.10 looks nice, it's very buggy. If computing is that important, I'd stick with 9.04 for now. I went back and am waiting for 10.04.

This is not advice, it is *opinion*.  Some people find 9.10 buggy, others find it works fine.  Who knows which will apply to the OP.  I don't neither does theozzlives.

I'll give you some advice.  Some users, me included, find that upgrade never works satisfactorily.  This can especially be the case if you have a lot of personal configuration or a lot of locally-installed software (ie not from the repos).  In such cases, a fresh install is preferable.

If you back up your /home directory, you should be able to slot it into your 9.10 install.  Or you can back up files individually.  Unfortunately, you'll have to reinstall all the software you got before.  A pain, I know.

To get a list of all your software before you reinstall, type into a terminal:

```
dpkg --get-selections > apps.txt
```

This will write a list of installed packages to a file called 'myapps.txt'.  If you copy that list to a usb stick or something, then after you reinstall you can check that list and reinstall everything listed.

---

### Post by theozzlives on 2009-11-16
It is to advice! The OP said he wanted a reliable computer to do his work on. I interpret that as he would prefer that to "cutting edge" where he constantly has to work around problems. Jaunty is the best answer for that for now.

---

### Post by Paqman on 2009-11-16
> **t0p said:**
>   Some people find 9.10 buggy, others find it works fine.

Based on responses in this forum, around 70-80% of people report no problems with Karmic, which is comparable with earlier releases.

Personally I think its a credit to the devs that they managed to maintain that kind of quality, given that they changed several major system components for Karmic (ie: Grub, HAL, Ext4, xsplash...)

---

### Post by halovivek on 2009-11-16
Ok can you please tell me. 
1. First upgrade from GRUB 1 to GRUB 2
2. Then run the system upgrade
3. After reboot will my system will work fine again?

---

### Post by ArinSky on 2009-11-16
> **Paqman said:**
> Based on responses in this forum, around 70-80% of people report no problems with Karmic, which is comparable with earlier releases.

Personally I think its a credit to the devs that they managed to maintain that kind of quality, given that they changed several major system components for Karmic (ie: Grub, HAL, Ext4, xsplash...)

But what % then do you figure jaunty is at? i'd guess higher.

just sayin...


also, you shouldn't need to upgrade grub1 to grub2, that should be part of the upgrade. I agree with skymera that you should just save all your data and do a fresh install.

---

### Post by kansasnoob on 2009-11-16
I actually agree with theozzlives regarding Karmic being buggy. I've been around since Gutsy and I've never seen anyone start a poll regarding whether this release would harm Ubuntu's reputation before.

I'd personally recommend to anyone staying with 8.04, 8.10, or 9.04 unless they're having specific problems that they think may be resolved in 9.10.

But let's address issues. If you upgrade a Jaunty w/legacy grub Karmic should still have legacy grub after the upgrade. If you upgrade a Jaunty w/grub2 then Karmic will have grub2.

Why do you want grub2 so badly?

I'm more concerned about the method(s) you're using to upgrade. You can not just upgrade Jaunty to Karmic using the Live CD. Did you then just try to upgrade through the Update Manager?

As I said, updating through Update Manager should not change grub versions. I'd like to see the results of the Boot Info Script performed using a Live CD on the computer with the failed upgrade.

Instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2009-11-16
Please let's not hijack this thread into who loves or hates Karmic, OK :D

We should perhaps just point out that any upgrade, reinstall, etc has the potential of causing loss of data, and that apps will often have to be reinstalled after an upgrade.

Eye on the ball everyone.

Thanks.

---

### Post by arashiko28 on 2009-11-16
You can run install and do not I repeat [COLOR="Red"]**DO NOT**[/COLOR] mark the format box. If you do that everything will be lost. Just choose the same partition as 9.04 and if you have 2 partitions like I do, mark the filesystem / and the home /home, leave the rest as is, do not mark the format box!!!
I got all of my files as I left them, and even when installed back the packages, I got the same configuration as before.

P.D: Always backup all of your precious data.
Best of lucks:p

---

### Post by dca on 2009-11-16
I just can't recommend upgrades through 'update manager'...  Too many architectural changes (as mentioned in previous posts) and as I've said, it rarely works the way you expect it in Windows or MAC so why should I expect the same in desktop Linux...

---

### Post by bodhi.zazen on 2009-11-16
Actually I find upgrades go smoother in Ubuntu then they ever went in Windows.

I have an install where I have gone 8.04 -> 8.10 -> 9.04 -> and now 9.10 without a major problem, although I did have some problems with the 9.10 upgrade (upgraded too early).

I think one of the biggest potential pitfalls in upgrading - Upgrading too early.

IMO many people upgrade when Ubuntu is still in pre-release (Alpha, Beta, RC) and then run into bugs ...

If you wait at least a week AFTER the release you will have better luck.

---

### Post by kansasnoob on 2009-11-16
> **bodhi.zazen said:**
> Actually I find upgrades go smoother in Ubuntu then they ever went in Windows.

I have an install where I have gone 8.04 -> 8.10 -> 9.04 -> and now 9.10 without a major problem, although I did have some problems with the 9.10 upgrade (upgraded too early).

I think one of the biggest potential pitfalls in upgrading - Upgrading too early.

IMO many people upgrade when Ubuntu is still in pre-release (Alpha, Beta, RC) and then run into bugs ...

If you wait at least a week AFTER the release you will have better luck.

That actually sounds quite right!

I had almost no problems with upgrading Hardy > Intrepid > Jaunty. And the problems I did have were easy to fix.

Sadly I started with Gutsy, I believe I had about 26 machines (seniors machines) on Gutsy working quite well when Hardy came out.

My initial upgrade went well so I ran around the county and upgraded everyone. Worst mistake I ever made! It was about a 50/50 deal.

It appears that upgrading from Jaunty to Karmic may be similar, but I must stress I've only done two such upgrades just for testing.

But in this case lets see what's going on, eh?

Tried to update using the Live CD??????

Let's see what's where on the box. The Boot Info Script will fill us in!

---

### Post by mivo on 2009-11-16
> **bodhi.zazen said:**
> Actually I find upgrades go smoother in Ubuntu then they ever went in Windows.

Service Packs never caused as many problems as upgrading Ubuntu. Most people stopped bothering upgrading and just do clean reinstalls. Also, in Ubuntu you go through this every six months, with Windows every 3-5 years.

Anyway, I agree with upgrading (in whatever way) only after some time. I'd not wait just a week, but at least a month. Also, always make a separate /home partition. 12-15 GB (it's almost too much) is a good size for /, swap depending on your needs, and the rest for /home. For some people a separate /var partition is useful, but the majority of users doesn't need that.

---

### Post by bodhi.zazen on 2009-11-16
Well, service packs are more akin to apt-get dist-upgrade where as what we are talking about (upgrading) is more akin to upgrading from Windows XP -> vista

apt-get update = service pack

upgrade = Ubuntu 9.04 -> 9.10 or Windows Vista -> 7

I have not upgraded XP -> Vista or Vista -> 7 , but previous windows upgrades went horrible.

---

### Post by Paqman on 2009-11-17
> **ArinSky said:**
> But what % then do you figure jaunty is at? i'd guess higher.


Nope. Karmic actually rates marginally higher overall than Jaunty. In fact it had a higher percentage of flawless installs than any previous release going back to Gutsy.
[URL="http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html"]
Statistical analysis of ubuntuforums.org release polls[/URL]

Don't believe the hype ;)

---

### Post by mivo on 2009-11-17
People with broken systems or no internet access have bigger problems than to vote in polls, or simply can't do it at all, so people without problems are over-represented.

Or you could argue that satisfied users do not read the forums, so people with issues are over-represented.

Polls of this kind are tiny, imbalanced statistical samples that offer very little value, and you can interpret them in any way that fits your own opinion. Their meaning is limited to the group that voted (and feels strongly enough to vote in the first place, so it's a large group of either enthusiasts or frustrated users), but as the participants were not properly selected, the results are not representative of the community as a whole and cannot be applied to it.

---

### Post by Nightstrike2009 on 2009-11-29
Personally I am disgusted with Canonical for releasing 9.10 in this state, I was happy with 9.04 3G Internet worked as did bluetooth, I "Upgraded" (Cough) to Ubuntu 9.10 and couldn't connect to internet, Blutooth down and sound issues too.

I may one day return to Ubuntu 10.4 (after a lot of caution) but for now I have migrated to Linux Mint 7, Internet connectivity should be a priority with a system reliant on internet for upgrades and programs (How do you download the fix when its available if you can access the net?) 

Is Ubuntu trying to lose its reputation with the notebook / laptop market on purpose?

PS: Thank god i can dual boot with Xp, this kind of behaviour buggy OS requiring urgent fixes is the reason, I left windows (for the most part) to use Linux in the first place.

Disgusting and unacceptable I have lost many converts to Linux due to Ubuntu 9.10 and I myself am sick of this "Working in one release, broke in the next release" mentality Ubuntu seem to suffer from. GET A GRIP, GET IT SORTED BEFORE RELEASE! :(

---

### Post by halovivek on 2009-11-30
I upgrade the ubuntu 9.04 then i upgraded the ubuntu 9.10.
First thing i lost is screen went blank.
So i have to reinstall the whole system. So i took back up of data only. nothing more.
I did a fresh installation of ubuntu 9.10.
I personally feel ubuntu 9.10 is not that much stable release as 9.04.

---

