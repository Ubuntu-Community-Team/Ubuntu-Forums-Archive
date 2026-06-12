---
title: "Installing Adobe Flash"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by usern on 2009-06-23
How do I Install adobe Flash in Ubuntu 8.04 ?

---

### Post by Wiebelhaus on 2009-06-23
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras flashplugin-nonfree

```

---

### Post by Zzl1xndd on 2009-06-23
What would probably be your best bet is going to Applications > Add/remove. Then set it to All Avilable application (there should be a drop down at the top) the search for Ubuntu and install the Ubuntu restricted Extras. 

This has Flash, Java, and a bunch of other good stuffs.

---

### Post by raymondh on 2009-06-23
> **usern said:**
> How do I Install adobe Flash in Ubuntu 8.04 ?

If you have flashplugin-nonfree, I suggest you remove that first.

```
Sudo apt-get remove flashplugin-nonfree
```

Then, go to the adobe website and download the .deb file for 8.04 and install. 

Restart your browser and have a go.

If you decide you don't like it ...

```
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Good luck.

---

### Post by balaknair on 2009-06-23
You can install the "ubuntu-restricted-extras" package- this will give you Adobe Flash, as well as Sun Java, MS Truetype Fonts, mp3 and DVD playback codecs and some other stuff, which is not included in the default Ubuntu install because of copyright issues.

Instructions given below


* Open Synaptic Package Manager(System menu> Administration> Synaptic), enable the 'Multiverse' repositories(Synaptic> Settings> Repositories), and click the reload icon. This will update the package lists.
* Now, search for the ubuntu-restricted-extras package, click the check box next to it and select 'Mark for installation'---> Apply

It's a fairly large download, so if you want just the Flash package, you can install it by searching for Flash(the package name you need is **flashplugin-nonfree**) instead.

Alternate method> via the command line-
Open a Terminal window(Applications menu> Accessories> Terminal) and copy paste the following line

*sudo apt-get install ubuntu-restricted-extras*

OR

*sudo apt-get install flashplugin-nonfree*

[I]Type in your password when asked and press enter, there will be no *** appearing as you type in the password.
[/I]
Hope this is helpful.

---

