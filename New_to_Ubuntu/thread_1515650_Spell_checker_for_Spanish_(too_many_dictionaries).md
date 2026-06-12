---
title: "Spell checker for Spanish (too many dictionaries)"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Dangger on 2010-06-22
Hi all! I'm having a weird issue. When I install the spell checker for Spanish it installs like 20 dictionaries (for every Spanish speaking country in the world). 

This is problematic because I end up with a huge menu in Firefox and in Open Office. I have to switch frequently from Spanish to English and with so many options it's not very efficient. 

Is there a way to install just one dictionary?

---

### Post by lkjoel on 2010-06-22
What dictionary do you want?
Spain, Mexico etc...

---

### Post by hamoid on 2010-06-23
I have the same issue, but worse because I write in four languages.
There are so many entries that they don't fit in the screen, and they are not sorted which makes it even harder. Each time I want to switch between the different languages I have to scroll up and down and it takes forever. 

Isn't it possible to exactly define which languages are shown? I only need 4, not 42.

(see attachment)

---

### Post by Dangger on 2010-06-27
> **lkjoel said:**
> What dictionary do you want?
Spain, Mexico etc...

Any is fine, but just one.

---

### Post by Dangger on 2010-06-27
> **hamoid said:**
> I have the same issue, but worse because I write in four languages.
There are so many entries that they don't fit in the screen, and they are not sorted which makes it even harder. Each time I want to switch between the different languages I have to scroll up and down and it takes forever. 

Isn't it possible to exactly define which languages are shown? I only need 4, not 42.

(see attachment)

This is exactly the problem. I uninstalled the spanish dictionaries in synaptic and then installed the spanish spellchecker in FF add-ons. But the problem is that OO is now without spellcheking for Spanish.

---

### Post by lkjoel on 2010-06-27
Could you tell me what packages are installed?
Myspell etc...

---

### Post by Dangger on 2010-06-28
> **lkjoel said:**
> Could you tell me what packages are installed?
Myspell etc...

Hi, it's aspell-es or myspell-es. Both have a similar description:

> This is the Spanish dictionary for use with the myspell/aspell spellchecker.
It is based on ispell dictionary put together by
Santiago Rodriguez and Jesus Carretero.

So in summary it's a bunch of dictionaries in one. No matter which one you install you get a list of all the countries in the world that speak Spanish, both in Open Office and in FF. 

Thanks a lot for you help. I really appreciate it.

---

### Post by lkjoel on 2010-06-28
Try to compile it from source.
I have attached Myspell-es source package.

---

### Post by AstroLlama on 2010-07-07
I had this same problem except I had country specific entries for english, french, italian, spanish, and portuguese (yeah, i switch between languages quite a bit for work). 

I solved the issue by going into synaptic and removing country-specific entries for aspell.

---

### Post by Dangger on 2010-09-04
> **lkjoel said:**
> Try to compile it from source.
I have attached Myspell-es source package.

I appreciate your help but I don't have the time or expertise to do stuff like this. This is what frustrates me sometimes about linux...

---

### Post by atti84it on 2010-10-18
I just opened a new bug : [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/663032](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/663032)

let's see what they say..

---

### Post by lkjoel on 2010-10-19
> **atti84it said:**
> I just opened a new bug : [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/663032](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/663032)

let's see what they say..
Need more info on that link.
What myspell/hunspell packages do you have?
And what dictionaries do you want?

---

### Post by atti84it on 2010-10-19
Theese are the packages that are installed at the moment:
myspell-en-au  myspell-en-za  myspell-fr myspell-en-gb  myspell-es myspell-it

Each of them provides several dictionaries. I want only one of each language, it doesn't really matter which one, so this is just an example: English (UK), Spanish (Spain), French (France), Italian (Italy).

There's a similar discussion here: [http://ubuntuforums.org/showthread.php?p=9806282](http://ubuntuforums.org/showthread.php?p=9806282)

---

### Post by Dangger on 2010-10-19
Problem already solved though this is a bug I think. There were repeated links in:

```
/usr/lib/firefox-3.6.10/dictionaries
```

But there were two or more links to each dictionary thus effectively multiplying the options in the FF menu. You just have to delete the repeated links using sudo or accessing as root.

---

### Post by atti84it on 2010-10-20
Wonderful! It works!
although I found that the directory you told me is a symlink to ```
/usr/share/hunspell
```(I didn't even know that you could symlink directories..)

anyway I think that common users shouldn't need to become root and delete symlinks to change this trivial option!

---

