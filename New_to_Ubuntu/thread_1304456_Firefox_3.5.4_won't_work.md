---
title: "Firefox 3.5.4 won't work"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by bookworm656 on 2009-10-29
I installed Firefox 3.5.4 using Ubuntuzilla (following the guide on this page: [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)), and it was working fine for awhile, but now it's not working. When I try to click the icon nothing happens, and when I try to start it from the Terminal I get this message:

```
/opt/firefox/firefox-bin: error while loading shared libraries: /opt/firefox/libxul.so: invalid ELF header

```
Does anyone know why that might be happening?

---

### Post by phillw on 2009-10-29
> **bookworm656 said:**
> I installed Firefox 3.5.4 using Ubuntuzilla (following the guide on this page: [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)), and it was working fine for awhile, but now it's not working. When I try to click the icon nothing happens, and when I try to start it from the Terminal I get this message:

```
/opt/firefox/firefox-bin: error while loading shared libraries: /opt/firefox/libxul.so: invalid ELF header

```Does anyone know why that might be happening?

Hi, the font of all things FireFox is here ....

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

It is a well supported thread - If you don't see your problem listed - feel free to ask them !!

Regards,

Phill.

---

### Post by lovinglinux on 2009-10-29
> **phillw said:**
> Hi, the font of all things FireFox is here ....

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

It is a well supported thread - If you don't see your problem listed - feel free to ask them !!

Regards,

Phill.

Thanks for your comments about my tutorial. Unfortunately, I don't know what's going on.

You could try to open the default profile directly with this:

```
firefox -P "nameoftheprofile"
```

or try opening Firefox Profile Manager then create a new profile and start it:

```
firefox -P
```


If that doesn't help, try this:

```
ubuntuzilla.py -a remove -p firefox
```

then

```
ubuntuzilla.py -a install -p firefox
```

This will reinstall Firefox 3.5.4.

---

### Post by bookworm656 on 2009-10-29
I uninstalled and reinstalled Firefox the way you said to, and now it's working. Thanks! (It probably would have taken me awhile to figure out the uninstall/reinstall commands on my own, since I'm really new to Ubuntu.)

---

### Post by lovinglinux on 2009-10-29
> **bookworm656 said:**
> I uninstalled and reinstalled Firefox the way you said to, and now it's working. Thanks! (It probably would have taken me awhile to figure out the uninstall/reinstall commands on my own, since I'm really new to Ubuntu.)

You are welcome. Keep in mind that is the Ubuntuzilla way of uninstall/reinstall, which is different from the regular install/uninstall commands using apt-get.

---

