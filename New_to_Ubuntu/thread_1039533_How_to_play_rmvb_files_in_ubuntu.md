---
title: "How to play rmvb files in ubuntu ?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mlotfi on 2009-01-14
Hi,

I have a link that has a movie in rmvb , when I clicked on it I got only a guarbage text file, should I install something ?

thanks

---

### Post by Michael.Godawski on 2009-01-14
hi,

have a look at this guide:


[LIST]
[*][http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)
[/LIST]

OR:

use the real player:


[LIST]
[*][http://www.real.com/linux](http://www.real.com/linux)
[*][http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux](http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux)
[/LIST]
I would try the Real Player first.

---

### Post by mlotfi on 2009-01-15
Hi Micheal,

I just followed the istructions on how to install RealPlayer11.bin, but I still get a text file with wired symbols opened instead the movie.

in othe website  I found behind the browser realplayer opened and a dialog box alert saying :

Could not find an appropriate lxplay or realplay in the system path to use as an embeded.


thanks

---

### Post by Terl on 2009-01-15
> **mlotfi said:**
> Hi Micheal,

I just followed the istructions on how to install RealPlayer11.bin, but I still get a text file with wired symbols opened instead the movie.

thanks

Did you follow this [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/")?

It says in that tutorial, specifically written for Ubuntu, to use MPlayer.  You might want to check through that link.

---

### Post by jsf_pp on 2009-01-15
i did it like this:

```
sudo apt-get install realplayer
```

and everything works fine.

btw, are you gettin those movies from [http://download-fanatico.blogspot.com/](http://download-fanatico.blogspot.com/) ?

---

### Post by mlotfi on 2009-01-15
mlotfi@majid:~/Desktop$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
mlotfi@majid:~/Desktop$

---

### Post by jsf_pp on 2009-01-15
damn! well, we tried at least... sorry, i dont know that much about it. i was just tellin you the way it worked for me.

---

### Post by jerome1232 on 2009-01-15
> **mlotfi said:**
> mlotfi@majid:~/Desktop$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
mlotfi@majid:~/Desktop$

That package is in the medibuntu repos, I bet you don't have those enabled. Here is how you add them [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

When done retry installing realplayer like that. You could also try helix-player, that's what realplayer is based on anyways.

---

### Post by Mze on 2009-01-15
Try this Firefox extension (i.e. if you're using Firefox as your primary browser) [MediaPlayerConnectivity]("https://addons.mozilla.org/en-US/firefox/addon/446").

---

### Post by mlotfi on 2009-01-15
How to uninstall reaplayer ?

thanks

---

### Post by Mze on 2009-01-15
[Realplayer installation methods]("https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods")

UbuntuWiki

---

### Post by mkvnmtr on 2009-01-15
I don't recall that file type but when I want to read or play a fill type that doesn't work I go to the package manager. I type in the search the file type and get back all the programs that work on that file type. I read about them and decide if one or all are what I am looking for. Install it and I am set to go. So far I have found nothing that I could not solve with that approach.

---

### Post by andrew.46 on 2009-01-15
Hi,

MPlayer will play these files although I believe the default Ubuntu version will have trouble. Can I suggest that people test their methods against a single rmvb file? The one I have used is contained on the MPlayer samples page and shows the first [few moments of the eagles reunion]("http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/hotel_california_ra5.1_640x480_30s.rmvb").

The svn MPlayer, allied with SMplayer, plays this flawlessly and I have attached a screenshot to show it in action. Unfortunately the road to compiling the svn MPlayer is not the easiest but there is a guide on these forums that [illustrates how to go about this]("http://ubuntuforums.org/showthread.php?t=1024592"). And yes it is my guide :-).

Can anybody assemble a screenshot of the RealPlayer playing this file?

Andrew

---

