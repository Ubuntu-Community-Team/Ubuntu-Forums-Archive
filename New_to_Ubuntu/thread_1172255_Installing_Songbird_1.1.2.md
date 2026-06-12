---
title: "Installing Songbird 1.1.2"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by pmj85 on 2009-05-28
Hi guys,

This should be a really simple one for most of you; the solution is likely staring me right in the face but, being a complete newbie (this is my first install) I'm at a complete loss.

I'm trying to install Songbird by following the guide here:

[Click]("http://www.arsgeek.com/2006/10/06/how-to-install-songbird-on-your-ubuntu-box-and-then-enjoy-the-music/")

The guide instructs me to type in the  following command to move the downloaded tar file from Desktop to Opt:

```
cd /opt

sudo cp ~/Desktop/Song* .
```However, this error is returned when I try:

```
cp: missing destination file operand after `/home/paul/Desktop/Song*.'
```As I say, I know most of you are likely sat there with your head in your palms but I'm absolutely clueless! I've been adventurous and tried botching a few bits and bobs on to the end of the command. Alas, the problem persists.

I get what the commands do but I have no idea why it is saying the destination file is missing. Could it be a permission error? Any help would be greatly appreciated! 

Oh dear, I'm not fairing too well am I? I can't even manage my first installation :oops:

---

### Post by powel212 on 2009-05-28
Here is a better set of instillation instructions

[http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

Powel

PS
Although it is officially out of beta it still is really a beta and although it is a great work in progress please be advised it is very buggy.

I use Banshee in Ubuntu

and I run itunes in a windows virtualbox when I want to sync my ipod.

P.

---

### Post by kpkeerthi on 2009-05-28
Or get the deb from here: [http://www.getdeb.net/release.php?id=4214]("http://www.getdeb.net/release.php?id=4214")

Download the deb file to your desktop and double-click on it to install.

---

### Post by pmj85 on 2009-05-28
Much appreciated, thank you! :) I'm about to head off home in a sec so I'll have to report back later.

re: iPod syncing, that's what I'm actually after (well, iPhone - I'm guessing they're one and the same). I'll also check the Windows (WINE?) thing out when I get home as an alternative.

Thanks for the advice!

---

### Post by powel212 on 2009-05-28
Songbird does not satisfactorily sync apple products.There is also no satisfactory solution in wine.

What I use is actually inside Ubuntu run a full version of windows, (not a dual boot).

You can run itunes 8.1 inside windows inside Sun VirtualBox inside Ubuntu. This way you have all that Linux has to offer plus seemless control of your very finicky apple products.

Example
[http://www.flickr.com/photos/sunrisefoto/3567107074/](http://www.flickr.com/photos/sunrisefoto/3567107074/)

sun Virtualbox
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Powel

---

### Post by pmj85 on 2009-05-28
This just gets better and better! 

I haven't had chance to have a play tonight (I'm posting this from my Windows computer. For shame!) but I'll have a good look at that tomorrow.

Thanks guys, info very much appreciated. I'm sure you'll see many more posts from me in the not too distant future :p

---

### Post by sigixv on 2009-05-28
the link provided by powel212 works best (at least that's how i did it a few week ago)

Didn't like songbird though, *nix version seems to be lacking a great deal in terms of usability and plugins in comparison to windows version. Podcast didn't work for me, search was slow in comparison with other players, you can't move the window between desktops or minimize it in the panel, unable to delete files from disk from inside the program...
Didnt test ipod sync due to these file management issues

A shame really, being a nice looking program

---

### Post by pmj85 on 2009-05-29
Thanks for the info guys :D

I'm now running Virtualbox with windows XP alongside Ubuntu; this allows me to hook up to the work network so I can still do my day to day bits and bobs! I've set it up so I have Ubuntu on one desktop and Windows on the other... it seems to work quite well (if a little slow; this laptop only has 512mb of ram).

I'm already sold on Linux - I'm going to purchase a faster laptop to make it more feasible for work use and also install it on my home computer... perhaps with a dual boot, just in case ;)

---

