---
title: "Linux Replacements"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Wovaki on 2009-02-07
I don't know if there is a place to find this information, if there is please let me know.

But I would like to know some replacements for a couple applications in Linux.

**1. Adobe Dreamweaver**
I don't use many features in Dreamweaver, but the main thing I will miss is code completion, it helps me alot since I am just learning to make website, I'm talking about the little window that pops up with suggestions.

**2. Photoshop**
I already know about GIMP, what I would like to know is: how do I get the plugin to make it look like Photoshop? I tried their main site, but I can't find anything.

I like GIMP, but I don't like having 3 windows open for just 1 program, I like the way Photoshop looks and feels. Also will this plugin remove any functionality?

**3. A server app**
I heard about XAMP or Apache or something, but I don't know where to get it or anything like that. I want to be able to make and test PHP files without being online.

Thats all I can think of for now, Thanks!
Wovaki

---

### Post by drs305 on 2009-02-07
This is the first place I look when I'm looking for an alternative:
[http://www.linuxalt.com/]("http://www.linuxalt.com/")

Gimp is listed for Photoshop. Gimp is very powerful once you get used to it. Several are listed for Dreamweaver. I've used Bluefish with success but don't have enough experience with the others to say if it is better or worse than the others.

---

### Post by cerealtx on 2009-02-07
installing php on ubuntu is a peice of cake, ```
sudo apt-get install php5
``` then use php <File.php> to run your php files

---

### Post by dr.silly on 2009-02-07
check out aptana its a great dreamweaver replacement

---

### Post by Wovaki on 2009-02-07
> **drs305 said:**
> This is the first place I look when I'm looking for an alternative:
[http://www.linuxalt.com/]("http://www.linuxalt.com/")

Gimp is listed for Photoshop. Gimp is very powerful once you get used to it. Several are listed for Dreamweaver. I've used Bluefish with success but don't have enough experience with the others to say if it is better or worse than the others.

Thanks, I'll check it out.
What about the photoshop plugin for GIMP?

> **cerealtx said:**
> installing php on ubuntu is a peice of cake, ```
sudo apt-get install php5
``` then use php <File.php> to run your php files
I can't get online with Linux, I only have dialup right now. Is there somewhere I can download it on Windows, then transfer it to Linux?

And after I have this, all I have to do is double click a php file?

> **dr.silly said:**
> check out aptana its a great dreamweaver replacement
Where can I find it/info on it?

---

### Post by mdsmedia on 2009-02-07
For the photoshop plugin for Gimp, look for GimpShop.

Never used Photoshop or GimpShop.

[http://www.gimpshop.com]("http://www.gimpshop.com")

For Aptana...you guessed it

[http://www.aptana.com]("http://www.aptana.com")

---

### Post by cerealtx on 2009-02-07
[http://www.php.net/downloads.php](http://www.php.net/downloads.php)

---

### Post by cerealtx on 2009-02-07
er should have added this stuff to, once u download it, ```
php-5.2.8.tar.gz
```then cd into the dir after its extracted, and type ```
./configure
``` it will go through some stuff then when u get the input line back type ```
sudo make install
```

---

### Post by hyper_ch on 2009-02-07
why do you give him the link to manually download php5 when it's in the repos?

---

### Post by dr.silly on 2009-02-07
XAMPP [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by hyper_ch on 2009-02-07
and why do you give him a link to xampp?

---

### Post by scottuss on 2009-02-07
They are only trying to be helpful I think... although some basic Google skills would have solved his problems I suppose!

---

### Post by hyper_ch on 2009-02-07
I know they try to help... but pointing to stuff outside the packages shouldn't be done if not necessary.

```

sudo tasksel

```

---

### Post by mdsmedia on 2009-02-07
Could it be because he specifically asked for a non repo download?

---

### Post by hyper_ch on 2009-02-07
> **mdsmedia said:**
> Could it be because he specifically asked for a non repo download?
Yes, that could be ;) my mistake ;)

sorry cerealtx & dr.silly

---

### Post by mdsmedia on 2009-02-07
Personally, I wouldnt use Ubuntu without a reliable net connection, or at least the DVD.

---

### Post by Wovaki on 2009-02-07
@up
Why wouldn't you use it without a good connection?


If I download just PHP, all I have to do is double click a php file and it will run, or do I need XAMPP too?

Thanks

---

### Post by cerealtx on 2009-02-08
> **cerealtx said:**
> er should have added this stuff to, once u download it, ```
cd /where/ever/you//downloaded/php-5.2.8.tar.gz
```then cd into the dir after its extracted, and type ```
./configure
``` it will go through some stuff then when u get the input line back type ```
sudo make install
```

thats how you install it

---

