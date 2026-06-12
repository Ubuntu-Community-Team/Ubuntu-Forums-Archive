---
title: "don't have internet connection, how to install softwares"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by sudipta.bhaskar on 2009-07-15
Hi, I am bhaskar. I am new to ubuntu 7.10. I don't have an internet connection in my computer. I have some cds of softwares containing linux packages like wine, mplayer etc. 
But I can't install them.
[B]I have followed the instructions in the installation text, but i can't even compile.
the instructions like ./configure, make, make install are not working. 
what i should do? please help[/B].
can u give me some address of sites where from i can download the .deb file format packages.
is there any way that i can download packages from other computers and install those manually, please help.
**i want to install the codecs to run microsoft formats multimedia.**
Thanks in advance.
**Please help.**

---

### Post by csabo2 on 2009-07-15
[www.getdeb.net](www.getdeb.net)

---

### Post by Cheesemill on 2009-07-15
Check out [Keryx]("http://keryxproject.org/") for installing programs on an off-line machine.

Be warned that this won't work on your machine (and neither will any other suggestions) because Ubuntu 7.10 has reached end of life and is no longer supported.

---

### Post by daimaru on 2009-07-15
if you want to compile source code, you have to first install the programs like make gcc etc
```

sudo apt-get install build-essential

```

---

### Post by tarps87 on 2009-07-15
> **daimaru said:**
> if you want to compile source code, you have to first install the programs like make gcc etc
```

sudo apt-get install build-essential

```

Not quite, no internet connection.

> **Cheesemill said:**
> ... (and neither will any other suggestions) because Ubuntu 7.10 has reached end of life and is no longer supported.

Not true, yes 7.10 has reached it end of life, but there are still ways to do it

If you have the cd you used to install it with your in luck, build-essentials should be on the cd.

Type
```
sudo apt-cdrom add
```
follow the instructions, now
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```
You can ignore any network errors as log as it asks you to install the package you should be fine.

To test
```
g++
```
Expected response: g++: no input files

Now you should be able to compile the programs using ./configure, make, make install.

---

### Post by aysiu on 2009-07-15
Good thing you have no internet connection, because 7.10 no longer receives security updates.

You may have a hard time finding packages for it even on another computer, though, since the repositories for it have also been taken offline (maybe you can find an archive of it somewhere).

Generally speaking, for offline installation of software, APTonCD is the way to go:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by durand on 2009-07-15
The first thing you should try to do is upgrade to a newer version of ubuntu. Since you don't have an internet connection, I'd recommend getting 8.04, which is a long term support release and supported until 2013. If you want, you could also get the latest ubuntu release, 9.04, which is supported until april 2010. You can download both from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) or ask for a CD to be sent from here: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) however that is only for 9.04.

---

### Post by aysiu on 2009-07-15
> **durand said:**
> The first thing you should try to do is upgrade to a newer version of ubuntu. Since you don't have an internet connection, I'd recommend getting 8.04, which is a long term support release and supported until 2013. If you want, you could also get the latest ubuntu release, 9.04, which is supported until april 2010. You can download both from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) or ask for a CD to be sent from here: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) however that is only for 9.04.
If you don't want to reinstall (i.e., if you want to upgrade), you should use the Alternate CD and not the Desktop CD.

---

### Post by durand on 2009-07-15
> **aysiu said:**
> If you don't want to reinstall (i.e., if you want to upgrade), you should use the Alternate CD and not the Desktop CD.

Oh yeah, I forgot that 8.04 was just after 7.10..whoops..

---

### Post by ramnarayan on 2009-07-15
> **sudipta.bhaskar said:**
> 
is there any way that i can download packages from other computers and install those manually, please help.
**i want to install the codecs to run microsoft formats multimedia.**
Thanks in advance.
**Please help.**

if you are in india try visiting the Ubuntu india site - and see if some one has the latest CD / DVD versions of Ubuntu near you and request for them / meet up

[http://ubuntu-in.info/wiki/index.php/Main_Page](http://ubuntu-in.info/wiki/index.php/Main_Page)

second - do you have any connection on any machine to the internet - if so follow some of the advise in the earlier posts - esp getdeb

third - if you are really keen to have an up todate and many software installed system then you could follow the link to a place where you could request for the entire dvd repository (for the cost of the media and postage only)

hope this helps

---

### Post by sudipta.bhaskar on 2009-07-16
Thanks for ur kind help. I am trying.

---

### Post by sudipta.bhaskar on 2009-07-16
> **ramnarayan said:**
> if you are in india try visiting the Ubuntu india site - and see if some one has the latest CD / DVD versions of Ubuntu near you and request for them / meet up

[http://ubuntu-in.info/wiki/index.php/Main_Page](http://ubuntu-in.info/wiki/index.php/Main_Page)

second - do you have any connection on any machine to the internet - if so follow some of the advise in the earlier posts - esp getdeb

third - if you are really keen to have an up todate and many software installed system then you could follow the link to a place where you could request for the entire dvd repository (for the cost of the media and postage only)

hope this helps
  
Thanks for ur help. I am trying.

---

### Post by sudipta.bhaskar on 2009-07-16
[FONT=Arial Black]**I have downloaded the realplayer in .deb format. While trying for installation it is saying that dependencies are not acceptable. What should I do?**[/FONT]
Please help.
Thanks in advance

---

### Post by ramnarayan on 2009-07-16
> **sudipta.bhaskar said:**
> [FONT=Arial Black]**I have downloaded the realplayer in .deb format. While trying for installation it is saying that dependencies are not acceptable. What should I do?**[/FONT]
Please help.
Thanks in advance

why not try 
[http://keryxproject.org/](http://keryxproject.org/)

this should solve your problem as well

---

### Post by BoardStupid on 2009-07-19
Thanks for pointing out Keryx. I've been looking for a load of updates for my brothers machine (he has no interenet access) and the dependancies were really starting to turn me crazy.

I used Keryx to select all the packages I wanted. It downloaded all the packages I needed, and I used APTonCD to create an iso of everything. A quick burn to CD using K3b and I'm good to go. If I remember, I will try to report back how everything went.

---

### Post by Bartender on 2009-07-19
Keryx is a work in progress.  

It sounds like the OP is way off the net.  I'm cursed with dial-up at home but have access to broadband by taking a laptop to the library.  Spent several hours figuring out how to set up keryx to use the GUI, then creating projects on the offline PC's, etc.
Keryx would work for some packages, but not most.  I posted at Keryx website and developer told me it's not ready for prime time yet.

If/when Keryx or some similar project becomes usable, it will be very helpful to people who don't have broadband at home but can access broadband at school, library, coffee shop, etc.  

But we're not there yet.

---

### Post by rraj.be on 2009-07-19
APTonCD works fine for most situation like this.

---

### Post by EXCiD3 on 2009-07-20
> **Bartender said:**
> Keryx is a work in progress.  

It sounds like the OP is way off the net.  I'm cursed with dial-up at home but have access to broadband by taking a laptop to the library.  Spent several hours figuring out how to set up keryx to use the GUI, then creating projects on the offline PC's, etc.
Keryx would work for some packages, but not most.  I posted at Keryx website and developer told me it's not ready for prime time yet.

If/when Keryx or some similar project becomes usable, it will be very helpful to people who don't have broadband at home but can access broadband at school, library, coffee shop, etc.  

But we're not there yet.

We are hard at work, expect a release soon! This next release will be the full deal, the first is more of a proof of concept, alpha verison. It still works, but there are certainly a lot of improvements that need to be done. We will be releasing a CLI version of [Keryx]("http://keryxproject.org") 1.0 soon!

---

