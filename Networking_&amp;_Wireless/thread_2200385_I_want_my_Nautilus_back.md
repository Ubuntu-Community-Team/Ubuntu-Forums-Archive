---
title: "I want my Nautilus back"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by Luxx on 2014-01-19
I have tried the newer file managers and they just don't do everything that Nautilus did. I'm getting tired of finding work-arounds for things that used to just work. 

I have a little problem installing Nautilus though. It seems it has disappeared completely and all I can get is nautilus-dropbox.

I try to uninstall nautilus-dropbox and terminal tells me it isn't installed. When I try to open Nautilus it gives me:
Initializing nautilus-dropbox 1.6.0

So if nautilus-dropbox isn't installed, why is it opening?

I want Nautilus back and I want to make it my default file manager, but with my system confusing nautilus-dropbox for nautilus, I don't know how I can do that. How can I fix this?

---

### Post by carl4926 on 2014-01-19
What files manager can you open from the dropbox tray icon?

---

### Post by Luxx on 2014-01-19
I'm not sure I understand your question. When I open the dropbox folder it seems to be opening in nemo.

Nemo is currently my default file manager.

I am having trouble uninstalling dropbox as well. Terminal says it is not installed. It seems to be saying that a lot lately.

---

### Post by carl4926 on 2014-01-19
Nemo is the cinnamon file manager
Are you sure you are running Ubuntu 13.10?

---

### Post by deadflowr on 2014-01-19
How did you install your system?

Nautilus is the default file manager for Ubuntu.
Are you using Ubuntu?

Edit: To add the what carl4926 stated, nemo is the file manager linux mint made for cinnamon.
It is a fork of nautilus.
Probably why the dropbox opens it.

---

### Post by Luxx on 2014-01-19
I'm sure. I did try cinnamon and some other DEs. I was not happy with Unity.

---

### Post by deadflowr on 2014-01-19
Why can't you find nautilus in the software center or the repos.
If using Ubuntu, it is there.
```
sudo apt-get install nautilus
```

---

### Post by Luxx on 2014-01-19
Um... that isn't working. Software Center says it's installed. Trying to launch it launches nautilus-dropbox instead of nautilus.

The problem is that nautilus-dropbox is launching instead of nautilus. I seem to have the wrong thing installed, but my computer doesn't seem to know it's the wrong thing that's launching.

---

### Post by Luxx on 2014-01-19
I was aware of changing the file manager when I tried cinnamon. I already knew nemo had been set as my default file manager.
Playing around with DEs and file managers may have contributed to this problem, although it was totally unexpected.

Nemo doesn't work in some of the ways I need it to, even though it's supposed to be a fork of nautilus 3.4, which would be the version I would install if I could, but I can't find a way to do that. So the default version will have to do for now... IF I can figure out how to get my computer to recognize it and open the right thing.

I don't want nautilus-dropbox to be my default file manager. I want nautilus to be my file manager, but how can I restore it if my computer keeps trying to use nautilus-dropbox instead?

---

### Post by ajgreeny on 2014-01-19
I have never heard of nautilus-dropbox, and I use Xubuntu 12.04, but one way round your problem my be to find the .desktop files (launchers) for nautilus, and perhaps nautilus-dropbox, in **/usr/share/applications** and if necessary edit them to the way you want them with gedit or whatever text editor you prefer to use.

Use command ```
ls /usr/share/applications
``` to find them all and then open the files you want to edit with command ```
gksudo gedit /usr/share/applications/nautilus.desktop
``` etc etc, and change the **Exec=nautilus-dropbox %U** to what you want, eg **Exec=nautilus %U**.

There are likely to be several .desktop files for nautilus-home, eg, nautlus-folder-handler, nautilus-scripts-manager, etc etc so choose what you want to edit carefully.

---

### Post by Luxx on 2014-01-19
I had purged all nautilus and dropbox stuff and finally reinstalled nautilus. It took a few tries, but I think I finally got everything and.... I am missing the Connect to Server entry under Places. I wasn't expecting that. But I seem to have Nautilus back.

@ajgreeny: Excellent idea. I have all sorts of stuff in there that I don't need and could cause conflicts; caja, mate, metactiy, muffin, etc I guess I wasn't as thorough about undoing my little DE trials as I should have been.

I got the Connect to Servers under Places back after replacing the stock Nautilus with 
Nautilus-1:3.8.90.really.3.4.2-0ubuntu1~ppa13.10+2
from [https://launchpad.net/~zdra/+archive/nautilus-3.4](https://launchpad.net/~zdra/+archive/nautilus-3.4)

> sudo add-apt-repository ppa:zdra/nautilus-3.4
sudo apt-get update

I'm very happy with that.

---

### Post by Luxx on 2014-01-19
Ok, I think this issue is fixed, but of course other issues always pop up when something gets fixed.
Thanks carl4926, deadflowr, & ajgreeny for your input.

Could purging & reinstalling nautilus cause issues with Xorg?

---

