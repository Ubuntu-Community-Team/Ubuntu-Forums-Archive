---
title: "package locked in synaptic"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by ray123 on 2011-09-05
Upgraded to 11.04, and tried to install pan newsreader from software Centre. Did not work. So I installed synaptic package manager and it says pan newsreader is locked, this is the only package marked as locked. Does anybody know how to unlock it

 Thanks in advance   :)

---

### Post by Nr90 on 2011-09-05
Im far from an ubuntu expert, but isn't synaptic installed from the start anyway?

---

### Post by 23dornot23d on 2011-09-05
A picture tells the story ..... click on the item thats locked - go to the menu - choose package  and click to remove the tick 
where shown - this will unlock it .....


[IMG]http://img707.imageshack.us/img707/8832/unlocks.jpg[/IMG]

---

### Post by ray123 on 2011-09-05
Thanks for the replies

Nr90

Synaptic is not installed by default in Ubuntu 11.10

23dornot23d

Yes that takes the lock off, but when you try to reinstall it,  it just locks up again. When I try to run it,  it says fix broken packages, then when I try to, it says broken packages are held. I thought it may have been a bug, but surely it would have been all packages affected. :D

---

### Post by Shazaam on 2011-09-05
Shut Synaptic down if you have it open then try these in terminal...

```
sudo apt-get -f install
```
Then...
```
sudo dpkg --configure -a
```

If you get no errors run Synaptic again.

---

### Post by ray123 on 2011-09-07
Sorry I have been so long in replying Shazaam. I tried to force install it and it came back with no errors, but when I used configure -a it came back with errors.
I tried reinstalling ubuntu again but I still have the same problem with Pan Newreader not installing, I have never had any problems with Pan before 11.10
:)

---

### Post by jtarin on 2011-09-07
Usually if a program is locked....it is installed already. Have you tried from the command line? Pan may not be compatible with your version of Ubuntu. A check might tell.

---

### Post by ray123 on 2011-09-07
Thanks jtarin

No wonder I am having problems on the command line I am typing Pan instead of pan.  When I run pan it says I have unmet dependences 

Depends:libgmime 2.0-2.0 but it is not installable you have a broken package

Does that mean I have to install synaptic to fix broken package, wait for an update or another solution

thanks to all for helping

:)

---

### Post by jtarin on 2011-09-07
Two ppa sources for package.

[http://www.ubuntuupdates.org/packages/show/287503](http://www.ubuntuupdates.org/packages/show/287503)

[https://launchpad.net/~klaus-vormweg/+archive/ppa](https://launchpad.net/~klaus-vormweg/+archive/ppa)

---

### Post by wildmanne39 on 2011-09-07
Hi, also you said you are using 11.10 correct? if so you do know that it is just for testing and is very unstable.

I see you have said you are using 11.04 then you said 11.10.

Also all support questions should be posted here.
[http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403)
Thank you

---

