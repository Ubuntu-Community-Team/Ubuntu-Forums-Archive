---
title: "Noob with 9.04 problems..."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Bilge_Rat on 2009-05-14
Hi all, first post and a complete novice with Linux. I started with v8.10 and now I wish I'd stayed with it. I'd had it for a week or so when I was prompted to upgrade to 9.04 and while it fixed one problem, it seemed to create a lot of others. I did a few searches and couldn't find any references to any of these problems so here they are...

1) Poor internet performance. This seems to happen every second or third screen. The thing just stalls. Sometimes it loads and other times it doesn't. This was not the case with 8.10 and internet was the primary reason for changing so this is a bit disappointment. Doesn't happen in Windows;

2) Poor sound quality. There seems to be some sort of electronic buzz in my headset (I don't use speakers) and my friends have a hard time hearing me on Skype. I tried a reinstall of Skype but it made no difference;

3) Unbelievable but Ubuntu has crashed twice. The whole system just rebooted I think. I can't remember exactly what happened but I've been reading about how to report bugs in case it happens again.

Before doing any bug reporting, I'd like to make sure none of this is me and some setting I need to change/should have changed. I was quite impressed with the first version I tried although any movie files played very poorly.

I should probably also say that my system is easily capable enough for Linux but for what it's worth:

AMD 64 3200+
3 GB RAM
Radeon X1950 Pro 512
200 GB partition for Linux.

I should probably also point out that compared with most Linux users, I'm not very knowledgeable at all. I've had a look at things like Terminal but I don't really know much about using it.  I've seen the synaptic Program Manager and had a bit of a play with it and I've changed a few things around to suit but nothing which would have any bearing on these issues.

Any help much appreciated.

---

### Post by mike555 on 2009-05-14
I guess you upgraded and didn't do a clean install, I'm thinking you should just backup and format and reinstall ...

---

### Post by Bilge_Rat on 2009-05-14
Yeah, that's right. I just followed the prompts and it sort of did its own thing.

By coincidence, a mate of mine did the same thing but had no problems at all.

If this is the normal practice then I'm a bit surprised the upgrade manager does thing this way. Oh well...

Thanks for your prompt reply Mike.

Maybe there needs to be a version for people like me called "Nubuntu"...!

---

### Post by BZF on 2009-05-14
[SIZE=1][COLOR=Blue]really there was just an error when installing, also partitions usually dont run as well as having ur comp 100% ubuntu[/COLOR][/SIZE]

---

### Post by Bilge_Rat on 2009-05-14
Even if Ubuntu is on a separate HDD?

---

### Post by Didius Falco on 2009-05-14
> **Bilge_Rat said:**
> Hi all, first post and a complete novice with Linux. I started with v8.10 and now I wish I'd stayed with it. I'd had it for a week or so when I was prompted to upgrade to 9.04 and while it fixed one problem, it seemed to create a lot of others. I did a few searches and couldn't find any references to any of these problems so here they are...

1) Poor internet performance. This seems to happen every second or third screen. The thing just stalls. Sometimes it loads and other times it doesn't. This was not the case with 8.10 and internet was the primary reason for changing so this is a bit disappointment. Doesn't happen in Windows;

2) Poor sound quality. There seems to be some sort of electronic buzz in my headset (I don't use speakers) and my friends have a hard time hearing me on Skype. I tried a reinstall of Skype but it made no difference;

3) Unbelievable but Ubuntu has crashed twice. The whole system just rebooted I think. I can't remember exactly what happened but I've been reading about how to report bugs in case it happens again.

Before doing any bug reporting, I'd like to make sure none of this is me and some setting I need to change/should have changed. I was quite impressed with the first version I tried although any movie files played very poorly.

I should probably also say that my system is easily capable enough for Linux but for what it's worth:

AMD 64 3200+
3 GB RAM
Radeon X1950 Pro 512
200 GB partition for Linux.

I should probably also point out that compared with most Linux users, I'm not very knowledgeable at all. I've had a look at things like Terminal but I don't really know much about using it.  I've seen the synaptic Program Manager and had a bit of a play with it and I've changed a few things around to suit but nothing which would have any bearing on these issues.

Any help much appreciated.

Hi, and welcome to the Ubuntu forums.

Had you applied all the updates that were available for 8.10 before you upgraded? Not doing so can cause problems.

My three rules for Upgrading:

1. Apply all updates to old version before upgrading to the new one.

2. Turn off all the Third Party sources by unchecking the box next to it in Software Sources.

3. Disable or uninstall all proprietary video drivers.

Even with those three rules, I much prefer a clean install. Since you've only been at it a week, it should be fairly easy to backup any data you want saved and do a fresh install.

While you are at it, a lot of people set up a separate partition for their /Home directory. That way, your data and configuration files are in a separate place and if you should need to reinstall, it will save that information. You'd have to reinstall the programs, but their setting will be intact.

An optional move, but one I use and recommend, is to set up a third partition just for your own data. You can name it whatever you want - it's not an actual part of Ubuntu, but it makes it easy to keep and back up just your own personal data - MP3's, things you've written, etc.

Feel free to ask as many questions as you want in the forums - there are a lot of knowledgeable people willing to help you out.

If you'd rather try and fix the current install, you could take a look at this guide to fixing your sound. I've found it very helpful:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working)

For the errors and lock-ups you are getting, you would need to provide more information before anyone could really help. Things like what you are doing when it happens, any error messages you can catch, etc.

Either way you decide to go, feel free to ask questions. Give yourself some time, there is a bit of a learning curve, but things start to fall into place fairly quickly once you've been at it a while.

Regards,

Didius

---

### Post by Niniel on 2009-05-14
> **BZF said:**
> [SIZE=1][COLOR=Blue]also partitions usually dont run as well as having ur comp 100% ubuntu[/COLOR][/SIZE]
That is total rubbish.
The only problem with not having only one OS on your computer is getting dual boot to work and reading/writing disks/partitions the other OS is/are using. 
Upgrading works well for a lot of people - e.g. I've been doing nothing but upgrades on a computer of mine since 7.10 - but sometimes there are problems. Hard to predicts which way it'll go. Mostly it's because of incompatibilities introduced by the new version of the distribution.

---

