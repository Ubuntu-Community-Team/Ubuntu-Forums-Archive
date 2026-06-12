---
title: "Firefox really messed up"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by scorchgeek on 2008-12-07
Okay, I recently decided to copy my fonts from Windows using a technique in a Ubuntu book. But now, when I start Firefox, on many websites, most of the text doesn't appear! I got SeaMonkey, and it's able to tell which (Windows) font is causing the problem, so I go into /usr/share/fonts and delete it. This would fix it until I rebooted. But now I can't find the font causing the problem in there! I tried changing the font in Firefox too.

Any ideas? I'm trying an upgrade to Intrepid Ibex, but I doubt that will help. Having a bit of difficulty posting too ;)

---

### Post by Dr Small on 2008-12-07
So, you copied the fonts to /usr/share/fonts ?
It could be a permission problem, for one.

Did you also copy fonts to ~/.fonts/ ?

---

### Post by scorchgeek on 2008-12-07
There is no such directory.

Also, I tried the Intrepid Ibex upgrade and it didn't help. Could someone post a list of what fonts are default so I can delete the ones that aren't, or is there someplace where I can get the full directory? I don't care about keeping the new ones at this point.

---

### Post by Arkaniad on 2008-12-07
~/.fonts = hidden folder maybe?
Check in terminal, i forget what ~ does.
(root?)
(current directory?) <-- likely this one.

;)

---

### Post by Catalyst2Death on 2008-12-07
If you put fonts in ~/.fonts then you should remove/rename the folder to see if that fixes it.
Hitting ctrl+h in the file window of nautilus will show hidden files and folders, ie ones which begin with '.'
'~' stands for $HOME, so its usually /home/(username)  but it can also be abused: ~username would take me to /home/username/  root has its own home, and so when you switch to root, you end up there...

Otherwise you can figure out which fonts are common among windows and ubuntu by doing this in the terminal Applications>Accessories>Terminal:

```
$ cd /usr/share/fonts/truetype/
$ ls > ~/fontlist
$ cd /media/disk/Windows/Fonts/
$ ls > ~/winfontlist
$ cd ~/
$ diff fontlist winfontlist

```
and that will output the differences between windows and ubuntu.  If you only copied ttf fonts over, you should replace:

```
$ ls > ~/winfontlist 
```
with:
```
$ ls | grep ttf > ~/winfontlist
```

This will at least tell you which fonts you might want to selectively remove.  If you end up accidentally removing ubuntu fonts, here is a list of the ttf fonts I have installed (may not be default but pretty close):

```
$ sudo apt-get install ttf-arabeyes ttf-indic-fonts-core ttf-opensymbol ttf-arphic-uming ttf-kochi-gothic ttf-thai-tlwg ttf-bitstream-vera ttf-kochi-mincho ttf-unfonts-core ttf-dejavu-core ttf-lao ttf-freefont ttf-liberation
```

---

### Post by madman92 on 2008-12-07
~/ appends the home directory in front of the slash
ex. ~/Documents = /home/matt/Documents

---

### Post by Arkaniad on 2008-12-07
> **madman92 said:**
> ~/ appends the home directory in front of the slash
ex. ~/Documents = /home/matt/Documents

THANKS!
):P
+1 brownie point to you, dear sir.

---

### Post by theozzlives on 2008-12-07
I copied windows fonts to ~/.fonts cause I wanted Lucida Casual and haven't had a prob. I deleted all the *.FON files and left the *.TTF. Try deleting all the *.FON files

---

### Post by scorchgeek on 2008-12-08
Great. I'll try the list and removing the FON files when I get home. Let you know if it works.

---

### Post by scorchgeek on 2008-12-08
BTW, I did an ls -a in my home directory and I don't have a .fonts, only .fontconfig. I don't know if they might be similar.

---

### Post by Catalyst2Death on 2008-12-08
.fontconfig and .fonts are different things.  You probably copied the fonts to /usr/share/fonts/truetype/ so you should work on them there.  Check and make sure that there aren't any *.FON files in /usr/share/fonts/truetype and delete them if they exist.

---

### Post by hobo89 on 2008-12-08
I don't know if this will be of any use to you, but thought I may as well post it anyway. I was just looking on Digg and saw this which caught my attention as I saw this thread earlier.
[http://www.makeuseof.com/tag/how-to-install-microsoft-core-fonts-in-ubuntu-linux/](http://www.makeuseof.com/tag/how-to-install-microsoft-core-fonts-in-ubuntu-linux/)

---

