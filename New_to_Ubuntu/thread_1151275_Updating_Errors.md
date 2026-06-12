---
title: "Updating Errors"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2009-05-06
[FONT=Trebuchet MS][COLOR=Blue]I need some help figuring out these errors that are reported every time I try to update after upgrading to Jaunty[/COLOR][/FONT][FONT=Trebuchet MS][COLOR=Blue].

```
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)

```[/COLOR][/FONT]

---

### Post by _Purple_ on 2009-05-06
Can you post your /etc/apt/sources.list?

---

### Post by aktiwers on 2009-05-06
Type :
```
 sudo gedit /etc/apt/sources.list
```

in termail and find the place where it says:
>  [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages 2 times.

Then remove the to of them, leaving them there only 1 time each.

Then hit save and close the window.

Now back in terminal type:
```
sudo apt-get update
```And the problem should be fixed.

It seams like you accidentally put the sources in there 2 times

---

### Post by kindafunnylookin on 2009-05-06
> **aktiwers said:**
> Type :
```
 sudo gedit /etc/apt/sources.list[code]

in termail and find the place where it says:


2 times.

Then remove the to of them, leaving them there only 1 time each.

Then hit save and close the window.

Now back in terminal type:
[code]sudo apt-get update
```And the problem should be fixed.

It seams like you accidentally put the sources in there 2 times
That did the job. Thank you

---

