---
title: "Adjusting laptop brightness?"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-06-03
Hi all

I have just received my Dell Inspiron notebook, wiped the hard drive and installed Lucid Lynx 64-bit in order to force myself to learn Linux.

I was impressed with how much ran completely out of the box, but one issue I am having is with the brightness of the screen.  It's clearly not as bright as it should be, and while hitting the 'brightness up/down' keys on the keyboard *does* bring a little display which suggests it recognises the commands, nothing is changing and I'm basically given the option of "dark" and "only very slightly less dark" -- neither of which actually make a difference.

I'm entirely happy with keeping this screen on 100% brightness all the time.  

Would any clever Linux pros be able to offer me some advice on how to do this?

---

### Post by sanderd17 on 2010-06-03
Can you go to system -> preferences -> energy... ? EDIT: Do what the post beneath here says. I use the dutch version so I don't know the exact english names.


there you have a brightness setting.

Otherwise, maybe you could install compiz config settings manager (ccsm), but that would be a bit of overkill to just get the screen brighter

PS. welcome to Ubuntu

---

### Post by formaldehyde_spoon on 2010-06-03
Not sure, but check Power Management in System > Preferences, and you can also right-click a panel > Add > Brightness App.

---

### Post by danielgrosvenor on 2010-06-03
I've already had a look in Power Management and had no success there.  However when I opened Synaptics Package Manager and typed 'brightness' I noticed something interesting:

It came up with a package called 'smartdimmer: change LCD brightness on Geforce cards" which appeared to already be installed.  I marked it for Re-Installation and received the following error:

[B]E: lib32nss-mdns: subprocess installed post-installation script returned error exit status 2
E: wine1.2: dependency problems - leaving unconfigured[/B]

---

### Post by sanderd17 on 2010-06-03
Didn't you get any 
```

run apt-get reconfigure to...

```
message?

---

### Post by danielgrosvenor on 2010-06-03
> **sanderd17 said:**
> Didn't you get any 
```

run apt-get reconfigure to...

```message?

I did not.

---

### Post by bodhi.zazen on 2010-06-03
Often on laptops there is a hardware key as well. Something like Fn -F4 , usually in purple.

Otherwise, try adjusting your ssettings with gnome-power-manager (you may need to install gnome-popwer-manager) and in your screensaver.

---

### Post by walkerchuckwalker on 2010-06-03
You can also try Fn key + up and down arrows for temporary adjustments (easy and quick), hope thats helpful.

---

### Post by danielgrosvenor on 2010-06-03
No luck yet unfortunately, but thanks for all your suggestions.

I'm currently trying to flash to the latest BIOS [(here's the thread if anyone can offer advice)]("http://ubuntuforums.org/showthread.php?t=1501007").  If that doesn't work, I'll hunt down Gnome-Power-Manager and give that a whirl. :-k

---

### Post by thepisu on 2010-06-05
This seems to be a bug (or a missing feature) of Lucid Lynx. Many users that upgraded from 9.10 to 10.04, losed the ability to change brightness, either automatically (when in battery mode), or manually with FN buttons.

I have a Sony Vaio VGN-FW31E, and have the same problems... 

I think it's related to some laptop-management package that has been removed in Lucid.

---

### Post by nogoodreason on 2010-06-05
> **thepisu said:**
> This seems to be a bug (or a missing feature) of Lucid Lynx. Many users that upgraded from 9.10 to 10.04, losed the ability to change brightness, either automatically (when in battery mode), or manually with FN buttons.

I have a Sony Vaio VGN-FW31E, and have the same problems... 

I think it's related to some laptop-management package that has been removed in Lucid.

Damn. Will I have to go through the hassle of downloading and burning a Karmic Koala .iso, or is there some "downgrade" option I can do via Terminal?

Thanks for your post. I think Lucid Lynx is great, but it's definitely not as polished as it could be.

---

