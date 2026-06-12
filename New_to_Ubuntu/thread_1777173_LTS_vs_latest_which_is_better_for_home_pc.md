---
title: "LTS vs latest: which is better for home pc"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by rng on 2011-06-07
What are the advantages of ubuntu 11.04 over ubuntu LTS 10.04? I need a system for home pc. 

Does the same versioning apply to kubuntu as well?

Also how do I find out which version I am running (I have misplaced the install livecd)?

---

### Post by iclestu on 2011-06-07
In turn.....

11.04 has new features that are not in 10.04. 10.04 has had more bugs squashed. Simplistic view maybe but it pretty much sums it up. If you want the latest gismos and software improvements go for 11.04 but be aware that some unpolished edges will be there. If you dont really care for the new-fangled greatness but want smooth stable and polished then go for 10.04lts

Yes, kubuntu versioning mirrors ubuntu

type

```
lsb_release -a
```

at the terminal to find our which distro you are using

---

### Post by rng on 2011-06-07
Thanks for answering all the questions. 

Can you mention any particularly important feature in 11.04 over 10.04 of ubuntu or kubuntu?

---

### Post by mastablasta on 2011-06-07
> **iclestu said:**
>  
Yes, kubuntu versioning mirrors ubuntu

 
 
However new Kubuntu has newer KDE (desktop environment) which has a lot of bugs fixed. Newer KDE can probably be also installed to 10.04 with a PPA. however you migth want to have it on form start. KDE in 10.04 still had plenty problems.

---

### Post by mastablasta on 2011-06-07
> **rng said:**
>  
Can you mention any particularly important feature in 11.04 over 10.04 of ubuntu or kubuntu?
 
in Ubuntu the only major feature is Unity interface (still very new and with bugs). If you go Ubuntu i would suggest 10.04 as it is really good. 
 
Also newer version will have newer drivers in kernel, so if you have a newer hardware and 10.04 doesn't work nicely there is a chance that newer version (11.04) will work just fine.
 
I use 10.04 on one and on the other i had to upgrade cause i had drivers issues.

---

### Post by mcduck on 2011-06-07
It's just a question of your own preference.

LTS version will give you better stability (not in the sense of computer crashing, but in the sense of the OS and environment not changing). It also allows you to keep  on using the OS longer time without having to upgrade to new Ubuntu version.

Installing latest version, on the other hand, will give you more up-to-date version of all programs, new features and performance tweaks, whatever stuff the developers use their time for. :) On the down side the support time for normal releases is shorter so you need to upgrade more often.

Of course new release might come with new bugs, but on the other hand it will also fix the bugs from the previous versions. Most of such things are hardware-related, so it depends on your computer which version is most bug-free for you. (in theory the latest version would always be the best one to use, but this isn't a perfect world...)

---

### Post by iclestu on 2011-06-07
> **rng said:**
> Thanks for answering all the questions. 

Can you mention any particularly important feature in 11.04 over 10.04 of ubuntu or kubuntu?

Not that I can think of, but then I cant really mention any specifc 'unpolished edges' that cause me difficulties either! ;)

If you are considering switching from windows the difference between windows and linux is HUGE compared to diff between ubuntu and kubuntu and, it turn difference between the respective version numbers is minimal next to difference between kubuntu and ubuntu... Guess you just got to take the plunge. For me, it would be 11.04 everytime but thats me.

Mastablasta undoubtedly has more knowledge of this than I do and, from his post, he appears to advocate 11.04 for kubuntu on basis of new KDE..... So if you went for kubuntu over ubuntu then 11.04 certainally has at least 2 votes! :)

*edit: based the above line on mastablasta's first post. He has since made other observations I wasn't aware for when replying.....*

---

### Post by ivanovnegro on 2011-06-07
After working with 11.04 I have to admit, its one of the releases you sure could skip.
I would really suggest to go with Ubuntu 10.04, its with a reason an LTS version.
If you want newer stuff, Ubuntu makes it easy with PPAs or backports.
In case of Kubuntu I would go for 11.04, it has a much more polished and stable KDE, KDE is just developping too fast to not catch it. KDE on 10.04, I really did not like it.

---

### Post by rng on 2011-06-07
Thanks everyone. 

How much data is transferred (how many MB) while upgrading to new version over the internet?

---

### Post by spook1980 on 2011-06-07
i perfer latest on my main machine and the one everybody else uses as an LTS as its very stable has  a full desktop and acts as the household file server, and for any kind of server always LTS,

---

### Post by iclestu on 2011-06-07
> **rng said:**
> Thanks everyone. 

How much data is transferred (how many MB) while upgrading to new version over the internet?

more than a little! It does take a while (more specific responses will no doubt follow from the boffins ;) )

---

### Post by ivanovnegro on 2011-06-07
> **rng said:**
>  

How much data is transferred (how many MB) while upgrading to new version over the internet?

That would be an amount but thats normal, it will update all your apps.
Backup all your files anyway, thats important before doing such things!
I would also suggest to do a clean install, its faster to perform and with the Live CD you can try first the new version to see if any issues are appearing before.
Also if you upgrade, its better to test the new version on a Live CD, never upgrade/install blindly, that will avoid bad surprises!

---

### Post by Sidewinder1 on 2011-06-07
LTS, here; my first (not LTS, was Gutsy) went to Hardy, then Lucid; no complaints. More importantly less messin' around; more 'puting... :-)

Side

---

### Post by danbuter on 2011-06-07
If you like gnome, then use 10.10. Avoid 11.04, it's crap. 10.04 is nice, but if you have a newer computer, you will have problems getting stuff to work.

---

### Post by pablolie on 2011-06-07
...another consideration is what hardware you are running. If you run one of the latest Intel CPUs and want to use their integrated graphics (I run an i2100t which is both fast and very low power) then 11.04 -believe it or not- is going to be a better choice for you. 

I wanted to stay with 10.04LTS -which I have been *extremely* happy with- but it just did not support SandyBridge as well as 11.04 for whatever reason.

That may be another consideration. It is also easy enough to switch the UI back to Ubuntu classic if you -like me- don't quite like the new Unity look.

---

### Post by ivanovnegro on 2011-06-07
> **danbuter said:**
> If you like gnome, then use 10.10. Avoid 11.04, it's crap. 10.04 is nice, but if you have a newer computer, you will have problems getting stuff to work.

Thats right with the newer Kernels but only if you have specific tasks to do or very recent hardware, I think a one year old machine does not need the newest Kernel to work.
I see more and more people always talking about the newest Kernel, I dont understand this perception, you dont need it always. An older one can work perfectly.
And the Kernel 2.6.32 on Lucid is a long supported Kernel and dont forget the power regressions of the 2.6.38., this is also a known fact I think, if not correct me. 
If you want especially a long battery life on a notebook I really think Lucid is the way to go and not Natty.

---

### Post by ivanovnegro on 2011-06-07
> **pablolie said:**
> ...another consideration is what hardware you are running. If you run one of the latest Intel CPUs and want to use their integrated graphics (I run an i2100t which is both fast and very low power) then 11.04 -believe it or not- is going to be a better choice for you. 

I wanted to stay with 10.04LTS -which I have been *extremely* happy with- but it just did not support SandyBridge as well as 11.04 for whatever reason.

That may be another consideration. It is also easy enough to switch the UI back to Ubuntu classic if you -like me- don't quite like the new Unity look.

Why to switch to an UI when you can have Gnome on Lucid or Maverick without the bugs of Natty? The Classic Gnome is not as good as on the older releases IMHO, its only the "fallback" and this word says everything, but I am not saying it does not work of course.

---

### Post by jramshu on 2011-06-07
10.04 LTS is a great choice. I have a fairly new machine, it's about a year old and I have never had any problems with hardware, wifi, etc. with 10.04, or 10.10(on another year old machine). I have had problems with 11.04, though easily fixed.

---

### Post by rng on 2011-06-07
Thanks everyone.

---

