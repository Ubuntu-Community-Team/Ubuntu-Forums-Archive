---
title: "Can't run mplayer,or vlc in Linux mint 7"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Colonel Sanders on 2009-11-02
[SIZE=5][FONT=Comic Sans MS] Hi,I have a slight problem.I am using Linux Mint 7,it's a good OS(fully updated). But 1 big problem is that I cant run a DVD, by just putting it in the drive. It seems like all of the copy righted dvd's (commercial movies)  have skippy video. When mplayer comes up to play what ever media file selected,it just turns blue,and disapears.Also vlc can't play dvd's either,acts just like mplayer...Does anyone know how to fix this?
Thanks!
[/FONT][/SIZE]

---

### Post by samjh on 2009-11-02
I'm not sure if this will work, but open up your terminal and run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then try playing your DVDs again.

---

### Post by RedRat on 2009-11-02
You might want to post something about your system, cpu, memory, speed of cpu so that others here might help you. Your description of the problem is a bit skimpy. Give us some info about your install.

Linux Mint (which version) comes with all the necessary codecs, ready and raring to go. How are you doing with Flash player in Firefox and YouTube? I can visit the site via the LiveCD of Linux Mint 7 and get the flash player to work.

More info is always helpful.

---

### Post by Colonel Sanders on 2009-11-04
[SIZE=5][FONT=Comic Sans MS] Allright here is some more info. The specs are...

Hp-d530 sff
3.0ghz(hyper threading)
Linux Mint 7(full install-besides window's)
160gb hd
504mb of ram(works great though..)
I have no problems with anything in Firefox,video's,flash,etc. Mplayer doesn't work at all( just show's up,and dissapears.Gnome-player works fine,(except for dvd's). Vlc player can run flv,mpeg,wmv,avi,etc{minus encrypted dvd's(AVI_movies,not media from a digital camera-video slow's down then speeds up,randomly.)I tried the terminal command from the post above,nothing happend. Let me know if u need more info...
[/FONT][/SIZE]

---

### Post by RedRat on 2009-11-04
> **Colonel Sanders said:**
> [SIZE=5][FONT=Comic Sans MS] [SIZE=4]Allright here is some more info. The specs are...

Hp-d530 sff
3.0ghz(hyper threading)
Linux Mint 7(full install-besides window's)
160gb hd
504mb of ram(works great though..)
I have no problems with anything in Firefox,video's,flash,etc. Mplayer doesn't work at all( just show's up,and dissapears.Gnome-player works fine,(except for dvd's). Vlc player can run flv,mpeg,wmv,avi,etc{minus encrypted dvd's(AVI_movies,not media from a digital camera-video slow's down then speeds up,randomly.)I tried the terminal command from the post above,nothing happend. Let me know if u need more info...[/SIZE] 
[/FONT][/SIZE]

OK, I am an 8.04 Hardy user who is looking into installing Linux Mint 7 or 8 on another computer. I have tried the LiveCD and everything works fine from the CD, that is why I am enticed. Mint 7 is nothing more than 9.04 with bells and whistles, at least that is what I have been told by the Mint people. It sounds as if there is something wrong with the mplayer install if all your other stuff is working.

Perhaps others could chime in here, but you might want trying to re-install mplayer from the Mint repositories. The only problem I can see from your specs is that memory might be a tad low, I don't know mplayer's memory requirements but if your other stuff is working, it ought to work. 

If I recall correctly, there is a sticky note referencing a page on installing all the necessary codecs for multimedia. Check under the multimedia forums down below on the main forums page. 

If this fails, I would suggest that you sign up for the Mint forum: 
[HTML]http://www.linuxmint.com/[/HTML]
They have a forum under "Community" and pose the question there. Sorry I couldn't be more help.

---

### Post by Colonel Sanders on 2009-11-05
[SIZE=5][FONT=Comic Sans MS] I just tried uninstalling mplayer-then reinstall it...Still the same thing happens,just dissapers. Looks like it's off to the mint forum.[/FONT][/SIZE]

---

### Post by Colonel Sanders on 2009-11-06
[SIZE=5][FONT=Comic Sans MS] Well I fixed it. I have come to find out that Mplayer,And VLC both had to problems,together....1 was that neither was reading the dvd drive,wrong location.2 was that both vlc-mplayer,had the wrong video plugin's selected.I just got lucky-for now I guess. :popcorn:
Till next time..
[/FONT][/SIZE]

---

