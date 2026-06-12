---
title: "command line"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by manners2345 on 2011-04-26
If I use this command line input, can I specify which desktop I want such as 10.04.2,32 bit

sudo apt-get install ubuntu-desktop 

 :D:D


Thank You 

Frederick Andrew
<snip>

---

### Post by v1ad on 2011-04-26
lol no. 10.04 is a distro version not a program. sudo apt-get install conky
that would install conky. if u want to install multiple files u do sud apt-get install file1 file2 file3 and so on.

---

### Post by Frogs Hair on 2011-04-26
That is the current Ubuntu desktop . You will get 32 or 64 bit depending on what ISO you installed to begin with. If you want to install one of the other desktop of the options finish the command with the name of the desktop environment you want to install.

Example: ```
sudo apt-get install kubuntu-desktop
```

---

### Post by matt_symes on 2011-04-26
Hi

Ubuntu-desktop is a metapackage that defines a list of packages to be installed for your desktop. Each version of Ubuntu only has one Ubuntu-desktop package.

You can check this with

```
apt-cache show ubuntu-desktop
```

or 

```
apt-cache showpkg ubuntu-desktop
```

It will only have one version and that is tied to your release. 

There are programs in the repository that have more than one version and it is possible to install a specific version of that package using

```
sudo apt-get install <package name>=<version>
```

If you want a specific desktop install that release or upgrade your current release.

What release are you currently using ?

```
cat /etc/lsb-release
```

Kind regards

---

### Post by manners2345 on 2011-04-26
I am using 10.10, I want to go back to 10.04.2. I have had nothing but trouble with 10.10, then when I upgraded my Internet connection to include wireless, everything just went in the toilet. The local Internet Techie for the ISP knows less than I do.

---

### Post by Miljet on 2011-04-26
As far as I know, there is no way to "downgrade" to an earlier version. You will have to reinstall to do that. If you redownload the 10-04 image, you should get the 10.04.2 version.

But at this point, I would wait for 11.04 to see if it works better for you unless you need it right now.

---

