---
title: "Lucid conflicts with Ubuntu Tweak"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by 311005901 on 2010-04-25
I upgraded from Karmic to Lucid and I had used Ubuntu Tweak for the "Complete Lockdown of All Panels".
Now, Lucid reverts me back to the Netbook Launcher interface and I want the regular desktop Ubuntu interface. I uninstalled maximus, and netbook-launcher, but I am prevented in altering the gnome-panel in any way. I have unchecked the complete lockdown in Ubuntu Tweak.

What can I do to have the vanilla Ubuntu panels back?
I'm thinking this is an Ubuntu Tweak issue...

---

### Post by warfacegod on 2010-04-25
Use Synaptic and Completely Remove ubuntu-tweak.

Although, I must say, this is the first issue I've heard of from U.T. This is likely do to Lucid still being a Beta.

---

### Post by 311005901 on 2010-04-25
Thanks for replying!
I did a sudo apt-get purge ubuntu-tweak and restarted and the panels are still the same... Any more suggestions?

---

### Post by JOHNNYG713 on 2010-04-25
New ubuntu tweak ! [http://launchpad.net/ubuntu-tweak/0.5.x/0.5.3/+download/ubuntu-tweak_0.5.3-1~lucid1_all.deb]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.3/+download/ubuntu-tweak_0.5.3-1%7Elucid1_all.deb")

---

### Post by 311005901 on 2010-04-25
I just got it and installed it. It runs fine, but when I run it from the terminal I get the message ```
 rm: cannot remove '/home/tim/.recently-used.xbel': Permission denied
``` I sudo rm'ed it myself, but then I get the error ```
 rm: cannot remove '/home/tim/.recently-used.xbel': No such file or directory
```

In the "GNOME Settings" tab, "Complete lockdown of all panels" is unchecked. 

Anything else?

I tried purging gnome-panel and installing it again.
I also installed ubuntu-desktop but it still boots up with unmovable panels...

---

### Post by 311005901 on 2010-04-25
Now I'm thinking this is an issue with gnome-panel.
I checked in gconf-editor and under /apps/panel/general/ the "locked_down" value is unchecked.

Also, whenever I log in, since I removed the ubuntu-netbook and netbook-launcher packages, an error pops up saying "The panel encountered a problem while loading "OAFIID:GNOME_GoHome"."
I click 'delete' each time, and it will not remove it from the panel.

---

### Post by tom.swartz07 on 2010-04-25
> **311005901 said:**
> I just got it and installed it. It runs fine, but when I run it from the terminal I get the message ```
 rm: cannot remove '/home/tim/.recently-used.xbel': Permission denied
``` I sudo rm'ed it myself, but then I get the error ```
 rm: cannot remove '/home/tim/.recently-used.xbel': No such file or directory
```

In the "GNOME Settings" tab, "Complete lockdown of all panels" is unchecked. 

Anything else?

I tried purging gnome-panel and installing it again.
I also installed ubuntu-desktop but it still boots up with unmovable panels...


Run it with sudo.

If you ever run something and it throws a "Permission Denied" error, just run ```
sudo !!
```
Sudo is the command to run it as a "Super User", and the !! means 'run the last command". combined, they mean "run the last command as a super user"
:D

---

### Post by 311005901 on 2010-04-25
Thanks, but that's not my biggest problem right now.

I'm still having difficulties with editing the panels and changing their position.

---

### Post by clhsharky on 2010-04-25
Ah upgrades such a pain,
but sure is a learning experience.

Sharky

---

### Post by warfacegod on 2010-04-26
```
sudo apt-get purge gnome-panel
```

```
sudo apt-get install gnome-panel
```

---

### Post by lockalidiot on 2010-04-26
Have you tried removing the go-home applet? I had a similar issue with my UNR even though I had removed maximus and UNR launcher. Then I read somewhere(here forums) that I should also get rid of the go-home applet. Now it's like any other desktop gnome.

---

### Post by 311005901 on 2010-04-26
Thanks for the reply! But... I already tried that.
I did ```
sudo apt-get purge gnome-panel
``` and ```
killall gnome-panel
``` and ```
sudo apt-get autoremove
``` and ```
sudo apt-get install gnome-panel
``` and then logged out and back in and the panel is back to its uneditable state.

Any other suggestions?

---

### Post by 311005901 on 2010-04-26
Aha! I found a way to get around it!
On the login screen, I have to change the session selection on the bottom of the screen to be "GNOME" instead of "Ubuntu Netbook Edition".
It's a little annoying, but I'll just have to remember this quick fix.
Thanks everybody for your help! :)

Is there a way I can delete this entry from the dropdown box? I want to get rid of that session.

---

### Post by warfacegod on 2010-04-26
> **311005901 said:**
> Aha! I found a way to get around it!
On the login screen, I have to change the session selection on the bottom of the screen to be "GNOME" instead of "Ubuntu Netbook Edition".
It's a little annoying, but I'll just have to remember this quick fix.
Thanks everybody for your help! :)

Is there a way I can delete this entry from the dropdown box? I want to get rid of that session.

Once you've set it to Gnome, it should remember it as the default session whenever you login with that username.

---

### Post by Goombie on 2010-10-20
I found an article about a problem similar to yours, which might help you:
[http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25]("http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25")

It was written for a beta version of Lucid, but the methods worked fine on my computer with the final release.

---

