---
title: "Different Icons on Different Desktops"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by MaxVK on 2008-12-22
Hi.

As the title suggests, I want to know if its possible to have different icons on different desktops, so for example I could have some development icons from the menus on one desktop, and some office icons from the menus on another desktop etc.

In the span of the same idea, would it then be possible to have different wallpaper on each desktop, matching the function of the icons and so on.

Cheers

Max

EDIT: Forgot to mention, I'm running 7.10 at the moment, if that makes any difference.

---

### Post by BDNiner on 2008-12-22
This maybe possible. you would have to setup desktops (which are independent of each other) as opposed to workspaces (which are the all on the same desktop). There are plugins for the compiz and patches for nautilus to enable different wallpapers.

---

### Post by xjcannonx on 2008-12-22
well there are some ways to get 4 different wallpapers but as far as i know, they will disable any clicking on the desktop, But I heard of another solution I have been meaning to try...

I heard if you take 4 different wallpapers and use gimp to set them side by side and save that, then that will work, but i am not sure yet...

As far as the other question, I do not know

---

### Post by LtPitt on 2008-12-22
Mmmh...
That would be the true use of multi desktop I'd think...

I hope someone has ideas =)

---

### Post by drs305 on 2008-12-22
Note that none of the following accomplishes what you really desire: independent desktops. In compiz, General, Desktops there are two settings which may apply. The 'horizontal virtual size' setting establishes the number of workspaces, which commonly sets what you would see in the 'workspace switcher'. In the same section, there is a setting for 'number of desktops', which seems like it may be what you really want. On my system I can't change the number to anything other than 1. That combined with the 'wallpaper' option in Window Management might provide a solution. Someone with more familiarity with those options will have to answer.

The 4 wallpapers is fairly easy to accomplish. 

I believe you can do it via compiz but know you can do it with an app called wallpapoz. It will allow you to choose which wallpaper you want on each workspace. Here is the link to wallpapoz:
[http://wallpapoz.akbarhome.com/index.html]("http://wallpapoz.akbarhome.com/index.html")

You can get the .deb from [http://www.getdeb.net/]("http://www.getdeb.net/")  You have to register to use getdeb but there is no charge. There isn't a listing for it in Intrepid but the Hardy version is working fine for me in Intrepid. 

To run it, place a command in Sessions for "daemon-wallpapoz". To set it up once you have installed it, run "wallpapoz".

---

### Post by MaxVK on 2008-12-23
Thanks for the replies everyone. I had a hunt about after posting last night and Iv found a few ways to get different wallpaper on each desktop, but nothing that will allow different icons on each desktop.

In all honesty the wallpaper is only secondary. Id still like to hear if anyone has ideas on the icons though, because that seems to make a lot of sense to me.

Happy holidays to everyone BTW ;)

Max

---

### Post by MaxVK on 2008-12-23
Okay, Iv been digging into this and it seems that this is not the only thread that mentions this particular thing.

Iv tried 'devilspie' (in synaptic), which can recognize a program window by name or ID etc, and move it to the specified desktop when it starts. Its not what we are looking for but it does have some use for now.

Only problem is that it doesn't automatically skip to the right desktop when it opens the programs there!

Max

---

### Post by drs305 on 2008-12-23
> **MaxVK said:**
> Okay, Iv been digging into this and it seems that this is not the only thread that mentions this particular thing.

Iv tried 'devilspie' (in synaptic), which can recognize a program window by name or ID etc, and move it to the specified desktop when it starts. Its not what we are looking for but it does have some use for now.

Only problem is that it doesn't automatically skip to the right desktop when it opens the programs there!

Max

I found devilspie a real pain to set up correctly - much more difficult than compiz. At the time, it was the only thing around. I had to position it in pixels from the left side of the first workspace, even for workspace 4. If you decide to tinker with devilspie,read about running the *debug.ds* feature - it will help you set up devilspie.

---

### Post by MaxVK on 2008-12-24
Hmm, that might have been an older version then, the one I'm using from the repos seems to work quite well, just as long as you remember the difference between workspaces and desktops. If you need the functionality it might be an idea to take another look.

With that said however, its hardly a replacement for the original idea and Iv yet to get it to automatically move to the correct 'Workspace' once it opens a program there.

In all my reading Iv yet to find an answer that doesn't require some heavy programming and recompiling. There are a number of scripts out there that suggest that they do what we need, but there are multiple reports to suggest that while they may work, they don't do so seamlessly, which makes it a bit futile.

Iv also noticed a number of complaints about this, because it seems that an awful lot of people have had the same idea, but that such an idea needs to be implemented by the Gnome developers, who are apparently not interested for some reason.

Which means we are going to have to make do with hacks and tricks to get the functionality we want, or go without.

Max

---

### Post by Ben Page on 2008-12-24
I have 6 different desktops with 6 different wallpapers and each desk has its own icons, but problem is that its in windows xp/vista. You can download an application called Cube 3d, it suposed to be a Compiz replacement for win, search the piratebay (its free when you crack it:P), then you can try running the app through Wine. I don't have Wine installed on my comp, I have dual boot config with XP, so I don't know if it will work and how.

---

### Post by MaxVK on 2008-12-24
Meh, I'm not sure Id want to try this with a Windows app under WINE - Iv a feeling that wouldn't be too stable somehow. I wouldn't want it crashing while I was working on something.

---

