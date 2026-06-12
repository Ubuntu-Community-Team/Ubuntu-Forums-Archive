---
title: "Why can't I get flash player plugin installed?"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by diapaman on 2011-08-31
i have tried installing it on firefox, chromium & chrome with no luck at all.

---

### Post by zealibib slaughter on 2011-08-31
Try this: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by donkyhotay on 2011-08-31
First of all before you do anything with the script that was suggested before I'd ask exactly *how* have you been trying to install the flash player. Most of the time installing straight from the repos works, don't try to download the file from the adobe website (which is a bad habit people pick up on other OS's).

---

### Post by diapaman on 2011-08-31
I tried downloading the .so file, but can't find which folder to put it in.

---

### Post by Vaphell on 2011-08-31
you can try
/usr/lib/mozilla/plugins/libflashplayer.so

either way check repository version first or if you really want 64bit version of flash - flash-aid addon for firefox which will do all the legwork for you.

---

### Post by Alwimo on 2011-08-31
I didn't think you would need to get a plugin if you use Chrome. I thought it comes with it.

---

### Post by donkyhotay on 2011-08-31
The easiest way to install flash is to simply load up the software center, do a search for flash, then select 'adobe flash plugin'. The easiest way to install anything in ubuntu is from the repos and the flash player is in the repos. As I mentioned before downloading files off the web from random sites is a habit people get into using windows however 99% of all the software you'll ever need is in the repos and installing from the repos is a matter of selecting it from the list and click install. If you have issues with the software center then launch up the CLI (terminal) and copy/paste the following.

```

sudo apt-get install flashplugin-nonfree

```

if that doesn't work then try the flash-aid script mentioned previously but that should be your *last* option not the first.

---

### Post by diapaman on 2011-08-31
It tells me... permission denied

---

### Post by donkyhotay on 2011-08-31
> **diapaman said:**
> It tells me... permission denied

permission denied... when you do what exactly?

---

### Post by diapaman on 2011-08-31
when i try to copy this file, libflashplayer.so, to this folder, /usr/lib/mozilla/plugins

---

### Post by beew on 2011-08-31
> **donkyhotay said:**
> if that doesn't work then try the flash-aid script mentioned previously but that should be your *last* option not the first.

Why the last? I very much recommend flash-aid over installing from the repository, it doesn't just install flash, but also clear up conflicting flash versions and optimizes it.

---

### Post by beew on 2011-08-31
> **diapaman said:**
> when i try to copy this file, libflashplayer.so, to this folder, /usr/lib/mozilla/plugins

You forget sudo. If you want to access /usr/lib you need root privilege. Anyhow, why do you insist on installing flash like this? It doesn't get updated if you install it manually. Just use flash-aid.

---

### Post by donkyhotay on 2011-09-01
> **beew said:**
> Why the last? I very much recommend flash-aid over installing from the repository, it doesn't just install flash, but also clear up conflicting flash versions and optimizes it.

For the beginning user the repos are easy to use and generally don't conflict (unless of course you add more repos which is a whole other issue). They're also the best way to install other software for future reference as well.

---

