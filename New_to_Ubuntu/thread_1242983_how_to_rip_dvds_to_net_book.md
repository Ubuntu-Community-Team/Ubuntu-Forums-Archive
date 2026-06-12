---
title: "how to rip dvds to net book"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-08-17
i am on the acer aspire one 8.9". i am going to be taking a trip to california by bus from michigan. i'd like to watch my movies but i dont wanna lug around all the dvds and the external drive. i found this tutorial but its confusing. [http://ubuntuforums.org/showthread.php?t=273635&highlight=ripping+dvds]("http://ubuntuforums.org/showthread.php?t=273635&highlight=ripping+dvds")

i wish it to be as easy as ripping a cd. just pop it in and press "rip" . thanks for any help. 

P.S. 

i am aware of copyright laws. i do not wish to make copies onto dvds... just onto my hard drive.

---

### Post by snakeman21 on 2009-08-17
I have a much better solution for you.  I actually have the same netbook you have, and I have done this repeatedly.  Plug in your external DVD drive.  Insert the DVD into the drive and wait for it to be recognized.  Then open a terminal and enter:

```
sudo dd if=/dev/dvd of=NAME_OF_MOVIE.iso
```

Replace "NAME_OF_MOVIE" with whatever you want the file to be named, usually the movie name.  You will not get a progress bar or any confirmation, but Ubuntu will rip the DVD to an .iso file in your home folder.  This usually takes between 10 and 30 minutes, depending on the size of the file.  When it is done, the terminal will let you know.  
To play the movie, you will need a program with DVD capabilities such as VLC.  Right-click on the .iso and select "open with VLC" and it will play just like the DVD, menus and all.  

Good luck!

Edit:  Keep in mind that a DVD can take up between 4 and 8 gigs, so watch your disk space when copying DVD's to your hard drive.  I actually put all of mine on my 230GB external HD to save disk space.

---

### Post by cirabisi2009 on 2009-08-17
when i type in the command line it comes up saying error cannot read /dev/dvd ... maybe i need to install the libdvdcss2 ?

---

### Post by snakeman21 on 2009-08-17
Hmmm... that's strange... It could be because you're using an external DVD drive, I actually use a different computer with a built-in drive.  You may need to do the same.  I'm guessing that because it's a USB drive, /dev/dvd is not the correct path.  I would just use a different computer to rip them before your trip.  If you don't a different computer running ubuntu, you could use a live CD or USB and follow the same instructions.

---

### Post by roharme on 2009-08-17
Is it legal to Rip a DVD!!!

---

### Post by snakeman21 on 2009-08-18
> **roharme said:**
> Is it legal to Rip a DVD!!!

Yes, it is, as long as you only rip ONE COPY for YOUR OWN use and you don't start burning more copies and distributing them.

---

### Post by Lars Emil Gutt on 2009-08-18
On my computer the dvd drive is 
/dev/sr0
Try to find out where your dvd drive is mounted.

---

### Post by jms1989 on 2009-08-18
you could try using /dev/sr0 or /dev/sr1 or /dev/scd0 or /dev/scd1 in that dd command. oh, you don't have to use sudo to run dd. :)

Just try each device with the usb dvd drive connected until you hit bingo, have fun. ;)

---

### Post by edu1962 on 2009-08-18
You could try using [COLOR="Red"]k9copy[/COLOR].[COLOR="Black"]Should be in your respetories (Synaptic).[/COLOR]

---

### Post by stinger30au on 2009-08-18
k9copy rocks

u can tell it to output an .iso file 2 if u want

sudo apt-get install k9copy

---

### Post by themusicalduck on 2009-08-18
The best program I found for ripping DVDs was handbrake - [http://handbrake.fr/](http://handbrake.fr/)

It's not in the repositories so you have to download the deb from that site.

Also I think OGMRip is pretty simple to use and it is in the repositories.

---

### Post by MrWES on 2009-08-18
> **cirabisi2009 said:**
> i am on the acer aspire one 8.9". i am going to be taking a trip to california by bus from michigan. i'd like to watch my movies but i dont wanna lug around all the dvds and the external drive. i found this tutorial but its confusing. [http://ubuntuforums.org/showthread.php?t=273635&highlight=ripping+dvds]("http://ubuntuforums.org/showthread.php?t=273635&highlight=ripping+dvds")

i wish it to be as easy as ripping a cd. just pop it in and press "rip" . thanks for any help. 

P.S. 

i am aware of copyright laws. i do not wish to make copies onto dvds... just onto my hard drive.

I take it you only want a hard file on your laptop you can play while traveling. First install vobcopy. From a terminal, Applications | Accessories | Terminal, type:
```
sudo apt-get install vobcopy
```

Now with the DVD in the drive just, and from the terminal type:
```
vobcopy -l -t movie_title.vob
``` (that's a lower case L)
that will rip the largest (main title) from the DVD. It'll take a few to several minutes depending on your PC. You can play .vob files with mplayer, totem, etc. That's all there is to it. I included a screen shot.

---

### Post by snakeman21 on 2009-09-08
Whatever happened with this?  Did you find a method to your liking?

---

### Post by realzippy on 2009-09-08
[QUOTE=

```
sudo dd if=/dev/dvd of=NAME_OF_MOVIE.iso
```


[/QUOTE]

...this works even with copy protected DVDs if you watch the DVD (e.g. with "Kaffeine") simultaneously.Of course you need libdvdcss2....

---

### Post by solitaire on 2009-09-30
the dd method is great 
** helpful hint is to install "dcfldd" it's an enhanced version (which you'll never need to use) but it DOES have one VERY useful feature over the standard dd

* Status output - dcfldd can update the user of its progress in terms of the  amount of data transferred and how much longer operation will take.  

it's in the repos

---

