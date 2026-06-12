---
title: "Update Manager-How much of this stuff do I actually need?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by ParadoxBlue on 2010-07-16
Recently installed Ubuntu and the update manager runs quite a bit more often than I thought it would. I'm just curious as to how many of these updates I actually need. Many of the "security updates" don't seem to have much to do with security from the descriptions. I realize a lot of these updates aren't anything new but just changes to what is already installed on my system and possibly adding a bit or so. I've already turned off the "pre-released/proposed updates". A beta tester I am not.

Anyway was just wondering. I'm a recent convert from Windows (haven't really missed it yet either) and the update feature in that OS was always a pain. For some reason Microsoft assumes that everyone has a hard drive the size of a small country.

---

### Post by kerry_s on 2010-07-16
once a version is released, it only gets security updates/fixes.
if you don't care about those things, don't update.

---

### Post by bodhi.zazen on 2010-07-16
> **ParadoxBlue said:**
> Recently installed Ubuntu and the update manager runs quite a bit more often than I thought it would. I'm just curious as to how many of these updates I actually need. Many of the "security updates" don't seem to have much to do with security from the descriptions. I realize a lot of these updates aren't anything new but just changes to what is already installed on my system and possibly adding a bit or so. I've already turned off the "pre-released/proposed updates". A beta tester I am not.

Anyway was just wondering. I'm a recent convert from Windows (haven't really missed it yet either) and the update feature in that OS was always a pain. For some reason Microsoft assumes that everyone has a hard drive the size of a small country.

It is very refreshing to see such a perspective.

It seems new users are almost obsessed with updates.

Personally, I set my system to automatically perform security updates only (I am paranoid that way).

The rest of the updates I review.  I update every 2-4 weeks.

If you are not running any servers (ssh , apache, mysql) and it is not broken, there is not need to update. If you are running servers, there tend to be fewer updates and some of those updates are more important then the average update to a desktop, IMO at least.

---

### Post by 3rdalbum on 2010-07-16
1. The labels used are "Security updates" and "Recommended updates". This gives you some clue as to whether you should install them or not.

2. Hard disk space is not an issue with updates. Each update simply replaces the older package. Running a set of updates that is 200mb to download might only use an extra 2mb of space.

3. Number of updates is a good thing, not a bad thing. Everybody likes bug fixes.

---

### Post by lolzwut on 2010-07-16
i dont know the answer sorry about that

---

### Post by k3lt01 on 2010-07-16
> **ParadoxBlue said:**
> Recently installed Ubuntu and the update manager runs quite a bit more often than I thought it would. I'm just curious as to how many of these updates I actually need.

Security updates aside, only because they are a necessary evil, I would say you only need to update the programs, and dependencies, you want to use. My laptop is set up very differently to my desktop so the updates for one are very different for the other (e.g. my laptop has OpenOffice while my desktop doesn't so only one of them will get OpenOffice updates). Therefore may I suggest you continue looking through Ubuntu and see what you actually use in it, anything you don't use un-install and then you may find your updates will reduce in size and number.

---

### Post by soldier1st on 2010-07-16
i have all 4 boxes ticked but only because i know a linux guy as he said he has never encountered any issues with pre-released and unsupported yet could those updates cause ubuntu to slow down or anything? also are they needed as i ain't no beta tester i only want a simple and fast ubuntu and not have to fix problems constantly(if it can be helped)

---

### Post by Paqman on 2010-07-16
Unless you're worried about bandwidth, i'd just go ahead and install them all. It's exceedingly unlikely that an update on a stable version of Ubuntu will cause any problems.

---

### Post by undrline on 2010-08-25
Is there a history to what's been updated so, if something does go awry after an update, you can look to see what you installed when?  I do read the updates, but I don't memorize them.  I've just started having mounting issues, and one of the updates I did recently said something about mounting; I want to roll it back and see if it fixes the issue.

EDIT: Nevermind.  File>History.  But, is there something I can add to make the synaptic history more robust: searching, current description of the packages, etc?

---

### Post by ENigma885 on 2010-08-26
**[COLOR="Red"]**There's no such a thing called an OS without updates!!**[/COLOR]**

**1-** Security Updates are out of question. 
**2-** As of normal library and program updates, they fix bugs and add features u most probably need.
**3-** The size of the updates is not an issue as long as ur connection is fine. Depending on ur perspective, I assume u don't install many programs. Consequently, ur updates will be minimal.
**4-** _If you want to save more space,_ 
[INDENT]**4A-** you can always delete the update cache, the downloaded packages, after being installed. They are located @ /var/cache/apt/archives
```
sudo aptitude clean
```[/INDENT]
[INDENT]**4B-** after a kernel update u will still have the old kernel there. It's not of any use as long as the newer kernel works well. So, you can remove the old kernels. I recommend using *UbuntuTweak* for this purpose. Add its PPA by ```
sudo add-apt-repository ppa:tualatrix/ppa
```
then ```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```
Launch it, select* Package Cleaner* (left menu), then *Clean Kernels* (right menu). 
You can also clean the cache from *Clean Cache * instead of following step#4.[/INDENT]

---

### Post by Col.Krumpet on 2010-08-26
> **ENigma885 said:**
> **[COLOR=Red]**There's no such a thing called an OS without updates!!**[/COLOR]**

**1-** Security Updates are out of question. 
**2-** As of normal library and program updates, they fix bugs and add features u most probably need.
**3-** The size of the updates is not an issue as long as ur connection is fine. Depending on ur perspective, I assume u don't install many programs. Consequently, ur updates will be minimal.
**4-** _If you want to save more space,_ [INDENT]**4A-** you can always delete the update cache, the downloaded packages, after being installed. They are located @ /var/cache/apt/archives
```
sudo aptitude clean
```[/INDENT][INDENT]**4B-** after a kernel update u will still have the old kernel there. It's not of any use as long as the newer kernel works well. So, you can remove the old kernels. I recommend using *UbuntuTweak* for this purpose. Add its PPA by ```
sudo add-apt-repository ppa:tualatrix/ppa
```then ```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```Launch it, select* Package Cleaner* (left menu), then *Clean Kernels* (right menu). 
You can also clean the cache from *Clean Cache * instead of following step#4.[/INDENT]

THANKS!!! I was gonna start a thread to ask how to clean old packages and kernel's from my system :D

---

### Post by ParadoxBlue on 2010-08-27
> **ENigma885 said:**
> **[COLOR=Red]**There's no such a thing called an OS without updates!!**[/COLOR]**

**1-** Security Updates are out of question. 
**2-** As of normal library and program updates, they fix bugs and add features u most probably need.
**3-** The size of the updates is not an issue as long as ur connection is fine. Depending on ur perspective, I assume u don't install many programs. Consequently, ur updates will be minimal.
**4-** _If you want to save more space,_ [INDENT]**4A-** you can always delete the update cache, the downloaded packages, after being installed. They are located @ /var/cache/apt/archives
```
sudo aptitude clean
```[/INDENT][INDENT]**4B-** after a kernel update u will still have the old kernel there. It's not of any use as long as the newer kernel works well. So, you can remove the old kernels. I recommend using *UbuntuTweak* for this purpose. Add its PPA by ```
sudo add-apt-repository ppa:tualatrix/ppa
```then ```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```Launch it, select* Package Cleaner* (left menu), then *Clean Kernels* (right menu). 
You can also clean the cache from *Clean Cache * instead of following step#4.[/INDENT]
Thanks for a few useful tips. Saving hard drive space is always good even if you have a terabyte or two (which I certainly don't). I view saving disk space the same way I look at saving money...Just do it! You never know when you might need/want it. 

You can also delete the update cache through Synaptic as well as the old kernels and headers, so I've learned.

Ubuntu Tweak is as of this writing the only program that is now displaying odd behavior since it updated through the ppa listed above. I get two error messages upon startup and the version of Tweak showing installed in Synaptic does not match the version listed when I click on the "About" button from within Tweak. Tweak is by no means a wonder program or any kind of godsend. The only reason I installed it to begin with is to see what all it does and then figure out how to do most of it manually.

---

### Post by ENigma885 on 2010-08-27
> **ParadoxBlue said:**
> 
Ubuntu Tweak is as of this writing the only program that is now displaying odd behavior since it updated through the ppa listed above. I get two error messages upon startup
The PPA listed above is the official one. Can you state what errors u get at startup?

> **ParadoxBlue said:**
> ...and the version of Tweak showing installed in Synaptic does not match the version listed when I click on the "About" button from within Tweak.
Yea, I noticed the same thing. Will file a bug report asap.

> **ParadoxBlue said:**
> Tweak is by no means a wonder program or any kind of godsend. The only reason I installed it to begin with is to see what all it does and then figure out how to do most of it manually.
I do agree. And I didn't even imply any of those fancy descriptions. Yet, it's a useful tool as long as u know wat u r doing with. I merely recommended it because the post u started the thread with was ur "4th".

---

### Post by ParadoxBlue on 2010-08-27
> **ENigma885 said:**
> The PPA listed above is the official one. Can you state what errors u get at startup?


Yea, I noticed the same thing. Will file a bug report asap.


I do agree. And I didn't even imply any of those fancy descriptions. Yet, it's a useful tool as long as u know wat u r doing with. I merely recommended it because the post u started the thread with was ur "4th".

Will post screenshots of error messages. It will be a few...relatives in this weekend for visit and am distracted.  :(

---

### Post by ParadoxBlue on 2010-09-01
> **ParadoxBlue said:**
> Will post screenshots of error messages. It will be a few...relatives in this weekend for visit and am distracted.  :(
I see your reason for trying to simplify things for me and thanks but please don't judge me by my "beans". Although I am actually a complete Linux noob I've have had a computer in the house for almost 20 years but it's always been running a Windows variation. I switched to Linux/Ubuntu for a few reasons but that's another story entirely. I've been Windows free since late March (not even running Wine) and I have yet to have any major regrets. Anyway I'm no stranger with tinkering "under the hood" of an operating system.

Fortunately as luck would have it I applied the newest upgrade to Tweak last night and upgraded to version 0.5.6 and the odd behavior went away. Whatever was wrong with the last update obviously has been taken care of with the newer version. At least Tweak seems to be running normally now on my system. Hopefully anyway else having some issues will see the same.

---

