---
title: "Having trouble installing wine and flash on dapper"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by bakutenshi on 2009-01-17
So here's the deal. I've been trying to set up ubuntu dapper (x86) remotely on a dedicated server to use as a seedbox. However, I've run into two main errors. Wine won't install correctly, which I need for utorrent (and yes I have ktorrent, but I still want to know what's going on wine), and flash won't install/won't work because I want to do a speedtest.net test in firefox. I've been looking around from google and on forums, but none of the solutions seem to help. I should probably add that there isn't very much of a gui with this, so anything I do, has to be done via the xterm terminal… (I tried to install synaptic package manager, and I think it did, but whenever I try to open it nothing happens).

So when I try to install wine from a repository as "sudo apt-get install wine" it says that I have unmet dependencies from libasound2, libc6, libgphoto2-2, libgphoto2-port0, libcms1, libldap2.4-2, and  libxm12, and "PreDepends: dpkg" and then there's the line "E: Broken packages". So then as an alternative, I tried to compile it from source. And I think it worked because at the end it says something like "wine compile complete", however, when I try to do "wine utorrent.exe" I get the error "bash: wine: command not found."


As for the more frustrating flash not working issue… installing from the repository also won't work with this (I did "sudo apt-get install flashplugin-nonfree"), and then it says there was an error connecting to "fpdownload.macromedia.com… download failed… The Flash plugin is NOT installed." I went to adobe's site in firefox, and tried to install it from there, but nothing seemed to happen. There was a random forum post that recommended installing these three alternative packages for those who couldn’t get flash to work (I can't remember/find the link), but those installs worked without a problem, but flash still didn’t work in firefox (even after restarting the browser). Then I tried this from [here]("http://www.cyberciti.biz/tips/linux-install-flash-player-10.html") and afterward, checked in "about:plugins" and just like in the screenshot, flash was listed! But it won't work!!!! I also downloaded the tar.bz for flash, but after I extract it, the ./configure command won't work, so I'm not sure how to proceed.

Any help and insight would be greatly appreciated. I've been stuck with these two problems for about a week now!!

---

### Post by bakutenshi on 2009-01-18
Okay nevermind, I finally got wine working by downloading wine 1.1.13 and compiling that (as opposed to 1.1.12 from before).

But I'm still having the Flash installation issues. 

Anyone got any ideas?? I would really appreciate some advice.

---

### Post by FreddyGod on 2009-01-19
do you have universe and multiverse repository enabled? cause the files could be on that repositories. And also latest wine is not in the repositories so u need to go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and follow the instructions there for adding wine to repositories.
Also if u can't install those dependencies u can go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and do a search there for what u need

---

