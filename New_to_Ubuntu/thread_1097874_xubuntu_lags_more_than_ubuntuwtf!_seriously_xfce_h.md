---
title: "xubuntu lags more than ubuntu?wtf?! seriously xfce hurts more than gnome?!"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-16
as stated for some unknown reason Xubuntu lags alooooooooooot more than ubuntu when i use a program that uses any cpu power at all. I try to play a game xubuntu lags like hell. When i compiled wine it lagged like hell. The memory's not the problem since i never see it get above 50%. The cpu however goes to 100% which is what i expect since my cpu's weak. But in ubuntu it wouldn't lag like it does here i use firefox and game or like earlier when i said compiling wine. I'd try to open firefox it'd lag then open. Why is XFCE doing this? Is there any logical reasnoning for this to happen? First the mouse issues and now random lag when i try to use cpu intensive porgrams as in wayyyyyyyyyyyyyy more than ubuntu. IN ubuntu i never had lag ever. And supposedly it wans't made for pcs that were weak. Xubuntu is supposedly made for weaker pcs. I'm on a weak laptop and ubuntu works far faster than xubuntu i don't get this and it's utterly effed up.

---

### Post by stoogiebuncho on 2009-03-16
Did you actually install Xubuntu or did you install Ubuntu and then install the xcfe-desktop package (or whatever it's called)?

You say you've tried Ubuntu and Xubuntu on the same machine and Ubuntu works better.  Maybe you should just use Ubuntu.

Xubuntu is made to be lighter than Ubuntu, but honestly, it's not really that light of a distro.  Especially if you're using a lot of Gnome and KDE apps.  If you're looking for something really light, you might try puppy linux or DSL (Damn Small Linux).  Though I hear they can be somewhat harder to install.

---

### Post by stchman on 2009-03-16
I have used Xubuntu and Ubuntu on lower spec machines and frankly I cannot tell the difference in performance.

---

### Post by 133794m3r on 2009-03-16
i installed the Xubuntu live disk and installed it from there. I wasn't using alot of gnome apps but i expected it to be lighter on the CPU than Ubuntu as that's it main reason to go to it or atleast that's how i read it.

edit: i basically had ubuntu not working so i wiped the HDD and installed xubuntu all the way using 100% of the HDD for its' self.

---

### Post by bekind2thenoob on 2009-03-16
If you want an easy to use lightweight distro then you could give Crunchbang Linux a try.

Its based off ubuntu (so its compatable with most ubuntu .debs and has acess to ubuntus repos), and uses gtk apps with the openbox window manager.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by kidux on 2009-03-16
I installed Ubuntu 8.10, then installed XFCE4, not the xubuntu desktop, and I found that upgrading my nvidia drivers to 180.xx fixed any sluggishness or lag I had.

---

### Post by 133794m3r on 2009-03-16
ok how much better is this distro at working with high cpu demanding apps?
well i'm on ati and i'm not going to update my graphics drivers until i decide upon this one :/ i'll try doing a manual update of this crappy driver and go from there. Also double click doesn't open a file -_- once more good job xubuntu good  job -___________-

edit:nvm i fixed the mouse thing had to adjuct double click spee thing.

---

### Post by .:Justus:. on 2009-03-16
> **133794m3r said:**
> ok how much better is this distro at working with high cpu demanding apps?
well i'm on ati and i'm not going to update my graphics drivers until i decide upon this one :/ i'll try doing a manual update of this crappy driver and go from there. Also double click doesn't open a file -_- once more good job xubuntu good  job -___________-

edit:nvm i fixed the mouse thing had to adjuct double click spee thing.

Are you using any window managers like beryl or compiz?
Because they don´t run very well in xfce to begin with, if you´re not using any window managers you might want to check all your drivers? Dunno seems weird to me. My xubuntu runs quite a lot better than ubuntu.

---

### Post by 133794m3r on 2009-03-16
if beryl or compiz came installed i guess i'm using them if they didn't i'm not. I've not installed any windows things for it. And the cpu driver might be to blame and in a few i'm going to update my graphics driver to the most recent 9.2 instead of what ubuntu wants to use aka 8.5. so that might do something if not then i have no idea.

---

### Post by .:Justus:. on 2009-03-16
> **133794m3r said:**
> if beryl or compiz came installed i guess i'm using them if they didn't i'm not. I've not installed any windows things for it. And the cpu driver might be to blame and in a few i'm going to update my graphics driver to the most recent 9.2 instead of what ubuntu wants to use aka 8.5. so that might do something if not then i have no idea.

**Definatly update the graphics driver**. On xubuntu compiz shouldn´t be preinstalled but you can check your synaptic package manager.

Simply delete it in your synaptic PM and then press alt+f2 and type:
```
xfwm4 --replace
``` 

Then see if it runs better.

---

### Post by 133794m3r on 2009-03-16
ok maybe you can explain this to me why isn't there an option to make scripts runable from the desktop on xubuntu? it's getting very very annoying having to go to command prompt to do anything.

edit": i tried it in the command prompt to be safe to see if it did jack and it said
```
macarthur@insanity:~$ xfwm4 --replace

** (xfwm4:31309): WARNING **: Another Window Manager is already running

```

ok yeah i just did the update of my driver or atleast i thought i did and it erm hmm no screenshot tool and my screenshot compo's not working atm plus i don't want to have to install the gnome-tools since it'll slow down my pc :/

---

