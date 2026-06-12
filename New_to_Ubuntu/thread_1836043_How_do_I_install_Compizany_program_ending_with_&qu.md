---
title: "How do I install Compiz/any program ending with &quot;.tar.gz&quot;"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Skipperr on 2011-08-30
Hey I'm having an hard time installing anything on Ubuntu. Can someone explain to me what to do?
I think this should be an easy one for the general Linux users :P.

Here's a screenshot of my problem.
[IMG]http://i.imgur.com/4m8OV.png

---

### Post by haqking on 2011-08-30
First of all anything you want to install, check it is not in the repos first, which Compiz is, so you can install it through software centre.

Second .tar.gz is just a packaging/compression format so to learn how to unpack contents see here
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

then the contents will vary, if it is .deb file that was packed you can just execute the .deb file.

If it is source then it needs to be compiled, see here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

enjoy ;-)

And the problem you are having is you need to be in the directory to carry out the autogen.sh.

So you need to change directory first to where it is located.

---

### Post by Enigmapond on 2011-08-30
Well first of all...welcome to the forum. There is no need to install a programme like Compiz by compiling. If you want the latest version, just add the repo:

```
sudo apt-add-repository ppa:compiz/ppa
```
Then:
```
sudo apt-get update && sudo apt-get install compiz
```

Cheers!

---

### Post by Skipperr on 2011-08-30
> **haqking said:**
> First of all anything you want to install, check it is not in the repos first, which Compiz is, so you can install it through software centre.

Second .tar.gz is just a packaging/compression format so to learn how to unpack contents see here
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

then the contents will vary, if it is .deb file that was packed you can just execute the .deb file.

If it is source then it needs to be compiled, see here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

enjoy ;-)

And the problem you are having is you need to be in the directory to carry out the autogen.sh.

So you need to change directory first to where it is located.
Ok well unpacking is as far as I've got. I'm installing compaz through the software center right now.

Is the thing you see on screen in my file browser what you call "source". 
And to install that I have to compile it is that correct? :P

---

### Post by haqking on 2011-08-30
> **Skipperr said:**
> Ok well unpacking is as far as I've got. I'm installing compaz through the software center right now.

Is the thing you see on screen in my file browser what you call "source". 
And to install that I have to compile it is that correct? :P

yes and the instructions are in the text file but you need to be in right location

However as said above you can via the repos as outlined above.

Every source may be a little different so the instructions are usually in the tar as a text file to follow

---

### Post by seawolf167 on 2011-08-30
Here is a how to for compiling from source.

[CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")
[CompilingHowTo]("https://help.ubuntu.com/community/CompilingSoftware")

If you install anything from the Software Center (or a standard "apt-get install"), you do not need to compile it.

---

### Post by seawolf167 on 2011-08-30
> **Enigmapond said:**
> Well first of all...welcome to the forum. There is no need to install a programme like Compiz by compiling. If you want the latest version, just add the repo:

```
sudo apt-add-repository ppa:compiz/ppa
```Then:
```
sudo apt-get update && sudo apt-get install compiz
```Cheers!


+1 - don't compile from source if you don't have to, its just an extra headache.

---

### Post by Skipperr on 2011-08-30
> **Enigmapond said:**
> Well first of all...welcome to the forum. There is no need to install a programme like Compiz by compiling. If you want the latest version, just add the repo:

```
sudo apt-add-repository ppa:compiz/ppa
```Then:
```
sudo apt-get update && sudo apt-get install compiz
```Cheers!


Got this
```

W: Failed to fetch http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Something wrong or is it all ok?
BTW is it a known bug that my downloads via software center get stuck at "waiting for apt-get to exit"?

---

### Post by bodhi.zazen on 2011-08-30
This link is from Fedora, but it reviews why installing from source is not such a great idea:

[https://fedoraproject.org/wiki/Package_management_system](https://fedoraproject.org/wiki/Package_management_system)

If you must, it is better to package the source code into a .deb

This is easy to do with a simple program, but as the program becomes more complex so does packaging.

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

If packaging is too hard, try a ppa.

---

### Post by pqwoerituytrueiwoq on 2011-08-30
> **Skipperr said:**
> Got this
```

W: Failed to fetch http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```Something wrong or is it all ok?
BTW is it a known bug that my downloads via software center get stuck at "waiting for apt-get to exit"?
that ppa currently does not have any versions for natty you can try setting it to maveric via software sources in the other tab (edit button)

[http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/)
as you can see there is no natty folder

---

### Post by Livin4Jesus on 2011-08-30
If you're lucky, it should by as easy as...
Extracting the tar.gz
CDing into folder
./configure, make, make install
With buggy programs, though, it may not be as easy...

Also, like everyone else said, try checking the repos.

---

