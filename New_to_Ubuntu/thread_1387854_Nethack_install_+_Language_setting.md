---
title: "Nethack install + Language setting"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-01-22
Okay, so I wanted to get Nethack rolling. I downloaded both packages, I know you only need one, and then went to unzip them, and did "sudo apt-get install nethack". All the reply is that: Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Pakket nethack is een virtueel pakket voorzien door:
  nethack-x11 3.4.3-10.6ubuntu2
   nethack-qt 3.4.3-10.6ubuntu2
   nethack-lisp 3.4.3-10.6ubuntu2
   nethack-console 3.4.3-10.6ubuntu2
U dient er één expliciet te selecteren voor installatie.
E: Pakket nethack heeft geen installeerbare kandidaat

"Source of requirements being built
Status info read...done
Package Nethack is a virtual package provided by: 
  nethack-x11 3.4.3-10.6ubuntu2
  nethack-qt 3.4.3-10.6ubuntu2
  nethack-lisp 3.4.3-10.6ubuntu2
  nethack-console 3.4.3-10.6ubuntu2
You must choose one specifically for install
E: Package nethack has no installable candidate"

And does anyone know how to put Ubuntu in English FULLY?

---

### Post by Mornedhel on 2010-01-22
> **Alex De Duck said:**
> Okay, so I wanted to get Nethack rolling. I downloaded both packages, I know you only need one, and then went to unzip them, and did "sudo apt-get install nethack".

I don't really get your meaning... What exactly did you download and unzip ? apt-get install already downloads the packages from the repositories.

Pick one of nethack-x11, nethack-qt or nethack-console (for respectively the graphical version, the graphical version with Qt controls for KDE, and the old-fashioned text-only version), and sudo apt-get install that. The "nethack" package is not meant to install anything, it's there to ensure that anything that requires the nethack functionality can depend on "nethack" instead of "nethack-x11 or nethack-qt or...".

---

### Post by Alex De Duck on 2010-01-22
Oooh... My bad. I thought you had to install it, and that the sudo command installed it. 

Sudo apt get install still doesn't do the trick though, so how do I pick one of those packages?

---

### Post by Mornedhel on 2010-01-22
> **Alex De Duck said:**
> Oooh... My bad. I thought you had to install it, and that the sudo command installed it. 

Sudo apt get install still doesn't do the trick though, so how do I pick one of those packages?

Well, if you want to install the console version, you just

```
sudo apt-get install nethack-console
```

If you want the graphical version, you do instead

```
sudo apt-get install nethack-x11
```

Then, assuming you're connected to the Internet, it should download, unpack, and install the corresponding version of NetHack.

Alternatively, you could open the Synaptic package manager (System > Administration > Synaptic Package Manager), scroll to the correct package, check it for installation and apply.

---

### Post by Alex De Duck on 2010-01-22
Thanks!

---

