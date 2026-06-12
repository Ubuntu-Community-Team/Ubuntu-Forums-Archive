---
title: "For the sake of learning (Terminal)"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by psam3 on 2010-01-18
I have used the CD command to move to my music folder. Now the question is, how do I start an MP3 in this folder using only the terminal? 

Thanks

---

### Post by baddog144 on 2010-01-18
You could get mplayer with
```

sudo apt-get install mplayer

```

and then:
```

mplayer filename.mp3

```

---

### Post by ankspo71 on 2010-01-18
Hi,
Are you wanting to play music without a GUI (inside the terminal)?

If so, try this
canberra-gtk-play -f <path-to-file>

I believe this is the command line audio player that plays the Ubuntu theme sounds.
hope this helps.

---

### Post by John Bean on 2010-01-18
> **psam3 said:**
> I have used the CD command to move to my music folder


No you didn't. Commands are case-sensitive and I'll bet you actually used one called "cd".

Well, you did say "for the sake of learning" :-)

---

### Post by psam3 on 2010-01-18
> **baddog144 said:**
> You could get mplayer with
```

sudo apt-get install mplayer

```

and then:
```

mplayer filename.mp3

```

Thanks, I had to give my files simpler names but it worked after that. 

> **John Bean said:**
> No you didn't. Commands are case-sensitive and I'll bet you actually used one called "cd".

Well, you did say "for the sake of learning" :-)

haha, yeah you are right, I did use the "cd" command

---

### Post by psam3 on 2010-01-18
> **ankspo71 said:**
> Hi,
Are you wanting to play music without a GUI (inside the terminal)?

If so, try this
canberra-gtk-play -f <path-to-file>

I believe this is the command line audio player that plays the Ubuntu theme sounds.
hope this helps.

I tried this too but it simply refuses to find my files:confused:

---

### Post by baddog144 on 2010-01-18
ou can always type just part of the filename and then press TAB to complete the filename. E.g if you have reallylong_complexFIlename.mp3, you could type reallylo<tab> and it would complete it for you :)

---

### Post by wmcbrine on 2010-01-18
> **psam3 said:**
> Thanks, I had to give my files simpler names but it worked after that.Not necessary. If spaces are the issue:

mplayer "a filename with spaces.mp3"

If it's something else, there's another way around it. Any file can be specified on the command line.

---

### Post by psam3 on 2010-01-18
> **baddog144 said:**
> ou can always type just part of the filename and then press TAB to complete the filename. E.g if you have reallylong_complexFIlename.mp3, you could type reallylo<tab> and it would complete it for you :)

Thanks that is helpful. If I could ask one more question, is their a way to simply tell it to play all files in a folder with a certain extension, like mp3?

---

### Post by baddog144 on 2010-01-18
Sure, just do
```

mplayer *.mp3

```
the '*' means "anything", so *.mp3 is "any file that ends in .mp3"

---

### Post by psam3 on 2010-01-18
> **baddog144 said:**
> Sure, just do
```

mplayer *.mp3

```
the '*' means "anything", so *.mp3 is "any file that ends in .mp3"

Awesome thanks :D

---

### Post by baddog144 on 2010-01-18
No problem, good luck with your command-line education ;)

---

### Post by ankspo71 on 2010-01-18
Hi,
In addition to commands being case sensitive, filenames are the same way, and the use of capital letters is very common with ripped music from cds.

You can use the ls command (that's a lower case L) which lists the contents of your directory. You could then see the file as you type out the filename. 

I agree with what the above poster said about spaces in filenames too. It's tricky writing out a full path with capital letters and spaces, so you made it easier on yourself by 'cd' into the directory first.

Enjoy using the terminal :)

---

### Post by PenguinInside on 2010-01-19
In addition to specifying a specific media player, you can use the system media player (whatever that's set to) by using gnome-open:

```
$gnome-open mysong.mp3
```

Once you type a few letters of the name, and press tab, the spaces are entered automatically for you as \  (backspace space).

By the way, gnome-open also works for any type of file that is registered with the system. (Media, audio, video, spreadsheet, PDF, etc.)

---

### Post by psam3 on 2010-01-19
> **PenguinInside said:**
> In addition to specifying a specific media player, you can use the system media player (whatever that's set to) by using gnome-open:

```
$gnome-open mysong.mp3
```

Once you type a few letters of the name, and press tab, the spaces are entered automatically for you as \  (backspace space).

By the way, gnome-open also works for any type of file that is registered with the system. (Media, audio, video, spreadsheet, PDF, etc.)

Thanks, I was actually sitting here after awhile trying to figure out how to open my pictures, since I had no idea the name of the program that you use to actually view them. gnome-open works perfectly. I was actually trying to open a PDF too.

---

### Post by wmcbrine on 2010-01-19
> **psam3 said:**
> Thanks, I was actually sitting here after awhile trying to figure out how to open my pictures, since I had no idea the name of the program that you use to actually view them.eog

> *I was actually trying to open a PDF too.*evince

Just for future reference. :) There are alternatives to those, too, but those are the defaults in Ubuntu.

---

### Post by nothingspecial on 2010-01-19
If you are getting serious about this why not try a full featured music player such as cmus or ncmpc.

For photos there is feh

Videos, I use mplayer-nogui

File manager - mc

videocoversion - ffmpeg

the list goes on.

A few tips. 

Learning all the keybindings/options of command line apps can be a pain. I use screen with byobu and dvtm to get round this

```
sudo apt-get install byobu dvtm
```

Screen is like a desktop environment for the console, start it by typing ```
byobu
```

Now you can have different "workspaces" in one terminal. F2 will create one. F3 and F4 will toggle forwards and backwards through them.

So you can have cmus, mc, elinks (web browser) on different workspaces.

dvtm is a tiling window manager for the terminal. Launch it with dvtm, inside your screen session.

Press Ctrl G then C and the terminal will split in 2. It has mouse support so you can toggle between them by clicking or use Ctrl G then K (forwards) or J (backwards). You can split it as many times as you like.

If you open 4 Then Ctrl G then G again will make it a nice grid shape. And this is where the usefulness is. You split the screen in 4. Launch cmus to play your music in one window and man cmus on another window and whatever you like in the other 2.

I`ll show you

[ATTACH]144149[/ATTACH]

I`m doing this on my netbook which isn`t ideal, but it`s just for illustration. On a decent sized monitor this is really useful.

---

### Post by psam3 on 2010-01-19
> **nothingspecial said:**
> If you are getting serious about this why not try a full featured music player such as cmus or ncmpc.

For photos there is feh

Videos, I use mplayer-nogui

File manager - mc

videocoversion - ffmpeg

the list goes on.

A few tips. 

Learning all the keybindings/options of command line apps can be a pain. I use screen with byobu and dvtm to get round this

```
sudo apt-get install byobu dvtm
```

Screen is like a desktop environment for the console, start it by typing ```
byobu
```

Now you can have different "workspaces" in one terminal. F2 will create one. F3 and F4 will toggle forwards and backwards through them.

So you can have cmus, mc, elinks (web browser) on different workspaces.

dvtm is a tiling window manager for the terminal. Launch it with dvtm, inside your screen session.

Press Ctrl G then C and the terminal will split in 2. It has mouse support so you can toggle between them by clicking or use Ctrl G then K (forwards) or J (backwards). You can split it as many times as you like.

If you open 4 Then Ctrl G then G again will make it a nice grid shape. And this is where the usefulness is. You split the screen in 4. Launch cmus to play your music in one window and man cmus on another window and whatever you like in the other 2.

I`ll show you

[ATTACH]144149[/ATTACH]

I`m doing this on my netbook which isn`t ideal, but it`s just for illustration. On a decent sized monitor this is really useful.

This is really useful, I have been playing around with it. I have a question though, can I use this in a real terminal? I know you can use a keyboard combination to get into the command line. I did this last night, which leads me to one more question :D How do I start gnome from the command line?

---

### Post by nothingspecial on 2010-01-19
Firstly, yes you can do all this from the real command line - ie without X.

The only thing I regulary use within X is firefox because no matter how much I love cli apps, you cannot get the same browsing experience with cli browsers although I do use them.

To start X from the command line 
```

sudo service gdm start
```

or ```
startx
```

I use Ubuntu minimal with xorg and firefox, but then I don`t do much fancy stuff. If you are interested, it is a really fast way to run your computer.

---

### Post by nick_goodfate on 2010-01-19
nothingspecial what program is running in the first "window" of your terminal ?

---

### Post by nothingspecial on 2010-01-19
> **nick_goodfate said:**
> nothingspecial what program is running in the first "window" of your terminal ?

If you mean top - left 

It is cmus

---

### Post by nick_goodfate on 2010-01-19
yes this is what i mean , #1 ! thnx !

---

### Post by psam3 on 2010-01-19
Thanks, I was gonna post this from Elinks but I haven't quite figured that out yet :D

---

### Post by nothingspecial on 2010-01-19
> **nick_goodfate said:**
> yes this is what i mean , #1 ! thnx !

Use it with dvtm.

Look at the man pages while you use it.

---

### Post by nick_goodfate on 2010-01-19
last question:-# with the comand :add /media/...../music i imported my music from my external hardisk . did it copied the files somewhere else or it just "looking" at the directory i gave it ?

---

### Post by l-x-l on 2010-01-19
> **baddog144 said:**
> You could get mplayer with
```

sudo apt-get install mplayer

```

and then:
```

mplayer filename.mp3

```


Thx for nugget. ;)

---

### Post by baddog144 on 2010-01-19
> **l-x-l said:**
> Thx for nugget. ;)
No problem, glad someone else found it useful too :D

---

### Post by PenguinInside on 2010-01-20
> **psam3 said:**
> Thanks, I was actually sitting here after awhile trying to figure out how to open my pictures, since I had no idea the name of the program that you use to actually view them. gnome-open works perfectly. I was actually trying to open a PDF too.

No problem.

gnome-open is a great command to remember so you don't have to remember the exact command name of a given program.

---

### Post by nothingspecial on 2010-01-20
> **nick_goodfate said:**
> last question:-# with the comand :add /media/...../music i imported my music from my external hardisk . did it copied the files somewhere else or it just "looking" at the directory i gave it ?

It`s just looking at the files :D

---

