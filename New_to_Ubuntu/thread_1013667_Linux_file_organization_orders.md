---
title: "Linux file organization orders?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-12-17
I moved from XP, where putting "+", or other symbols in front of the filename moved them to the beginning of the list of files, and helped me organize things neatly without relying on alphabetical sorting. I noticed those symbols do nothing to file order in linux.

Is there any way to name a file so it comes up before others/always have a file in a certain place in the order regardless of the other's orders (kind of like adding a "separator" between it and the other folders, like with a bookmark in firefox)? ie: an important folder is placed at the top of a list of folders whenever organizing the folders by name/other method? I know I can manually move files to a place, but that doesn't keep them aligned neatly natively in the order I choose, and that's what I want.

Also, on a related note, how do you add additional metadata columns in a file view that you can't choose from the menu? I'd like to add an option to view every file under my MUSIC folder with track numbers as a column, so I can arrange them by track number. Track number isn't one of the view options, and I can't understand why it's not already!

---

### Post by Pconfig on 2008-12-17
Hey,

to solve your problem in sorting you could try to add an emblem to the files you want on top. You can do this by

right click ==> properties ==> emblems and then select one.

After you've done that, you click

edit ==> preferences ==> arrange items ==> by emblems (in nautilus)

And there you go, the files with an emblem come on top.
I don't really know a solution for sorting on tracknumber though.

---

### Post by Pconfig on 2008-12-17
I also found this thread.

Seems you can get ubuntu to sort the same way as windows ;)

[http://ubuntuforums.org/archive/index.php/t-471154.html](http://ubuntuforums.org/archive/index.php/t-471154.html)
(Still no fix for the tracknumbers though)

Edit:
It's probably impossible to show tracknumbers
[http://www.linuxquestions.org/questions/ubuntu-63/mp3-tags-in-nautilus-459379/](http://www.linuxquestions.org/questions/ubuntu-63/mp3-tags-in-nautilus-459379/)

---

### Post by BastardNamban on 2008-12-17
Oh ****. You mean gnome is TOO SIMPLE for me- it can't do what I want???

WTF? There is no way to add simple metadata columns?

So, basically, I'd have to switch to Xubuntu to get the KDE desktop environment.

This sucks. It's all this little stuff that's adding up to piss me off.

---

### Post by aheckler on 2008-12-17
To be fair, I don't think you can reasonably expect Linux/GNOME/Ubuntu to cater to everyone's tiny quirks about how they like to have their system function, that's just unrealistic.

---

### Post by hambone79 on 2008-12-17
I don't know if this helps, but I use a similar method to force my folders/files to the top of the list by adding numbers to the beginning. Here is an example:

01_Documents
01_Graphics
01_Video
02_CAD Files
02_CAD Templates

Using the number system lets me decide at what level I want them to appear in the list.

As for your other requests, I think these would be great ideas to suggest to the [Nautilus]("http://projects.gnome.org/nautilus/") developers. Who knows, you may see them in the next release of Gnome.

---

### Post by BastardNamban on 2008-12-17
aheckler, I actually agree with you. I'm a bit weird with the folder organization.

What really and truly astonishes me about gnome based Ubuntu is that with the multitudes of impressive stuff I see it can do, I cannot BELIEVE they didn't put in more column options, especially for track number. I would think that is a basic item, but I guess I'm wrong.

So, KDE has that option- but I'm using gnome. I finally am getting used to gnome ubuntu, and I think I want to switch to Kubuntu for the single KDE option of showing track number.

---

### Post by Captain_tux on 2008-12-17
As **hambone79** mentioned, have you considered writing a note to the developers? 

It may just be the spark they need to incorporate the functionality!

---

### Post by BastardNamban on 2008-12-17
I will try that. I have no idea what to say, as I would think many others would have suggested that simple item by now!

EDIT: I took your advice and emailed the nautilus team. I gotta say, though, it feels like asking something of The Wizard of OZ,
a bunch of almighty programmers behind a curtain, too busy to be bothered or take seriously some newbie's suggestions,
especially since they are XP inspired. I feel like I'll just be shooed away for mentioning XP at all, but track listing columns
are something I really can't believe they left out...

I guess we'll just see what happens, huh?

---

### Post by philinux on 2008-12-17
How about installing dolphin. I have a few kde apps like k3b already installed.

---

### Post by handydan918 on 2008-12-17
> **BastardNamban said:**
> Oh ****. You mean gnome is TOO SIMPLE for me- it can't do what I want???

WTF? There is no way to add simple metadata columns?

So, basically, I'd have to switch to Xubuntu to get the KDE desktop environment.

This sucks. It's all this little stuff that's adding up to piss me off.

You're not alone. Linus Torvalds agrees with you...

> "This 'users are idiots, and are confused by functionality' mentality of Gnome is a disease. If you think your users are idiots, only idiots will use it. I don't use Gnome, because in striving to be simple, it has long since reached the point where it simply doesn't do what I need it to do.
Please, just tell people to use KDE." 

---

### Post by BastardNamban on 2008-12-17
What's Dolphin, and how would that help me? Can you explain?

EDIT: Handydan, does that mean you agree with Torvalds? How is he still thought of in this community after saying something like that- he DID create
linux, but do you people agree with that view?

I'm not sure what someone can do with KDE that they can't in gnome. I value simplicity, but does asking for what I have in this thread mean I don't
think I'm an idiot? Do I really want to do things that can only be done in KDE, or would KDE confuse me?

---

### Post by philinux on 2008-12-17
Dolphin is kde's file manager. It's in the ubuntu repo's via synaptic. This means you keep gnome but have the option of using dolphin instead on nautilus.

---

### Post by BastardNamban on 2008-12-17
Interesting. Would that mean I have to get rid of Nautilus? I've looked at a Gnome vs. KDE comparison- I like the simplicity of Gnome, but I wanted some extra stuff that only KDE seems to offer. Would using Dolphin instead of Nautilus give me the ability to organise by track number, and does it use emblems like nautilus?

---

### Post by Captain_tux on 2008-12-17
> **BastardNamban said:**
> I will try that. I have no idea what to say, as I would think many others would have suggested that simple item by now!

I guess we'll just see what happens, huh?

And that's exactly the point... you can't complain about something unless you choose to be a part of the solution.

---

### Post by BastardNamban on 2008-12-17
Well, technically you can, but it makes you look like an a$$. I emailed them so I hopefully don't look like one :p

---

### Post by eaidoido on 2008-12-18
i read your email about nautilus feature requests. you mention wanting to place an image on the folder for quick navigation. one option would be to change the icon into a picture. or, what i do, i find some good looking alternative icons, there are many freely available online at places such as [gnome-look.org]("http://gnome-look.org"), and i replace my music folder with something that is more suitable than the uniform blank folder. cheers

---

