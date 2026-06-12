---
title: "trouble with installation"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by lad3391 on 2008-12-09
i have two separate installation problems. 
A)the first is with mplayer. i've tried sudo apt-get install mplayer, as well as installation through synaptic. neither work. when i try to install SPM i get this

mplayer:
 Depends: libdirectfb-0.9-25  but it is not installable

i tried to install that file via terminal but no dice with that.

B) ive also tried to install cinelerra (its a movie editor type thing) it doesnt show up in SPM even with extra repositories added, i went ahead and tried to install it via terminal. 

The following packages have unmet dependencies:
  cinelerra: Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
E: Broken packages

Then i tried to install this libopenexr2c2a also in terminal

However the following packages replace it:
  libopenexr2ldbl
E: Package libopenexr2c2a has no installation candidate

then i tried installing libopenexr2lbdbl and got the following

E: Package libopenexr2ldbl has no installation candidate


I've tried sudo apt-get update to no avail, I've tried to work these issues out on my own for a while before coming in here asking for help, so anything i can get would be greatly appreciated. thanks in advance!

---

### Post by handydan918 on 2008-12-10
Statements like I tried but it didn't work" really don't tell anyone anything. If you post the exact command you used and the exact error output, it maight be trivial to remedy. 

In the mean time, it seems you may have b0rken packages.

 Synaptic>Settings>filters>broken packages may help you figure it out.

---

### Post by kansasnoob on 2008-12-10
What version of Ubuntu is this?

---

### Post by lad3391 on 2008-12-10
this is the intrepid ibex. here EVERYTHING for the mplayer problem. anything else you need, im more than happy to help you help me

thomas@thomas-laptop:~$ sudo apt-get install mplayer
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdirectfb-0.9-25 but it is not installable
E: Broken packages

thomas@thomas-laptop:~$ sudo apt-get install libdirectfb-0.9-25 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdirectfb-0.9-25 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdirectfb-0.9-25 has no installation candidate


[B][SIZE="5"]
heres the stuff for cinelerra[/SIZE][/B]

thomas@thomas-laptop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
E: Broken packages


thomas@thomas-laptop:~$ sudo apt-get install libopenexr2c2a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenexr2c2a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenexr2ldbl
E: Package libopenexr2c2a has no installation candidate

thomas@thomas-laptop:~$ sudo apt-get install libopenexr2c2a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenexr2c2a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenexr2ldbl
E: Package libopenexr2c2a has no installation candidate

---

### Post by lad3391 on 2008-12-11
bump? ;/

---

### Post by vishal_mala on 2008-12-11
I would advice you to start all over again. fix all the broken packages, u can do it through an option in synapatic pack mgr. after doing this open Add /remove through the apps menu, and search mplyaer or whatever you want to install. If you found your software, click on the tick mark and click apply changes, I have obs that sometimes when nothing works add removes works gr8, and yes make sure you have removed/fixed all the broken or damaged package files, maybe this much should help you.

---

### Post by zvacet on 2008-12-11
@ **lad3391**

Check in system>admin>software sources that you have universe and multiverse enabled,because Mplayer is in multiverse repo.With that repos enabled you should be able to install Mplayer from synaptic without any problem.But if you still have problems try 

```
sudo apt-get -f install
```

For cinelerra look [here.]("http://cinelerra.org/getting_cinelerra.php#intrepid")

---

### Post by lad3391 on 2008-12-16
firstly, thanks for your help, but I didnt really get anywhere. I tried to fix the broken packages, it said it fixed them. but im still having all the same problems with mplayer.

---

