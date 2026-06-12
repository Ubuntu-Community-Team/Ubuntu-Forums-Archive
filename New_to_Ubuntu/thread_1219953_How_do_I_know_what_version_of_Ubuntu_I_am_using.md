---
title: "How do I know what version of Ubuntu I am using?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Jerubaal on 2009-07-22
I installed Feisty from cd and have always done my updates. Does that mean I now have 9.04 installed? I never really pay attention to what the updates are, but occasionally get a message asking whether I want to keep my existing menu.lst settings, which I do. Would this be when the version changes?

---

### Post by CLomax on 2009-07-22
**System** -> **About Ubuntu**

---

### Post by ~sHyLoCk~ on 2009-07-22
> **Jerubaal said:**
> I installed Feisty from cd and have always done my updates. Does that mean I now have 9.04 installed? I never really pay attention to what the updates are, but occasionally get a message asking whether I want to keep my existing menu.lst settings, which I do. Would this be when the version changes?

What's the output of 
```
lsb_release -a
```

---

### Post by mhurst102282 on 2009-07-22
If you are just doing updates and didn't do any upgrades you are still using 7.04.

---

### Post by ~sHyLoCk~ on 2009-07-22
> **mhurst102282 said:**
> If you are just doing updates and didn't do any upgrades you are still using 7.04.

True besides you need to upgrade to the immediate next release and not directly to any other future release! E.g.-> You need to upgrade to 7.10 first from 7.04 before you can upgrade to 8.04

---

### Post by Jerubaal on 2009-07-22
I'm at work (windoze) so will have to check when I get home. I recall changing the desktop image from hardy back to the elephant hide, so I must have got that far. 

Thanks for the all the swift replies!

---

### Post by credobyte on 2009-07-22
To check Ubuntu version, open terminal and type in:
```
uname -a

```

uname has a few more arguments, so .. check manpages - might be useful :)

---

### Post by moredhel on 2009-07-22
> **credobyte said:**
> To check Ubuntu version, open terminal and type in:
```
uname -a

```

uname has a few more arguments, so .. check manpages - might be useful :)

The best part of using uname is that it's distro-agnostic where as lsb_release might not exist in other distros.

---

### Post by ~sHyLoCk~ on 2009-07-22
> **credobyte said:**
> To check Ubuntu version, open terminal and type in:
```
uname -a

```

uname has a few more arguments, so .. check manpages - might be useful :)

That's not gonna give the Codename or version afaik! Atleast it doesn't for me. 
```

shy@z$ uname -a
Linux shy 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 09:49:51 UTC 2009 x86_64 GNU/Linux
```

---

### Post by moredhel on 2009-07-22
> **~sHyLoCk~ said:**
> That's not gonna give the Codename or version afaik! Atleast it doesn't for me. 
```

shy@z$ uname -a
Linux shy 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 09:49:51 UTC 2009 x86_64 GNU/Linux
```

Huh. Well you could work it out from the kernel release :D

---

### Post by ~sHyLoCk~ on 2009-07-22
> **moredhel said:**
> Huh. Well you could work it out from the kernel release :D

Or ```
cat /etc/issue
```  :P

EDIT: [OT]I love ur dp! Fellow fallout fan! :D[/OT]

---

### Post by Jerubaal on 2009-07-23
Well, that was a scary moment or five!

I had Hardy Heron installed (thanks CLomax) and then selected the option to show upgrades, so I could then upgrade to 8.10. However, because I had customised my own menu.lst, I wanted to keep the current one. Message after message came up asking me if I wanted to keep it, which was a bit confusing. I guess it was updating each and every kernel along the way.

When it came to restarting, it showed me the login screen (I never normally see that) and then it would login, show my usual wallpaper and then go back to the login screen. Very frustrating. I remembered seeing a message saying my vlinuz (or something like that) was damaged and I may need to fix my GRUB, which I tried. Eventually I tried editing the boot command line to change the kernel number from 2.6.22-14 to 2.6.27-14 (leaving the rest of the line intact). Fortunately this worked first time, so I could go into the terminal end edit my menu.lst.

The only dodgy looking thing was that my screen res was different, which I then mucked up even more because I couldn't remember what it should be. Eventually managed to get that more-or-less sorted out.

I guess I need to start all my apps to make sure they work ok, then this time, clone the partition before upgrading the final step to 9.04... I shall now go and read the forum for further upgrade advice! If I wasn't sleep deprived, maybe I would have had an easier time of it. Babies and upgrading don't mix!!!

---

### Post by lisati on 2009-07-23
> **moredhel said:**
> Huh. Well you could work it out from the kernel release :D

This thread is in "Absolute beginner talk", so I'll go with clomax's suggestion:
**System -> About Ubuntu**

---

