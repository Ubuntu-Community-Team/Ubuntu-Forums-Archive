---
title: "No sound in Amarok"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Milind on 2010-04-03
I'm using Lucid Lynx. I can play my music collection in Movie Player and Rhythmbox but on trying in Amarok 2.3.0 I get only total silence. Can anyone help me out with this problem ?

---

### Post by bobin on 2010-04-03
Is the indicator moving quickly from start to end?

---

### Post by Milind on 2010-04-03
> **bobin said:**
> Is the indicator moving quickly from start to end?

No, it doesn't move at all. Besides, I've discovered that Amarok doesn't even show any of my mp3s in its file list. And now, on starting up, it briefly shows a message at bottom right (see screen-shot) that Phonon cannot play mp3 files. I checked the FAQ and did what it said but the problem persists.:(

[IMG]http://farm3.static.flickr.com/2737/4487852519_f2a8f70983.jpg[/IMG]

---

### Post by lidex on 2010-04-04
Try this command;
```
sudo apt-get install phonon-backend-xine
```

In a terminal: "Applications>Accessories>Terminal"
Restart Amarok.

---

### Post by Milind on 2010-04-04
> **lidex said:**
> Try this command;
```
sudo apt-get install phonon-backend-xine
```

In a terminal: "Applications>Accessories>Terminal"
Restart Amarok.

When I tried that this is what I got in Terminal :

[COLOR="Red"]milind@milind-desktop:~$ sudo apt-get install phonon-backend-xine
[sudo] password for milind: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phonon-backend-xine is already the newest version.
phonon-backend-xine set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/COLOR]

---

### Post by NightwishFan on 2010-04-04
Check phonon settings in the KDE Control Center. It is called Sound or Multimedia. (Havent played with KDE much lately). It should be installed if you have amarok. Well it might be :/

Make sure it is using Xine to do so. You might also need xine plugins.
```
sudo aptitude install libxine1-ffmpeg
```

---

### Post by Milind on 2010-04-04
> **NightwishFan said:**
> Check phonon settings in the KDE Control Center. It is called Sound or Multimedia. (Havent played with KDE much lately). It should be installed if you have amarok. Well it might be :/

Make sure it is using Xine to do so. You might also need xine plugins.
```
sudo aptitude install libxine1-ffmpeg
```

Thanks a lot, NightwishFan. Installing that did the trick. Now Amarok 'sees' and plays my mp3s. :p

---

### Post by NightwishFan on 2010-04-04
AmaRock on. :guitar:

---

### Post by bgreenaway on 2010-04-13
Fixed it for me as well. Thanks.

---

### Post by coorior on 2010-05-04
Did the trick for me too.
 Thanks a LOT !!!

---

### Post by brallan on 2010-05-11
At some point, amarok used to advise you to install mp3 support the first time you tried to play an mp3 file. since it stopped doing that, i have always just installed the meta-package kubuntu-restricted-extras, which I assume also installed the above package.

---

### Post by Morrighan on 2010-05-19
Helped me three! :D=D>
Thank you!\\:D/

---

### Post by the_webninja on 2010-05-19
THANKS a Bunch it FIXED MINE TOO!! :)

---

### Post by Azyx on 2010-05-21
Thanx help me to with ```
sudo apt-get install libxine1-ffmpeg
```  :)

Old Amarok search for codecs automatikally, just like Rhytmbox and Totem do now...strange that this disappear in this newer version of Amarok..

/Cheers

---

### Post by pmooney78 on 2010-05-26
Solved it for me too, after upgrading 8.10 -> 9.04 -> 9.10. 

Incidentally, I hate the new version of Amarok, but haven't found anything that I like better. :(

---

### Post by DaH-RaT on 2010-06-25
worked for me as well woot. i missed my amarok :(

---

### Post by scherubin2 on 2010-07-08
> **NightwishFan said:**
> Check phonon settings in the KDE Control Center. It is called Sound or Multimedia. (Havent played with KDE much lately). It should be installed if you have amarok. Well it might be :/

Make sure it is using Xine to do so. You might also need xine plugins.
```
sudo aptitude install libxine1-ffmpeg
```


Thank NightwishFan, it also worked for my Fujitsu Siemens S series laptop

---

### Post by NightwishFan on 2010-07-08
Sure. Keep on rocking. :)

---

### Post by gitarist on 2010-10-09
it didn't work for me.
when i try to install libxinel-ffmpeg in the terminal it says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxinel-ffmpeg

how come he can't find it?

---

### Post by NightwishFan on 2010-10-09
Wrong name, its "libxine1-ffmpeg". With the number 1.

---

### Post by coldbluesteel on 2010-11-06
YAY!! Amarock is BACK!!!

Thanks!

---

### Post by elnetotaca on 2011-03-24
AWESOME!
worked for me 2.
Thanks!

---

### Post by RememberWhenItRained on 2011-04-12
> **coorior said:**
> Did the trick for me too.
 Thanks a LOT !!!
ditto

---

### Post by NightwishFan on 2011-04-12
):p

---

### Post by javiert on 2011-05-14
> **bobin said:**
> Is the indicator moving quickly from start to end?

Hi

I have this problem that you said. How i can solve it? Because I ran 

sudo aptitude install libxine1-ffmpeg

and I still can not listen the music.

thank you

---

