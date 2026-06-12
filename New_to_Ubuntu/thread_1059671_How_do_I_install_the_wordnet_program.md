---
title: "How do I install the wordnet program?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-02-04
Its the wordnet dictionary program that you sometimes see on dictionary.com and dict.org

I downloaded a file, not sure which one i was suppose to download.

but i extracted it and couldn't install it. How do I install this on my ubuntu?

[http://wordnet.princeton.edu/obtain](http://wordnet.princeton.edu/obtain)

---

### Post by azurepancake on 2009-02-04
Quite simple really, the 'WordNet' application is included in the Ubuntu repositories. Simply open a terminal (Applications-->Accessories-->Terminal) and type the following:

```
sudo apt-get upgrade
sudo apt-get install wordnet
```

And thats it. I'm afraid I am not too familiar with this software, but to execute it you can probably simply type 'wordnet' into your terminal or locate it in the 'Applications' section of Gnome. 

Many great programs already exist in the repositories. Type the following to query for a specific package:

```
sudo apt-cache search *package-name*
```

You might want to check out the link in my signature, "How to install ANYTHING in Ubuntu" for a nice little introduction to installing software.

---

### Post by utnubuuser on 2009-02-04
find a good step-by-step tutorial on installing from source.  Not everything is compatible.  There might be dependency issues that cannot be satisfied without a whole lot of work.

LOL  - or if it's in the repositories, follow the above step.

(sorry, couldn't check, synaptic is busy with some updates.)

---

### Post by jorcarras on 2012-04-26
To install WordNet in Ubuntu type following command in the terminal.
"sudo apt-get install science-linguistics" .

 After installation to use the WordNet GUI type "wnb" and hit enter in the command line. To use WordNet in command line mode type "wn" and hit enter command. 

(via):
[http://jaganadhg.freeflux.net/blog/archive/2009/09/04/installing-wordnet-in-ubuntu.html]("http://jaganadhg.freeflux.net/blog/archive/2009/09/04/installing-wordnet-in-ubuntu.html")

---

