---
title: "How to install file with BIN extension?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by locodog on 2010-05-12
I've downloaded Google Earth, and it's *.bin file, there is not application associated with it, so how do I install programs like this?

---

### Post by adam22 on 2010-05-12
Very simple.

Step 1. Open Terminal (Applications>Accessories>Terminal)

Step 2. Navigate via terminal to directory the .bin file is in. I will use the Desktop...

```
cd Desktop
```Step 3. type "ls" into terminal (that is an L) and hit enter.

Step 4. Type this into terminal and hit enter

```
sudo chmod +X GoogleEarthLinux.bin
```Step 5. Type this into terminal and hit enter

```
./GoogleEarthLinux.bin
```Step 6. Run through the graphical installer that appears

Step 7. Right click the .desktop file and check the box to allow it to execute as a program, now you should have an icon for the program on your desktop.

Step 8. Enjoy.

---

### Post by bodhi.zazen on 2010-05-12
Depends on the application, typically you open a terminal and ..

```
chmod a+x file.BIN
sudo ./file.BIN
```

I advise you install Google earth from the repos

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

