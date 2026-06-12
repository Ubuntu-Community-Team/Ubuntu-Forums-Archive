---
title: "Flash Movies Not working please help!"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Steelsteve on 2009-09-06
Ok so my last problem was i could not get my firefox browser to work for youtube and other similar sites. However I tried to go onto HULU for some higher quality videos of my favourite shows. And I get nothing. Not even a black screen. I went onto some other high quality video sites and I do get the window where the movie is supposed to be in, but no picture.

I recenly installed ubuntu-restricted-extras using Synaptic, but now i want to get the higher quality flash. Can anyone help me please?

---

### Post by coldReactive on 2009-09-06
Is it a big white box for the sites that give no picture and when you right-click the box, it does nothing? If so, restart firefox every time it happens. (Known issue with flashplugin-nonfree on linux.)

---

### Post by MelDJ on 2009-09-06
maybe try this link? [http://www.ubuntugeek.com/fix-for-fi...-in-hardy.html]("http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html")

---

### Post by Steelsteve on 2009-09-06
> s it a big white box for the sites that give no picture and when you right-click the box, it does nothing? If so, restart firefox every time it happens. (Known issue with flashplugin-nonfree on linux.)

No, it is black and when i right click it says auto-playing and if i have it stop playing (except on Hulu which i can't find the box) a transparent play button appears

---

### Post by coldReactive on 2009-09-06
> **Steelsteve said:**
> No, it is black and when i right click it says auto-playing and if i have it stop playing (except on Hulu which i can't find the box) a transparent play button appears

Then you don't have flash installed, you have gnash or swfdec.

```
sudo apt-get purge gnash-common gnash swfdec-gnome swfdec-mozilla
```

then run

```
sudo apt-get install flashplugin-nonfree
```

restart firefox and see if flash is in **about : plugins** (no spaces)

---

### Post by Steelsteve on 2009-09-06
uhm... what if you can't enter a password into the terminal. nothing appears (unless ha's supposed to happen) when i asks for the sudo password. This also happened when i tried to type in my login password (with a blnd eye) as the sudo password

But if Youtube does work wouldn't that mean that flash is installed?

---

### Post by coldReactive on 2009-09-06
> **Steelsteve said:**
> uhm... what if you can't enter a password into the terminal. nothing appears (unless ha's supposed to happen) when i asks for the sudo password. This also happened when i tried to type in my login password (with a blnd eye) as the sudo password

But if Youtube does work wouldn't that mean that flash is installed?

No, it doesn't mean that the real flash player is installed. The password thing is normal, typing your password doesn't give any asterisks nor does it show your password, it's normal, and a good thing. But if you prefer asterisks or dots instead of nothing, replace sudo with gksudo.

---

### Post by Steelsteve on 2009-09-06
> **coldReactive said:**
> No, it doesn't mean that the real flash player is installed. The password thing is normal, typing your password doesn't give any asterisks nor does it show your password, it's normal, and a good thing. But if you prefer asterisks or dots instead of nothing, replace sudo with gksudo.
ok, that did absolutly nothing. it didn't change anything. Perhaps someone should go to hulu and try a video themselves. Just to check to see if it's not a personal plugin problem and is more... global

---

### Post by 3rdalbum on 2009-09-06
If you're using 64-bit Ubuntu, you should try installing the 64-bit Flash Player from the Adobe website. Remove the "flashplugin-nonfree" and "nspluginwrapper" packages first.

The "flashplugin-nonfree" package, on 64-bit, installs the 32-bit Flash player and a wrapper to make it work with your 64-bit Firefox; this doesn't work very well.

---

### Post by Steelsteve on 2009-09-06
3rdalbum, first off i don't know how to install that package. I've tried to find something but so far not a thing. 

Also, more info on my supposed problem: flash games load all at once instead of like they should. all the menus appear at the same time and all the noise can't be shut off...

---

### Post by Steelsteve on 2009-09-08
bump for attention

---

### Post by theozzlives on 2009-09-08
Hulu works fine on mine and all I have installed is ubuntu-restricted-extras and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). Running 64 bit, but works the same on 32.

---

### Post by Steelsteve on 2009-09-08
nevermind, i wasn't using sudo and using gksudo

---

### Post by coldReactive on 2009-09-08
> **Steelsteve said:**
> How do you install Medibuntu? i tried to put the following into the terminal and it went "WFT? what's that?"

```
gksudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list 
```

the problem is the option 'output'. if you have another way to install it, then please help

Follow the manual method described in this thread then: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by theozzlives on 2009-09-08
are you using the right repository for your version? BTW: what version are you using?

---

### Post by Steelsteve on 2009-09-08
> **theozzlives said:**
> are you using the right repository for your version? BTW: what version are you using?
i use jaunty (it's right under my name man, didn't you see?)

---

### Post by Steelsteve on 2009-09-08
ok, medibuntu didn't work... hulu is still horrible (in fact, it makes it look like the screen is having a seizure) and games still don't load correctly

and just in case, i am running a Toshiba Sattlite A215 with a 64 bit Jaunty OS

---

### Post by TetonsGulf on 2009-09-08
Just out of curiosity, are you trying to connect from a school or from behind a firewall?

If you are try opening port (tcp/1935) in your firewall. If not, well, we'll keep looking.

---

### Post by Steelsteve on 2009-09-08
well, currently it's behind a firewall (i have tried at my college but wi fi doesn't connect for firefox under 75%, but that's a separate issue). 

Also, i have no clue how to navigate to find the ports. Wndows was easier but ubuntu is confusing right now (still 2 weeks in so i am REALLY new, i'll learn as i go though)

---

### Post by Steelsteve on 2009-09-18
bump for attention... this is still not fixed...

---

### Post by Steelsteve on 2009-09-18
see last post...

---

### Post by coldReactive on 2009-09-18
> **Steelsteve said:**
> Also, i have no clue how to navigate to find the ports. Wndows was easier but ubuntu is confusing right now (still 2 weeks in so i am REALLY new, i'll learn as i go though)

Windows is easier because it's mainstream, and all the companies support it. How did that happen? Microsoft basically "bribed" the world. But don't continue this discussion here. Make a new thread for that sort of thing.

---

### Post by Steelsteve on 2009-09-18
> **coldReactive said:**
> Windows is easier because it's mainstream, and all the companies support it. How did that happen? Microsoft basically "bribed" the world. But don't continue this discussion here. Make a new thread for that sort of thing.
PLeae don't get off topic. Anyways I can't seem to install the 64-bit linux version for flash. CAN YOU HELP ME?

---

