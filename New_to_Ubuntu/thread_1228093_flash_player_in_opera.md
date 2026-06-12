---
title: "flash player in opera"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by davellew69 on 2009-07-31
Hi chaps and Chapesses, I am having a problem using flash player in opera? i can watch news videos on bbc website, watch youtube  all fine in firefox, and konquer, but not having much luck in opera...I am puzzled

---

### Post by Liolikas on 2009-07-31
Very old article but maybe it will help:
[http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html](http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html)

---

### Post by davellew69 on 2009-07-31
thanks, i`ll give it a go now

---

### Post by davellew69 on 2009-07-31
no luck, as its old  most of the links don`t work

---

### Post by Liolikas on 2009-07-31
Key part is here:
```

Now you need to install Flash9 (maybe 10) from (adobe.com)

Now you need to extract this file using the following co(m)mand

sudo tar xzvf install_flash_player_9_linux.tar.gz

Now you need to go in to the install_flash_player_9_linux directory

cd install_flash_player_9_linux/

sudo cp libflashplayer.so /usr/lib/opera/plugins

sudo cp flashplayer.xpt /usr/lib/opera/plugins

```

That may be enough in 2009 not 2007 if not write here.

---

### Post by davellew69 on 2009-07-31
tar: install_flash_player_10_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
llewellyn@llewellyn-desktop:~$ sudo tar xzvf install_flash_player_9_linux.tar.gz 
 

no luck, am i doing something wrong

---

### Post by Liolikas on 2009-07-31
You have to download it at first:
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

---

### Post by davellew69 on 2009-07-31
downloaded it, but still getting the same message

---

### Post by Liolikas on 2009-07-31
show:
```

ls

```
You have to cd into donloads folder first then tar -x...

---

### Post by davellew69 on 2009-07-31
ok im now lost..lol

---

### Post by RomeReactor on 2009-07-31
Hi. Are you using Ubuntu 32 bit or 64? How did you install Flash for the other browsers?

---

### Post by davellew69 on 2009-07-31
as far as i know its a 32 bit, i installed flash by downloading deb file, the intsalling

---

### Post by RomeReactor on 2009-07-31
In Opera, go to 'Tools->Preferences->Advanced'; on the window that pops up, you should see various sections. Highlight 'Content', and make sure the "Enable plug-ins" box is checked. Press the "Plug-in Options" button, and see if it lists Flash there; if it doesn't, press "Find New...". If it still doesn't show the Flash plugin, post the "Plug-in path" line. And make sure you don't have multiple versions of Flash installed, or Gnash.

---

### Post by W4l0ck on 2009-07-31
I have the same problem.

---

### Post by oldos2er on 2009-07-31
Much easier just to run
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

 Sorry, I should've read the OP more carefully.

 If you've downloaded flash to your desktop, you first need to run **cd ~/Desktop** before untarring the file. Then the rest of the instructions should work.

---

