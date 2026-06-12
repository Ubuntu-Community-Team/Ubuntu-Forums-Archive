---
title: "Flash Crash 100% of the Time!!!"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by kilo8001 on 2009-07-15
I'm not even sure where to begin other then Firefox crashes every time I try to watch streamed videos! I've looked up and down through other forums and troubleshooting but cannot come to a conclusion as to why this problem persists to continue.  I would be very grateful for some help regarding this matter.

Best Regards, Kyle

---

### Post by kilo8001 on 2009-07-15
I have already installed the latest version of Adobe flash and even tried others then Adobe. I firstly installed it by going to there website and downloaded the .tar file, unpacked it, and installed it with no problems, yet the crash of Firefox still occurs. I then found a (resolved) thread that dealt with the same problem I'm having which said to install a media player add on for firefox and use vlc to play flash through, still nothing.  I then found another that stated "turning off desktops special effects" may resolve it, still nothing. I am now at the point where I think it may be a problem with X. It is getting very frustrating, I'm sure there are a ton of variables as to why this s happening and I myself have looked into a lot of them with no such luck yet. If there is any info at all needed which may clarify the situation please ask me to post it.

Thanks, Kyle

---

### Post by kilo8001 on 2009-07-15
I'm not even sure where to begin other then Firefox crashes every time I try to watch streamed videos! I've looked up and down through other forums and troubleshooting but cannot come to a conclusion as to why this problem persists to continue. I have already installed the latest version of Adobe flash and even tried others then Adobe. I firstly installed it by going to there website and downloaded the .tar file, unpacked it, and installed it with no problems, yet the crash of Firefox still occurs. I then found a (resolved) thread that dealt with the same problem I'm having which said to install a media player add on for Firefox and use VLC to play flash through, still nothing. I then found another that stated "turning off desktops special effects" may resolve it, still nothing. I am now at the point where I think it may be a problem with X. It is getting very frustrating, I'm sure there are a ton of variables as to why this s happening and I myself have looked into a lot of them with no such luck yet. If there is any info at all needed which may clarify the situation please ask me to post it.

Thanks, Kyle

---

### Post by lovinglinux on 2009-07-15
What version of Ubuntu and Firefox are you using? Does the crash occurs o every flash streaming video page, or just when you try to see it in fullscreen?

If you are using Firefox 3.5 and the it crashes only when viewing videos at fullscreen, then follow **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

If you are using Firefox 3.0.x, then try the command below on a terminal:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash libflashsupport flashplugin-nonfree-extrasound flashplugin-nonfree adobe-flashplugin && sudo apt-get install flashplugin-nonfree
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by lovinglinux on 2009-07-15
Please don't create duplicated threads.

---

### Post by Sef on 2009-07-15
merged threads.

---

### Post by lovinglinux on 2009-07-15
> **Sef said:**
> merged threads.

Thank you

---

### Post by binbash on 2009-07-15
Same problem here on a couple of PCs

---

### Post by kilo8001 on 2009-07-15
Thanks for the response,

I'm sorry about the double post as I wanted to move it to the "Media & Video" section of the forum and a moderator switched it back to here creating two of them. :roll:

Anyway, I'm using Ubuntu 8.04 Intrepid and for Firefox I'm using version 3.0.11 Canonical - 1.0.

I will give Gnash a try although I'm pretty sure I've been down that road, I will get back to you once I've tried!

---

### Post by LewRockwell on 2009-07-15
I browsed over all the posts and I'd make note that equipment was not specified and it appears OP has not experimented with 9.04 Jaunty(or if this has been done it is not related in the trouble-call)

.

---

### Post by lovinglinux on 2009-07-15
> **kilo8001 said:**
> I'm sorry about the double post as I wanted to move it to the "Media & Video" section of the forum and a moderator switched it back to here creating two of them. :roll:

It was my fault. I reported it to a moderator. When you need to move a post to another forum, use the report button on the bottom-left of the post sidebar.

> **kilo8001 said:**
> I will give Gnash a try although I'm pretty sure I've been down that road, I will get back to you once I've tried!

The command from my previous post is not to install gnash, but to make sure it is uninstalled. The same applies to swfdec plugin. That command will uninstall all flash plugins, plus libflashsupport and then re-install only the one from Adobe. This will make sure you don't have any conflicting plugins and additional libraries that could cause problems.

BTW, I don't recommend gnash.

---

### Post by kilo8001 on 2009-07-15
It Worked!!!!

Thank you very much for your help! I will continue to learn Ubuntu/Linux as best as I can so hopefully I can help others in the future myself. I will also take a closer look at the command you gave me and learn it.

Once again thank you very much for your time and efforts in helping me out!

Best regards, Kyle:-D

---

### Post by kilo8001 on 2009-07-15
great!

I actually had un installed Gnash before and i was concerned about plug-ins conflicting with one another as well but was going kooky looking up and down synaptic trying to figure out what was what

---

### Post by lovinglinux on 2009-07-15
> **kilo8001 said:**
> It Worked!!!!

Thank you very much for your help! I will continue to learn Ubuntu/Linux as best as I can so hopefully I can help others in the future myself. I will also take a closer look at the command you gave me and learn it.

Once again thank you very much for your time and efforts in helping me out!

Best regards, Kyle:-D

You are welcome

---

### Post by kilo8001 on 2009-07-15
**                                            _[size=5]thread resolved[/size]_**

---

### Post by vinutux on 2009-07-15
> **kilo8001 said:**
> **                                            _[size=5]thread resolved[/size]_**

[B][COLOR="DarkGreen"]
not this way..marked it under thread tools

Thread tools->mark this thread resolved
[/COLOR][/B]

.

---

### Post by kilo8001 on 2009-07-15
Ummm... looked under thread tools and no such option is available??

---

### Post by lovinglinux on 2009-07-15
> **vinutux said:**
> [B][COLOR="DarkGreen"]
not this way..marked it under thread tools

Thread tools->mark this thread resolved
[/COLOR][/B]

.

That feature has been disabled a loooong time ago.

---

### Post by vinutux on 2009-07-15
> **kilo8001 said:**
> Ummm... looked under thread tools and no such option is available??

sorry...........that feature is disabled........don't know Y.....but very helpfull one

---

### Post by kilo8001 on 2009-07-15
So was my method of marking the thread resolved proper?

---

### Post by lovinglinux on 2009-07-15
> **vinutux said:**
> sorry...........that feature is disabled........don't know Y.....but very helpfull one

It was causing database overhead

> **kilo8001 said:**
> So was my method of marking the thread resolved proper?

Yes, but people usually use the word SOLVED.

Another method would be adding the word solved to the thread tags. 

Anyways, since they disabled this feature I never bothered marking it again.

---

### Post by vinutux on 2009-07-15
yeh.....so leave it...

---

