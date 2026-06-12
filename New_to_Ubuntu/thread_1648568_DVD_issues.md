---
title: "DVD issues"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Ukai on 2010-12-19
I have a DVD that I want to watch on my lubuntu laptop, that I'm pretty sure is 10.04.  I know the drive is DVD, but I can't figure out how to just play them.  Any help is appreciated.

---

### Post by amjjawad on 2010-12-19
> **Ukai said:**
> I have a DVD that I want to watch on my lubuntu laptop, that I'm pretty sure is 10.04.  I know the drive is DVD, but I can't figure out how to just play them.  Any help is appreciated.

I'm not on Lubuntu right now but if the default player couldn't run the DVD, try to install VLC.

Do you have another machine to check the DVD? just to make sure it's fine.

---

### Post by rockerphil on 2010-12-19
in order to play DVDs on Ubuntu you need the software that decodes the DVD called libdvdread4. you can install this by running this in a terminal

```
sudo apt-get install libdvdread4
```

then simply run this in a terminal to configure it

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

after rebooting you should be able to play the majority of proprietary DVDs with any of the major media players, i personally prefer VLC. hope this helps,

Phil

---

### Post by Ukai on 2010-12-19
> **amjjawad said:**
> I'm not on Lubuntu right now but if the default player couldn't run the DVD, try to install VLC.

Do you have another machine to check the DVD? just to make sure it's fine.

Yes, the DVD works.  What does VLC stand for?  Can I find it in Synaptic?


> **rockerphil said:**
> in order to play DVDs on Ubuntu you need the software that decodes the DVD called libdvdread4. you can install this by running this in a terminal

```
sudo apt-get install libdvdread4
```

then simply run this in a terminal to configure it

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

after rebooting you should be able to play the majority of proprietary DVDs with any of the major media players, i personally prefer VLC. hope this helps,

Phil

It said it couldn't find "libdvdread4"

---

### Post by amjjawad on 2010-12-19
> **Ukai said:**
> What does VLC stand for?  

Google it :)

> Can I find it in Synaptic?
Yes.

---

### Post by cavalier911 on 2010-12-19
Before you can play an encrypted retail dvd open a terminal.
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

menu/sound and video/gnome mplayer
File/Disc/Open DVD

---

### Post by Quackers on 2010-12-19
It may be beneficial to install ubuntu-restricted-extras as well. Available via synaptic.

---

### Post by cascade9 on 2010-12-19
> **Ukai said:**
> Yes, the DVD works.  What does VLC stand for?  Can I find it in Synaptic?

It said it couldn't find "libdvdread4"

VLC originally stood for "VideoLan Client". Its in synaptic. 

No "libdvdread4"? *blinks* Sure you're on 10.04? The older versions have different versions- 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by HermanAB on 2010-12-19
Howdy,

Note that all the restricted Codecs for Ubuntu are in Medibuntu (a fork of Mandriva's Penguin Liberation Front at [http://plf.zarb.org):](http://plf.zarb.org):)
[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by Ukai on 2010-12-19
> **cavalier911 said:**
> Before you can play an encrypted retail dvd open a terminal.
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

menu/sound and video/gnome mplayer
File/Disc/Open DVD

This worked, thanks for your help, everyone.

---

### Post by Steve Kusch on 2010-12-19
I still can't play DVD's I pasted the code in the terminal, but then I am promted for a password I cant type anything.

---

### Post by CharlesA on 2010-12-19
> **Steve Kusch said:**
> I still can't play DVD's I pasted the code in the terminal, but then I am promted for a password I cant type anything.
Passwords aren't echoed to the screen when you type them into a terminal.

Just type in your password and hit enter.

---

### Post by Steve Kusch on 2010-12-19
I put in the code in the terminal. I hit enter. then I am asked for a sudo password. then my keyboard wont work and I cant type anything.
:popcorn:

---

### Post by CharlesA on 2010-12-19
> **Steve Kusch said:**
> I put in the code in the terminal. I hit enter. then I am asked for a sudo password. then my keyboard wont work and I cant type anything.
:popcorn:
Type your password and hit enter. Passwords aren't shown on the screen.

---

### Post by Joeb454 on 2010-12-19
It's important to note what CharlesA says here - the sudo password is the same password as **your** user account :)

---

### Post by Steve Kusch on 2010-12-19
I can't play my DVD's I pasted the text several types, then I hit enter and I am asked for my password and I can't type anything at all. I don't understand why it is such a difficult thing to decode or just have permission to play a DVD.

---

### Post by Joeb454 on 2010-12-19
Have you tried typing your password and pressing enter?

For example, if I wanted to install [geany]("apt://geany"), this would happen: ```
joe@kashyyyk:~$ sudo apt-get install geany
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  geany
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,857kB of archives.
After this operation, 7,496kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick/universe geany amd64 0.19.1-1 [2,857kB]
Fetched 2,857kB in 4s (674kB/s)  
Selecting previously deselected package geany.
(Reading database ... 166300 files and directories currently installed.)
Unpacking geany (from .../geany_0.19.1-1_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up geany (0.19.1-1) ...
joe@kashyyyk:~$
```

Note how the password doesn't show, despite the fact I have typed it and pressed enter, yet the command still runs with root privileges. This is how ***any*** password input works on the command line.

---

### Post by lbarnes on 2010-12-19
The terminal will NOT show your entered password and will look like your keyboard is not working.  When prompted for a password just type it and hit enter whether it looks like your keyboard is working or not.

---

### Post by rockerphil on 2010-12-19
as said before, after pasting the command in to the terminal you hit enter and you're gonna see something like this:

```
[sudo] password for phil:
```

now, you say you can't type anything, but i don't think you understand what everyone is saying here. you simply type the same password you use to log in to Ubuntu. the cursor isn't going to move and nothing will appear as you type, not even asterisks (the little stars) but it's still accepting it. after typing your password simply press enter and that should do it. hope this helps,

Phil

---

### Post by Eddison on 2011-01-01
Want to say a BIG thank you to [rockerphil]("http://ubuntuforums.org/member.php?u=454258")  for libdvdread4. I bought a Samsung laptop for my wife (Christmas), and deleted w7 yes !! deleted it ! Then installed 10.10 and raved about how good Ubuntu is to her. Its her first computer, so I thought it would be good to have her get used to ubuntu even though its a learning curve.
But ! the DVD player would not work !! I had to keep telling her I'll get it fixed on the forums !! but I have been asking and asking and no one seemed to know. Problem was, I had installed libdvdread2 and not read4.
Its late :shock: and now I can show the wife Avatar playing in all the nice colors tomorrow!

So thanks again for this dude. BTW, reading the above posts.. some of you men have massive patience :lolflag:

I love ubuntu again !!


eddison

---

