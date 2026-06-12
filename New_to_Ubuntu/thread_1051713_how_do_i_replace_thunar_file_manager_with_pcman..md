---
title: "how do i replace thunar file manager with pcman."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by imlinux on 2009-01-27
i have installed xubuntu as from gnome but thunar file which is default file manager for xfce is giving me problems like its windows doesn't closes i have to xkill every time.also  right click menu doesn't work unless i hold the right click.so i wanna replace thunar altogether as default with more faster and light weight file manager pcman as default.please help me.

---

### Post by utnubuuser on 2009-01-27
In terminal:> sudo apt-get install pcmanfm

---

### Post by kerry_s on 2009-01-27
```
sudo mv /usr/bin/thunar /usr/bin/thunar.save
sudo ln -s /usr/bin/pcmanfm /usr/bin/thunar

or

gksu mousepad /usr/local/thunar
put:

#!/bin/sh
exec pcmanfm "$@"

make it executable:
chmod +x /usr/local/thunar


```

you should try and fix thunar first instead.
try removing it and reinstalling:
sudo apt-get remove --purge thunar
sudo apt-get install thunar

also try deleting all the thunar settings folders/files in your home(ctrl+h to see hidden).

---

### Post by utnubuuser on 2009-01-27
In Ubuntu, this also brings up some options (assuming programs are installed)> sudo update-alternatives --config file-manager


Oops, sorry,  that's for the default editor.  Doesn't seem to work for default file-manager.

If you're interested in a good read about this subject,  check out:> man update-alternatives

---

### Post by imlinux on 2009-01-27
> **kerry_s said:**
> ```
sudo mv /usr/bin/thunar /usr/bin/thunar.save
sudo ln -s /usr/bin/pcmanfm /usr/bin/thunar

or

gksu mousepad /usr/local/thunar
put:

#!/bin/sh
exec pcmanfm "$@"

make it executable:
chmod +x /usr/local/thunar


```

you should try and fix thunar first instead.
try removing it and reinstalling:
sudo apt-get remove --purge thunar
sudo apt-get install thunar

also try deleting all the thunar settings folders/files in your home(ctrl+h to see hidden).
 well i tried what you said but right click problem still persists and now i even lost my "places" icon from the panel how do i bring it back.

---

### Post by imlinux on 2009-01-27
> **utnubuuser said:**
> In Ubuntu, this also brings up some options (assuming programs are installed)

Oops, sorry,  that's for the default editor.  Doesn't seem to work for default file-manager

i have installed pcman file manager but as i type--> ```
user@user-desktop:~$ sudo update-alternatives --config file-manager
No alternatives for file-manager.
user@user-desktop:~$ 

``` it gives me error which extra things do i need to install

---

### Post by jerome1232 on 2009-01-27
I searched around for ways to change the default file manger in xfce and this is the most promising i've come across thus far

[https://lists.ubuntu.com/archives/ubuntu-users/2006-May/076983.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-May/076983.html)

Basicly you edit "/etc/xdg/xfce4/desktop/menu.xml"

and replace whatever your current file manager is with pcmanfm.

---

### Post by kerry_s on 2009-01-27
> **imlinux said:**
> well i tried what you said but right click problem still persists and now i even lost my "places" icon from the panel how do i bring it back.

if you did the first 1:
sudo rm /usr/bin/thunar
sudo mv /usr/bin/thunar.save /usr/bin/thunar

if you did the second 1:
sudo rm /usr/local/thunar

---

### Post by kerry_s on 2009-01-27
question:
how much memory do you have?

cause you have the symptoms of a lowram system,that can't keep up with the gui.

how about list of your full specs?

---

### Post by imlinux on 2009-01-27
> **kerry_s said:**
> question:
how much memory do you have?

cause you have the symptoms of a lowram system,that can't keep up with the gui.

how a list of your full specs?
i have 512mb ram

---

### Post by imlinux on 2009-01-27
> **kerry_s said:**
> if you did the first 1:
sudo rm /usr/bin/thunar
sudo mv /usr/bin/thunar.save /usr/bin/thunar

if you did the second 1:
sudo rm /usr/local/thunar

i am sorry too late i have completely removed xubuntu desktop with xfce will reinstall it again

---

### Post by kerry_s on 2009-01-27
> **imlinux said:**
> i have 512mb ram

hmm, that should be plenty of ram to run xfce and then some.

is this something that just started recently or has it been boned since you first installed?

---

### Post by imlinux on 2009-01-27
> **kerry_s said:**
> hmm, that should be plenty of ram to run xfce and then some.

is this something that just started recently or has it been boned since you first installed?
yea it started recently i don't know if its some bug

---

### Post by kerry_s on 2009-01-27
> **imlinux said:**
> yea it started recently i don't know if its some bug

have you tried any window managers, less stuff tied together gives less problems.

i run jwm, pcmanfm, firefox, etc... on 700mhz 128mb ram and my other laptop is 450mhz 256mb ram.
there are many wm's that can give you more bang for the buck.

---

### Post by imlinux on 2009-01-27
> **kerry_s said:**
> have you tried any window managers, less stuff tied together gives less problems.

i run jwm, pcmanfm, firefox, etc... on 700mhz 128mb ram and my other laptop is 450mhz 256mb ram.
there are many wm's that can give you more bang for the buck.
memory isn't the restrain its just thunar started acting weird, every time i right-click a icon in manager window i have to hold the click to keep right click menu ON otherwise it disappears.

---

### Post by kerry_s on 2009-01-27
> **imlinux said:**
> memory isn't the restrain its just thunar started acting weird, every time i right-click a icon in manager window i have to hold the click to keep right click menu ON otherwise it disappears.

what i meant is you can have a even faster setup and it would be way more stable.

---

### Post by widda on 2010-03-01
I just got xfce for xubuntu , and it went really troppo, and got weirder, wouldnt even shut down etc, many menu items non responsive, till finally it busted down to popping up a terminal for me saying this is all you've got pal.
 But I remembered fsck, from one time when had I made it to the surface for a gulp of internet connection
So I typed that in the open terminal and it started to fix am coupla things, no idea what, but I believed it of course. 
Then it blinked for 5 minutes and said Press Y or N, Y if you want blahblah fixt too. Well they kept coming, and i kept hitting the Y.

Wondrous things have happened, xubuntu and xfce is pretty cool today, like 95% together and 5% struggling, instead of v.versa lol.

Sorry about lack of technical precision, nothing I can do about that yet, but mighty pleased with ingenuity and communication of system, cos I know as much about command line as my dog does, and I dont even have a dog.

---

### Post by vickoxy on 2012-03-03
Don´t want to write new thread. So, i tried, following these steps here: [http://stuff.body-builders.org/xfce-replace-thunar-with-pcmanfm/](http://stuff.body-builders.org/xfce-replace-thunar-with-pcmanfm/)
to replace thunar with pcmanfm (Xubuntu 11.10 64bit). Although pcmanfm works well, i never succeeded to make pcmanfm working/drawing on desktop - thunar is there default file manager. I set up in xfce-setup pcmanfm as default file manager, but nothing. Any idea here?

---

