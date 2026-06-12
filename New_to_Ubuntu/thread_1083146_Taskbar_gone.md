---
title: "Taskbar gone"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by bevsmith on 2009-02-28
I right clicked on the taskbar and chose delete thinking well if it's that easy to delete it must be that easy to put it back.

Three hours later after reading all over the net still clueless.


Thanks for any help

---

### Post by HermanAB on 2009-02-28
The easy way to fix it, is to make a new user account.

Cheers,

Herman

---

### Post by MarblePanther on 2009-02-28
Try ```
gnome-panel
``` in terminal.

---

### Post by bevsmith on 2009-02-28
> **HermanAB said:**
> The easy way to fix it, is to make a new user account.


Interesting. This told me that there must be some config files in the users folders (xml?) controlling this panel thing.

I diff(ed) the heck out of the dot files but I didn't get anywhere. Do you know which files I'm looking for?

And what's up with the files that start with a % ? There all empty or is there something special about them keeping me from messing with them even as the root user?

thanks

---

### Post by SunnyRabbiera on 2009-02-28
Huh why use root?
Root is not good.
It should be simple, if you still have a panel on your desktop right click on it and select "add panel"
To get a window list right click your new panel and select "add to panel"
add the window list applet, that should do it.

---

### Post by MarblePanther on 2009-02-28
Have you tried my suggestion?  It should work.

---

### Post by bevsmith on 2009-02-28
> **MarblePanther said:**
> Have you tried my suggestion?  It should work.

Yes it worked fine.

Now I have one user with the taskbar and one without (remember I deleted it for one of the users) so there is most likely a file in the user's directories with a name like .gnomeconfig or something like that contolling these panals.

As the root user in a shell I can compare the files between /home/user1 and /home/user2 and figure out where the config is for this taskbar thing and then have control over all of this sort of thing. So far no success I was hoping someone could tell which file so I didn't have to hunt.

Yes being the root user can be dangerous but I've been doing it for more than a decade. The sudo command is too laborious.

---

### Post by RomeReactor on 2009-02-28
Hi. The configuration files for gnome-panel are in **~/.gconf/apps/panel**; log in to the user account with the missing taskbar, open a terminal, and run:
```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```
That will restore the panels to their default settings.

---

### Post by MarblePanther on 2009-03-01
> **bevsmith said:**
> Yes it worked fine.

Now I have one user with the taskbar and one without (remember I deleted it for one of the users) so there is most likely a file in the user's directories with a name like .gnomeconfig or something like that contolling these panals.

As the root user in a shell I can compare the files between /home/user1 and /home/user2 and figure out where the config is for this taskbar thing and then have control over all of this sort of thing. So far no success I was hoping someone could tell which file so I didn't have to hunt.

Yes being the root user can be dangerous but I've been doing it for more than a decade. The sudo command is too laborious.

Oh right, sorry.  I understand what you mean now.  Yes the OP above is right.

---

### Post by mudguts on 2009-03-18
Romereactor...   you just saved my bacon.   I was playing around with the look and styling of ubuntu and deleted my favorite taskbar too.. I like to have it there so I can see my open windows..

it's coming along.. one day at a time, but it's nice to have that bar back.

thanks

[Screenshot]("http://i663.photobucket.com/albums/uu360/mudgts/computers/Screenshot.png")

---

### Post by tad1073 on 2009-03-18
have you tried to right-click on the existing panel and select new panel?

of coarse you will have to add back what you had there.

---

