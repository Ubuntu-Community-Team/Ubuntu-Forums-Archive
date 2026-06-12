---
title: "looking for a  a good dvd ripper"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-24
so any ideas?

---

### Post by lisati on 2009-07-24
For DVDs that you are allowed to legally copy, check the add/remove software list, there are one or two programs available there.

---

### Post by cgb on 2009-07-24
acidrip works pretty good.

---

### Post by wojox on 2009-07-24
dvdshrink works good as well.

[http://sourceforge.net/projects/dvdshrink/](http://sourceforge.net/projects/dvdshrink/)

---

### Post by binbash on 2009-07-24
k9copy , dvd::rip

---

### Post by stinger30au on 2009-07-24
k9copy

sudo apt-get install k9copy

it will copy a piece of toast if you feed it in the drive too:P

---

### Post by danggrianto on 2009-07-24
how about VLC?
look at this [website]("http://www.therealcaffeine.com/how-to/rip-dvd-with-vlc/")

---

### Post by KEE on 2009-08-06
> **stinger30au said:**
> k9copy

sudo apt-get install k9copy

it will copy a piece of toast if you feed it in the drive too:P

lol i cant get k9copy to do anything. it says its copy/extracted in just a few secs but never really does it  =/ it lies lolz

---

### Post by CaptainMark on 2009-08-06
if your wanting to take them for portable devices handbrake rocks

---

### Post by Ubun2 Us3r on 2009-08-06
i second handbrake, its really fast and is easy to use

---

### Post by stickystuff361 on 2009-08-06
Acid::rip is a very easy tool to use, very customisable options and in the repositories.

---

### Post by powel212 on 2009-08-06
Ripping DVDs takes an increadibly long time. 

My solution is to put the DVD in my drive open it in nautilus (file browser)

pull the .vob files off of the disc and place them on the desktop. There are usually 4-8 of these .vob files.

Then I drag the .vob files one by one, (making sure i get them in the right sequential order), into Avidemux and then save the new movie file as an mpeg. and your done.

This process takes about 10 minutes instead of hours. This way you end up with really big files but Avidemux can also recode the files down to xvid which are much smaller.

You can also use "cat" in a terminal to combine the .vob files into .mpeg file which is also a really fast way to get your DVD movies off the disc and into an avi file.

in a terminal

```
cat /home/user/desktop/movie01.vob /home/user/desktop/movie02.vob /home/user/desktop/movie03.vob /home/user/desktop/movie04.vob > /home/user/desktop/movie-finished.mpg
```

I hope that helps

Powel

---

### Post by oldos2er on 2009-08-06
> **KEE said:**
> lol i cant get k9copy to do anything. it says its copy/extracted in just a few secs but never really does it  =/ it lies lolz

 Maybe this will help: [https://help.ubuntu.com/community/K9Copy#Using%20K9Copy](https://help.ubuntu.com/community/K9Copy#Using%20K9Copy)

---

### Post by k3lt01 on 2009-08-07
I use dvd::rip. Sure it takes a fair while to do its thing but it does it sooooooo well. You can customise many aspects of the rip from file type output to output quality in both sound and video.

---

### Post by KEE on 2009-08-08
> **oldos2er said:**
> Maybe this will help: [https://help.ubuntu.com/community/K9Copy#Using%20K9Copy](https://help.ubuntu.com/community/K9Copy#Using%20K9Copy)

yeah still not sure where is this "MPEG4 Encoding tab"? maybe its outdated version =/ heres a pic of k9copy that i have [http://www.facebook.com/photo.php?pid=3098442&l=007e5e0a67&id=786568222](http://www.facebook.com/photo.php?pid=3098442&l=007e5e0a67&id=786568222)

---

### Post by oldos2er on 2009-08-08
I think 'Create MPEG4' is what you want.

---

### Post by donkyhotay on 2009-08-08
I use acidrip, it works pretty well.

---

### Post by KEE on 2009-08-08
> **oldos2er said:**
> I think 'Create MPEG4' is what you want.

yea that's the icon that says it encoded it in 5ms once you click it  =/

---

### Post by Narada on 2009-08-08
+1 for Handbrake

---

### Post by TransitMan on 2009-08-08
> **jessic said:**
> I use Sothink DVD Ripper,I feel it is ok.you can go to [http://www.softdir.net/dvd-video.html](http://www.softdir.net/dvd-video.html)  to download it,it at the 2ed page.

[B][URL="http://www.softdir.net/software/sothink-dvd-ripper-4c22bd444899d3b6047a10b20a2f26db.html"]
[/URL][/B]

You're offering a Windows only solution. 
This is a Linux forum, and the OP is looking for a Linux solution.
Please remember this when making suggestions on what programs may be available to use.

---

