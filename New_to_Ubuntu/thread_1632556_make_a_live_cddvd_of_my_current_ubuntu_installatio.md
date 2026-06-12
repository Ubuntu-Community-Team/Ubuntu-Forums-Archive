---
title: "make a live cd/dvd of my current ubuntu installation"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-28
):PHello everyone, I was wondering if it's possible to make a live cd of my current ubuntu installation.The filesystem usage is now 2.8 gb so it should fit into a cd when compressed, right:-s? This will be very useful if anyday for some reason I format my hard disk and have to reinstall ubuntu.... it would take lots of days to make it like it is now:frown:, so a preconfigured distro of my own can come really handy:biggrin:. Also in case a live cd can't be made, do tell me the way to make an install cd/dvd.(Can live dvd's be made?:-\").

And lastly, what approx. filesystem usage range can be compressed and placed in an installation/live cd? What is the approx. range for a dvd?:-({|=

P.S.... From tomorrow my exam will start:cry: and I might be slow to follow the thread or remain silent for 1 or 2 days. Pls don't mind that....:redface:

---

### Post by carl4926 on 2010-11-28
You can use 'dd'
to make a copy of the partition and save it as an image

If your Ubuntu install is on sda2

```
dd if=/dev/sda2 of=/home/username*/backup.image bs=4096 conv=noerror
```

replace username* with your username

---

### Post by theozzlives on 2010-11-28
Remastersys works well for just that job.

---

### Post by dhiman33 on 2010-11-29
Yessss\\:D/... remastersys looks like EXACTLY the thing I need.... so making a live dvd is also possible?:-o I might use this to create an ubuntu distro with all my favourite games+applications!! The repositories will also be there sitting already updated, right? I use some softwares like handbrake,mediainfo which are from 3rd party rep. Will they also be retained with their software sources intact in the sources list?(Hurrah!!)

8-[Now this is a big question. When I first tried to install an application in ubuntu, it said it needed to update the repos first:evil:.So I couldn't install any app before it downloaded repository files. In this case, the new ubuntu will have a repository from start,:mrgreen: and so it wouldn't need net connection to install some predownloaded deb packages from another machine, is it?[-o<

P.S.... Today's exam didn't went in a good way(crying); let's see what happens tomorrow.

---

### Post by ivarn on 2010-11-29
I'm sorry about your exam.
Well, if you go to synaptic, click on the "edit" menu, update packages and then "repair broken packages" since you can't update nor download updates.
This will fix that problem.
And no, remastersys won't save any customized data, configs or serial codes unless you choose the "private use" options.
Because all your configs, docs and registrations are being saved in your /home/yourname folder. If you want to make a private backup I suggest you first clean the browser history and then from the terminal run "sudo apt-get autoclean". This will delete all cache files and other things that just eats up your disk space for no reason.

---

### Post by QLee on 2010-11-29
> **dhiman33 said:**
> ...
8-[Now this is a big question. When I first tried to install an application in ubuntu, it said it needed to update the repos first:evil:.So I couldn't install any app before it downloaded repository files. In this case, the new ubuntu will have a repository from start,:mrgreen: and so it wouldn't need net connection to install some predownloaded deb packages from another machine, is it?[-o<
...

By the way, I find your use of all the "smilies" is distracting, in my opinion, asking questions in plain text is probably more likely to get you good answers. But not everyone will agree with me about that and you may choose to ask any way you want to.

Updating of the repos, meaning downloading the package list from the repo, is the way the package manager insures that it uses the newest version of a package available. That is what you want to do.

The repository exists on a server somewhere, not on your system, you always have to download (update and upgrade)  to have the latest version and often, newest version will have some security upgrade (update, in this context). It is what you want to do. (It's unfortunate that many times, even in documentation, the terms "update" and "upgrade" are used in a somewhat confusing manner. Especially in English for someone who's first language is not English, which I suspect describes you.)

The debs (packages) that have been previously downloaded to install on your system are kept in, /var/cache/apt/archives. But those will be the versions that were available when they were downloaded and installed and not necessarily the newest versions.

---

### Post by dhiman33 on 2010-11-30
To ivarn: ok ivarn, then u mean I can install an ubuntu system in any machine without net connection and can install any packages offline right from the start! what I have to do is just to select "repair broken packages" under synaptic(Cheers, then\\:D/).

To qlee: SMILIES RULEZ!:guitar:(U see, one single smilie can express something thousand words can't!)

To everyone: Oh no I coudn't install remastersys!:confused: I added "_deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) __karmic_/" to the sources list, then software manager tried to update package list and failed! It says "Failed to download information", "check ur internet connection", and in the details....these lines...

[I]W:Failed to fetch [http://www.geekconnection.org/remastersys/repository/karmic/Sources.gz](http://www.geekconnection.org/remastersys/repository/karmic/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.[/I]

Then I downloaded their source file but how to compile it?

Anyways, in the source folder there was a remastersys-gui file which was executable.. I ran it but couldn't understand the differences between options.I know "backup" backs up everything+personal data but does it make a live disk? And then _what's the difference between dist,distcdfs and distiso_? I chose "dist" option and clicked on o.k twice to get this lines....

"Your  and .md5 files are ready in /remastersys.  It is recommended to test it in a virtual machine or on a rewritable cd/dvd to ensure it works as desired.  Click on OK to return to the main menu."

All this happens in a second, so there's no chance that an image is written. Also I can't find those created files. Now what to do?:-s



P.S.... todays exam was practical, the labwork went fine but the viva went damn bad:evil:.... I coudn't answer one single question:cry:...better not be in ubuntuforums for a few days or my result might become very unpredictable!:tongue:

---

### Post by dhiman33 on 2010-12-01
:popcorn::popcorn::popcorn:

---

### Post by dhiman33 on 2010-12-02
bump
:popcorn::popcorn::popcorn:

---

