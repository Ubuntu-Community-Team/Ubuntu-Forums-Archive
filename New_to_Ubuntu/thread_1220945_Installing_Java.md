---
title: "Installing Java"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by bob brazie on 2009-07-23
I am trying to run and application that requires JAVA.

I need help finding the current version and how to install it.

I am new to ubuntu 9.04 and not afraid to ask for help. <g>

Thanks in advance. Bob.

---

### Post by mathay on 2009-07-23
There are two approaches to go about this: first is the GUI approach.

If you're using GNOME, go to the upper right hand corner of your screen and click *Applications*. From there, go to the bottom of the box and click *Add/Remove...* Make sure you select the option to search through all available packages, after that, type 'Java' is in the search box and voila. 

Ther command-line approach, which is much quicker in my opinion, is simply this:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Make sure you have the multiverse repository enabled or you will have an issue downloading/installing. 

To enable the multiverse, go to System > Administration > Software Sources

The first tab (*Ubuntu Software*) should have the option for which you have been searching (*Software restricted by copyright or legal issues (multiverse)*). Check that box and you should be good to go.

---

### Post by Arup on 2009-07-23
For Sun Java you need to enable medibuntu repository first, go to [www.medibuntu.org](www.medibuntu.org) to see how to.

---

### Post by wojox on 2009-07-23
Or you could:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 3rdalbum on 2009-07-23
If you use the command-line approaches listed above, at some point during the install process you will be presented with a "license agreement" text-based screen. You need to press the Tab key at this point in order to highlight the "I agree" button, and then press Space bar to "click" the button.

If you install the suggested packages using Synaptic Package Manager or the Add/Remove Applications program, you won't have this problem.

---

### Post by bob brazie on 2009-07-23
I was looking in the add-remove section of the applications menu and was a little confused (again) as to which one to install after I did a search for "java". There were more than one possibilities.

Do you have a recommendation on which one to choose?

Thanks. Bob.

---

### Post by XCan on 2009-07-23
> **bob brazie said:**
> I was looking in the add-remove section of the applications menu and was a little confused (again) as to which one to install after I did a search for "java". There were more than one possibilities.

Do you have a recommendation on which one to choose?

Thanks. Bob.

Go to synaptics instead, System -> Administration -> Synaptics Package Manager. Search for "sun java".

---

### Post by bob brazie on 2009-07-23
There are quite a few reference's to 'sun java". I am not sure what I am looking at there.

---

### Post by nwadams on 2009-07-23
just do this in a terminal 
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

that is by far the simplist

---

### Post by XCan on 2009-07-24
As mentioned, it is really much easier if you just typed the command
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Anyway, if you really want to use the GUI still, then search for
```
sun-java6-jre (Java runtime, mandatory if you want to run java apps)
sun-java6-plugin (plugin for firefox)
sun-java6-fonts (optional)
```

---

### Post by bob brazie on 2009-07-25
Thanks to all and that is what I did.

Being new to Ubuntu and 9.04 I am wondering if there is a list of these commands and what applications and utilities they will install.

It is far easyer than looking to either the aplications/removeinstall or the package manager.

---

### Post by oldos2er on 2009-07-25
[https://help.ubuntu.com/community/InstallingSoftware#Via%20a%20Text%20Based%20Methods](https://help.ubuntu.com/community/InstallingSoftware#Via%20a%20Text%20Based%20Methods)

---

