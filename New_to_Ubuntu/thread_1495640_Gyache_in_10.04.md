---
title: "Gyache in 10.04"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by | Gnome | on 2010-05-28
Can anyone here tell me how to install Gyache in Ubuntu 10.04?
I had installed it in 9.04 successfully.
But can't in 10.04. I searched everywhere but didn't find.
Thanks

---

### Post by Nick_Jinn on 2010-05-29
Yes, I would like to know as well.



And seriously, somebody needs to figure out a 'protocal' or whatever the proper terminology is to make this advice backwards compatible....It shouldnt be that with every release every help topic that already exists becomes worthless again (to noobs anyway, the people who need them most).


Cant there be some stable repository that doesnt change with each new release?

I might be talking out of my *** again, since I am no coder or developer, but one of these days there needs to be a work around  for this besides expecting everyone to immediately already know what the terminal commands mean and how to edit them for each new distro.

---

### Post by BlackGrapes on 2010-06-02
I too need this.

---

### Post by nhasian on 2010-06-02
The latest version of Gyache is 1.2.6 and was released march 4th.

you will have to download the sourcecode and compile it yourself from here:

[http://sourceforge.net/projects/gyachi/files/gyachi/](http://sourceforge.net/projects/gyachi/files/gyachi/)

---

### Post by | Gnome | on 2010-06-03
^^
Compile?
How? Anyone please explain!

---

### Post by TenPlus1 on 2010-06-03
get the .deb files from here and install by double-clicking...

[http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi](http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi)

---

### Post by nhasian on 2010-06-03
hey i found a PPA for you.

    ```
sudo add-apt-repository ppa:loell/ppa
```

    ```
sudo apt-get update && sudo apt-get install gyachi
```

i still think it is better to compile yourself to get the latest version though.  more info on how to compile is [here]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by | Gnome | on 2010-06-04
Thanks nhasian!

Ok, I downloaded the source code and untarred it.
Then I also installed automake.
I saw the install.txt file and it said to run ./autogen.sh first.
So did I.
But it shows following.

```
searching for GNU gettext intl directory...
 -> /usr/share/gettext/intl ... no
 -> /usr/local/share/gettext/intl ... no
 -> /opt/share/gettext/intl ... no
 -> /usr/gettext/intl ... no
 -> /usr/local/gettext/intl ... no
 -> /opt/gettext/intl ... no
 -> /usr/gnu/share/gettext/intl ... no
 -> /opt/local/gettext/intl ... no
 -> /opt/local/share/gettext/intl ... no
ERROR: Cannot find gettext/intl directory.
ERROR: Install GNU gettext and gettext-devel in /usr or /usr/local prefix.
```

I have no clue what to do
Please suggest.

---

### Post by Linuxforall on 2010-06-04
For 10.04 loell ppa won't work, you need latest ppa from Darwin Bautista at [https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa)

---

### Post by nhasian on 2010-06-04
thanks Linuxforall i didn't see that.  looks like he's got the most recent version too so no need to compile it yourself then :KS

---

### Post by BlackGrapes on 2010-06-05
^^ Yup! that worked! No need of compilation.
Thanks Linuxforall!

---

### Post by | Gnome | on 2010-06-05
Ya thanks!

---

### Post by Linuxforall on 2010-06-05
> **nhasian said:**
> thanks Linuxforall i didn't see that.  looks like he's got the most recent version too so no need to compile it yourself then :KS

You are welcome, it works quite well here with my Lucid x64 and Microdia chipset webcam.

---

### Post by ubu_lin on 2010-07-31
> **Linuxforall said:**
> For 10.04 loell ppa won't work, you need latest ppa from Darwin Bautista at [https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa)
 
hi, I installed gyachi from above mention ppa on ubuntu 10.04, but voice chat is not working, any one has the same problem, any help ??

---

### Post by seanarickymurphy on 2010-08-14
Yes have the same problem here as well, how can I call others in gyachi?

---

### Post by TNAFan on 2010-10-23
Well, unfortunately his PPA no longer has Gyachi in it.  So where do we go from here?  Anyone?

---

### Post by adibogos89 on 2010-10-31
You will have to manually download the karmic packages (that seem to work just fine in lucid) from here: [https://launchpad.net/~loell/+archive/ppa/+build/1806226](https://launchpad.net/~loell/+archive/ppa/+build/1806226)

First install the [gyachi-data_1.2.9-0.1~karmic_all.deb]("https://launchpad.net/%7Eloell/+archive/ppa/+build/1806226/+files/gyachi-data_1.2.9-0.1%7Ekarmic_all.deb") package and then [gyachi_1.2.9-0.1~karmic_i386.deb]("https://launchpad.net/%7Eloell/+archive/ppa/+build/1806226/+files/gyachi_1.2.9-0.1%7Ekarmic_i386.deb") and you're all set.

They seem to keep the same ppa for lucid gyachi (**ppa:loell/ppa**), but they only offer the 64 bit build because they failed to build the i386 one.

---

### Post by kmrs75 on 2010-12-11
Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

---

