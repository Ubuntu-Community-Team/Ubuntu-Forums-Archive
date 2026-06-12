---
title: "apt-get / aptitude verläßlich?"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by paaating on 2011-03-14
Hey,

i'm still and absolute linux beginner but I'm really lovin it so far. Just somethin I was wondering. I constantly trip over apt-get and aptitude commands, gimp 2.7 developer install or brother driver install, and I was wondering if they are all safe and can be installed without caution? With safe i basically mean that phishing or similar things are not possible?

Kind regards,
Patrick

*edit*
Sorry for the german beforehand. I blanked for a second. Can't seem to be able to change the topic :/

---

### Post by t0p on 2011-03-14
It depends on where you are downloading the stuff from.  If it is, say, an official Gimp site or an approved mirror, you should be alright.  If it's some random site that you found through Google or something, you *might* possibly download something nasty.  Personally, I think it's unlikely you'll get an evil download - I never have, and at times I'm not as security-minded as I should be.  But it's good to have a general security policy in regards to software sources: if you can't identify the source as approved, go somewhere else.

---

### Post by paaating on 2011-03-14
Okay like I thought. Is there a possibility of checking if it's fine? And are there ways of resetting the system to say, 3 hours ago?

---

### Post by Sef on 2011-03-14
> And are there ways of resetting the system to say, 3 hours ago?

No, but if you had a back up, you could reinstall that.

> Is there a possibility of checking if it's fine?

[MD5sum]("https://help.ubuntu.com/community/HowToMD5SUM") or SHA1.

---

### Post by theDaveTheRave on 2011-03-14
To check if a software piece is OK and 'phishing friendly' isn't going to be easy, unless it is coming from the official repositories.

If it is a large project and isn't in the repo's you will most likely be OK. But if you are ever unsure you can always check the software vendor via the forums or google searches (eg things like 'blahblah software broke my ubuntu').

However that said. There are a number of 'projects' that are interesting and only have a small user base. I can only suggest that you directly contact the lead developper / maintainer to see how they come across. Check to see what sort of response you get (just like buying a used car).

With respect to 'rollback' that isn't quite so easy.

The best thing may be to create an image of your system, then if anything goes wrong you will be easily able to return to your last known good setup.

The other options are...
create a 'testing user' on your system. then you can check out the behaviour before installing into your main user area.

a virtual machine to run your 'unknown' system through as a test. This is much easier with a 'free' OS like linux as you can easily and cheaply get install disks.

In fact a virtual machine is probably going to be your best bet, or use an old defunct pc, as the system requirements for most linux systems can be much less if you build a minimal system.

David

---

### Post by paaating on 2011-03-14
Thanks alot for the help!

I'm asking specifically because of these two:

[http://ubuntuforums.org/showpost.php?p=10559696&postcount=364](http://ubuntuforums.org/showpost.php?p=10559696&postcount=364)

My brother printer actually worked after using this. It was only after I installed when i thought about possible phishing attacks.

The other was a gimp developers repository I can't find right now

---

