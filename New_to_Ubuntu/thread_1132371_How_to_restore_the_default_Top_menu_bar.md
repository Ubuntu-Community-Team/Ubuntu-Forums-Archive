---
title: "How to restore the default Top menu bar"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Vendettaseve on 2009-04-21
Hey everyone

I made the mistake of letting a windows user on my laptop the other day and she deleted my top menu bar, how would I restore it, or at least make a new one with the default configuration, as I can only seem to get blank ones when I try to create new ones :(

Thanks in advance

V

---

### Post by steve101101 on 2009-04-21
right click a panel. then select add new panel. then add all the needed buttons.

---

### Post by saidinesh5 on 2009-04-21
1)right click on the blank one and "add to panel"
2) add the main menu 
3) also the system tray thing .

n tada, here you got your previous panel back(if needed , move things a bit here n there). even check out the other additions you can make. they can be real handy

---

### Post by Vendettaseve on 2009-04-21
I tried doing that already but cannot seem to find any of the original buttons IE the clock, the 3 dropdown menu's for programs places and settings etc or the correct network monitor(the one I did find is massively different :(  )

---

### Post by leonardo_neo on 2009-04-21
> **Vendettaseve said:**
> Hey everyone

I made the mistake of letting a windows user on my laptop the other day and she deleted my top menu bar, how would I restore it, or at least make a new one with the default configuration, as I can only seem to get blank ones when I try to create new ones :(

Thanks in advance

V

Right click on bottom panel----->New Panel

Now go to the newly created panel. Right click---->Add to panel

1. clock
2. Notification area
3. volume control
4. Menu bar

You can change the position of these applets by simply dragging them. If you wish then you can add some more applets whatever you like.

If you need some more help, then you can ask here. 

:)

---

### Post by sayems on 2009-04-21
There are times where you would want to mess with your Gnome, playing around with it and start adding/removing stuffs here and there.

If you have, somewhat, intentionally broken your Gnome settings (for instance, missing window buttons, disappearing application menu, or even worse, crashing gnome-panel), there is still a solution.

All you need to do now is to restore the Ubuntu/Gnome default settings.

To give you an idea, all Gnome settings are stored in folders, and they are user specific. That said, by simply removing these customization folders, you will be able to get back the fresh settings!

Type the following into your command : Alt+F2
[B]
rm -rf .gnome .gnome2 .gconf .gconfd .metacity[/B]


Eventually, do a restart and you should get back the default Ubuntu/Gnome settings!

And it's time to start playing with the Gnome customizations again ;)

---

### Post by Vendettaseve on 2009-04-21
Thank you for your help everyone, I have not yet got it working but I can see that it is just a matter of fiddling to get it back to the way I like it, 

You have all been very helpfull and answered perfectly :D

---

### Post by steve101101 on 2009-04-21
glad we all could help. removing the settings was very smart.

---

### Post by Avinash.Rao on 2009-08-03
Hi guys,

I removed the exit menu at the top right hand corner, this also displays the full name of the user logged in and various other options like shutdown, hibernate, switch user, suspend, restart, lock screen etc.

How can i add this to the panel without deleting the gconf and gnome files?

Thanks
Avinash

---

### Post by CatKiller on 2009-08-03
> **Avinash.Rao said:**
>  I removed the exit menu at the top right hand corner, this also displays the full name of the user logged in and various other options like shutdown, hibernate, switch user, suspend, restart, lock screen etc.

That's the user-switcher applet. Add it back the same as you'd add any applet to the panel.

---

### Post by Avinash.Rao on 2009-08-03
I dont find this in add to panel list. Where is this?


> **CatKiller said:**
> That's the user-switcher applet. Add it back the same as you'd add any applet to the panel.

---

### Post by CatKiller on 2009-08-03
> **Avinash.Rao said:**
> I dont find this in add to panel list. Where is this?

It's there on mine (Jaunty). It's possible that it was called "Fast User Switcher" in previous releases.

---

### Post by philinux on 2009-08-03
All the applets are in alphabetical order. User Switcher. Jaunty

---

### Post by Avinash.Rao on 2009-08-03
Thanks i got it.. 

After reboot, the network manager applet is missing? I also noticed that, the network manager applet doesn't show any connections. I added them manually but they disappear. And it always shows the **X** mark as if there are no network connections.. But, the LAN is working perfectly.

> **philinux said:**
> All the applets are in alphabetical order. User Switcher. Jaunty

---

### Post by CatKiller on 2009-08-03
> **Avinash.Rao said:**
>  After reboot, the network manager applet is missing?

Have you also removed the Notification Area?

---

### Post by Avinash.Rao on 2009-08-03
You are right, i added notification area and i got back the icon on the panel. But, it shows me the Network adapters installed on the machine, they are greyed out and says device not managed. How do i get the IP information here?

> **CatKiller said:**
> Have you also removed the Notification Area?

---

### Post by CatKiller on 2009-08-03
> **Avinash.Rao said:**
> You are right, i added notification area and i got back the icon on the panel. But, it shows me the Network adapters installed on the machine, they are greyed out and says device not managed. How do i get the IP information here?

I have no idea. I don't like NetworkManager that much so, since it still works manually, I don't use it. It's probably best to start a new thread on that, since your panel problem is sorted now.

---

### Post by Avinash.Rao on 2009-08-03
ok thanks :)

---

