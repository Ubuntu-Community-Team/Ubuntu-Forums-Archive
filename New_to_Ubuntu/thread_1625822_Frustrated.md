---
title: "Frustrated"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by tmcthree on 2010-11-19
I'm getting pretty fed up with ubuntu. 
At first I really liked it for its speed but I'm rapidly going off it. 

There was a bug where my messaging menu was repeated in the upper panel so that it was overlayed on the other commands, such as "shut down". I tried to delete the copy and ended up deleting the whole panel. Now I don't know how to get it back.

And my graphics tablet has suddenly stopped working properly. (seemingly since the last update.)

No one seems to be able to tell me how to sync folders between my laptop and desktop.

I've got work to do tonight but I can't do it because of the graphics tablet.

Edit. If I reinstall ubuntu will it delete my programs/files?

Very very very fed up.

---

### Post by santosh83 on 2010-11-19
> **tmcthree said:**
> I'm getting pretty fed up with ubuntu. 
At first I really liked it for its speed but I'm rapidly going off it. 

There was a bug where my messaging menu was repeated in the upper panel so that it was overlayed on the other commands, such as "shut down". I tried to delete the copy and ended up deleting the whole panel. Now I don't know how to get it back.

And my graphics tablet has suddenly stopped working properly. (seemingly since the last update.)

No one seems to be able to tell me how to sync folders between my laptop and desktop.

I've got work to do tonight but I can't do it because of the graphics tablet.

Edit. If I reinstall ubuntu will it delete my programs/files?

Very very very fed up.

I'm not sure but just invoking 'gnome-panel' in your terminal might do the job. As for syncing, again I'm not sure at all, but it looks as if Ubuntu One was created for just this purpose. No idea about the graphics tablet, but someone knowledgeable will surely be along soon enough to help you with that.

---

### Post by Garandir on 2010-11-19
Bare with me, as I'm on windows, so I can't give exact instructions.

For the panel: As long as you have one panel, right click it, and you should be able to create a new panel, and add everything back to it via right click.

Graphics Tablet: Not sure, but since they seem to be popular, you could probably find a guide on Google.

Syncing: Are you referring to using Ubuntu's built-in sync or a 3rd-party program?

Reinstalling: It will. I would recommend using a partitioning program to create a separate partition for the data, move the data onto it, reinstall using custom partition settings so that you don't delete/overwrite the partition with the data on it, then move the data back afterwords, or just mount it.

---

### Post by tmcthree on 2010-11-19
> **Garandir said:**
> Bare with me, as I'm on windows, so I can't give exact instructions.

For the panel: As long as you have one panel, right click it, and you should be able to create a new panel, and add everything back to it via right click.

Graphics Tablet: Not sure, but since they seem to be popular, you could probably find a guide on Google.

Syncing: Are you referring to using Ubuntu's built-in sync or a 3rd-party program?

Reinstalling: It will. I would recommend using a partitioning program to create a separate partition for the data, move the data onto it, reinstall using custom partition settings so that you don't delete/overwrite the partition with the data on it, then move the data back afterwords, or just mount it.

I've tried right clicking, which gives me a blank panel. Then right clicking to add everything back. Unfortunately I don't know what was there in the first place, and there doesn't seem to be an option to add some of the things I do remember. The places menu for example, or administrator or system..........

Can't I just get the default menus back?

---

### Post by sisco311 on 2010-11-19
> **tmcthree said:**
> 
Can't I just get the default menus back?

Yep, open a terminal and run:
```
gconftool-2 --recursive-unset /apps/panel
```
then:
```
killall gnome-panel
```
If the default panels don't show up automatically, run:
```
gnome-panel &> /dev/null &
disown
```

---

### Post by DogMatix on 2010-11-19
Here is a link to a script that will reset your panels for you.

[LINK]("http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/")

---

### Post by santosh83 on 2010-11-19
> **tmcthree said:**
> I've tried right clicking, which gives me a blank panel. Then right clicking to add everything back. Unfortunately I don't know what was there in the first place, and there doesn't seem to be an option to add some of the things I do remember. The places menu for example, or administrator or system..........

Can't I just get the default menus back?

The 'Main Menu' item will bring back your applications/places/... menu I think.

---

### Post by tmcthree on 2010-11-19
> **DogMatix said:**
> Here is a link to a script that will reset your panels for you.

[LINK]("http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/")

Thanks that did the trick for the panels!

Thanks everyone who responded.

---

### Post by Wtower on 2010-11-19
I really would like to help. This first frustrating issues will soon wear off after you setup everything as you want and then you can enjoy a quite steady os. We first users are just so much into windows that things in linux that are in the end so easy seem like a mountain.

> No one seems to be able to tell me how to sync folders between my laptop and desktop.

Try unison from software centre. I have found it to be an excellent utility for this matter. And that was before I discovered that turning my desktop into a sftp server with openssh and then with dyndns and some careful security considerations now I can access my files from everywhere, surely something nearly impossible with some other operating systems.

Regards

---

### Post by DogMatix on 2010-11-19
An easy way to synch folders between your lappy and desktop would be Dropbox. Which allows 2GB of space for free.

[LINK]("http://www.dropbox.com/")

---

### Post by realzippy on 2010-11-19
Had a quick look at your problems (threads):
*Graphics tablet drivers*
Suggest you send favux (the guy from the thread) a private message asking for help;maybe he unsubscribed from that thread after 2 weeks..he is online in the moment.

*Desired virtual resolution*
...more info,which graphicscard/driver,generally possible;basically you need a "virtual resolution"...


FN brightness keys samsung NC10
[https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10)
...e.g.,not sure if it helps.Or start a new thread with "samsung NC10 FN keys" in threadtitle...

---

