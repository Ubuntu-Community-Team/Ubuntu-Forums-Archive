---
title: "Dillo for Ubuntu"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by createdcreature on 2011-05-30
Is there a Dillo browser for Ubuntu? I discovered it when I was using Virtual PC with Feather and Damn Small Linux? I know dillo is pretty basic, but I am just wondering, as it is very fast to start up. I use Ubuntu 11.04 (Natty)with all the latest updates. I tried sudo apt-get install dillo, but it is not in the repository!

---

### Post by Joe of loath on 2011-05-30
It may be out there, but TBH it's so basic that you only use it if you *have* to :p A light webkit browser like Midori, Arora or Epiphany will be almost as fast, and so much more usable.

Also, as an aside, having your (I assume) real name and address in public isn't a good idea. I'd consider changing your username and location ;)

---

### Post by juancarlospaco on 2011-05-30
LuaKit, uzbl

---

### Post by createdcreature on 2011-05-31
I am now using Links for this kind of thing and it is just as good as Dillo.

---

### Post by createdcreature on 2011-10-07
Just a thought though, how would I run dillo on ubuntu?

---

### Post by Toz on 2011-10-07
> **Robert Moyse said:**
> Just a thought though, how would I run dillo on ubuntu?

1. Make sure you have **build-essential** installed.

2. Install required dependencies:
```
sudo apt-get install libfltk1.3 libfltk1.3-dev libjpeg8 libjpeg8-dev zlib1g zlib1g-dev
```

3. Download the dillo version 3 source code from [http://www.dillo.org/download/]("http://www.dillo.org/download/") (version 3.0.1 as of this writing)

4. Unzip the source:
```
bunzip2 dillo-3.0.1.tar.bz2
tar xvf dillo-3.0.1.tar
```

5. Compile the source:
```
cd dillo-3.0.1
./configure
make
sudo make install-strip

```

6. Run the program
```
dillo
```

---

### Post by mibart on 2011-10-07
> **Joe of loath said:**
> 
Also, as an aside, having your (I assume) real name and address in public isn't a good idea. I'd consider changing your username and location ;)
Why do You claim that? Do You remember those golden years before PHP forums, when almost everyone post on Usenet with real name? What is wrong with using real name on Internet?

---

### Post by thatguruguy on 2011-10-07
"thatguruguy" happens to be my birth name.

---

### Post by createdcreature on 2012-02-24
Solved! Go to [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dillo/]("http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dillo/") (English Only) and pull the debian package for 3.0.2. Open it up in a package manager and install it and create shortcuts if needed. Done!

---

