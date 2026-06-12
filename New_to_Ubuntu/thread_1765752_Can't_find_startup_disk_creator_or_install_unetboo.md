---
title: "Can't find startup disk creator or install unetbootin"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Tetenterre on 2011-05-23
I am running v9.04 (netbook remix) on an Advent 4211 (rebadged MSI Wind). I am trying to install v10.4. I have downloaded ubuntu-10.04.2-desktop-i386.iso. Then I hit the problems:

* When I right-click the ISO file, "Write to Disk" is not an option in the menu (as per instructions on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)).

* When I try the USB option, I find that there is no Startup Disk Creator in the Administration menu.

* I downloaded unetbootin; the file arrived as unetbootin-linux-549 -- Ubuntu seems to think that it is a Windows file as it tries (unsuccessfully) to open it with WINE. I tried forcing it to open with Archive manager, but that won't do it either.

Grateful for any help, please.

Thanks in advance...

---

### Post by TeoBigusGeekus on 2011-05-23
Put an empty cd in the tray and try this
```
wodim -v dev=/dev/cd /path/ubuntu-10.04.2-desktop-i386.iso
```
If that doesn't work, replace cd with cdrw, sr0, etc.

---

### Post by eltonw on 2011-05-23
> **Tetenterre said:**
> I am running v9.04 (netbook remix) on an Advent 4211 (rebadged MSI Wind). I am trying to install v10.4. I have downloaded ubuntu-10.04.2-desktop-i386.iso. Then I hit the problems:

* When I right-click the ISO file, "Write to Disk" is not an option in the menu (as per instructions on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)).

* When I try the USB option, I find that there is no Startup Disk Creator in the Administration menu.

* I downloaded unetbootin; the file arrived as unetbootin-linux-549 -- Ubuntu seems to think that it is a Windows file as it tries (unsuccessfully) to open it with WINE. I tried forcing it to open with Archive manager, but that won't do it either.

Grateful for any help, please.

Thanks in advance...

It is possible that your download of UNetbootin was corrupted: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")
Since you are running ubuntu, it should be a simple matter to install UNetbootin using **synaptic** which is already on your system, and UNetbootin would be in your list of available packages

---

### Post by Tetenterre on 2011-05-23
Trying TeoBigusGeekus's fix now -- CD is burning...

> **eltonw said:**
> It is possible that your download of UNetbootin was corrupted: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Yup, that's the one I tried.

> 
Since you are running ubuntu, it should be 
a simple matter to install UNetbootin using **synaptic** which is already on your system, and UNetbootin would be in your list of available packages

Sorry, should have mentioned that I tried to get UNetbootin via synaptic and terminal -- both give 

```
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?
```

and 

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb
  404 Not Found
```

..and then fail to install UNetbootin.

---

### Post by beew on 2011-05-23
> **Tetenterre said:**
> Trying TeoBigusGeekus's fix now -- CD is burning...



Yup, that's the one I tried.



Sorry, should have mentioned that I tried to get UNetbootin via synaptic and terminal -- both give 

```
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?
```and 

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb
  404 Not Found
```..and then fail to install UNetbootin.

That is because 9.04 has long passed its end of life so its repositories are dead.  You would have to install programs manually.

The Linux version of Unetbootin is a .bin file. So you download it to your desktop, say then right click it to change permission to executable, then go to the terminal and run
```
cd Desktop
  sudo ./name_of_bin_file.bin

```

---

### Post by Tetenterre on 2011-05-23
> **TeoBigusGeekus said:**
> Put an empty cd in the tray and try this
```
wodim -v dev=/dev/cd /path/ubuntu-10.04.2-desktop-i386.iso
```
If that doesn't work, replace cd with cdrw, sr0, etc.

scd0 did it.

Thank you -- this is being posted from v10.4 .

---

### Post by TeoBigusGeekus on 2011-05-23
Glad to hear you've made it!
Don't forget to mark the thread as solved.

---

### Post by eltonw on 2011-05-23
> **Tetenterre said:**
> Trying TeoBigusGeekus's fix now -- CD is burning...



Yup, that's the one I tried.



Sorry, should have mentioned that I tried to get UNetbootin via synaptic and terminal -- both give 

```
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?
```

and 

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb
  404 Not Found
```

..and then fail to install UNetbootin.
You may need to add the PPA to your system. See HERE:[https://launchpad.net/~gezakovacs/+archive/ppa]("https://launchpad.net/~gezakovacs/+archive/ppa")

---

