---
title: "fluxbox wallpaper problem"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-18
hi the default fluxbox wallpaper is very bland so I want to use my own
I followed the instructions below to the letter but no go

[http://www.everyjoe.com/newlinuxuser/howto-set-background-wallpaper-in-fluxbox/](http://www.everyjoe.com/newlinuxuser/howto-set-background-wallpaper-in-fluxbox/)

any ideas?

---

### Post by bodhi.zazen on 2009-06-18
[http://community.fluxbuntu.org/index.php?topic=98.0](http://community.fluxbuntu.org/index.php?topic=98.0)

---

### Post by HandyAndy on 2009-06-23
If you prefer a more visual style of desktop configuration there are a couple of little GUI tools that I find work well with fluxbox:

gsetroot - a wallpaper viewer/changer
gtk-chtheme - a GTK+2x theme preview/switcher

Both are in the repos.

---

### Post by billgoldberg on 2009-06-23
I've written a Fluxbox guide before that you will want to read if you have problems with Fluxbox.

[http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)

---

### Post by Duke Togo on 2009-06-25
thanks
excellent guide

---

### Post by Duke Togo on 2009-06-25
btw
fbsetbg -f /path/to/image.png

gives me the wallpaper I want but not after I have shutdown and restarted the system
how can I make this "stick"?

---

### Post by Locutus_of_Borg on 2009-06-25
sudo apt-get install feh

feh --bg-scale image.jpg

---

### Post by Duke Togo on 2009-06-25
can you please clarify that I put the first instruction into the terminal to download the package then
feh --bg-scale \route\to\my\picture.jpg
and it said file doesn`t exist

The following NEW packages will be installed
  feh giblib1
0 upgraded, 2 newly installed, 0 to remove and 24 not upgraded.
Need to get 241kB of archives.
After this operation, 578kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) hardy/universe giblib1 1.2.4-5 [19.4kB]
Get: 2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) hardy/universe feh 1.3.4.dfsg.1-1 [222kB]
Fetched 241kB in 0s (357kB/s)
Selecting previously deselected package giblib1.
(Reading database ... 174396 files and directories currently installed.)
Unpacking giblib1 (from .../giblib1_1.2.4-5_i386.deb) ...
Selecting previously deselected package feh.
Unpacking feh (from .../feh_1.3.4.dfsg.1-1_i386.deb) ...
Setting up giblib1 (1.2.4-5) ...

Setting up feh (1.3.4.dfsg.1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
richard@richard-laptop:~$ feh --bg-scale \home\richard\Pictures\HAL.jpg
feh WARNING: homerichardPicturesHAL.jpg - File does not exist
feh ERROR: Couldn't load image in order to set bg
richard@richard-laptop:~$

---

### Post by Locutus_of_Borg on 2009-06-25
any particular reason you are using \ instead of / in the path?

---

### Post by Duke Togo on 2009-06-25
maybe because I`m and idiot:oops:

---

### Post by Duke Togo on 2009-06-25
so that worked but it still didn`t stick after a restart though

---

### Post by Locutus_of_Borg on 2009-06-25
you will have to put it into your startup script in order to execute it every time

just copy that command: feh --bg-scale image.jpg

and paste it into the bottom of this file: ~/.fluxbox/startup
save and exit the file

now it will be persistent.

---

### Post by Duke Togo on 2009-06-25
:confused:
ok I did that and when I restart I get no wallpaper but I do get a startup~ and startup~~ file
both with the code at the bottom??

---

### Post by Duke Togo on 2009-06-25
ok I deleted the startup~~ file and restarted
still no wallpaper though
contents of startup~

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/richard/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/richard/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/richard/.fluxbox/log"

feh --bg-scale /home/richard/Pictures/HAL.jpg

---

### Post by rockerphil on 2009-06-25
i'm an avid user of Fluxbox and have built my own minimal version of Ubuntu using fluxbox as the WM. here's how i made my wallpaper "stick" as you call it. open up the ~/.fluxbox/startup file and add the command stated above to set your wallpaper to the list. here's the output of my ~/.fluxbox/startup file as an example.

```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/phil/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/phil/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/phil/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
 idesk &
 fbsetbg -f /home/phil/Desktop/wallpaper14.jpg &
 xmms &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/phil/.fluxbox/log"
```

the command i'm talking about is the "fbsetbg -f /home/phil/Desktop/wallpaper14.jpg &" this will have Fluxbox load your wallpaper on startup. hope this helps,

Phil

edit: be sure not to use that EXACT command as the path to your desired wallpaper may vary

---

### Post by bodhi.zazen on 2009-06-25
The way I set the BG is in 

~/.fluxbox/init

Add / edit this command :

```
session.screen0.rootCommand:	fbsetbg -l
```

---

### Post by Locutus_of_Borg on 2009-06-25
> **Duke Togo said:**
> ok I deleted the startup~~ file and restarted
still no wallpaper though
contents of startup~

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/richard/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/richard/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/richard/.fluxbox/log"

feh --bg-scale /home/richard/Pictures/HAL.jpg
my bad, fluxbox will overwrite that setting according to what's in the init file

you could do as bodhizazen says, or you can open the file ~/.fluxbox/init and look for the line that says "session.screen0.rootCommand:" and add "feh --bg-scale /home/richard/Pictures/HAL.jpg" after it

or if you want to feel leet:
```

sed -e "s|session.screen0.rootCommand:|session.screen0.rootCommand: feh --bg-scale /home/richard/Pictures/HAL.jpg|ig" ~/.fluxbox/init > ~/.fluxbox/init
```

but..it might be safer to just edit it by hand... ;p

---

### Post by bodhi.zazen on 2009-06-25
> **Locutus_of_Borg said:**
> or if you want to feel leet:
```

sed -e "s|session.screen0.rootCommand:|session.screen0.rootCommand: feh --bg-scale /home/richard/Pictures/HAL.jpg|ig" ~/.fluxbox/init > ~/.fluxbox/init
```

Use the -i flag with sed.

sed -i -e 's|foo|bar' ~/.fluxbox/init

And also check out fbsetbg -l , shorter .

---

### Post by Locutus_of_Borg on 2009-06-25
sed -i 

wow, not sure how i never knew about that, but that i am inexperienced with sed

thanks


how exactly does fbsetbg -l work?
it appears to simply set the background to whatever it previously was, if the OP wants to change his background from whatever it defaults to, to an image file, won't fbsetbg -l just make it some kind of checkered gray pattern or some such design?

---

### Post by bodhi.zazen on 2009-06-25
If a user sets the bg to an image when using FB

fbsetbg -l simply calls the same image when you log in (the most recent image set to bg).

IMO this is still the easiest solution :
[http://community.fluxbuntu.org/index.php?topic=98.0](http://community.fluxbuntu.org/index.php?topic=98.0)

simply add an entry into your menu.

---

### Post by Locutus_of_Borg on 2009-06-25
ah i see


and yeah, that looks to be the best solution

i am curious though, how does it know to use esetroot -scale?
is that simply the default associated program for image files?

---

### Post by bodhi.zazen on 2009-06-25
yes ;)

---

### Post by Duke Togo on 2009-06-26
thanks a lot
fbsetbg -f /path/to/wallpaper.jpg &
worked a treat
out of interest why does the "&" at the end of the code make so much difference?

---

### Post by bodhi.zazen on 2009-06-26
& makes the program run in the background.

---

### Post by Duke Togo on 2009-06-26
I see thanks
btw
I did a recent restart and it was back to the original style so I`m confused as I didn`t change any settings

---

### Post by Duke Togo on 2009-06-26
whoops, as its fluxbox I did an exit not restart
have to get used to that

---

