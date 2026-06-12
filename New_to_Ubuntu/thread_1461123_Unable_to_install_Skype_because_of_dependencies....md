---
title: "Unable to install Skype because of dependencies...But already installed?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by FusionAura on 2010-04-23
Hi,

I have already installed the required depenencies, however somehow to deb manager still says its not installed...Any help?

[IMG]http://i44.tinypic.com/24zy9ld.png[/IMG]

---

### Post by FusionAura on 2010-04-23
Any help?

---

### Post by jaco223 on 2010-04-23
> **FusionAura said:**
> Any help?

Did you check to see if skype is indeed already installed?
Open a terminal and type

```
whereis skype
```

---

### Post by FusionAura on 2010-04-24
Gives me a 

skype:

---

### Post by ddecator on 2010-04-24
Skype works for me, but I have libasound2 installed. If you try to install libasound2, what happens? Trying to install it via Synaptic may show you that it conflicts with other packages you have installed.

---

### Post by jaco223 on 2010-04-24
> **FusionAura said:**
> Gives me a 

skype:

I searched around and found this:

[http://ubuntuforums.org/showthread.php?t=679953&highlight=libasound2](http://ubuntuforums.org/showthread.php?t=679953&highlight=libasound2)

Look at post #4.

Did you download the skype installer from here:

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

Maybe this will help you get skype installed.


Jaco

---

### Post by HermanAB on 2010-04-24
Howdy,

Note that you can always download the 'static' version of Skype from their web site, put it anywhere in your home directory (/usr/local/bin is best actually) and run it.  It has no dependencies, so it 'Just Works'.

---

