---
title: "Totem problems"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by nobodygh on 2009-06-23
Whenever I open a file into Totem it quits as soon as it has finished loading. I've tried everything I could think of to fix it. I installed every codec I could find and I even tried running Totem-xine(as everybody says I should) but that gave me exactly the same problem. So what am I to do now?

---

### Post by nobodygh on 2009-06-23
Oh, and I run Totem version 2.26.1 on Ubuntu 9.04(jaunty)

---

### Post by halitech on 2009-06-23
did you install ubuntu-restricted-extras?

---

### Post by nobodygh on 2009-06-23
Yes, but no luck

---

### Post by theguywhoneedshelp on 2009-06-23
Hello. I need help. (Sorry for posting this here, I cant find *new tropic*!)
Where can I find wine for ubuntu 9.4?
Im new here and this forum looks complicated to me. ](*,)

Ps. I have posted a reply here before but I cant find it! (LOL)

---

### Post by halitech on 2009-06-23
> **nobodygh said:**
> Yes, but no luck

what file format are you trying to play?

---

### Post by xtjacob on 2009-06-23
Why don't you try VLC?

---

### Post by xtjacob on 2009-06-23
> **theguywhoneedshelp said:**
> Hello. I need help. (Sorry for posting this here, I cant find *new tropic*!)
Where can I find wine for ubuntu 9.4?
Im new here and this forum looks complicated to me. ](*,)

Ps. I have posted a reply here before but I cant find it! (LOL)
Folloe these instructions: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Troll_the_Great on 2009-06-23
> **theguywhoneedshelp said:**
> Hello. I need help. (Sorry for posting this here, I cant find *new tropic*!)
Where can I find wine for ubuntu 9.4?
Im new here and this forum looks complicated to me. ](*,)

Ps. I have posted a reply here before but I cant find it! (LOL)

You can find wine for Jaunty here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Download what version you like. 
By the way, at the top of the page is a button entitled "New Thread". From there you can open your own threads, it's not nice to hijack someone else's...
Cheers!

---

### Post by nobodygh on 2009-06-23
> **xtjacob said:**
> Why don't you try VLC?

Where do I find VLC for ubuntu? And how do I install it?

 @ halitech. the format that I'm trying to run is wmv

---

### Post by halitech on 2009-06-23
either look in synaptic or open a terminal
```
sudo apt-get install vlc
```

---

### Post by nobodygh on 2009-06-23
Okay, I found VLC on add & remove programs. Installing it now:)

But I still need to get Totem to work, I can't live with the idea that I have a non-working linux program on my PC

---

### Post by nobodygh on 2009-06-23
Okay, so VLC does exactly the same thing as Totem. It loads the file, and then quits immediately. Maybe this is some bigger problem?

---

### Post by halitech on 2009-06-23
does it happen with all .wmv files or just the one? is the file drm'ed?

---

### Post by nobodygh on 2009-06-23
It happens to all file types, not only wmv. And that's all files of all file types. With both VLC and Totem. Except for one mpg file, where I get only sound, but no graphics.:confused:

---

### Post by nobodygh on 2009-06-23
What does drm'ed mean?

---

### Post by halitech on 2009-06-23
drm - digital rights management

what kind of video card do you have and do  you have the drivers installed for it?

---

### Post by Closed_Port on 2009-06-23
Some suggestions:

1. Try running vlc and totem from a terminal and see if you get any output when they fail.
2. Try an other ouput modul. As I don't know how to do this in totem-xine, open vlc, go to extras->settings (I'm not on an English system here, so it might be labeled differently), choose Video and then choose for example X11 as the output.

Save the changes, restart vlc and see if it works then.

---

### Post by nobodygh on 2009-06-23
> **halitech said:**
> drm - digital rights management

what kind of video card do you have and do  you have the drivers installed for it?

Thanks

Okay, that brings to another important question. How do I check what graphics card I have? I mean, isn't there some system tool that can help me with that?

I know I have some onboard graphics card, but I'm not sure about the specifications though. I'm sure that once I learn how to use Ubuntu to gather info on my graphics card I'll be able to find and install the necessary drivers. Otherwise I'll open a thread on installing drivers...

---

### Post by halitech on 2009-06-23
open a terminal and post the results of
```
lshw -C video
```

---

### Post by nobodygh on 2009-06-24
lshw -C video gives me this:

> *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


If I run VLC and Totem in Terminal both gives me an insufficient resources error. It's all starting to make sense now...

---

### Post by Closed_Port on 2009-06-24
I looked around a bit and it seems you are not the only one hit by this problem.

The first thing I'd suggest is to turn of compiz if you are using it, as many people report having this problem only when running compiz.

You could also try an other video output. For example, start vlc in a terminal with vlc --vout x11 and see if you can play the file now. If you can, it's probably a driver problem with the xv video-out.

Finally, if you are running jaunty: Jaunty is known to have some issues with intel graphic cards. What worked for me quite well was to install newer drivers from the x-updates ppa. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Be aware though that you are really mucking around with your system if you use the last option. So try it on your own risk.

Some hopefully helpful stuff I found:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257)
[https://bugs.launchpad.net/ubuntu/+bug/299280](https://bugs.launchpad.net/ubuntu/+bug/299280)
[http://ubuntuforums.org/showthread.php?t=1130582&repost](http://ubuntuforums.org/showthread.php?t=1130582&repost)

---

### Post by nobodygh on 2009-06-26
The second option(running VLC with X11) worked, so it must be a driver problem. How do I fix it? With option 3? Because, yes, I'm running Jaunty.

If I DO pursue the last option, what would the "damage" to my system be? and would it be reversible? If so, how?

---

### Post by Closed_Port on 2009-06-26
> **nobodygh said:**
> The second option(running VLC with X11) worked, so it must be a driver problem. How do I fix it? With option 3? Because, yes, I'm running Jaunty.

If I DO pursue the last option, what would the "damage" to my system be? and would it be reversible? If so, how?
There's no guarantee that option 3 would fix it, but for me and from what I read for many others, the newer drivers do a good job. So I think it would be worth a try.

As to what could happen. I think the worst thing that could happen is that X doesn't work anymore. If that happened, you'd have to downgrade to the old drivers via the command line. 

Anyway, I don't think the risk is all that great, but as always when doing something like this, make sure to back up your important data first.

---

### Post by nobodygh on 2009-06-29
I've just installed the newer drivers, but I still get the insufficient resources error. So no luck there

---

