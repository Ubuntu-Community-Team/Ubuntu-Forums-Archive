---
title: "Oops, I removed the fast user switcher applet thing"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by humphreybc on 2010-01-02
I was playing around (foolishly) in Synaptic and must have removed some core packages related to the applet that sits in the top right hand corner of your panel by default, with your username and when clicked, gives you shutdown options as well as changing your Pidgin/Empathy status.

I'm sure you know the applet I'm talking about.

I rebooted and this applet gave me an error, so I deleted it from my panel and went into Synaptic, searched for "fast user switcher applet" and reinstalled all the relevant packages.

Now I can't find the right applet under the list when I click "Add to Panel" - can someone advise?

Thanks!

PS - this is a different applet to the "Fast User Switcher" one, which displays your full name in bold and your little picture.

---

### Post by warfacegod on 2010-01-02
I think you are looking for *User Switcher*.

---

### Post by aidanr on 2010-01-02
Or indicator applet session.

---

### Post by warfacegod on 2010-01-02
> **aidanr said:**
> Or indicator applet session.

I'm thinking he may have removed both. Neither one completely fits his description but together they do.

---

### Post by dzon65 on 2010-01-02
indicator applet session.

---

### Post by humphreybc on 2010-01-02
User Switcher is the one I talked about that I've got but it isn't what I want.

I've got Indicator Applet in the list, but not Indicator Applet Session.

indicator-session or similar was one of the packages I reinstalled.

---

### Post by dzon65 on 2010-01-02
Synaptics>indicator applet session>install>log out/in>rightclick panel>add..........voila!
"indicator-session or similar was one of the packages I reinstalled.".......there is no similar,you need this one,that is,for what you desribed.

---

### Post by warfacegod on 2010-01-02
Nice desktop. How did you get your panels translucent? I've been looking to do that for a while but this what I've had for the last .5 years.

---

### Post by dzon65 on 2010-01-02
> **warfacegod said:**
> Nice desktop. How did you get your panels translucent? I've been looking to do that for a while but this what I've had for the last .5 years.
That's fairly easy.Rightclick panel>properties>background>color>set transparency (in my case,I made a custom gradient/transparent image.For the windows I use emerald,the nice and simple theme.I think this by far an amazing theme,one can tweak it really nicely.I managed to let the emerald kinda "follow" the panel's gradient,making the panel and the windows merge.Like this:

---

### Post by dzon65 on 2010-01-02
I just saw.The theme you're using uses a panel rc.You could do some changes in the themes gtkrc.You could start by taking out the panel png's and panel gtk(rc).But,apply the changes in the main gtkrc as well cause otherwise,whenever you'll do some terminal work in the home folder itll report as error>file missing.

---

### Post by warfacegod on 2010-01-02
> I managed to let the emerald kinda "follow" the panel's gradient,making the panel and the windows merge

Yeah, I did that too. 

> 
I just saw.The theme you're using uses a panel rc.You could do some changes in the themes gtkrc.You could start by taking out the panel png's and panel gtk(rc).But,apply the changes in the main gtkrc as well cause otherwise,whenever you'll do some terminal work in the home folder itll report as error>file missing.

I have only a rudimentary idea as to what this means. Thanks for replying.

---

### Post by dzon65 on 2010-01-02
Home folder>show hidden files>.themes>the theme you're using>gtk2>look for panel gtkrc>take out the panel png
Same path>take out the panel gtkrc (script)>log out/in

---

### Post by dzon65 on 2010-01-02
It's a real pitty there's no glasser extension for linux available.Once FF 3.7 is there,it won't be needed as that FF-version will support transparency as it is.As for the transparency possibilities (for now) in ubuntu,well,they're half done.(text getting transparent as well.......etc..)
As for your problem,it is fairly easy.Try taking them out the script,save them somewhere and I'm pretty sure you'll have a fully transparent panel.
That FF thing:[http://dzon65.deviantart.com/art/hotmail-trans-129814717](http://dzon65.deviantart.com/art/hotmail-trans-129814717)

---

### Post by warfacegod on 2010-01-02
> Home folder>show hidden files>.themes>the theme you're using>gtk2>look for panel gtkrc>take out the panel png
Same path>take out the panel gtkrc (script)>log out/in

This worked. Too well! It killed most of my themes' look. It looked like I was using Nautilus as root. Fortunately, I made copies and put them back.

---

### Post by warfacegod on 2010-01-02
> That FF thing:[http://dzon65.deviantart.com/art/hot...rans-129814717](http://dzon65.deviantart.com/art/hot...rans-129814717)

Very slick.

---

### Post by dzon65 on 2010-01-02
Oops!!Just take out the image the themer used as panel background,the script for the panel as well.Don't take out the whole script,you'll end up using clearlooks.(which of course can be tweaked as well,don't let "them" fool you saying the theme doesn't support color settings,just needs root).Hey,do you like some cool xsplash and gdm tweaking?Have fun:[HowTO: Comprehensive Guide to Customising GDM and XSplash - Ubuntu Forums ]("http://ubuntuforums.org/showthread.php?t=1333683")
Might wanna backup ;-)

---

### Post by warfacegod on 2010-01-02
I ran across that thread last week and meant to read it more thoroughly but I forgot to bookmark and then couldn't find it again. Thanks.

I started this thread because I wanted to change the look of my login screen. I never got the older gdm working properly in my 9.10 upgrade or what I'm on now 9.10 fresh install.

[http://http://ubuntuforums.org/showthread.php?t=1332432]("http://http://ubuntuforums.org/showthread.php?t=1332432")

---

### Post by dzon65 on 2010-01-02
If you're only into changing your gdm/splash,there's another one.This will actually install a menu,no need to do terminal.But that's only the login.:[http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

---

### Post by dzon65 on 2010-01-02
> **warfacegod said:**
> I ran across that thread last week and meant to read it more thoroughly but I forgot to bookmark and then couldn't find it again. Thanks.

I started this thread because I wanted to change the look of my login screen. I never got the older gdm working properly in my 9.10 upgrade or what I'm on now 9.10 fresh install.

[http://http://ubuntuforums.org/showthread.php?t=1332432](http://http://ubuntuforums.org/showthread.php?t=1332432)

You're sure about the link.Server keeps bumpin'.

---

### Post by warfacegod on 2010-01-02
[http://ubuntuforums.org/showthread.php?t=1332432]("http://ubuntuforums.org/showthread.php?t=1332432")


[http://http://ubuntuforums.org/showthread.php?t=1332432](http://http://ubuntuforums.org/showthread.php?t=1332432) is wrong, I didn't notice that http: was in there twice, sorry.

---

### Post by dzon65 on 2010-01-02
LOL,didn't see it.Well, I hope the guy starting this thread managed to solve his problem.Hope you enjoy the feedback (small world isn't it).Have fun!
Kind regards,J.

---

### Post by warfacegod on 2010-01-02
> LOL,didn't see it.Well, I hope the guy starting this thread managed to solve his problem.Hope you enjoy the feedback (small world isn't it).Have fun!
Kind regards,J.

Indeed, thanks. I just realized that we completely hijacked his thread. Regards.




Sorry thread starter guy.

---

### Post by dzon65 on 2010-01-02
The thread starter guy is from New Zealand,........I'm sure he can take a punch.Take care guys.

---

### Post by humphreybc on 2010-01-02
> **dzon65 said:**
> The thread starter guy is from New Zealand,........I'm sure he can take a punch.Take care guys.

Lol no worries guys I just woke up and saw 3 pages of new replies.... I was like "hmm surely my question wasn't that hard..."

Anyway I've managed to get it working so that's great.

Cheers!

---

### Post by warfacegod on 2010-01-02
I hereby dub thee; Sir humphrey thread starter floating head guy that can take a punch. Knight of New Zealand.


It would be nice if the Add to Panel menu had more detail and more descriptive names (like you now have).

---

