---
title: "Trying to install madfuload, not in repositories"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-15
(SOLVED)
In order to get my M-audio Ozone working in Studio, I must install(?) "madfuload".  I've been able to download it, and put it in my home folder.  However, when I try to write the command:

sudo apt-get install madfuload

madfuload is not found (this was a suggested method from a forum member)

When I'm in the middle of the procedures I was originally following to get Ozone recognized, at some point I am told to type:

sudo tar xvfz <madfuload archive file>

 I get this error message:

-bash: syntax error near unexpected token 'new line'

Also, it's possible that things have changed since the instructions I'm following were written.  The last version was Gutsy in the Forum post, and I am using Hardy.  Does anyone know where I can get madfuload onto my computer, or how after downloading something, it can be installed?  I would have thought a "simple":
sudo apt-get install madfuload 
would do it.  It has not.

please help, thanks in advance

---

### Post by zvacet on 2009-02-15
I don´ know it this will help you,but try t odownload it from [here.]("http://mirror.unmul.ac.id/ubuntu/pool/multiverse/m/madfuload/")

---

### Post by kk0sse54 on 2009-02-15
sudo apt-get install won't work because it's not in the repos. instead download it like you have and then extract it into whatever folder you want. From there you'll probably have to compile it by hand which usually involves four command
```

cd <folder name>
./configure 
make  
sudo make install
``` However I suggest you first look within the extracted folder and attempt to find a README file which will most likely have installation instructions in case there's already an executable or build script available.

Edit: Just followed zvacet link and there seems to be a deb available. Just download that and open it with the deb installer. At a second look it does seem to appear in the repo but you don't have multiverse repo enabled.

---

