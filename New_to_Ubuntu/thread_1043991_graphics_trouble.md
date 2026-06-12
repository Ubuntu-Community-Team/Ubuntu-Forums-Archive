---
title: "graphics trouble"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by mustard greens on 2009-01-19
my computer occasionally shuts down the graphics format, offering me a choice of several options including running in low graphics mode and details of the crash which mean little to me.  I have been running compiz in high graphics mode for more than a year with no trouble and now this.  I have a built in graphics controler and a duel core processor with 2GiB ram.  any help would be appreciated.  below is my integrated graphics controller info
 description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
thanks

---

### Post by gettinoriginal on 2009-01-21
Any system changes lately, updates, installations, uninstalls ??  I would simply check Synaptic to see if you still have "xserver-xorg-video-intel" installed.  :p

---

### Post by mustard greens on 2009-01-21
xserver-xorg-video-intel is installed.  no major updates to my system to report, although I usually accept any new patches that come along from trusted repositories.  it happened again today and the error message was a new one
"(EE)intel(0):Failed to destroy server context"
does this help anyone to understand my problem?
thanks

---

### Post by gettinoriginal on 2009-01-21
Please copy/paste the following into terminal and post the results:
```
sudo gedit etc/X11/Xorg.conf
```

---

### Post by mustard greens on 2009-01-22
I copied and pasted,"sudo gedit etc/X11/Xorg.conf".  what I got was it left the terminal and opened a new window.  the window had no information, just a flashing cursor.

[IMG]/home/aaron/Desktop/Screenshot-Xorg.conf (-home-aaron-etc-X11) - gedit.png[/IMG]

could not figure out how to post the screenshot.  do I have to post it to a website somewhere first?

---

### Post by mustard greens on 2009-01-22
ok, so I figured out the picture thing.  heres the screen shot

[IMG]http://ubuntuforums.org/picture.php?albumid=861&pictureid=2931[/IMG]

---

### Post by gettinoriginal on 2009-01-22
you can create and use an xorg.conf file. To do so, try booting Ubuntu in Recovery Mode and selecting xfix, then see if an xorg.conf file is created.
To do this, when the grub splash starts, hit escape and select "recovery mode, let it run, then choose "try to fix x"

---

### Post by mustard greens on 2009-01-22
I was unable to see if an xorg.conf file was created.  the sequence went by very quickly and then returned me to the try to fix X screen.  by the way, thanks for sticking with me on this.  so this may sound silly, but this graphics crash has only ever occurred while my girlfriend was playing AisleRiot Solitaire.  do you think it is possible to be the culprit?  it seems benign considering all the compiz flash Ive had going on with no problem forever, but maybe there is an incompatibility.

---

### Post by gettinoriginal on 2009-01-22
no, I play that all the time

try this again:
```
sudo gedit /etc/X11/Xorg.conf
```

---

### Post by mustard greens on 2009-01-23
still just opens an empty window. was there more that was supposed to happen with the "try to fix X", or something I was supposed to note in the readout?
we are suspending all solitaire play for the mean while just in case.

---

### Post by mustard greens on 2009-01-26
I dont have enough knowledge to prove that Aisle riot solitaire was the culprit, but since discontinuing its use I have not had a single graphic issue.

---

### Post by gettinoriginal on 2009-01-26
How wierd, it probably is possible that Aisle Riot corrupted during installation. :confused:  But I believe that they come as a package, so don't know if you can just uninstall Aisle Riot.  Sorry for all the hassle I put you through :(

---

### Post by mustard greens on 2009-01-27
it definitely wasnt a hassle.  I appreciate that you took the time.  Im still not sure what the problem is so I dont think I will mark it solved yet.  Im still confused about the attempts with "sudo gedit /etc/X11/Xorg.conf".  should there have been info there, or only if there had been a problem?

---

### Post by gettinoriginal on 2009-01-27
Ubuntu is working at eliminationg the need for an xorg file, so some of us have it, and some don't, it depends on the hardware involved.  As long as your system is working, then don't worry about it.  But if you have any more problems, you can try this which is supposed to generate an Xorg file:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mustard greens on 2009-01-31
after more than a week with no problems I was able to reproduce the problem twice by opening aisle riot solitaire.  I will attempt to uninstall and reinstall it to see if that helps.

---

### Post by mustard greens on 2009-02-08
I have tried reinstalling the gnome game package and still aisle riot seems to crash my graphics.  I have no evidence to prove it, but the only time the crash happens is while we play that game.

---

