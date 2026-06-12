---
title: "Problems installing Amazon MP3 Downloader"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by mameshiba on 2010-10-16
I tried to install this this morning as there's a new album release I really want to buy, but when I try and install it the Package Installer comes up with this message:

> **[COLOR="Red"]Error: Dependency is not satisfiable: libboost-filesystem1.34.1[/COLOR]**


I went into Synaptic to see if this was in there, but it wasn't. However, I have got all of the things entitled 'libboost-filesystem[-]' installed.

Any and all help would be greatly appreciated!

---

### Post by Hippytaff on 2010-10-16
have you tried

```

sudo apt-get install [B][COLOR=Red][COLOR=black]libboost-filesystem1.34.1
[/COLOR][/COLOR][/B]
```[B][COLOR=Red][COLOR=black]

in the terminal?

Also it might be worth trying

```

sudo apt-get update && sudo apt-get upgrade

```[/COLOR][/COLOR][/B]

---

### Post by mameshiba on 2010-10-16
Tried the first one and got this:

> E: Invalid operation install*libboost-filesystem1.34.1
 

I ran the other code in terminal; it stopped at

> Processing triggers for python-central ...

and I still can't install the downloader. Heh.

---

### Post by Hippytaff on 2010-10-16
try

```

sudo apt-get -f install

```

---

### Post by Hippytaff on 2010-10-16
What format is the downloader (not exe is it?)

---

### Post by mameshiba on 2010-10-16
Tried that code. This is what I got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


It's a .deb package.

---

### Post by Elfy on 2010-10-16
[http://wiki.ubuntuforums.org/showthread.php?p=9304460](http://wiki.ubuntuforums.org/showthread.php?p=9304460)

should do the job

---

### Post by Elfy on 2010-10-16
> **Hippytaff said:**
> try

```

sudo apt-get -f install

```

Do you know what this command is for? Nothing here suggesting that the --fix-broken option is needed for ;)

---

### Post by mameshiba on 2010-10-16
Thanks! That did it!

:guitar:

---

### Post by Hippytaff on 2010-10-16
> **forestpiskie said:**
> Do you know what this command is for? Nothing here suggesting that the --fix-broken option is needed for ;)

thought the missing dependency was fixable with it...I just learned something :-)

still new and eager to help other people enjoy ubuntu**embarrassed face**

---

### Post by Elfy on 2010-10-16
> **Hippytaff said:**
> thought the missing dependency was fixable with it...I just learned something :-)

still new and eager to help other people enjoy ubuntu**embarrassed face**

I guessed - carry on :D

Nothing to be embarassed about at all. 

A tip though is to use the manual pages for commands - you can get them in a terminal with 

```
man *command*
```

or online at [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

---

### Post by KB8NO on 2010-12-26
Thanks for the help.  Here is a simple way I devised for the terminal-syntax impaired to install Amazonmp3 in Ubuntu 10.10 using GUI and outlined in the attached doc file.

---

