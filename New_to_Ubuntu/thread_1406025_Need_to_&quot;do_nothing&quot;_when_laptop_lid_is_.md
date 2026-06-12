---
title: "Need to &quot;do nothing&quot; when laptop lid is closed"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by gigi1234 on 2010-02-13
Hi! I am running 9.10 on a Dell XPS m1330 laptop. I would like to find a way to have the computer "do nothing" when the laptop lid is closed. I close the lid frequently when moving around my house and don't want to computer to suspend or hibernate. Currently there is no menu option for this but maybe there is a file I could alter in the terminal?

Thanks!

---

### Post by m_duck on 2010-02-13
If memory serves, if you right click the battery icon in the system tray and go to preferences, there is a tab relating to when the computer is on battery power, and in there is a drop down with different actions to take when the lid is closed, one of them being "no action".

---

### Post by x33a on 2010-02-13
Well one way is to disable gnome-power-manager if you don't need its features.

---

### Post by switch10 on 2010-02-13
Go to System>Preferences>Power Management.  It will say "when laptop screen is closed"  and then there will be a drop down list.  choose do nothing.  On both AC power and Battery power tabs.

---

### Post by scared0o0rabbit on 2010-02-13
Or you could always do what I accidentally did, break the sensor that tells the laptop it's screen is closed lol.

---

### Post by SOULRiDER on 2010-02-13
> **switch10 said:**
> Go to System>Preferences>Power Management.  It will say "when laptop screen is closed"  and then there will be a drop down list.  choose do nothing.  On both AC power and Battery power tabs.

That's what I do. However, making it turn off the monitor will help you save some battery.

---

### Post by HermanAB on 2010-02-13
OK, but bear in mind that when you close the lid, the laptop will get very hot, so you may have to do something anyway, like spin down the hard disk, shut down the screen and so on.

---

### Post by dwhitney67 on 2010-02-14
> **HermanAB said:**
> OK, but bear in mind that when you close the lid, the laptop will get very hot, so you may have to do something anyway, like spin down the hard disk, shut down the screen and so on.

It is not uncommon to operate a laptop with the lid closed when using an external monitor.  The heat issue you wrote of so far has not impacted my systems, both at home and at work.

---

### Post by Reathziel on 2010-02-20
You can solve that typing gconf-editor in your terminal then go to 
/apps/gnome-power-manager/buttons/lid_ac and set the value to "nothing" (without "")
It should work ;)

---

### Post by shimmo on 2010-04-09
Sounded good ... looked promising in gconf-editor BUT does not work either.

---

### Post by vbmds on 2010-04-11
I also use my laptops with an external monitor so this function is important for me also. I tried Reathziel recommended solution and it worked perfectly for me. 

Now I can stash the laptop under my desk - I also use an external mouse and keyboard, so until the power button is next required, I don't need access to the the laptop now.

---

### Post by spillin_dylan on 2010-04-11
Right click a Gnome Panel.

Add To Panel -> Inhibit Applet

One-click on/off solution to prevent suspend/hibernate/anything.


That's what I use, and it seems to work pretty good.  I usually just have it on the inhibit power save mode all the time anyway.

---

### Post by alican timur on 2010-07-04
it does for me.. are you sure you're "doin it rite"?

---

### Post by jonguitud on 2012-04-13
You just need to open a terminal and type:

```
gsettings set org.gnome.settings-daemon.plugins.power lid-close-battery-action blank

```and...

```
gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action blank
```be careful not to type "sudo" nor to login as "root".

See ya!

---

### Post by oldos2er on 2012-04-13
Closed. Please don't bump old threads.

---

