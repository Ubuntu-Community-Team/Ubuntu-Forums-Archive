---
title: "How to customize ttf-mscorefonts-installer to include custom dlddir"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by bhadotia on 2009-06-24
Please  read this carefully before replying.

My university blocks .exe from being downloaded so I downloaded all the .exe font file for installing msttcorefonts from sourceforge from internet cafe and transferred them to my computer.
Now how do I tell apt-get that the font .exe files are kept in a local directory so that it does not continue downloading them (without any success) and thus give errors as these:
```
403:Forbidden
```

---

### Post by Technoviking on 2009-06-24
> **bhadotia said:**
> Please  read this carefully before replying.

My university blocks .exe from being downloaded so I downloaded all the .exe font file for installing msttcorefonts from sourceforge from internet cafe and transferred them to my computer.
Now how do I tell apt-get that the font .exe files are kept in a local directory so that it does not continue downloading them (without any success) and thus give errors as these:
```
403:Forbidden
```
Couldn't you just apt-get install msttcorefonts at the Internet cafe?

The is a weird policy for a University to have, and unsecure since Windows patches are all .exe or .msi.

T-V

---

### Post by bhadotia on 2009-06-24
> **Technoviking said:**
> Couldn't you just apt-get install msttcorefonts at the Internet cafe?


Well Forgot to take my laptop with me there:D

> **Technoviking said:**
> 
The is a weird policy for a University to have, and unsecure since Windows patches are all .exe or .msi.

T-V

No, they exclude windows update servers from being blocked ;). But downloading other third party stuff on windows is a pain:(.

It really was a [pain]("http://ubuntuforums.org/showthread.php?t=1191756") getting these .exe files and now I will have to read tons of docs just to install these fonts unless someone here helps.

---

### Post by Technoviking on 2009-06-24
You can extract the fonts from the .exe files with cabextract 
To install
```
sudo apt-get installl cabextract
```
Command line usage.
```
cabextract [options] [-d dir] <cabinet file(s)>
```
ie 
```
cabextract arial.exe
```

Then make a directory called msttcorefonts in .fonts or /usr/share/fonts/truetype if you want the fonts system wide and copy all the .ttf files extracted to one of those directories.

Then refresh your font cache
```
sudo fc-cache -f
```

T-V

---

### Post by bhadotia on 2009-06-24
> **Technoviking said:**
> You can extract the fonts from the .exe files with cabextract 
To install
```
sudo apt-get installl cabextract
```
Command line usage.
```
cabextract [options] [-d dir] <cabinet file(s)>
```
ie 
```
cabextract arial.exe
```

Then make a directory called msttcorefonts in .fonts or /usr/share/fonts/truetype if you want the fonts system wide and copy all the .ttf files extracted to one of those directories.

Then refresh your font cache
```
sudo fc-cache -f
```

T-V


Technoviking, thanks for the reply but I already knew that hack.
But I was wondering how would I make ttf-mscorefonts-installer know that the fonts are already there in a local directory so that it does not download seperately. This way I will have the  msttcorefonts package installed from the repos and it will get updated automatically.

P.S.: i have already followed your instructions above and have the fonts in my /usr/share/fonts/truetype/msttcorefonts.

---

### Post by bhadotia on 2009-06-26
Alright downloaded the package from the internet cafe. By the way thanks for all the help ;)

---

