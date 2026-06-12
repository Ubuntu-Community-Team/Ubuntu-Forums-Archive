---
title: "Best CD/DVD Writer for Ubuntu?"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-23
I tried to open an ISO file through Ubuntu and right to a CD and was not able to.  What is the best application for this type of thing?

---

### Post by freds3251 on 2011-05-23
I use Brasero Disk Burner and K3B. For most of the time I use K3B, cuz I make alot of movies and its works perfect for that. Either one will Write ISO files to Disk for you. Hope This helps!!

---

### Post by Hedgehog1 on 2011-05-24
I use Nero for Linux (and Nero in Windows, too). These are both 'for pay', but work very well.

The Nero for Linux has a 30 day trial.

***The Hedge***

:KS

---

### Post by cosine352 on 2011-05-24
K3b

---

### Post by jaychandran_s on 2011-05-24
Brasero rocks, and if you are used to Nero on windows, then be ready to be amazed! With brasero, you can do all that you are most likely to do and much more. for more details, visit [http://projects.gnome.org/brasero//index.html](http://projects.gnome.org/brasero//index.html)

---

### Post by wildmanne39 on 2011-05-24
> **TAspr said:**
> I tried to open an ISO file through Ubuntu and right to a CD and was not able to.  What is the best application for this type of thing?
Hi, you do have to install the restricted packages for it to work. I recommend using this link and going down the whole page that way you flash,mp3 cd,dvd and all will work, [http://ubuntuforums.org/showthread.php?t=766683:D](http://ubuntuforums.org/showthread.php?t=766683:D)

---

### Post by jtarin on 2011-05-24
I've tried quite a few with varying results and have settled on Gnome Baker in my Ubuntu installation. I use Brasero in Slackware quite well.

---

### Post by hakermania on 2011-05-24
Brasero, Devede, K3B

---

### Post by TAspr on 2011-05-24
> **jaychandran_s said:**
> Brasero rocks, and if you are used to Nero on windows, then be ready to be amazed! With brasero, you can do all that you are most likely to do and much more. for more details, visit [http://projects.gnome.org/brasero//index.html](http://projects.gnome.org/brasero//index.html)

Please tell me how to download the tar bal file located above and tell me how to execute it please?  

I am complete newb when it comes to this type of file.  Any help would be greatly appreciated.

---

### Post by halovivek on 2011-05-24
i am using basero, its doing fine.

---

### Post by jtarin on 2011-05-24
Don't download the tarball.Use Synaptic.
Be aware if your using Gnome desktop you will end up downloading a bunch of KDE dependencies with Brasero.

---

### Post by jre6 on 2011-05-24
Install brasero by typing this in terminal:
```
sudo apt-get install brasero
```
Of course, you need to have a working internet connection.

---

### Post by garycahill on 2011-05-24
Brasero is my vote.

---

### Post by kaldor on 2011-05-24
> **TAspr said:**
> Please tell me how to download the tar bal file located above and tell me how to execute it please?  

I am complete newb when it comes to this type of file.  Any help would be greatly appreciated.

As the others have said, use the "Ubuntu" way. The Tarballs are just packages of the source code to be compiled; you can't execute them, you need to build them.

Ubuntu uses precompiled .deb packages. You can install these very easily. 

Method 1: Go to the Ubuntu Software Centre (Applications > Ubuntu Software Centre) and search for the application you want, and press "Install".

Method 2: Terminal commands are not needed, but I personally find it much quicker than navigating through menus. Install brasero with *sudo apt-get install brasero* and it will take care of itself.

Remember, it isn't Windows; you do not need to go hunting for software for most of the things you need.

---

### Post by TAspr on 2011-05-24
> **kaldor said:**
> As the others have said, use the "Ubuntu" way. The Tarballs are just packages of the source code to be compiled; you can't execute them, you need to build them.

Ubuntu uses precompiled .deb packages. You can install these very easily. 

Method 1: Go to the Ubuntu Software Centre (Applications > Ubuntu Software Centre) and search for the application you want, and press "Install".

Method 2: Terminal commands are not needed, but I personally find it much quicker than navigating through menus. Install brasero with *sudo apt-get install brasero* and it will take care of itself.

Remember, it isn't Windows; you do not need to go hunting for software for most of the things you need.

Let me ask you another question please; is the "sudo apt-get install" and whatever comes after it, they way you look up software fro Ubuntu?  How about seeing if it is available first?

---

### Post by jtarin on 2011-05-24
You can use Synaptic also to search for software. Usually if I find something I want online built or not built for another distro, I will search Synaptic first to see if it's in the repositories. If not then I might Google the name of the application with the additional term of .deb,but that's not a guarantee you will find something compatible with your version. Then if I don't find it by those two methods and I really want/need it.....I will buld it.

---

### Post by TAspr on 2011-05-24
> **jtarin said:**
> You can use Synaptic also to search for software. Usually if I find something I want online built or not built for another distro, I will search Synaptic first to see if it's in the repositories. If not then I might Google the name of the application with the additional term of .deb,but that's not a guarantee you will find something compatible with your version. Then if I don't find it by those two methods and I really want/need it.....I will buld it.


Well, that's a whole "nother" ball game there, I am just not ready to compile anything at this point.

---

### Post by kaldor on 2011-05-24
> **TAspr said:**
> Well, that's a whole "nother" ball game there, I am just not ready to compile anything at this point.

Yep, and you shouldn't need to ;)

To search for packages before installing, run "sudo apt-cache search firefox" (firefox being an example) and that will give you a fairly large list. I always just run apt-get install; it'll ask you before you install, anyway.

Edit: And of course, the terminal isn't *needed*. You can easily just use the Ubuntu Software Centre to have a nice, organized list.

---

### Post by sidzen on 2011-05-24
CLI . . . not 'needed' perhaps, but the easiest.

[PHP]sudo apt-get remove brasero && sudo apt-get update[/PHP]

[PHP]sudo apt-get -f install k3b && sudo apt-get install k9copy[/PHP]

[PHP]sudo apt-get autoremove && sudo init 6[/PHP]

Log in and burn, rip, copy CDs/DVDs to your heart's content!

---

### Post by jtarin on 2011-05-24
sidzen....it's not necessary to use the PHP code insertion button when you want to comment in a box as you have, you can also just use the "#"(code) button on the reply menu.

---

### Post by TAspr on 2011-05-24
> **sidzen said:**
> CLI . . . not 'needed' perhaps, but the easiest.

[PHP]sudo apt-get remove brasero && sudo apt-get update[/PHP][PHP]sudo apt-get -f install k3b && sudo apt-get install k9copy[/PHP][PHP]sudo apt-get autoremove && sudo init 6[/PHP]Log in and burn, rip, copy CDs/DVDs to your heart's content!

Why would I want to get rid of brasero?  Out of curiosity in the first part?  Isn't that what most people were telling me to get?

---

### Post by TAspr on 2011-05-24
Well, the most visually pleasing is the "K3b" by far.  Is that a KDE program?  What others in KDE are like that?  Wow, it's fantastic.  The Brasero disk burner has me take the CD/DVD out because it cannot eject it, but the K3b does everything.  I think it will be be K3b & Brasero as my launcher choices, but keep a few others around as well.  Thanks for recommending both of them.

---

### Post by sidzen on 2011-05-25
Good!
Glad you go what you wanted -- it's all about choices!
Cheers

---

### Post by TAspr on 2011-05-25
> **sidzen said:**
> Good!
Glad you go what you wanted -- it's all about choices!
Cheers

More important, is that a KDE program?

---

### Post by cjv8888 on 2011-05-25
> **TAspr said:**
> More important, is that a KDE program?

It does not matter.  k3b runs flawlessly in Gnome.

---

### Post by wildmanne39 on 2011-05-25
> **TAspr said:**
> I tried to open an ISO file through Ubuntu and right to a CD and was not able to.  What is the best application for this type of thing?

Hi, I use the same as the other post but also make sure you go to this link and go all the way through the page to get all media needs taken care of. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) :)

---

### Post by jtarin on 2011-05-25
> **TAspr said:**
> More important, is that a KDE program?
Yes. It is a KDE program but it will run in Gnome. To do this it will download all the associated dependencies it needs.Be aware of the size of the download before you start while not extremely large it is somewhat more than you would think. Some people will need to consider bandwidth and drive space.

---

### Post by TAspr on 2011-05-25
> **cjv8888 said:**
> It does not matter. k3b runs flawlessly in Gnome.
 
Yes, but the reason I ask, is that do all KDE programs run as smoothly as this if it is a KDE program or is it this specific program?

---

