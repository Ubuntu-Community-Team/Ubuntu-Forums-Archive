---
title: "Wine Problem"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Kchymet on 2009-09-20
I tried to install wine, but I keep getting the following error while following the directions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb). I am running Kubuntu 9.04, and don't know too much about how it works. How would I go about installing wine?

Terminal Output:
kchymet@kchymet-laptop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
kchymet@kchymet-laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list
--2009-09-20 12:16:50--  [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list)
Resolving wine.budgetdedicated.com... 81.171.111.247, 81.171.111.247
Connecting to wine.budgetdedicated.com|81.171.111.247|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 192 [text/plain]
Saving to: `/etc/apt/sources.list.d/winehq.list'

100%[========================================================================>] 192         --.-K/s   in 0s

2009-09-20 12:16:51 (9.13 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [192/192]

kchymet@kchymet-laptop:~$ sudo apt-get update
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 54 in source list /etc/apt/sources.list
kchymet@kchymet-laptop:~$ sudo apt-get install wine
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by Bachstelze on 2009-09-20
You should have this on line 54 of your sources.list:

```
http://wine.budgetdedicated.com/apt
```

Delete that line.

---

### Post by Kchymet on 2009-09-20
> **Bachstelze said:**
> You should have this on line 54 of your sources.list:

```
http://wine.budgetdedicated.com/apt
```Delete that line.

How do I go about deleting that line?

---

### Post by themusicalduck on 2009-09-20
Type ```
sudo gedit /etc/apt/sources.list
``` into a terminal and find the line in the text file.

---

### Post by callumacrae on 2009-09-20
Open sources.lst as root, find that line and delete.

If you can't find it, search for it.

~Callum

---

### Post by Hosmion on 2009-09-20
Did you type in the long list of what you need to do or did you just :

```
sudo apt-get install wine
```

---

### Post by t0p on 2009-09-20
You need to open the file /etc/apt/sources.list in a text editor.  For example hit Alt+F2 and type into the box:

```
sudo gedit /etc/apt/sources.list
```

This opens up the file in text editor (gedit).  It should be pretty apparent what you need to do from here.

---

### Post by Kchymet on 2009-09-20
Ok, I got into the file, and found line 54, but it has much more than the short line mentioned above.

Line 54:
```
http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```

Do I delete the whole thing, or just "http://wine.budgetdedicated.com/apt"?

---

### Post by Bachstelze on 2009-09-20
> **Kchymet said:**
> Ok, I got into the file, and found line 54, but it has much more than the short line mentioned above.

Line 54:
```
http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```

Do I delete the whole thing, or just "http://wine.budgetdedicated.com/apt"?

Whole thing.

---

### Post by t0p on 2009-09-20
Is there any particular reason why you want to install the version of wine from winehq.org rather than the one in the repositories?  If there is no pressing need to have the latest version, you can install wine simply by opening a terminal and typing:

```
sudo apt-get install wine
```

---

### Post by Kchymet on 2009-09-20
I can't save sources.list now.

This is my error:
> The document could not be saved, as it was not possible to write to /etc/apt/sources.list.
  Check that you have write access to this file or that enough disk space is available.
I tried saving it, and creating a second file and dragging it into place. I have come to the conclusion that I don't have access to the file. How can I fix this?

---

### Post by Kchymet on 2009-09-20
Nevermind, I found why I didn't have access. Thanks for the help everyone.

---

