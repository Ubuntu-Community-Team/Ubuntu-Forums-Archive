---
title: "Oh boy... now I have done it! LOL Help me personalize?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by WyvernAldyth on 2011-08-23
OK... need some help here. Please speak slowly and use small words!

Last time I dealt with Linux was Red Hat!

Just bought notebooks and had choice of ubuntu or windows. As I hate windows... decided to get back into being somewhat tech savvy.

SPECS: Ubuntu 10.4.3 with Gnome 2.30.2

Trying to make my teen daughter's notebook "the bestest B-day present EVER".

Finally gave up trying to change the gdm like I really wanted to to this: [http://gnome-look.org/content/show.php/Gir+%28Invader+Zim%29?content=67489](http://gnome-look.org/content/show.php/Gir+%28Invader+Zim%29?content=67489)
Read about 20 threads on how to do it and could not get anywhere.

Changed the background and installed one! I am not COMPLETELY useless. LOL

I want to know if there is a way to change alert sounds and such. Where do I save the sounds I have downloaded? Where do I go to change them? Can I change different ones (pick a new one for closing a window, start-up, log off, error, etc)?

Please pretend you are speaking to your 80 year old grandma if you can post directions on how to do this. Step by step. Assume I know nothing... including how to get to a terminal screen.

Anyone out there with a ton of patience?

---

### Post by androssofer on 2011-08-23
> **WyvernAldyth said:**
> OK... need some help here. Please speak slowly and use small words!

Last time I dealt with Linux was Red Hat!

Just bought notebooks and had choice of ubuntu or windows. As I hate windows... decided to get back into being somewhat tech savvy.

SPECS: Ubuntu 10.4.3 with Gnome 2.30.2

Trying to make my teen daughter's notebook "the bestest B-day present EVER".

Finally gave up trying to change the gdm like I really wanted to to this: [http://gnome-look.org/content/show.php/Gir+%28Invader+Zim%29?content=67489](http://gnome-look.org/content/show.php/Gir+%28Invader+Zim%29?content=67489)
Read about 20 threads on how to do it and could not get anywhere.

Changed the background and installed one! I am not COMPLETELY useless. LOL

I want to know if there is a way to change alert sounds and such. Where do I save the sounds I have downloaded? Where do I go to change them? Can I change different ones (pick a new one for closing a window, start-up, log off, error, etc)?

Please pretend you are speaking to your 80 year old grandma if you can post directions on how to do this. Step by step. Assume I know nothing... including how to get to a terminal screen.

Anyone out there with a ton of patience?

okey dokey...

for ur login screen changes etc id get urself "ubuntu tweak" to do so run these commands in terminal one at a time... 

applications >> accessories >> terminal

```

 sudo add-apt-repository ppa:tualatrix/ppa
```

    ```
sudo apt-get update
```

    ```
sudo apt-get install ubuntu-tweak
```

then it will b in:

applications >> system tools >> ubuntu tweak

it has a nice GUI for tweaking things about your system and makin it cool..

to get sounds, u wanna head here :

[http://gnome-look.org/index.php?xcontentmode=25](http://gnome-look.org/index.php?xcontentmode=25)

and download a theme from there. it shud save to:

/home/username/Downloads/

(replacing username with your username) then extract it, open ur file browser, go into the mentioned folder and right click on the downloaded file. shud b .zip or .tar.gz then click "open with archive manager" then extract it.. tht will create a new folder in your Downloads folder with your sound theme in it :-). lets call it "soundThemeFolder"

 then open terminal again and do:

```
cd Downloads
```

so now your in your downloads folder. then u wanna do:

```
sudo mv soundThemeFolder /usr/share/sounds
```

and this will move your soundThemeFolder to /usr/share/sounds.

then open sound prferences:

system >> prefernces >> sounds

then u can select it as a theme :-).

hope thts easy enough to get through.. any issues ask and i'll break em down..

---

### Post by 3rdalbum on 2011-08-23
The reason you couldn't get the login screen to change is because the file you linked to is too old.

That file is from 2007, to work on the login screen that was around in 2007. Ubuntu 10.04 is from 2010 (already getting a bit old and crusty, now) and has a rewritten login screen that is not so fully themable.

Sorry! Linux changes so quickly, your Red Hat experience is probably totally useless if its more than a few years ago.

No idea about the alert sounds these days. I just leave it at defaults.

Just so you know, Ubuntu 11.04 is the current version. If you decide to follow some tutorials or HOWTOs online, make sure they are relevant to 10.04. Linux changes so quickly that most instructions for 11.04 won't work on 10.04, and vice-versa.

---

### Post by WyvernAldyth on 2011-08-23
My Red Hat experience was in 2002! LOL And I actually did a small bit of actual binary in 1981 (so I could break into my dad's work computer bank on an actual "terminal" and play Zork!) I did web design with old school html in 1999. So... I am not actually TOTALLY useless and learn quick at least. I am just a bit behind the times. Wonderful world of computing... blink and you are outdated! LOL

I guess I now need to find out how to actually CREATE a theme or sound theme... as I do not see one that is based on G.I.R. from Invader Zim... which is what would make my daughter's day.:(

I love "tweaking" and creating themes and crap. Just need to get my bearings and I will be set to go!

BTW - Androssofer - had no problem installing the tweak program. GREAT directions! thanks!

---

### Post by WyvernAldyth on 2011-08-23
> **androssofer said:**
> 

[http://gnome-look.org/index.php?xcontentmode=25](http://gnome-look.org/index.php?xcontentmode=25)

and download a theme from there. it shud save to:

/home/username/Downloads/

(replacing username with your username) then extract it, open ur file browser, go into the mentioned folder and right click on the downloaded file. shud b .zip or .tar.gz then click "open with archive manager" then extract it.. tht will create a new folder in your Downloads folder with your sound theme in it :-). lets call it "soundThemeFolder"

 then open terminal again and do:

```
cd Downloads
```so now your in your downloads folder. then u wanna do:

```
sudo mv soundThemeFolder /usr/share/sounds
```and this will move your soundThemeFolder to /usr/share/sounds.

then open sound prferences:

system >> prefernces >> sounds

then u can select it as a theme :-).

hope thts easy enough to get through.. any issues ask and i'll break em down..

Hmm...

Found a "Portal" one that would be good for now (we love Portal - she has "Still Alive" as ringtone on her phone). I did get it moved... but it does not show up under sound preferences in order to let me choose and switch to it.

Ideas?

---

### Post by androssofer on 2011-08-23
> **WyvernAldyth said:**
> Hmm...

Found a "Portal" one that would be good for now (we love Portal - she has "Still Alive" as ringtone on her phone). I did get it moved... but it does not show up under sound preferences in order to let me choose and switch to it.

Ideas?

u got a link to it?

i'll download and try it on mine...

portal is epic! haha

---

### Post by WyvernAldyth on 2011-08-23
> **androssofer said:**
> u got a link to it?

i'll download and try it on mine...

portal is epic! haha


Sure do!
 [http://gnome-look.org/content/show.php/Portal+GLaDOS+fan-made+sounds?content=140969&PHPSESSID=e3a44a7b4eba2cc820993043dff8a15e](http://gnome-look.org/content/show.php/Portal+GLaDOS+fan-made+sounds?content=140969&PHPSESSID=e3a44a7b4eba2cc820993043dff8a15e)

Still working on learning enough to actually create a sound theme of my own. Have a crapload of .wav files. Just need to know how to convert (if needed) and assign them to actions and save them. No problem... right? Should be a piece of cake (the cake is a lie!)

Anyone have a clue if there is a tutorial anywhere on this sort of thing? I refuse to let the "true" geeks have all the fun!

---

### Post by M1ttenz11 on 2011-08-23
> **WyvernAldyth said:**
> 
Anyone have a clue if there is a tutorial anywhere on this sort of thing? I refuse to let the "true" geeks have all the fun!

I haven't done a thing like this in my life, but, I google'd it for you because im so nice and I think this link
[http://www.srijanchoudhary.com/linux/creating-ubuntu-sound-themes-for-9-10-and-10-04.html](http://www.srijanchoudhary.com/linux/creating-ubuntu-sound-themes-for-9-10-and-10-04.html)
gives quite a basic and straightforward step by step guide on how to create your own sound theme. But I did not read all of it. I hope this helps :)

This is going to be one hell of a Birthday Present eh?

---

### Post by Megaptera on 2011-08-24
I do hope you don't end up with this!!!
[http://hannahmontana.sourceforge.net/Site/Home.html](http://hannahmontana.sourceforge.net/Site/Home.html)

---

### Post by androssofer on 2011-08-24
wots wrong with hannah montana!?i mean.. ahem... yeah, down with that sorta thing! haha.

on an similar note: you can download:

"gnome color chooser" in the software center. like ubuntu tweak it lets u customise stuff. i use to tweak the colour and width of the scroll bars... but u can tweak almost anything relating to colour on it!

ps: too busy atm to download and try the sound theme :-(, work then eminem concert! tough life i know.... will b thurs b4 i get a chance.. so ur on ur own til then!

pps: if u get ur sound theme done, post the link! b gd to hear...

---

### Post by WyvernAldyth on 2011-08-24
Hanna montana won't fly. My kid is into "Blood on the Dancefloor" and "Blackveil Brides". LOL

OK... gonna go check out that link for sound theme design and see what trouble I can get into! 

I think Ubuntu is doing themselves a wee bit of a disservice. They are trying too hard to be as simple as possible. It is fine to make it simple for someone like my mother, so she can use it "out of the box" with no problems. But if they want to be thought of as something other than "geekware" they need to promote how truly customizable and cool it can really be for those of us that love the bells and whistles it really can provide!

---

### Post by M1ttenz11 on 2011-08-29
I can sort of agree yes.
And also the curiosity kicks in and I start to wonder how far you've got on with this.
Must be making some progress now :P

Good luck.

---

