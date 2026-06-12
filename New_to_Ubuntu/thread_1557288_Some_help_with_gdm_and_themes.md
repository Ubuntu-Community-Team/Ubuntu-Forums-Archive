---
title: "Some help with gdm and themes"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-08-20
Hello all,
    I'm trying to install a new theme for gdm and am having the following problem:

When I try to intall "gdm-themes" from command line I get the following error - 
```
Package gdm-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gdm-themes has no installation candidate

```

What is the solution to this?

---

### Post by ubudog on 2010-08-20
Are all the software sources checked in "Software Sources"?

---

### Post by LowSky on 2010-08-20
woodsonoversoulare you still using 7.04 or have you upgraded to a newer (hopefully 10.04) release?


Side note

Ubuntu 10.04 has two packages with 'gdm-themes' in their names and they are ubuntume-gdm-themes and sabily-gdm-themes, I have no idea if they will do what your looking to do.

---

### Post by ubudog on 2010-08-20
Type:
```
apt-cache search gdm-themes
```
because maybe you typed the wrong package name.

---

### Post by woodsonoversoul on 2010-08-20
Great! Sweet, thanks; I got the sabily themes.

Now, when I try to run gdm from command line, I get:
```
** (gdm-binary:14211): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:14211): WARNING **: Could not acquire name; bailing out

```

Any idea what could be causing that, or an I going about this the wrong way?

---

### Post by woodsonoversoul on 2010-08-20
bump

---

### Post by ubudog on 2010-08-20
Did you try setting it with System>Preferences>Appearance?

---

