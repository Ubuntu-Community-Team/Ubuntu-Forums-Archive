---
title: "Find current Window Manager and changing window manager"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by zer010 on 2011-03-18
Ok, I 'm working with 10.04LTS.  I've tried Googling for this, but I keep coming up with ways to change the Desktop Environment, like GNOME to KDE or XFCE. I need  to change Window Managers like Metacity to Compiz and back again.  I'd rather do this from the CLI, so I need a command that will tell me what my current WM is and then one for switching between the two. 
Thanks in advance.

---

### Post by el_koraco on 2011-03-18
dunno about the cli (edit: i think the command is mutter --replace, or compiz --replace, didn't test it though), but you can go to gconf editor - desktop - gnome - session - required components, and there it is.

---

### Post by zer010 on 2011-03-18
> **el_koraco said:**
> dunno about the cli (edit: i think the command is mutter --replace, or compiz --replace, didn't test it though), but you can go to gconf editor - desktop - gnome - session - required components, and there it is.
Isn't that something I gotta install?

---

### Post by el_koraco on 2011-03-18
i'm sorry, not mutter --replace, but metacity --replace.

---

### Post by zer010 on 2011-03-18
> **el_koraco said:**
> i'm sorry, not mutter --replace, but metacity --replace.
"mutter' sounds like it'd be a lightweight WM....:D

---

### Post by zer010 on 2011-03-19
I've been looking EVERYWHERE for this.  I found someone else asking the same on another forum, but they got penalized for Double Posting or bumping....:???:   I've even been trying to find a config file that would name the default starting WM, but no luck. /usr/bin/startx doesn't mention it....
Anyone have any more ideas? :-k

---

### Post by stinkeye on 2011-03-19
Install wmctrl
```
sudo apt-get install wmctrl
```

Find window manager
```
wmctrl -m | grep Name | awk '{print $2}'
```


To load compiz```
compiz --replace &
```


To load metacity```
metacity --replace &
```

---

### Post by zer010 on 2011-03-19
> **stinkeye said:**
> Install wmctrl
```
sudo apt-get install wmctrl
```Find window manager
```
wmctrl -m | grep Name | awk '{print $2}'
```
To load compiz```
compiz --replace &
```
To load metacity```
metacity --replace &
```

Awesome! Thanks so much! I've never really used awk, but first time for everything, right?
I really appreciate this! ^.^d

---

### Post by stinkeye on 2011-03-19
Is there any reason you want to do this in the cli and not just use
**fusion-icon**.

---

### Post by zer010 on 2011-03-19
> **stinkeye said:**
> Is there any reason you want to do this in the cli and not just use
**fusion-icon**.
Somewhat out of curiosity and I didn't want to install the icon yet. 
Nice AWN, BTW.  Is that a Conky I see above the Fusion menu?
Edit: Also what icon set are you using?

---

### Post by stinkeye on 2011-03-19
Yep conky it is.
Click on my name above my avatar and view public profile and you'll find some pics.

Icons are [**_[COLOR="DarkRed"]Gartoon Redux[/COLOR]_**]("http://gnome-look.org/content/show.php/Gartoon+Redux?content=74841")

The icons are also in the repos as **gnome-icon-theme-gartoon** but the link above is a more complete set.

---

### Post by zer010 on 2011-03-19
Awesome Conky and really liking the background. It all ties in very well. ^.^d
I just reinstalled, so I've yet to start adding visuals except for my simple Conky. Gotta have the Conky! lol

---

### Post by zer010 on 2011-03-19
This is what mine used to look like before... Didn't get a clean shot when I took this...

---

### Post by stinkeye on 2011-03-19
> **zer010 said:**
> Awesome Conky and really liking the background. It all ties in very well. ^.^d
I just reinstalled, so I've yet to start adding visuals except for my simple Conky. Gotta have the Conky! lol
Thanks. Yeah conky is a desktop must have.
I run 5 conkys.
gmail
surf report
wind and waves forecast with an image from the local windsurf site
calendar
sysinfo band underneath the panel


> This is what mine used to look like before... Didn't get a clean shot when I took this...
Nice, lua background as well.

---

### Post by zer010 on 2011-03-19
I got the lua.bg from VinDSL to whom I'm infinitely grateful for his work in ferreting out the memory leak... ^.^d

---

### Post by zer010 on 2011-03-19
I hate to say, but after checking those pics and thinkin about my old setup, I just installed the icon anyways...
However, I'm very glad to have the knowledge of how to get that info without it, so this thread and it's posts are not in vain.

---

