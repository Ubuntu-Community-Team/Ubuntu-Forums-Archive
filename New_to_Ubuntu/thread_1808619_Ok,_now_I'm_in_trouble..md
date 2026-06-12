---
title: "Ok, now I'm in trouble."
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-20
So, a few hours ago, after asking a few questions about upgrading my 10.04 to 11.04, I started the process of upgrading, first to 10.10, to then be able to upgrade to 11.04.
After a slow start, things started to go a lot faster, until, while in the middle of installing the upgrades, the computer froze up completely. I couldn't switch desktops, nor anything else except moving the cursor and shutting the computer off. So, after waiting for about 15 minutes to see if it was something temporary, I hit restart (which, BTW, was showing as "required". From then on, Ubuntu won't start (and neither will the recovery mode), and, every time, I get this message:

> [B]Install problem!
[/B]The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.


Is there a way I can solve this?

Thanks in advance. :)

---

### Post by Swagman on 2011-07-20
I did warn you about upgrading a wubi install.

Basically you tried to update a virtual filesystem. I could be wrong but I suspect you  will need to use windows remove program and re-install.

**THAT'S WHY** I advised you move stuff you want to keep over to your windows drives.

Sorry about that.. Don't blame me, I'm only the messenger.. Also.. I'd done the very same thing you have done !!

---

### Post by Inodoro Pereyra on 2011-07-20
Yep, you did. And I didn't listen. :(

I don't blame you for anything. On the contrary, I thank you for taking the time. Most of my stuff is backed up anyway, but I'd hate to have to reinstall all the extra programs I had installed, and I'd probably lose many bookmarks I want to keep.

Anyway, I'm gonna wait for a while, and see if anybody knows a way to fix it. Otherwise, I guess I'm gonna have to suck it up. :(

Thanks again for everything.

---

### Post by halitech on 2011-07-20
thats the downside to wubi, can't use a live cd to rescue stuff because it doesn't see the filesystem as even existing. I'd suggest if you are going to do it all over again, do a true dual boot install

---

### Post by seawolf167 on 2011-07-20
Sounds like the installation may not have completely finished especially if you don't get any boot or loading screens. Too bad its a wubi install or you could boot off a livecd and try to fix the issue. I'm almost always a proponent of fresh installs (made very easy with a separate /home partition). I think at this point it may be easier for you to simply reinstall and restore your backups to the fresh installation.

Additionally, you may want to take this opportunity to switch to a full install on its own dedicated partition(s) and dual boot instead of using wubi.

Just my $.02

---

### Post by Inodoro Pereyra on 2011-07-20
Hmmm...so the consensus is that this is not salvageable. Damn!:(

Well, if I'm gonna have to reinstall, I'm not installing Windows at all, just Ubuntu. I had the XP for a program I don't need anymore.

So now I'm gonna try and download 11.04, if I can. Otherwise, if I start with the 9.10 CD, it's gonna take me forever.

Thanks again everybody for taking the time. :)

---

### Post by seawolf167 on 2011-07-20
Considering you are doing a fresh install, there are a couple things I recommend

[LIST]
[*]Make a backup image of your hard drive now in case you need to restore something later, I suggest using [Clonezilla]("http://www.clonezilla.org")
[*]Create at least 3 partitions
[LIST]
[*]/ (root) mounted at / (root) of type ext4
[*]/home mounted at /home of type ext4
[*]swap of type swap
[/LIST]
[*]You can take a look at using Wine ```
sudo apt-get install wine
``` to run your Windows programs or even use a virtual os
[*][Here ]("https://help.ubuntu.com/community/Installation")is the official installation how-to
[*]And the official dual boot [how-to ]("https://help.ubuntu.com/community/WindowsDualBoot")just in case you decide to go that route
[/LIST]

---

### Post by rMatey on 2011-07-20
What Seawolf said.  Been there, done that.  But ya learn from yer mistakes.

---

### Post by Inodoro Pereyra on 2011-07-20
Thanks.
I will do that in the future, when I can get a newer computer, but on this one I have a 40 GiB hard drive. No way I can make an image.
On the other computer (the desktop I'm using now) I tried using Wine to run Solidworks, but no luck. I don't know if I was using it correctly, though, as I couldn't find any "Wine for dummies" tutorial...](*,)

---

### Post by seawolf167 on 2011-07-20
Do you have an external hard drive you can write the image too? They are pretty cheap now-a-days.

As for Solidworks, unfortunately is pretty terrible running though Wine, I'd suggest dual booting if you need to use it. [Here ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=318")is the WineHQ review page (pretty terrible huh?).

---

### Post by Inodoro Pereyra on 2011-07-20
I have an external hard drive, but it's almost full. As per cheap, I've been unemployed since December 2009, so, right now, nothing is cheap for me.

So it wasn't just me who couldn't get the Solidworks to work. Good to know. Now I feel a little less of an idiot...:)

---

### Post by seawolf167 on 2011-07-20
> **Inodoro Pereyra said:**
> So it wasn't just me who couldn't get the Solidworks to work. Good to know. Now I feel a little less of an idiot...:)

I definitely feel your pain - I have to dual boot because there are some programs I just have to use for work that are only available (and working 100%) in a Windows environment :(

---

### Post by halitech on 2011-07-20
I know with your connection speed this might not work but there are sites like Adrive where you can get a free storage account. As long as you have enough room to make the image, you could then back it up to something like that

---

### Post by CVGH on 2011-07-20
If you have lots of RAM and a ISO/CD/DVD of XP or W7, try Virtualbox.
I have to do this because I need iTunes for my iPhone......

---

### Post by Inodoro Pereyra on 2011-07-20
> **seawolf167 said:**
> I definitely feel your pain - I have to dual boot because there are some programs I just have to use for work that are only available (and working 100%) in a Windows environment :(

Yep, same here.
Now, to be completely honest, I have to admit Windows 7 works pretty well (especially if you compare it with the previous versions), but, after almost 2 years enjoying Ubuntu, every time I have to open Windows, it feels like the computer is dirty. And having to deal with the stupid antivirus software...:mad:

> **halitech said:**
> I know with your connection speed this might not work but there are sites like Adrive where you can get a free storage account. As long as you have enough room to make the image, you could then back it up to something like that

Hmmm...for what I read, Adrift is free just for a 24 day trial...
Either way, yeah, making an image online at my speeds would probably take a while...:lolflag:

---

### Post by halitech on 2011-07-20
Adrive does have paid accounts but you can get a free one that doesn't expire, I've had one there now for a few years

[http://www.adrive.com/plans](http://www.adrive.com/plans)

and you wouldn't make the image online, you would make it on your computer and transfer it to Adrive (or similiar)

---

### Post by Inodoro Pereyra on 2011-07-20
Hmmm... Either way, with the time it's taking just to download an ISO file, I doubt I can do something like that.
For now, I'm gonna keep it simple. Only Ubuntu on the laptop, and the desktop will remain untouched. Later on, we'll see...

Thanks again everybody for the help. :D

---

### Post by seawolf167 on 2011-07-21
No problem - glad we got it some-what sorted out!

---

