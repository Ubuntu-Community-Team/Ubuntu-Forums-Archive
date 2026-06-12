---
title: "burning a music cd"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by rlj399 on 2009-07-05
Everytime i burn a cd with mp3 files it never plays in the cd player of cars, i've used k3b and brasero so i'm guessing there's some kind of mode i have to put it in, but i have no idea. help anyone?

---

### Post by MrWES on 2009-07-05
> **rlj399 said:**
> Everytime i burn a cd with mp3 files it never plays in the cd player of cars, i've used k3b and brasero so i'm guessing there's some kind of mode i have to put it in, but i have no idea. help anyone?

With K3B, are you burning a data cd, or an audio cd? If you're burning a data cd, it'll contain the mp3 files and it sounds like your auto cd player doesn't play those. Make sure you choose audio cd project in K3B. Also, I'm assuming you have installed ubuntu-restricted-extras, which will contain the necessary codes to make audio conversions.

```
sudo apt-get install ubuntu-restricted-extras
```

~Bill

---

### Post by lisati on 2009-07-05
Another thing to look for is if you're burning the CD as a "multi session" CD. Some CD players prefer the disk to be "closed" or "finalised", and won't play them if they're recorded in a way that will let you add more files or tracks. (The same can be said of DVDs as well)

---

### Post by djpurity on 2011-04-28
> **MrWES said:**
> With K3B, are you burning a data cd, or an audio cd? If you're burning a data cd, it'll contain the mp3 files and it sounds like your auto cd player doesn't play those. Make sure you choose audio cd project in K3B. Also, I'm assuming you have installed ubuntu-restricted-extras, which will contain the necessary codes to make audio conversions.

```
sudo apt-get install ubuntu-restricted-extras
```

~Bill

=D> \\:D/ #-o

Thank you Bill for posting this nice instruction set on how to install the restricted extras. There seems to be SO many special SUDO command lines that need to be entered to enable different parts of Ubuntu before all the magic happens. And that is part of what irks me about it. How do I know what all these secret commands are without trolling around Ubuntu Help Forums looking for secret SUDO command lines to enter in the terminal, or other instructions on how to use packages and how to do this and that. Is there some manual for Ubuntu out there that has all of this listed, or is this just common sense stuff for hardcore Linux/Unix/Debian fanatics who over time have made it their life to just make this their business and common sense? Meanwhile people like me, who dabbled in Unix in college getting my comp sci BS degree and then evolved into dual-booting Red Hat Linux and Windows whatever at the time (98SE?) and then after a whole lot of tragedy hit me for years and I lost my flow with my computing skills, whatever they were once worth. So basically, I am doing a total refresher with all of this, and reminding myself about how it all fits together, and I am not recalling all these commands and needs and what needs to be done in what order first to make it all come together and work.

There has to be some Ubuntu for Dummies printed out by now, right? :oops:

](*,)

---

### Post by oldos2er on 2011-04-28
Old thread.

[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by djpurity on 2011-05-15
Okay is this bad that I ran the command line that you mentioned to get the ubuntu-extras, and then it said that it was already up to date but there were 6 files that were already installed and no longer needed. Did I want to clean them up? It listed a command to remove them. 6 files. 

sudo Apt-get autoremove

and then it went through a while and tested all kinds of responses and removed some things, and anyway, was that the right thing to do? Or should I have left them be? I am confused now.

I just want to make an audio CD that can be sent to someone across the country that can put in his CD player (yes they still sell those things) and play my CD I make with the songs he wants on it. But I can't get a program to make a universal audio music CD that can be played in any CD player, like the old style ones that you put the CD in, or in a car, or whatever.... that is what I need help on. Please advise.

:confused:

---

### Post by NoNameWill on 2011-05-15
You want to convert your mp3's to .wav files. 

To do so you will want to use a converter. There is a GUI app in Ubuntu Software Center called Sound Converter. There are many others too.

or ```
sudo apt-get install soundconverter
```


unless packages got broken during the autoremove you are probably ok.

---

### Post by alphacrucis2 on 2011-05-15
> **djpurity said:**
> Okay is this bad that I ran the command line that you mentioned to get the ubuntu-extras, and then it said that it was already up to date but there were 6 files that were already installed and no longer needed. Did I want to clean them up? It listed a command to remove them. 6 files. 

sudo Apt-get autoremove

and then it went through a while and tested all kinds of responses and removed some things, and anyway, was that the right thing to do? Or should I have left them be? I am confused now.

I just want to make an audio CD that can be sent to someone across the country that can put in his CD player (yes they still sell those things) and play my CD I make with the songs he wants on it. But I can't get a program to make a universal audio music CD that can be played in any CD player, like the old style ones that you put the CD in, or in a car, or whatever.... that is what I need help on. Please advise.

:confused:

You have to burn the CD as an audio disk. The stereo CD players usually don't understand data CD's, or mp3 files. Note that you can get a lot more mp3's on a data CD than you can get audio tracks on an audio CD. That is because mp3 files are highly compressed. K3B has an option to create audio CD. When you do that it knows that mp3 files have to be converted to full sized CD audio tracks.

---

### Post by alphacrucis2 on 2011-05-15
> **NoNameWill said:**
> You want to convert your mp3's to .wav files. 

To do so you will want to use a converter. There is a GUI app in Ubuntu Software Center called Sound Converter. There are many others too.

or ```
sudo apt-get install soundconverter
```


unless packages got broken during the autoremove you are probably ok.

You don't need to convert anything as K3B should handle the conversion itself.


Edit. Just to be clear. You need to install the package libk3b6-extracodecs for the automatic conversion to work in k3b.

---

