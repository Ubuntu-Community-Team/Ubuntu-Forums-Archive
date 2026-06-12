---
title: "How can I install packages with no internet?"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by JimStewartBrown on 2009-09-28
I am brand new to this linux/ubuntu thing, only having experience with windows (and not very technically oriented either).

I just installed Ubuntu 9.04 on an old compaq desktop (1.97Ghz Athlon, 512mb RAM, integrated Intel graphics - can't recall number, as well as sound) but no internet (don't worry, I know the problem - it's not hooked up yet)

Everything seems to work fine, but I wanted to add more packages to get more exprience with what Ubuntu and Linux have to offer, and the household wifi plans are a little far off for now.  

Is there a way to download packages to a usb drive (either while in vista, or utilizing the ubuntu live CD) from our new laptop with an internet connection?

Any help would be appreciated.  Plus, if the wife sees how AWESOME this Ubuntu/Linux thing is supposed to be, maybe she'll want to use it too (as she is tired of the Blue Screen)

Thanks in advance.

---

### Post by pedro3005 on 2009-09-28
Sure you can do that :D Look at this site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by astrakhan on 2009-09-28
you can download packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

but you have to remember to download the dependencies too (the packages which your application depends on), sometimes these dependecies also have dependencies which aren't already installed and dependencies of dependencies and so on...

then to install just use ```
sudo dpkg -i packagename
```

it can be a bit of a nightmare... of course if you install packages from repositories direct to your ubuntu, dependencies are automatically installed. why not fix up the internet first?

---

### Post by pedro3005 on 2009-09-28
Wait, no need for commands to install DEBs! Isn't it way simpler to just double-click it?

---

### Post by arochester on 2009-09-28
Look at [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by JimStewartBrown on 2009-09-28
Thanks for all the input.  I can't wait to give them a try when I get back from work.

I think I might be able to handle this.  I'll keep you posted.

 . . . and the internet thing - well, I'm on a bit of a "spending freeze," and who wants to wait, I want to play with my new ubuntu toy.

---

### Post by wojox on 2009-09-28
You could also look at: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Cheezespread on 2009-09-28
Or you could just copy it from a friend who already uses Ubuntu from their /var/cache/apt/archives folder. Copy them and install ;)

---

### Post by t0p on 2009-09-28
When I started using Ubuntu, I had no internet connection.  And, although it's possible to install software from [packages.ubuntu.com]("http://packages.ubuntu.com"),  it can be a real pain.  If you fall into [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell"), it really can be hell!  [AptOnCD]("http://aptoncd.sourceforge.net/") is a solution, but it involves quite a bit of time downloading stuff.

To be honest, lack of internet connection made running Ubuntu very much a pain.  I was close to giving up in exasperation, but luckily I found out I could connect to the internet via my cellphone.  Maybe you could do something similar?  Check the link in my sig for tips.  And good luck!

---

### Post by fuzzyk.k on 2009-09-28
Installing many packages using for example ```
dpkg -i *
``` can sometimes kill your system

---

### Post by Bartender on 2009-09-28
+1
I've tried Keryx twice in the last few months.  Keryx involves some command line work which a newbie is unlikely to be able to follow.  Finally I had a USB stick with a bunch of packages to install to the target PC.  To get them to install you use the dpkg *i command or even "force" (recommended on Keryx forum).  I did this once, not using the force command, and one package failed to install.
Got more packages a week later, installed, now the PC is stuck and says it can't do any more upgrades until Synaptic talks to the servers.

Linux offline or behind a dial-up connection is still a big old pain.

---

### Post by kambrik on 2009-09-28
Follow this how to [http://www.compuhowto.com/linux/ubuntu/ubuntu-update-with-no-internet/]("http://www.compuhowto.com/linux/ubuntu/ubuntu-update-with-no-internet/")

---

### Post by EXCiD3 on 2009-09-28
As many people have mentioned, installing via dpkg is not ideal. However there is a nice remedy to this if you use Keryx and copy the files over to the cache folders and install them via apt-get as if you had internet. You can use the LocalRepoAdd.py script to do this that's bundled with Keryx.

And for an extra bonus, Keryx works on any platform, Linux/Mac/Windows so you can grab new packages from any machine. :)

---

### Post by JimStewartBrown on 2009-09-29
Thanks everyone for you help.  I used synaptic on the liveCD to see what all the dependencies were, then in vista, downloaded them from packages.ubuntu.com to a usb drive.  From there, double-clicking them handled the install, although I had two stubborn packages that were mutually dependent on one another.  I moved them to /home, then ran dpkg -i * and DONE!  That was amazing, now I can listen to mp3's and explore the wonders of the open source world!

---

### Post by Justin2 on 2009-10-04
When I first started using Ubuntu I didn't have an internet connection either. 
Even though I now use a 3G USB modem I still don't use it to download Ubuntu Software packages but only to check e-mails, surf the web, etc.

Its far easier and cheaper to just buy the entire Ubuntu Software repositories on DVD from various places/shops that sell Linux DVDs that post them to you. You can buy the entire Ubuntu repositories (usually 6 DVDs) as well as restricted software/ packages like playing encrypted (store Bought movie DVDs) on a separate DVD called MediBuntu repository.
I usually buy my DVDs from a place called FOSSCDs.
Check out their website below:

[http://www.fosscds.co.za/index.php?cPath=21_34_164](http://www.fosscds.co.za/index.php?cPath=21_34_164)

[http://www.fosscds.co.za/product_info.php?products_id=526](http://www.fosscds.co.za/product_info.php?products_id=526)

Once you have the repo DVDs you go into synaptic and on one of the settings click on add CDROM. After adding all DVDs you click refresh/reload. Once you select something to install it will ask for the relevant DVD (DVD3 for example) and not install via an internet connection.

---

### Post by itsbrad212 on 2009-10-04
really simple. just go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Justin2 on 2009-10-04
Just make sure that if you use the Ubuntu Repository DVDs to install programs that you have a full/normal install of Ubuntu and have NOT installed Ubuntu with the WUBI installer via Windows otherwise these disks won't work.

---

### Post by praveesh on 2009-10-04
If you come across, mutually dependant packages, you can make a repository cd with the help of aptoncd and use synaptic to install them. You don't need to write the repository cd iso created by aptoncd to install softwares . You can use cdemu a daemon tools like took for Ubuntu . It is recomended to use synaptic instead of dpkg

---

