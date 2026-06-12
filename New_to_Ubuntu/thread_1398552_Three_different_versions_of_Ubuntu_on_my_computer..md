---
title: "Three different versions of Ubuntu on my computer."
date: 2010-02-04
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-04
Just wondering why when I boot up, apart from my Win XP,  I have a choice of three different versions of Linux.generic.... There is a version 14, 17 and 18.

---

### Post by da burger on 2010-02-04
I believe that is to give you a different choice of kernel to run. In other words you would be running a different version of linux behind ubuntu.

---

### Post by Tholley on 2010-02-04
If you are running regularly update in your system,the old kernel left behind when ubuntu installs a new linux kernel.The old kernels leave in grub menu,so grub becomes longer and longer.
 
there are ways you can delete some of them out of grub if you wish.
 
I see you are using 9.10...
 
In 9.04 you used to be able to delete the old ones using Startup Manager, I think you can use Ubuntu Tweak now to do it in Karmic.

---

### Post by doas777 on 2010-02-04
the extra kernels won't hurt and don't take up signifigant disk space. I advise you to keep at least one kernel back though, just incase the next kernel update renders your box unbootable. that way you can just load up the older one.

---

### Post by audiomick on 2010-02-04
G'day.
They are old kernels, it means your kernel has been updated twice since the install.
You can happily ignore it, it is not costing you much disk space, a couple of MB I think.

You can remove them from the grub menu, but leave them there. Don't ask me how, though; I have always shied away from doing it.  ;)

You can remove them completely, but I don't know how to do that either. Maybe some nice person will show up who knows.

It is advised to keep at least one older than the current kernel. That way if something goes wrong with the current one, you can still boot into the previous one.

I will have a bit of a search and see if I can find a "how to" for the old kernels.
You are on a fresh installed 9.10, aren't you? That would have grub2. There is info about editing the boot menu here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
You could probably do it with the "startup manager" as well. I haven't looked at that yet, but it can be installed with synaptic package manager.

---

### Post by ThePinkWitch on 2010-02-04
> **da burger said:**
> I believe that is to give you a different choice of kernel to run. In other words you would be running a different version of linux behind ubuntu.

oh cool, I can screw three versions up instead of just one :D Thanks for that info :)

---

### Post by audiomick on 2010-02-04
HI.
According to this post
[http://ubuntuforums.org/showpost.php?p=8636542&postcount=2](http://ubuntuforums.org/showpost.php?p=8636542&postcount=2)
you can just remove the old kernels with the package manager.

---

### Post by drs305 on 2010-02-04
I included a brief section on older kernels and what you can do with them in a guide on StartUp-Manager.

Here is the link. The section on hiding/removing older kernels is near the bottom. Be sure to read the note on Ubuntu-Tweak as well, an easy way to remove older kernels.

[ HOWTO: StartUp Manager & Kernel Display Options  ]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Tholley on 2010-02-04
Ubuntu 9.10 (GRUB 2) left out the option to clean kernels in Startup Manager, but
 
If you&#8217;d like a GUI, Ubuntu-Tweak is a good choice where you can remove them from *Applications->Package Cleaner->Clean Kernel*
 
Install Ubuntu-Tweak,see:[[COLOR=#14568a]http://ubuntuguide.net/installupgrade-latest-ubuntu-tweak-in-ubuntu9-109-048-108-04[/COLOR]]("http://ubuntuguide.net/installupgrade-latest-ubuntu-tweak-in-ubuntu9-109-048-108-04")

---

### Post by ajgreeny on 2010-02-04
just uninstall the oldest of the three with synaptic, leaving the two most recent.  Search for 2.6.31-14 in the search system of synaptic and remove all the installed packages that show with that number.

All of those amount to about 170MB for each kernel, not just a couple, so if you are short of space it is worth getting rid of all except the two most recent numbered kernels and associated packages.

---

### Post by warfacegod on 2010-02-04
> **ThePinkWitch said:**
> oh cool, I can screw three versions up instead of just one :D Thanks for that info :)

After my own heart!

---

### Post by Rex Bouwense on 2010-02-04
> **warfacegod said:**
> After my own heart!

I like that attitude.

---

### Post by ThePinkWitch on 2010-02-04
> **audiomick said:**
> HI.
According to this post
[http://ubuntuforums.org/showpost.php?p=8636542&postcount=2](http://ubuntuforums.org/showpost.php?p=8636542&postcount=2)
you can just remove the old kernels with the package manager.

Thanks AGAIN Michael :D

---

### Post by ThePinkWitch on 2010-02-04
> **warfacegod said:**
> After my own heart!

I reinstalled Ubuntu for the Fifth time day before yesterday. You would be so proud LOL

---

### Post by ThePinkWitch on 2010-02-04
> **Rex Bouwense said:**
> I like that attitude.

LOL Thanks :) I'm incredibly stupid I keep banging my head against the keyboard.

---

### Post by ThePinkWitch on 2010-02-04
> **Tholley said:**
> If you are running regularly update in your system,the old kernel left behind when ubuntu installs a new linux kernel.The old kernels leave in grub menu,so grub becomes longer and longer.
 
there are ways you can delete some of them out of grub if you wish.
 
I see you are using 9.10...
 
In 9.04 you used to be able to delete the old ones using Startup Manager, I think you can use Ubuntu Tweak now to do it in Karmic.

Thanks Tholley :)

---

### Post by ThePinkWitch on 2010-02-04
Ty For reply ajgreeny :)

---

### Post by ThePinkWitch on 2010-02-04
> **drs305 said:**
> I included a brief section on older kernels and what you can do with them in a guide on StartUp-Manager.

Here is the link. The section on hiding/removing older kernels is near the bottom. Be sure to read the note on Ubuntu-Tweak as well, an easy way to remove older kernels.

[ HOWTO: StartUp Manager & Kernel Display Options  ]("http://ubuntuforums.org/showthread.php?t=818177")

Thankyou reading that now :)

---

### Post by warfacegod on 2010-02-04
> **ThePinkWitch said:**
> I reinstalled Ubuntu for the Fifth time day before yesterday. You would be so proud LOL

I've done that many over the last six months.

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> I've done that many over the last six months.
Beaten by a girl! How do you feel now?;)

---

### Post by warfacegod on 2010-02-04
> **audiomick said:**
> Beaten by a girl! How do you feel now?;)

I'm not breaking stuff to my utmost, I am ashamed.  ...Where's my sawzall?....


(warfacegod falls to his knees and hangs his head in abject misery at the realization of his utter failure.)

---

### Post by ThePinkWitch on 2010-02-04
> **warfacegod said:**
> I'm not breaking stuff to my utmost, I am ashamed.  ...Where's my sawzall?....


(warfacegod falls to his knees and hangs his head in abject misery at the realization of his utter failure.)

There there..let me on your system for five minutes..I'll break it for you. It's the least I can do for all your help :D

---

### Post by warfacegod on 2010-02-04
> **ThePinkWitch said:**
> There there..let me on your system for five minutes..I'll break it for you. It's the least I can do for all your help :D

Absolutely not!

---

### Post by warfacegod on 2010-02-04
I can break stuff on my own. Thanks though.

---

### Post by danwosere2007 on 2010-02-04
> **ThePinkWitch said:**
> Just wondering why when I boot up, apart from my Win XP,  I have a choice of three different versions of Linux.generic.... There is a version 14, 17 and 18.

3 different versions of ubuntu? Thats just greedy man, what do you expect ;)

---

### Post by ThePinkWitch on 2010-02-04
> **warfacegod said:**
> Absolutely not!


LOl well who doesn't like to share then? It made sense to me. I'm a natural and you're so busy helping out on the forum. I could break it and you could have the fun of fixing it. Fine! *sulking off into the sunset* Anyhoo I'm sure I'll continue breaking my own :D

---

### Post by ThePinkWitch on 2010-02-04
> **danwosere2007 said:**
> 3 different versions of ubuntu? Thats just greedy man, what do you expect ;)

You know what? If I'd a known I had three at a time to break I wouldn't have reinstalled FIVE times lol. ;)

---

### Post by warfacegod on 2010-02-04
> **ThePinkWitch said:**
> You know what? If I'd a known I had three at a time to break I wouldn't have reinstalled FIVE times lol. ;)

3 X 5 = 15 installs to break!

---

