---
title: "Lost Gui after editing xorg.conf in ubuntu 8.04"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by shishir_knit on 2009-02-17
I just edited the xorg.conf and now after logging in my account 
i could only see the white screen 


reply as soon as possible
it will be appreciated

---

### Post by taurus on 2009-02-17
Did you make a backup of /etc/X11/xorg.conf before you edited?  At the GUI login screen, press <Ctrl><Alt><F2 and login with your name and password.  Then, post the output of this command to see if there is a backup that actually worked before you edited it.

```
ls -la /etc/X11
```

---

### Post by philinux on 2009-02-17
Reboot your machine.

When the grub menu appears press the esc key. Using the down arrow key select the option "recovery mode" and press enter. When the menu appears choose xfix. When this has done it's stuff choose resume normal boot.

---

### Post by shishir_knit on 2009-02-17
I searched and deleted the xorg.conf file in <ctrl><alt><f1>

---

### Post by avtolle on 2009-02-17
You deleted it from the command line. Open a terminal as you did before, and do```
cd /etc/X11
``` which will change directories to the correct one. At the prompt that then appears do```
ls
```and see if there is a file named xorg.config.failsafe. If there is do (again from the terminal0```
cp xorg.config.failsafe xorg.config
```to create a new file. Then exit the terminal and restart.

---

### Post by shishir_knit on 2009-02-17
igot to know through internet that xorg.conf regenerates so i deleted all the files of name xorg.conf
and took the same file from other system to copy at the same place 
but it did not work

---

### Post by shishir_knit on 2009-02-17
i also ran the command dpkg-reconfigure xserver-xorg

but it also not worked
what can i do now

---

### Post by anaconda on 2009-02-17
> **shishir_knit said:**
> igot to know through internet that xorg.conf regenerates so i deleted all the files of name xorg.conf
and took the same file from other system to copy at the same place 
but it did not work

It is true that the new version of xorg doesnt need xorg.conf file anymore, (If the file doesnt exist it will autodetect) BUT I think Ubuntu 8.04 still uses the older version.

If I remember correctly I once repaired xorg,.conf by booting to Ubuntu liveCD and then just copied the xorg.conf from there to the hd. (I think liveCD creates the xorg.conf file)
I am not sure, but I vaguely remember I did that..:p

---

### Post by shishir_knit on 2009-02-17
copying doesnt helped me can u give me some other way

i also tried for recovery mode run but there is same result

waiting for reply

---

### Post by zika on 2009-02-17
> **shishir_knit said:**
> i also ran the command dpkg-reconfigure xserver-xorg
but it also not worked
what can i do now
if I were in Your shoes I would try```
sudo apt-get reinstall xserver-xorg
``` in Ctrl-Alt-F1 once I get a hold of it. that might recreate xorg.conf if I'm right.
that assumes You have internet connection before X. if You do not, and You would like to try this than You should make /etc/network/interfaces and /etc/resolv.conf and then ```
sudo /etc/init.d/networking restart
``` in that Ctrl-Alt-F1 ... restart might need one <enter> when it is finished to get a prompt back, do not worry about that. than You could try what I've suggested since then Your networking would be up and running I hope.
[COLOR=MediumTurquoise]**what is the graphic card?**[/COLOR]

---

### Post by EnGorDiaz on 2009-02-17
> **anaconda said:**
> It is true that the new version of xorg doesnt need xorg.conf file anymore, (If the file doesnt exist it will autodetect) BUT I think Ubuntu 8.04 still uses the older version.

If I remember correctly I once repaired xorg,.conf by booting to Ubuntu liveCD and then just copied the xorg.conf from there to the hd. (I think liveCD creates the xorg.conf file)
I am not sure, but I vaguely remember I did that..:p

ofcourse it makes a xorg file you have uninstall any propriestary video drivers though and start a fresh

---

### Post by shishir_knit on 2009-02-18
i just tried what u said
now the command dpkg-reconfigure xserver-xorg
is also giving error that package is not installed properly
what can i do now

---

### Post by zika on 2009-02-18
> **shishir_knit said:**
> i just tried what u said
now the command dpkg-reconfigure xserver-xorg
is also giving error that package is not installed properly
what can i do now
 command chould be:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` I'll assume that You are talking to me ... ;) did You try the advice about booting with liveCD?
You did not answer yet which graphic card You have. that might help us think about how xorg.conf should look like ... and even try to recreate it. if its nvidia then I have minuscule experience but with ATI I might even be of some help. nevertheless these days xorg.conf is getting more and more depreciated so ...
it might help if You would paste the errors You get, so we could get some more information You might even think of as irrelevant.

try and put (command would be ```
gksudo gedit /etc/X11/xorg.conf
```then paste  and ```
gksudo gedit /etc/X11/xorg.conf.failsafe
```then paste ... this both as **/etc/X11/xorg.conf** and **/etc/X11/xorg.conf.failsafe**```
# xorg.conf.failsafe (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
``` and reboot with "fix" option.

now, after *phigh* option and with these files in place You might try to reinstall xserver-xorg. if that doesn't work and if I am on-line we could try to create a failsafe xorg.conf for ATI.

---

### Post by shishir_knit on 2009-02-18
i my new on ubuntu so 
i m not able to know how to get my ati card name
its ati chipset 
can u tell me the command to find it

and i hav tried from live cd but it did not work

---

### Post by zika on 2009-02-18
> **shishir_knit said:**
> i my new on ubuntu so 
i m not able to know how to get my ati card name
its ati chipset 
can u tell me the command to find it
and i hav tried from live cd but it did not work
OK, its ATI, that is enough. try what I have posted above.

---

### Post by shishir_knit on 2009-02-18
ok i m going to try this 
i will reply u its result in few minutes

---

### Post by zika on 2009-02-18
> **shishir_knit said:**
> ok i m going to try this 
i will reply u its result in few minutes
don't hurry! take Your time and contemplate on every step. just take it as easy as possible ... ;)

---

### Post by shishir_knit on 2009-02-18
i copied the file and reboot my system
and in recovery mode i just did the xfix
but i got the error that 
xserver-xorg is not installed properly or is in broken package
and there is no GUI once more

---

### Post by shishir_knit on 2009-02-18
waitin for ur reply

---

### Post by zika on 2009-02-18
> **shishir_knit said:**
> i copied the file and reboot my system
and in recovery mode i just did the xfix
but i got the error that 
xserver-xorg is not installed properly or is in broken package
and there is no GUI once more
I'm confused right now.
maybe this would help:```
sudo dpkg --configure -a
sudo apt-get -f install xserver-xorg
sudo apt-get update
sudo apt-get upgrade
```and if it doesn't add this to that batch```
sudo apt-get install &#8211;reinstall xserver-xorg
```[COLOR=Blue]**please be aware that I not sure what is installed on Your machine and be aware that we are deep in messing up everything. backup any valuable data right now, as long as You have the access to Your data.**[/COLOR]

---

### Post by shishir_knit on 2009-02-18
ok

---

### Post by shishir_knit on 2009-02-18
on command line interface
sudo apt-get --configure -a
is giving not a bash command
i hav written it in this way as u hav written 
is it not the way in which we hav to write it on command line interface

---

### Post by shishir_knit on 2009-02-18
sorry
the error is
command line option --configure is not understood

---

### Post by philinux on 2009-02-18
sudo **dpkg** --configure -a

---

### Post by shishir_knit on 2009-02-18
sudo dpkg --configure -a 
has run
but update and upgrade is not able to run 
i think so net is not connected
how could i check internet connection is working properly on command line interface

---

### Post by shishir_knit on 2009-02-18
zika thanx for ur contribution
now i m going to format my system

thank u once more

---

### Post by zika on 2009-02-18
> **shishir_knit said:**
> zika thanx for ur contribution
now i m going to format my system
thank u once more
sorry to hear that. I'm a fixer not re-installer ... ;) good luck. if I could be of any help. do not hesitate to ask.

---

