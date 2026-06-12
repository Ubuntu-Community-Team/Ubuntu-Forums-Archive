---
title: "Help with Linux Ubuntu &quot;E: dpkg was interrupted&quot;????"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Mountain Linux on 2009-01-09
I can't install anything from the instal/remove applications under applications or install any packages from Synaptic Package Manager. It says "E: dpkg was interrupted. You must manually run  dpgk --configure -a".

What does this mean? I tried to run it in Terminal but it wouldnt work. It sais something about a "superuser"...

Anyone Help?

---

### Post by snova on 2009-01-09
Applications -> Accessories -> Terminal

```
sudo dpkg --configure -a
```

sudo is necessary to run this program with administrator privileges.

---

### Post by Joeb454 on 2009-01-09
Moved to ABT :)

And as above, running ```
sudo dpkg --configure -a
``` from a terminal should fix that :)

---

### Post by abn91c on 2009-01-09
follow that command with ```
sudo apt-get -f install
```

---

### Post by Mountain Linux on 2009-01-09
Ok I got that, but I got another question.

How do I enable my desktop effects?
It says that I can't, not even the normal effects. What drivers should I download (if there is any)?

---

### Post by taurus on 2009-01-09
What kind of graphic card do you have?  Look in System -> Administration -> Hardware Drivers and see if your graphic card is on the list.  And if it is, then install a driver for it before you can run compiz.

---

### Post by Mountain Linux on 2009-01-09
I went to my drivers and it doesnt have anything there except for my linksys plugin network connection thing...
Isnt there an already installed graphics driver on my Acer already?

---

### Post by Mountain Linux on 2009-01-09
Oh great. I did that sudo dpkg install thing and now when I try to open my synaptic package center it says "unable to get exclusive look. This usually means that another package management application (like apt-get or aptitude) is already is running. Close that application first."

There aren't any applications running...Help on this?

---

### Post by taurus on 2009-01-09
Yes, there is already a driver for your graphic card but unfortunately, it's probably a generic driver, vesa, so if you want the 3D stuff, you have to get a card that supports it and you have to install a driver for it.

```
lspci | grep VGA
```

---

### Post by Mountain Linux on 2009-01-09
yOk so I did that and it said that I have that driver in my computer..Now what?

Oh and the thing is, the "Extra" graphics used to work earlier but why not now? I think I deleted somthing out of Synaptic Package Manager but don't know what... Any help?

---

### Post by taurus on 2009-01-09
If you have a card and a drive that support 3D, then go into System -> Preferences -> Appearance -> Visual Effects and pick either Normal: or Extra:.

---

