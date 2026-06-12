---
title: "Can't watch embedded FLV movie in Ubuntu"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by G-Com on 2009-10-27
This is what I get:

[IMG]http://img43.imageshack.us/img43/5640/screenshotaec.jpg[/IMG]

Help...!

---

### Post by MelDJ on 2009-10-27
cant really see it. attach to your post instead of putting it in.

maybe you will find a solution here: [Firefox optimization and troubleshooting thread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by howefield on 2009-10-27
What happens when you press the grey play button, is that an error on the black screen behind ?

---

### Post by G-Com on 2009-10-27
> **howefield said:**
> What happens when you press the grey play button, is that an error on the black screen behind ?
Nothing.  It just alternately flashes "TEXT TEXT TEXT" and "PLAYLIST (7)"

---

### Post by G-Com on 2009-10-27
Here's an attached image:

---

### Post by philinux on 2009-10-27
Can you play flash on other sites?

Have you got flashblock on or adblock or noscript. Try turning these off.

---

### Post by wojox on 2009-10-27
This is from Loving Linux's Optimization thread:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

There maybe a conflict or you may need to upgrade Flash.

---

### Post by Dougie187 on 2009-10-27
> **wojox said:**
> This is from Loving Linux's Optimization thread:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

There maybe a conflict or you may need to upgrade Flash.

Instead of doing ```
sudo apt-get install flashplugin-nonfree
```

I would recommend doing ```
sudo apt-get install ubuntu-restricted-extras
```
This package is comprised of more things that will help later. Like codecs and java and stuff like that.

---

### Post by lovinglinux on 2009-10-27
> **wojox said:**
> This is from Loving Linux's Optimization thread:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

There maybe a conflict or you may need to upgrade Flash.

Yes, that's exactly the solution. The big PLAY button in the OP video screenshot means gnash is managing flash content, instead of flashplugin-nonfree.

---

### Post by G-Com on 2009-10-27
A big 

[SIZE=7]**THANK YOU! **[/SIZE]

to Dougie and lovinglinux.

That worked perfectly! :) :) :)

---

### Post by lovinglinux on 2009-10-27
> **G-Com said:**
> A big 

[SIZE=7]**THANK YOU! **[/SIZE]

to Dougie and lovinglinux.

That worked perfectly! :) :) :)

A big 

[SIZE=7]**YOU ARE WELCOME! **[/SIZE]

:lol:

---

