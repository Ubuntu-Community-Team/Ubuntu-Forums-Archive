---
title: "WUBI - Ubuntu and Xubuntu is it possible?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by rybaxs on 2009-04-13
is it possible to install two wubi in windows? 


thanks!

---

### Post by anjilslaire on 2009-04-13
No need. Install Ubuntu, then from within Ubuntu, just install the Xubuntu desktop environment:

From the terminal (Applications>Accessories>Terminal):
```

sudo apt-get install xubuntu-desktop

```

Then simply use the Session menu at the logon screen to select Gnome or XFCE as desired.

---

### Post by rybaxs on 2009-04-13
> **anjilslaire said:**
> No need. Install Ubuntu, then from within Ubuntu, just install the Xubuntu desktop environment:


I want is that, I have an WindowsOS, then I've installed Xubuntu using WUBI, and then I want to install Ubuntu again. So there will be 3 OS operating in the computer. Windows, Xubuntu(Qimo) using WUBI, Ubuntu(8.10)
using WUBI. but Ubuntu8.10 wubi wants to uninstall Xubuntu wubi.. does it make sense? sorry :(

thanks anjilslaire, greatly appreciated for the reply

---

### Post by lisati on 2009-04-13
Is one *ubuntu on Wubi, the other *ubuntu on regular dual-boot an option?

---

### Post by Didius Falco on 2009-04-14
> **rybaxs said:**
> . does it make sense? sorry 

Okay, I think I understand what you are asking.

You want to know if you can use Wubi to install Ubuntu inside Windows, then use Wubi to install Xubuntu, separately, inside Windows.

According to the Wubi Wiki:

> **How do I install multiple distros?**

 You can install your favorite distro from within Wubi (see the advanced settings) and then once you are in Ubuntu, you can install the other desktop environments as normal packages. Each desktop environment is available as a single package (e.g. kubuntu-desktop). You will not have to reboot to change the desktop, simply log-off and choose the desktop environment in the options at login. 

Here is a link to the Wubi Guide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by rybaxs on 2009-04-14
> **lisati said:**
> Is one *ubuntu on Wubi, the other *ubuntu on regular dual-boot an option?

*Ubuntu on Wubi, the other *Ubuntu is on Wubi also. But Wubi accepts only one *Ubuntu.

Thanks **lisati** :)

I'll try **Didius Falco** reply called Multiple Distro interesting.
mmmm. where can i find the settings, in the installation mode or in the OS? mmm. it was said that only the desktop package is multiplied.. mmmm

does XFCE, gnome desktop environment only the difference between *Ubuntu?
Its like am installing an Feudora and Hardy using Wubi. but Wubi only accepts one OS. i need the OS to be installed.

well.. thanks a lot my friend. I've just use the band-aid solution. hehehe :D to make it work.

---

### Post by Didius Falco on 2009-04-14
You can install the XFCE desktop environment and the KDE desktop environment from Synaptic (in the OS). For XFCE, do a search in Synaptic for "XFdesktop4".

Here is a good guide on how to install the different desktop managers. I recommend bookmarking it, as it contains a lot of information about not only this, but lots of other *ubuntu tips and guides.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Good luck!

---

