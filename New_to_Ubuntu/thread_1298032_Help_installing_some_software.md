---
title: "Help installing some software"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by timmyhiggy on 2009-10-22
Hi

Im having trouble installing some software i downloaded.

installation instructions are as follows:
> The tar file will unzip into a star-nanahope/ directory in the directory you downloaded the tar file to. This release can be placed anywhere. When using the software, set the STARLINK_DIR environment variable to the location of the star-nanahope/ directory, i.e. if I had unzipped it into a /home/bradc/software directory, then the STARLINK_DIR environment variable would be set to /home/bradc/software/star-nanahope. 

On some systems you may need the libg2c.so library. On Fedora Core (and presumably all Red Hat-derivative systems) this can be found in the compat-gcc-32 RPM. On Ubuntu (and presumably all Debian-derivative systems) this can be found in the libg2c0 package. 

The 64-bit release requires glibc 2.5 and fairly recent versions of the X11 libraries (7.1 or higher). An up-to-date Gentoo, Fedora Core 6, or SUSE 10.1 are distributions that are known to work.

I have unzipped it to /home/tim/programs/star-nanahope but im having trouble setting environment variables. All the online tutorials say 
"just type CODE=$/home/tim/Documents"
or whatever to get a new environment variable with a value of the path to documents, but when i do that then cd to it I get an error of:

tim@netbook:~$ cd $CODE
bash: cd: $/home/tim/Documents: No such file or directory

and it's not there when i type env either. any pointers would be very welcome!

---

### Post by LewRockwell on 2009-10-22
[https://help.ubuntu.com/community/Starlink](https://help.ubuntu.com/community/Starlink)

.

---

### Post by timmyhiggy on 2009-10-22
LewRockwell you have no idea how grateful iam!

Any ideas how i could add a launcher into the applications menu at the top?
i tried preferences --> main menu and then adding a new item within a category where the command input (third option down) says "gaia" (my understanding was that you should put whatever you would type into the terminal here) but it never launches it. is it only launchable from the command line?

---

### Post by a7j_72 on 2009-10-22
It should be as simple as clicking "browse" and finding the file.

---

### Post by timmyhiggy on 2009-10-22
OK after a bit of experimentation i found that .sh is a launcher! now got the launcher working.

I know this sounds really pathetic but what formats are accepted as icons for the launcher or the "physics" category i want it to go in? all the formats i try never appear when i look for the replacement icon...

---

### Post by a7j_72 on 2009-10-22
let me know if this helps... 
[http://ubuntuforums.org/showthread.php?t=1294113&highlight=file+icons](http://ubuntuforums.org/showthread.php?t=1294113&highlight=file+icons)
(fourth to-oldest post)

---

### Post by timmyhiggy on 2009-10-22
That didn't work sadly, and i dont think its worth the time i could potentially put in just to change the logo!! I think ill call it a day here but that you both very much!

---

### Post by timmyhiggy on 2009-10-22
by complete fluke i found that if you just save the pic you want into your home directory then you can just type the path in the address bar for the image change, and rather than crashing it actually looks it up for you, allowing you to change it!

---

### Post by a7j_72 on 2009-10-23
> **timmyhiggy said:**
> by complete fluke i found that if you just save the pic you want into your home directory then you can just type the path in the address bar for the image change, and rather than crashing it actually looks it up for you, allowing you to change it!

Awesome , thanks for posting.

---

