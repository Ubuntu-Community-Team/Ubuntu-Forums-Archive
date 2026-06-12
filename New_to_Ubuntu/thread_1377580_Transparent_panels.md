---
title: "Transparent panels"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by RabbitWho on 2010-01-10
still with Jaunty.... I just installed the Xfce desktop in the hopes of seeing some performance difference in the computer.. and it worked! But I am very shallow and miss the transparent panels. 

Allright you're thinking, easily solved, Help button, here's what it gets me:
> 
     The Panel Manager can be opened from the Xfce Settings Manager or from the      right-click menu on one of the panel items.   
**Figure 6. Panel Manager**

**[nice picture of the panel appearance window, but with one little thing extra to mine, the ability to slide the transparency back and forth]**




[B]
[snip][/B]





Transparency         ***If your system and the window manager support it,*** you can set the         transparency level of the panel. You can also choose if you would          like the panel to become fully visible when the mouse moves over         it.

so why is the option there in the picture but not there for me? The system must be able to support it as it works in gnome.. and the window manager.. well that's xfce isn't it? 

Any ideas what I'm doing wrong or what I can do to get the panels transparent? 

(besides running compiz, as the whole point of installing xfce was to speed the computer up, i'm not to slow it down again) 


Thanks :)

---

### Post by RabbitWho on 2010-01-10
Another small problem.. i had a link on my panel to the terminal for so long I can't remember where it is... i've been looking all over the place and i have to search for it with google desktop in order to get it up, and of course i look at the location it gives me as well, but when I go there it's not there. . . it's probably invisible >.< just like my keys

---

### Post by dzon65 on 2010-01-10
As for the terminal,look in synaptics for xfce terminal.Install,should appear in the applications menu,rightclick to add to panel.

---

### Post by RabbitWho on 2010-01-10
Twas already installed, it's located in the usr share folder, right clicking did nout, it refused to drag onto the panel.. so I just copied the command from the properties and made a launcher for it, that's one problem solved at least, thanks!

---

### Post by gsmanners on 2010-01-10
If you want special effects like panel transparency in Xfce, your best bet is to go to Window Manager Tweaks and turn on display compositing.

---

### Post by RabbitWho on 2010-01-10
That worked! thank you!

only problem is it makes the writing and icons transparent as well... 

[http://forum.xfce.org/index.php?topic=3398.0](http://forum.xfce.org/index.php?topic=3398.0) there's a patch or it, but it requires compiz to work. 

I can make it look as if it's transparent by doing this:

[http://xubuntu.wordpress.com/2007/10/12/howto-set-a-background-image-for-your-panel/](http://xubuntu.wordpress.com/2007/10/12/howto-set-a-background-image-for-your-panel/)

But I don't really feel like going through all that every time I change my backgrounds, so I'll stick with opaque. 

Thanks again to you both all the same! Great help :)

---

### Post by RabbitWho on 2010-01-10
Arf, I have to mark this unsolved again. 

I said, yanno, what the hec, i'll put a backround image in.. i followed the instructions here:
[http://xubuntu.wordpress.com/2007/10/12/howto-set-a-background-image-for-your-panel/](http://xubuntu.wordpress.com/2007/10/12/howto-set-a-background-image-for-your-panel/)

and now my panels don't exist at all through xfce and even my gnome ones are messed up, patchy and with bits of blue on them or no reason. I tried reinstalling both the xfce and the gnome panels and that did no good

Is there a way to find that file i made and if i can can i just clear it and everything will go back to normal? if it wasn't for google desktop and the terminal i wouldn't be able to do anything at all, I better be careful not to break them as well!




> 
TOUCH(1)                         User Commands                        TOUCH(1)

NAME
       touch - change file timestamps

SYNOPSIS
       touch [OPTION]... FILE...

DESCRIPTION
       Update  the  access  and modification times of each FILE to the current
       time.

       A FILE argument that does not exist is created empty.

       A FILE argument string of - is handled specially and  causes  touch  to
       change the times of the file associated with standard output.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       -a     change only the access time

Gosh darn it, i take that to mean clearing the file won't do any good because i don't know what used to be there
....


Ah ha! I got the panels up with
```

 xfce4-panel &
```
and they seem in good health, but they're not commming up on start up 

It reminds me of this comic:
[http://xkcd.com/349/](http://xkcd.com/349/)

I know what he's trying to do is more difficult but at this point I'll be so happy if everything was just back how it was when I started... at least I didn't delete any grubs this time!

Weyhey i fixed it!

What happened was she had written to be sure and save the image in the home folder, this being Ubuntu and I not being a root user i couldn't save in the home folder but i FIGURED (stupidly) that to save it in the home/username folder would do just as well, so when the computer was starting up the panel and got to the picture link it panicked and refused to load. .. or it caused an error I should say.. so what I did was just delete the line about background image and walla, it comes up on start up again. If I wasn't so stupid i'd say i was a genius.

---

