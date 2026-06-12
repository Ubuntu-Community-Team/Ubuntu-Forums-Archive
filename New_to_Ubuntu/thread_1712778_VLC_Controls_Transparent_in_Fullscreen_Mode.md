---
title: "VLC Controls Transparent in Fullscreen Mode"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Berrex on 2011-03-23
Hello. A few weeks ago, kamitsukai made a post about VLC's volume controls being entirely transparent when VLC was in fullscreen mode, except for a portion of the volume controls. The thread is here: [http://ubuntuforums.org/showthread.php?t=1691707](http://ubuntuforums.org/showthread.php?t=1691707)

The thread was closed because it was assumed that the issue only pertained to Linux Mint. However, I am using Kubuntu 10.10 and am having the exact same issue, so I am certain that it applies to Kubuntu as well, and is therefore relevant to this forum. If anybody knows of a way to make VLC's controls opaque in full screen for Kubuntu 10.10, I would appreciate it. Thanks!

---

### Post by barbedsaber on 2011-03-23
if you're using KDE, it is almost certainly relevant.

my first piece of advice is that you turn off any advanced desktop effects you have on, even if that's not a long term solution, it could narrow down the problem.

---

### Post by Berrex on 2011-03-23
Thanks for the prompt response, barbedsaber. I disabled desktop effects, and the result was that the controls turned mostly black. Here's a screenshot:
[http://img6.imagebanana.com/img/bg2mcrnw/snapshot1.png](http://img6.imagebanana.com/img/bg2mcrnw/snapshot1.png)

---

### Post by barbedsaber on 2011-03-23
hmm, very strange

do you happen to know the model of graphics card you are using, and the drivers you have installed for that card. And are the controls affected in windowed mode?

---

### Post by barbedsaber on 2011-03-23
for what it's worth, I don't actually know what's wrong here, so if anyone else wants to jump in and solve this problem, feel free to do so...

---

### Post by barbedsaber on 2011-03-23
made this google search
[http://www.google.com.au/search?sourceid=chrome&ie=UTF-8&q=transparant+controls+VLC+kde#hl=en&pwst=1&sa=X&ei=_86JTbu8JpOGvAPz07TkDg&ved=0CBUQvwUoAQ&q=transparent+controls+VLC+kde&spell=1&fp=4d28cd33eab3f83e](http://www.google.com.au/search?sourceid=chrome&ie=UTF-8&q=transparant+controls+VLC+kde#hl=en&pwst=1&sa=X&ei=_86JTbu8JpOGvAPz07TkDg&ved=0CBUQvwUoAQ&q=transparent+controls+VLC+kde&spell=1&fp=4d28cd33eab3f83e)

found this thread on the arch forum
[https://bbs.archlinux.org/viewtopic.php?id=104574](https://bbs.archlinux.org/viewtopic.php?id=104574)

it appears to be an ongoing bug. (which seems like a pretty big one imho)
they have suggested a workaround (creating a new user, downgrading QT, both very annoying workarounds)
I suggest you take a look at the bug report, or look into making a bug report with VLC directly (rather than through arch, seeing as you are not using arch :P )

also, in the bug report ([https://bugs.archlinux.org/task/21386](https://bugs.archlinux.org/task/21386)) someone mentions that they solved the problem by not using the "oxygen" theme, perhaps that would be a useable workaround

sorry for the wall of text :P

---

### Post by Berrex on 2011-03-23
I have an nVidia Geforce 8800GT, and the drivers I have installed are the latest nVidia drivers from jockey-kde (260.19.06). As far as windowed mode, the controls are integrated into the main window, like so:
[http://img6.imagebanana.com/img/ojlwiaxk/snapshot1.png](http://img6.imagebanana.com/img/ojlwiaxk/snapshot1.png)

I have to go to bed right now as it's getting pretty late over here, but I'll check this thread again when I wake up tomorrow. If I can furnish any additional information, please let me know.

EDIT: Thanks for the links. I'll check them out tomorrow and will post the results! :)

---

### Post by Berrex on 2011-03-23
I switched the theme to Plastique really quickly before going to bed and the problem disappeared! So it seems to be related to the Oxygen theme... I will research this more tomorrow. I'll post here with an update. Thanks again!

---

### Post by ankspo71 on 2011-03-23
Hi,
The third post on the following link has a fix to try:
[http://forum.videolan.org/viewtopic.php?f=13&t=88390](http://forum.videolan.org/viewtopic.php?f=13&t=88390)
Hope that helps.

---

