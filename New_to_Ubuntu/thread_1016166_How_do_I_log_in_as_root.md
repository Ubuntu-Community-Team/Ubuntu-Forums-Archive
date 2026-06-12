---
title: "How do I log in as root"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by suomalainen on 2008-12-19
Ubunteros,

Can someone tell me how I can login as root?

Please...


Thanks

---

### Post by SunnyRabbiera on 2008-12-19
Right, logging in as root is dangerous and quite stupid.
sudo should do fine.

---

### Post by suomalainen on 2008-12-19
ok now you got me confused! Sorry!

If you search my threads for today you'll see one relating to adobe.

What I want to do is record an adobe flash video as it plays. The person that replied said it can be done by looking in my tmp folder as the file is playing. I think I found the file in question BUT permission lists owner as root. 

Thus, I thought that if I'm in root then maybe then I can copy this file as it is playing....

Does this make sense now????

---

### Post by SunnyRabbiera on 2008-12-19
> **suomalainen said:**
> ok now you got me confused! Sorry!

If you search my threads for today you'll see one relating to adobe.

What I want to do is record an adobe flash video as it plays. The person that replied said it can be done by looking in my tmp folder as the file is playing. I think I found the file in question BUT permission lists owner as root. 

Thus, I thought that if I'm in root then maybe then I can copy this file as it is playing....

Does this make sense now????

for this stuff, in a terminal just hit gksudo nautilus.
You can also get unplug for firefox too:
[https://addons.mozilla.org/en-US/firefox/addon/2254](https://addons.mozilla.org/en-US/firefox/addon/2254)

---

### Post by suomalainen on 2008-12-19
jimmy the saint,

Does this regulation keep me from learning how to copy the file?

Thanks.

---

### Post by sisco311 on 2008-12-19
> **suomalainen said:**
> jimmy the saint,

Does this regulation keep me from learning how to copy the file?

Thanks.

You can open the file manager as root:
```
gksu nautilus
```
or use the cp command:
```
sudo cp /path/to/file /destination/dir
```

When you have a little time, please read:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

and

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by suomalainen on 2008-12-19
mikewhatever,

And may I ask why I'm being prevented to learn how to copy a file please?

---

### Post by pshootr on 2008-12-19
> **suomalainen said:**
> jimmy the saint,

Does this regulation keep me from learning how to copy the file?

Thanks.

It seems to me you have been instructed numerous times how to do what you need to do "with-out" having to log on as root!

---

### Post by jimmy the saint on 2008-12-19
You are not being prevented from learning how to copy files.  you have been told to use sudo or gksudo several times.  that is how you copy root-owned files.  If you wish to learn dangerous and advanced ways to possibly damage your machine, google will direct you to thousands of tutorials.  This forum is about teaching you SAFE ways to perform the actions.  No fewer than 6 people have told you how to do it.  I recommend you take our advice and do it the correct way.

---

### Post by SunnyRabbiera on 2008-12-19
> **suomalainen said:**
> mikewhatever,

And may I ask why I'm being prevented to learn how to copy a file please?

well nothing is preventing you, its just a forum rule not to get normal users to use root access.
Look you dont need the tmp directory if you use unplug, if you want to save flash videos you can use that extension.
People stop confusing the matter here, if he just wants to save a flash video firefox has unplug :D

---

### Post by suomalainen on 2008-12-19
Folks,

Thanks for the info! I guess this post is moving little fast... and perhaps your assuming I poseess a certain skill level?

At this percise moment, I don't know what works and what doesn't...

I just wanted to learn if I can copy this file that's all. I had no intention of starting a battle or a war. Just wanted to copy a file. nothing more.

---

### Post by SunnyRabbiera on 2008-12-19
> **suomalainen said:**
> Folks,

Thanks for the info! I guess this post is moving little fast... and perhaps your assuming I poseess a certain skill level?

At this percise moment, I don't know what works and what doesn't...

I just wanted to learn if I can copy this file that's all. I had no intention of starting a battle or a war. Just wanted to copy a file. nothing more.

People are just trying to warn you away from using root thats all.
But seriously if you want to download a flash video use unplug for firefox.

---

### Post by sdennie on 2008-12-19
Thread closed.  The solution to the users problem has been given several times and there is no need to instruct him on using root logins or anything of that nature.

---

