---
title: "Dial up modem gcc  install problems"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by Fittersman on 2006-08-21
tried to install these three things

gcc-3.4_3.4.4-6ubuntu8_i386.deb <--did not want to install gave me error message of some sort, cant remember it will get it if oyu need it

cpp-3.4_3.4.4-6ubuntu8_i386.deb <-- installed correctly

gcc-3.4-base_3.4.4-6ubuntu8_i386.deb <-- installed correctly

and when i type in ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc into the terminal it says permission denied

how do i get the first package to install and what do i need to change so i have the right permissoin?

---

### Post by croak77 on 2006-08-21
How did you install gcc-3.4? Trough apt?
```
sudo aptitude install gcc-3.4
```

As far as your symlink you need to do it as sudo.

---

### Post by Fittersman on 2006-08-21
i just installed them off the desktop by clicking on it and it said there was a problem in red typing and the button that says install package wasnt highlighted and i couldnt click it.

---

### Post by croak77 on 2006-08-21
What do you mean 'off the dekstop'? Did you manually download them or use apt-get,atpitude,adept, or synaptic? What was the error message?

What are you trying to compile? Have you installed the build-essential package? Do you specifically need gcc-3.4 or will gcc-4 do?

---

### Post by Fittersman on 2006-08-22
> What do you mean 'off the dekstop'?
i had the file that looks like a box on the desktop and i double clicked on it and tried installing it that way

> Did you manually download them or use apt-get,atpitude,adept, or synaptic?
i manually downloaded them, my dial-up doesnt work on ubuntu yet

> What was the error message?
hold on ill get it later and edit this post

> What are you trying to compile? Have you installed the build-essential package? Do you specifically need gcc-3.4 or will gcc-4 do?

I have no idea, im just trying to follow instructions from another post

---

### Post by croak77 on 2006-08-23
I don't think double-clicking on a .deb file will install it. You need to be root. If you open up a a terminal, type sudo dpkg -i /path/to/program.deb. You are going to need all the dependencies of the .deb you are installing. 

What modem do you have? Have you tried any Linux live-cd? Does you internet work with one of those?

What directions are you following?

---

### Post by Fittersman on 2006-08-24
well heres the guide i was following

[http://www.ubuntuforums.org/showthread.php?t=93852](http://www.ubuntuforums.org/showthread.php?t=93852)

i have a agere winmodem

and the dial up doesnt work with live cds.

what you want me to do with the dependencies once i type that into the terminal?

---

### Post by croak77 on 2006-08-24
Well I would try to follow this:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

