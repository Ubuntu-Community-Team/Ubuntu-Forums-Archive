---
title: "New user, troubles with banshee"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by naruto60231 on 2008-12-20
I installed banshee via Add/remove program manager in application, and am trying to update to 1.4 with video support. 

I need this new version to sync videos and music to my IPod,but I am having trouble installing it.

I had to add this APT line: deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
to my third party software sources before I updated, but when I went to reload I got this error message:

"Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

So I ignored it and went into terminal and entered: 
"Sudo apt-get install banshee-1"

It registered the update and set it up in my update manager

I opened my update manager and selected check, but it refused to load my banshee update with an error message:
"Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

What is wrong? If anyone knows, please post here, or PM me, I have been working for an hour on this and can't get the update to load.

---

### Post by taurus on 2008-12-20
Can you post your /etc/apt/sources.list?

---

### Post by chrisod on 2008-12-20
What is wrong is that the files aren't there. Double check that you have the addresses correct for the source directory.

---

### Post by naruto60231 on 2008-12-20
You can check the banshee site itself, I copied and pasted the third party source directly from the website.

Banshee 1.4 site for Ubuntu Intrepid Ibex, hardy, and gusty:

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

### Post by naruto60231 on 2008-12-20
I tried adding both lines as seperate APT lines, but, now my banshee won't update. When I type in my terminal command: "sudo apt-get install banshee-1" it comes back reading that I have the latese version of banshee when I don't, I still don't have video support or anything.

---

### Post by clive littlewood on 2008-12-20
Hi

I installed Banshee 1.4.1 direct from synaptic.

It is the latest version and i can play videos OK  !!!        :P


Regards

Clive

---

### Post by naruto60231 on 2008-12-20
Sorry, but how do I get into synaptic? I am new as I said.

---

### Post by naruto60231 on 2008-12-20
If you meant synaptic package manager, I can't get that to work either. When I try to "upgrade" it gives me an error message.

---

### Post by chrisod on 2008-12-20
Open Banshee and check under the *About* menu at the top to see what version of Banshee you are actually running.

---

### Post by naruto60231 on 2008-12-20
0.13.2 lol, pretty old version.

---

### Post by Zeedok on 2008-12-20
We need to check that you have correctly entered your sources/repos:

1. Open a terminal (Applications - Terminal)
2. Type at the command prompt:

```
sudo gedit /etc/apt/sources.list
```

3. Enter your password when prompted
4. Your "sources.list" file will open in a text editor
5. Make a backup copy - you can do this via the command line, but I  just select all, copy and paste it into a Tomboy note (Applications - Accessories - Tomboy) - then it's easy to find if something goes wrong.
6. The look through your sources.list, at the bottom you should find:

```
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
```

If not, then cut and paste it and then save and close the file.
7. Open Synaptic (System - Administration - Synaptic Package manager), enter your password
8. Hit "Reload", upper left corner
9. Search for Banshee and now you should see version 1.4.1 available for installation

If you can't find it, Select "Origin" in the bottom left of Synaptic, select the launchpad universe source to check (see my screenshot to see what I mean)

Good luck.

---

### Post by clive littlewood on 2008-12-21
Hi

I would suggest that you purge your version of Banshee from add remove.

Then check for any remaining config files (make sure hidden files are checked in your home folder)

Then install Banshee using synaptic manager, just search for Banshee then tick the box and follow the instructions for installation.

I promise you the version in synaptic is the latest and will play video.

Clive

PS. Please don't pm unless invited   :(

---

