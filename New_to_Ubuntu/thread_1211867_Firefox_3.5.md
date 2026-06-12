---
title: "Firefox 3.5"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by old_dope on 2009-07-13
I am already running Firefox 3 but would like to upgrade to the latest version 3.5. The only problem is i would have to download a file:
firefox-3.5.tar.bz2 to my desktop . Could someone tell me how i proceed from here please. Thanks

---

### Post by CatKiller on 2009-07-13
firefox-3.5 is in the repositories.

---

### Post by gjoellee on 2009-07-13
Firefox 3.5 is in the repo.

Click on the link, to install firefox 3.5: [apt://firefox-3.5](apt://firefox-3.5)

---

### Post by t0p on 2009-07-13
I take it you downloaded firefox-3.5.tar.bz2 from [www.getfirefox.com?](www.getfirefox.com?) Okay, you need to right-click it and select **Extract to here**.  A folder called **Firefox** will appear.  Inside the folder is a shell script, also called Firefox.  You run that script, and it runs Firefox 3.5 for you.

If you move that Firefox folder to your home directory, you can start Firefox 3.5 with the command

```
~/firefox/firefox
```

Or you can right-click on a panel and add a launcher that runs the command.

Of course, you can do as the others advised, and install Firefox 3.5 from the repositories, with the command

```
sudo apt-get install firefox-3.5
```

But when I did that last week, what I got was the beta, with the code-name "Shiretoko".  That archive you get from [www.getfirefox.com](www.getfirefox.com) is not a beta.  It is not a "release candidate".  It is the final version of Firefox 3.5.  But of course, if you don't install through apt-get, or at least a .deb, you won't get automatic updates.  Your choice.

---

### Post by CatKiller on 2009-07-13
> **t0p said:**
> But when I did that last week, what I got was the beta, with the code-name "Shiretoko".

While Shiretoko was the development name for Firefox 3.5, the version you had was not the beta; it was the final release. The decision was made to keep the Shiretoko branding since Firefox 3.0 and Firefox 3.5 are designed to work well side-by-side, so only one of them could be called "Firefox." Since Firefox 3.0 was the version that was available when Jaunty was released, that was the one that got to be called "Firefox." When Karmic comes out, Firefox 3.5 will be the default, and so that is the one that will get to be called "Firefox."

More details [here]("http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html").

---

### Post by JohnLau on 2009-07-13
click here to install firefox 3.5.
If you want to make it your default browser, please follow [my guide]("http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/")

---

### Post by old_dope on 2009-07-13
I have checked in both Synaptic Package Manager and Add/Remove and Firefox-3.5 is not there!

I clicked on the links provided by (gjoelee) and (JohnLau) and nothing happened?

I also tried opening a terminal and typing:

sudo apt-get install firefox-3.5

as suggested by t0p and was rewarded with the following:

E: Couldn't find package firefox-3.5

What's going on?

---

### Post by CatKiller on 2009-07-13
> **old_dope said:**
> What's going on?

It's in the Universe repository.

Actually, if you're still on Intrepid, it might not be in the Intrepid repository. Just the Jaunty one.

I believe there's a script called UbuntuZilla that is able to download and install the newest version if you still want to stay on Intrepid.

---

### Post by twright on 2009-07-13
You can run firefox from the downloaded archive perfectly well, all you need to do is extract it to your home folder and then drag and drop the firefox file onto the panel. If you want to replace the default firefox with it you can do so by opening a terminal and typing:```
sudo ln -s **<path to new firefox>** /usr/local/bin/firefox
```

---

### Post by Short__Error on 2009-07-13
So is this the final version of FF-3.5 or just another beta version???

---

### Post by philinux on 2009-07-13
> **Short__Error said:**
> So is this the final version of FF-3.5 or just another beta version???

see post #5

---

### Post by Garyhans on 2009-07-13
Thanks so much for this thread. Installed flawlessly. Java works. Flash on youtube crashes when full screen is selected. I had to disable hardware acceleration in flash to get full screen to work just like I did with 3.0 Version. But on the bright side I noticed quite a speed increase in Browsing. Thanks Again.

---

### Post by old_dope on 2009-07-13
I have found Firefox but it's already installed so that must be Firefox 3. Perhaps the problem lies with the fact that i am running Xubuntu 8.10? I did try to upgrade Xubuntu from 8.10 to 9.04 from inside the Update Manager but for some reason this wouldn't take so i re-installed Xubuntu 8.10. O woe is me!

---

### Post by DizzyEwok on 2009-07-13
Just install it from the repositores mate.

---

### Post by lovinglinux on 2009-07-13
For future reference...


The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by 5nak3 on 2009-07-13
Just my $0.02, I followed LovingLinux's tutorial choosing method 1 and it works a treat, and I'm on Hardy (8.04). 

Give it a go, you should be fine with it!

---

### Post by maxpoweron on 2009-07-13
I submitted a post asking how to upgrade Firefox 3.0.11 to 3.5.  I found a separate post stating install Ubuntuzilla.  It worked great for my PC running Ubuntu 9.04.  The link is at 

[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way]("http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way")

---

### Post by JohnLau on 2009-07-13
Which version of ubuntu are you using? It is only availible on the official Jaunty(9.04) update repository. If you are using older version of ubuntu, you'll have to add a software source
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)
Visit this page for details
John

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

