---
title: "Problem editing /etc/default/grub; trying to change default boot"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-25
This is a problem I'm having on a friends computer as well as my own after upgrading to 11.04.

I used to use StartupManager to made changes to the default OS to select when booting the computer, but now when I run it it shows me a lot more entries for old kernels that I don't see listed in grub when I actually boot.  It's almost like it's accessing some other/older version of grub instead of the new one.  So I decided to see about manually editing grubs configuration to get the results I need.

According to the Grub community documentation, you have to edit /etc/default/grub and look closely at the GRUB_DEFAULT=0 paremeter, and zero simply means "the first thing in the list", which by default is the most recent kernel.  When I went to open up his grub file, this number said something like 27, not 0.  I thought, "Does it think 27 is zero?  How can it even put that number in when there is only like... 7 lines in the menu?"  I didn't get into experimenting with this much but changing this number didn't seem to have an effect on the grub menu.

I have the same problem on my own computer (though I've not yet checked to see what number it has under the default option.

Anybody else encounter this problem?

---

### Post by sandyd on 2011-05-25
> **diablo75 said:**
> This is a problem I'm having on a friends computer as well as my own after upgrading to 11.04.

I used to use StartupManager to made changes to the default OS to select when booting the computer, but now when I run it it shows me a lot more entries for old kernels that I don't see listed in grub when I actually boot.  It's almost like it's accessing some other/older version of grub instead of the new one.  So I decided to see about manually editing grubs configuration to get the results I need.

According to the Grub community documentation, you have to edit /etc/default/grub and look closely at the GRUB_DEFAULT=0 paremeter, and zero simply means "the first thing in the list", which by default is the most recent kernel.  When I went to open up his grub file, this number said something like 27, not 0.  I thought, "Does it think 27 is zero?  How can it even put that number in when there is only like... 7 lines in the menu?"  I didn't get into experimenting with this much but changing this number didn't seem to have an effect on the grub menu.

I have the same problem on my own computer (though I've not yet checked to see what number it has under the default option.

Anybody else encounter this problem?
try
```

sudo dpkg-reconfigure [package-name]

```

I don't remember the package name for grub. I think it was grub-common/grub-pc

---

### Post by Hedgehog1 on 2011-05-26
The new version of grub carried with Natty no longer stores the default in the same way (and I don't know that StartupManager has been updated to be natty compatible for this option yet)

In any case, if you want to have Windows appear on the top of the Grub menu, you can do this:

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

followed by:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by diablo75 on 2011-05-27
> **Hedgehog1 said:**
> The new version of grub carried with Natty no longer stores the default in the same way (and I don't know that StartupManager has been updated to be natty compatible for this option yet)

This is why Linux is not mainstream.  That's all I'm gonna say and need to say.

---

### Post by bolucpap on 2011-05-27
Well, Windows is mainstream, but try configuring it to boot Linux or some other non-Microsoft OS as default. As far as I can recall, it's not possible.

---

### Post by Hedgehog1 on 2011-05-27
> **diablo75 said:**
> This is why Linux is not mainstream.  That's all I'm gonna say and need to say.

Your install was dual booting before you asked how to customize the new release, yes?

Things change between OS releases (that is why we upgrade :D ).  Happens in Windows, too.

In any case, did this correct your boot menu order?

***The Hedge***

:KS

---

### Post by mike_f on 2011-05-29
> **diablo75 said:**
> .. snip ..

I used to use StartupManager 

StartupManager is ludicrously limited in functionality and, unfortunately, the Ubuntu and GNOME 'teams' have been giving little priority to end user customization *cough*gdm*unity*cough* of late.

**BTW the maintainer of SUM has announced this month that he is abandoning this project** ([see link]("https://launchpad.net/startup-manager/+announcement/8300")).

Fortunately, [another developer]("https://launchpad.net/~danielrichter2007") has come to the rescue with '[Grub Customizer]("https://launchpad.net/grub-customizer")'. I really hope that the Ubuntu team will support him and make this a supported Debian package. THANK YOU, MR. RICHTER!!

The package is not in the regular repositories - add this PPA per the instructions on this page ([link here]("http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html")). Good luck!

---

### Post by diablo75 on 2011-05-29
> **mike_f said:**
> StartupManager is ludicrously limited in functionality and, unfortunately, the Ubuntu and GNOME 'teams' have been giving little priority to end user customization *cough*gdm*unity*cough* of late.

**BTW the maintainer of SUM has announced this month that he is abandoning this project** ([see link]("https://launchpad.net/startup-manager/+announcement/8300")).

Fortunately, [another developer]("https://launchpad.net/~danielrichter2007") has come to the rescue with '[Grub Customizer]("https://launchpad.net/grub-customizer")'. I really hope that the Ubuntu team will support him and make this a supported Debian package. THANK YOU, MR. RICHTER!!

The package is not in the regular repositories - add this PPA per the instructions on this page ([link here]("http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html")). Good luck!

I've installed Grub Customizer... but I'm not exactly sure how to use it...

---

### Post by diablo75 on 2011-05-30
I managed to get the app figured out.  Basically you want to click to highlight the "os-prober" line and then click the up arrow at the top to push that category to the top of the list.  Then click save.

Problem solved!!!  Thanks a ton for the help everyone!

(P.S., I've attached two screenshots for visual aid, but the numbering of them are backwards so ignore the file names; it's pretty obvious what you have to do).

---

