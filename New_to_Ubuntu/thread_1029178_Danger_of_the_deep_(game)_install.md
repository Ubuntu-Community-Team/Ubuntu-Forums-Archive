---
title: "Danger of the deep (game) install"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by marcgh on 2009-01-03
Now that I am able to do most of my work in Ubuntu I have to start thinking also about relaxing.

i have downloaded (from : [http://dangerdeep.sourceforge.net/download.html](http://dangerdeep.sourceforge.net/download.html)) the GNU/Linux (x86 & x86-64):- dangerdeep-0.3.0-linux-installer.bin

I was thinking install would start when I click on the .bin file but I got the following message : 

[http://ubuntuforums.org/attachment.php?attachmentid=98541&stc=1&d=1230979932](http://ubuntuforums.org/attachment.php?attachmentid=98541&stc=1&d=1230979932)

What did I did wrong?
Thanks in advance for any help

---

### Post by linux_tech on 2009-01-03
in terminal, type ```
ls
``` as needed to locate the dangerdeep-0.3.0-linux-installer.bin file

then cd to that directory
for example, if you downloaded to the desktop then type:
```
cd Desktop
```

then type:

```
chmod +x dangerdeep-0.3.0-linux-installer.bin
```
next type:
```
 ./dangerdeep-0.3.0-linux-installer.bin
```
and then install should begin

---

### Post by marcgh on 2009-01-03
Thanks, Linux_tech.
Problem solved.
Happy new year!

---

### Post by marcgh on 2009-01-03
Sorry to bother again.
I think install ( following above instructions) went well.
But when I click on the created desktop icon...thats what I get.

---

### Post by ChristopherDante on 2009-01-30
Yeah - that's as far as I got as well.
Looks to me like root owns everything and I don't see a way of getting around this issue.

..darn...!

---

### Post by abasel on 2009-02-13
My install seems to go well but no shortcut is created so can't work where to find or run the install

---

### Post by abasel on 2009-02-13
Ok so I found the shortcut but it doesn't run

---

### Post by RomeReactor on 2009-02-13
Hi. Did you install Danger From The Deep using sudo, or as a regular user? Is your Ubuntu installation 32 bit or 64? If you're unsure about this last part, run the following from a terminal:
```
uname -m
```
If it returns **x86_64**, you have Ubuntu 64 bit, in which case the executable should be **dangerdeep_x86-64**; otherwise, you have Ubuntu 32 bit, and the executable is just **dangerdeep**. Run the executable from the terminal, and post any errors you get there.

If the error you get is "command not found", run this for Ubuntu 32 bit:
```
sudo updatedb; locate dangerdeep
```
or, for Ubuntu 64 bit:
```
sudo updatedb; locate dangerdeep_x86-64
```
When the executable shows up, run it in the terminal using the complete path, and again, if you get errors, please post them.

---

### Post by pro-guide on 2009-02-14
This is the error I get when trying to run danger from the deep.


 $ /usr/games/dangerdeep_x86-64
/usr/games/dangerdeep_x86-64: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by RomeReactor on 2009-02-14
> **pro-guide said:**
> This is the error I get when trying to run danger from the deep.


 $ /usr/games/dangerdeep_x86-64
/usr/games/dangerdeep_x86-64: error while loading shared libraries: **libSDL_image-1.2**.so.0: cannot open shared object file: No such file or directory

Install libsdl-image1.2:
```
sudo aptitude install libsdl-image1.2
```

---

### Post by pro-guide on 2009-02-21
Thanks! :popcorn:

---

