---
title: "In the first steps"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by andreapl25 on 2009-08-04
ok, i got a new laptop, and we were trying to install skpe.

we were following these instructions
[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

in the process we received this message
E: Type ‘--20:52:22--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

What does this mean?? 

And the problem is we cant access the synaptic package manager or the update manager

and whay cant we access these folders any more??

Please help!!!!!!!

---

### Post by zvacet on 2009-08-04
Type in terminal

```
cat etc/apt/sources.list
```

and post output here.

---

### Post by kansasnoob on 2009-08-04
Please go to Terminal and post the output from the following command:

```
cat /etc/apt/sources.list
```

---

### Post by kansasnoob on 2009-08-04
> **zvacet said:**
> Type in terminal

```
cat etc/apt/sources.list
```

and post output here.

Great minds think alike:D

I noticed those instructions were for Feisty.

---

### Post by oldos2er on 2009-08-04
Open medibuntu.list in a text editor, with admin (root) privileges:
```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
```

 Edit the first line; either comment it out by adding #, or remove the "--20:52:22--" text. Lines in any repository list must begin with either deb or deb-src. Once you're done, save and exit the file, then run
```
sudo apt-get update
```

---

