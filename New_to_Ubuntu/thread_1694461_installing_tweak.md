---
title: "installing tweak"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by wordmaster on 2011-02-24
When I try to install the .deb package of ubuntu tweak, I get the following error;

Error: Dependency is not satisfiable: python (>= 2.7)


Please help.

---

### Post by Perfect Storm on 2011-02-24
Which version of ubuntu do you use?

---

### Post by _0R10N on 2011-02-24
That's odd! Where did you get that .deb? I have python 2.6.6.3 and selected tweak 3.01 for installation and it didn't require anything extra. Also, which version of Tweak are you trying to install? 

If you're trying to install from a repo, maybe you added an experimental repo to your sources.list file, check for any no-traditional repo in that file


Kind regards!

---

### Post by lkjoel on 2011-02-24
> **wordmaster said:**
> When I try to install the .deb package of ubuntu tweak, I get the following error;

Error: Dependency is not satisfiable: python (>= 2.7)


Please help.
Try this in a Terminal window:
```
sudo apt-get install ubuntu-tweak

```
It will install ubuntu-tweak from the Ubuntu repos.

---

### Post by rburkartjo on 2011-02-25
word if what lkj says doesnt work go to the ubuntu tweak website and download the newest deb install. then install that

---

### Post by philinux on 2011-02-25
> **lkjoel said:**
> Try this in a Terminal window:
```
sudo apt-get install ubuntu-tweak

```
It will install ubuntu-tweak from the Ubuntu repos.

It's not in ubuntu repo's you have to get it from their site.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by rburkartjo on 2011-02-25
yea phil i sure wish they would add this to the repos.

---

### Post by rburkartjo on 2011-02-25
he could always add the ppa to the software sources

---

### Post by philinux on 2011-02-25
> **rburkartjo said:**
> yea phil i sure wish they would add this to the repos.

The developers of Tweak would have to go through this process.

[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by ClyN3il on 2011-04-05
Why is this thread marked solved? There is no working solution in the thread. I am having this same problem (trying to install Ubuntu Tweak version 0.5.10-1, on Natty Beta 1) using the deb downloaded from their website. Ubuntu Tweak, as has been pointed out, is not in the Ubuntu repositories. I clearly have the necessary python installed (python 2.6, and 2.7, and 3..).

---

### Post by 5149.5 on 2011-04-05
Here is how I installed tweak:

```
sudo add-apt-repository ppa:tualatrix/ppa
 sudo apt-get update
 sudo apt-get install ubuntu-tweak 

```

---

### Post by ClyN3il on 2011-04-05
It seems to work now... (Using the PPA method as above.) I installed a bunch of updates, and I think some of them were python-related...maybe that's what did it.

PS: For others' reference, if you're using Natty beta, you should probably use the PPA...it looks like the deb you get when you download from Ubuntu Tweak's main page is the one that's supposed to be for Maverick (0.5.10-1...the PPA gave me 0.5.11-1~natty1).

---

### Post by greylion on 2011-05-15
Installed a fresh xubuntu 10.10 i386, installed all updates.

Downloaded from ubuntu tweak website, got the exact same problem; dependency error for python (=>) 2.7
Only then did I notice it was the natty version.
Googled the error, found this thread.

Installing from PPA works, but it's odd that the website offers a natty .deb to a maverick install.

---

### Post by c0rrupt0r on 2011-05-26
I had this same problem while trying to download and install the deb off of Ubuntu Tweak website but then again did some thinking after reading Greylion's Post above and on the ubuntu tweak website it says just under the button to download it "Old versions (for Ubuntu 10.10 and before)" So I clicked that and it brought me to another page for the version I needed and here you go. [https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download) Make sure you get the one for maverick and it installs flawlessly for me.

---

