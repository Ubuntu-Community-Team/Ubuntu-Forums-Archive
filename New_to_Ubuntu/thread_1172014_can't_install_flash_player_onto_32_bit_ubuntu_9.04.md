---
title: "can't install flash player onto 32 bit ubuntu 9.04"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by naye3m on 2009-05-28
Hello,

I downloaded the .deb ubuntu 8.04+ flash player from the internet but when i try to install it, it does not go thru. Instead i get this message: [COLOR=Red]Error: dependency is not satisfiable:libcurl3[/COLOR]. I tried typing sudo apt-get install flashplugin-installer but it only says couldnt find package flash plugin-installer. Help please?

Thx in advance.

---

### Post by Wiebelhaus on 2009-05-28
Let's try to knock out all those pesky restricted packages real fast while performing some quick maintenance!

Run:


```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```



Then Run:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

Then:

```
sudo apt-get install libdvdcss2
```


```
sudo apt-get install w32codecs
```


```
sudo apt-get install ubuntu-restricted-extras
```


```
sudo apt-get install flashplugin-nonfree 
```


You could consolidate those last four into one command but let's watch those packages install for diagnostic reasons , Then log out and then back in and report back , good luck!

---

### Post by Paqman on 2009-05-28
> **Wiebelhaus said:**
> 
```
sudo apt-get install w32codecs
```


```
sudo apt-get install ubuntu-restricted-extras
```


```
sudo apt-get install flashplugin-nonfree 
```


Once you've got Medibuntu you can actually do all three of these in one step:

```

sudo apt-get install non-free-codecs

```

More info about the [Medibuntu non-free-codecs package]("http://packages.medibuntu.org/jaunty/non-free-codecs.html")

---

### Post by Wiebelhaus on 2009-05-28
> **Paqman said:**
> Once you've got Medibuntu you can actually do all three of these in one step:

```

sudo apt-get install non-free-codecs

```

More info about the [Medibuntu non-free-codecs package]("http://packages.medibuntu.org/jaunty/non-free-codecs.html")

Nice! Thanks for the simplification.

---

### Post by forth on 2009-06-02
> **naye3m said:**
> Hello,

I downloaded the .deb ubuntu 8.04+ flash player from the internet but when i try to install it, it does not go thru. Instead i get this message: [COLOR=Red]Error: dependency is not satisfiable:libcurl3[/COLOR]. I tried typing sudo apt-get install flashplugin-installer but it only says couldnt find package flash plugin-installer. Help please?

Thx in advance.

Hi 

I had that same problem this morning, (probs with deb file dependency: libcurl3) a simpler fix to this (or should I say workaround) is to download the tar.gz file instead, extract it, and run the installer from a command prompt, it worked for me and I now have the new BBC iPlayer working on Jaunty Jackalope.

---

### Post by copan on 2009-06-10
Wiebelhaus,

Rise Against never sounded so sweet on youtube.  Thank you.

---

