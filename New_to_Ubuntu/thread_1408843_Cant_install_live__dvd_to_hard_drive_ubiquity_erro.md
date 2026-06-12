---
title: "Cant install live  dvd to hard drive: ubiquity error"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by inameiname on 2010-02-16
Within the past two weeks or so, I have been unable to install my custom-made DVD of Ubuntu Karmic, made by Remastersys, onto another computer and/or this one. Each time, it seems to be a problem involving 'ubiquity', as it's saying "ubiquity has crashed."

I have questioned this to the Remastersys folks, who seem certain it's not a problem on their end, but of either a newly updated version of ubiquity or something on my computer. I have been told that it doesn't seem to be an issue with ubiquity, as I have tried uninstalling, reinstalling, upgrading, downgrading it, along with ubiquity-frontend-gtk and whatnot countless times, but nothing works. 

As far as being an issue on my computer, I literally just reinstalled Ubuntu from scratch, from the iso downloaded from [www.ubuntu.com]("http://www.ubuntu.com") earlier today, and updated it with whatever updates were found in the official repos, as well as those from additional ones I've added, all of which have worked flawless for months. 

It seems that the issue lies either in ubiquity, as it simply won't open at all, not even anything stated if I put "sudo ubiquity" or "ubiquity --desktop %k gtk_ui" in the terminal, OR it's a conflict between it and a recent update from one of my sources.list. I'll give you my sources.list if desired.

If anybody can help, that would be great, as I have no way to back up my computer, nor able to put that backup onto others through a custom live dvd.

---

### Post by inameiname on 2010-02-17
Finally, after lots of testings and analysis, I have figured out the problem. It is indeed a PPA repository that had some sort of update which messed with 'ubiquity'. So what I did was reinstalled the entire computer again, but then went through each PPA to see which was causing the problem. 

There is something updated about two weeks ago or so in the following which conflicts with 'ubiquity' (as well as 'nautilus-actions' too actually) which will mess it up to the point where it cannot even open, thus not being able to back up:

deb [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 

So to those who have a similar problem, I suggest checking to see if you have 'janvitus' repository in your sources.list.

Woosh, boy to I feel better now. :P Thanks for all those that have tried to help, which allowed me to deduce some things to get to the point that I was to be able to find the problem.

---

