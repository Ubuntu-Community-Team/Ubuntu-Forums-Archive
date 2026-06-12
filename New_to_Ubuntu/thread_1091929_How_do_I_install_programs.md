---
title: "How do I install programs?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Aerotha on 2009-03-09
How do I install a program using the console? I know there is a package manager but I can't feel like a real linux user until I can...Thank you guys!
also if anyone can provide a few tips for a newbie that would be great!

Edit: I know there are guides on google, but I cannot get them to work...and I can't get my drivers to quote work :S

---

### Post by TWO on 2009-03-09
> **Aerotha said:**
> How do I install a program using the console? I know there is a package manager but I can't feel like a real linux user until I can...Thank you guys!
also if anyone can provide a few tips for a newbie that would be great!

Basically, you enter type in ```
sudo apt-get install [name of package]
```Where I've written [name of package] you'll write the name of the program (or individual package) that you'd like to install. If it is a program, everything else that is needed will also be installed.

You will be prompted for your password the first time you run sudo though, do bare in mind.

Oh, and there's nothing wrong with relying on Synaptic Package Manager to install programs, or the Add/Remove programs option either! 

Have fun!

Edit: In fact, by using the graphical package manager (Synaptic Package Manager), you'll be able to easily search for other programs that you might be interested in.

Oh, and you asked about "tips" for newbies. Depends what types of things you want to be able to do. Please specify!

---

### Post by bekind2thenoob on 2009-03-09
sudo aptitude install [name of package] (to install)

sudo aptitude remove [name of package] (to remove)

sudo aptitude update (to refresh your package list)

---

### Post by DGortze380 on 2009-03-09
> **TWO said:**
> Basically, you enter type in ```
sudo apt-get [name of package]
```
Where I've written [name of package] you'll write the name of the program (or individual package) that you'd like to install. If it is a program, everything else that is needed will also be installed.

You will be prompted for your password the first time you run sudo though, do bare in mind.

Oh, and there's nothing wrong with relying on Synaptic Package Manager to install programs, or the Add/Remove programs option either! 

Have fun!

the 'package manager' IS apt-get. Synaptic and Add/Remove are Graphic Front Ends for this manage. Just like in Fedora your package manager would yum.

My 'newbie suggestion' is that you post an individual thread for each of the questions you run across. Please search and try to fix it yourself first, then post, and we'll be happy to help.

---

### Post by TWO on 2009-03-09
> **DGortze380 said:**
> the 'package manager' IS apt-get. 

I'm pretty certain I was referring to **graphical front end **of the package manager anyway. :confused:

Where is the point of contention?

---

### Post by DGortze380 on 2009-03-09
> **TWO said:**
> I'm pretty certain I was referring to **graphical front end **of the package manager anyway. :confused:

Where is the point of contention?

There is no contention ... just clarifying ... it's useful knowledge.

---

### Post by Aerotha on 2009-03-14
> **TWO said:**
> Basically, you enter type in ```
sudo apt-get install [name of package]
```Where I've written [name of package] you'll write the name of the program (or individual package) that you'd like to install. If it is a program, everything else that is needed will also be installed.

You will be prompted for your password the first time you run sudo though, do bare in mind.

Oh, and there's nothing wrong with relying on Synaptic Package Manager to install programs, or the Add/Remove programs option either! 

Have fun!

Edit: In fact, by using the graphical package manager (Synaptic Package Manager), you'll be able to easily search for other programs that you might be interested in.

Oh, and you asked about "tips" for newbies. Depends what types of things you want to be able to do. Please specify!

Will this get them off the internet? or just my "Home" folder?

---

### Post by 3rdalbum on 2009-03-14
It gets them off the internet.

I gather you mean that you want to learn how to compile programs from source code. If so, then why don't you tell us what you are trying to compile and where you are failing.

---

### Post by Aerotha on 2009-03-14
> **3rdalbum said:**
> It gets them off the internet.

I gather you mean that you want to learn how to compile programs from source code. If so, then why don't you tell us what you are trying to compile and where you are failing.

trying to get DarcNES from [http://www.zophar.net/linux/nes/darcnes.html](http://www.zophar.net/linux/nes/darcnes.html)

When I enter the command
sudo apt-get install DarcNES

it says it cannot be found

---

### Post by 3rdalbum on 2009-03-14
You don't understand.

The line "sudo apt-get install" will only install software from the software repositories. You know when you open up the Synaptic Package Manager program and take a look at all the software available in there? That's what "apt-get" can install. It can't install stuff you download yourself - that's not its purpose.

You'll probably find some NES emulators in Synaptic. ALWAYS look in Synaptic Package Manager for software before trawling the internet.

If you really need DarcNES for some reason, you need to download it from the web address you gave me (use the X11 GTK version) and follow the installation instructions included with the source code. DarcNES is a bad example, as it looks like it hasn't been updated since 2001; I don't think it will work with today's Linux distributions. That's another good reason to look in Synaptic Package Manager before downloading random programs from the web - Synaptic has programs that are guaranteed to work with your current version of Ubuntu with a minimum of fuss.

---

### Post by Aerotha on 2009-03-15
> **3rdalbum said:**
> You don't understand.

The line "sudo apt-get install" will only install software from the software repositories. You know when you open up the Synaptic Package Manager program and take a look at all the software available in there? That's what "apt-get" can install. It can't install stuff you download yourself - that's not its purpose.

You'll probably find some NES emulators in Synaptic. ALWAYS look in Synaptic Package Manager for software before trawling the internet.

If you really need DarcNES for some reason, you need to download it from the web address you gave me (use the X11 GTK version) and follow the installation instructions included with the source code. DarcNES is a bad example, as it looks like it hasn't been updated since 2001; I don't think it will work with today's Linux distributions. That's another good reason to look in Synaptic Package Manager before downloading random programs from the web - Synaptic has programs that are guaranteed to work with your current version of Ubuntu with a minimum of fuss.
Oh okay, iwas under the assumption that it just went through some Reservoir on the Internet some place and found something with a matching name...So just for future reference, how do I install a Tar.gz?

---

### Post by oldos2er on 2009-03-16
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

