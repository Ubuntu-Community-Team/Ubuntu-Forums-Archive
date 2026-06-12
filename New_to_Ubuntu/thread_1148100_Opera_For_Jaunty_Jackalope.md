---
title: "Opera For Jaunty Jackalope?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Testrum on 2009-05-04
Can anyone tell me how to install Opera for Jaunty Jackalope? I can't seem to get the .deb file to work and have a hard time with compiling from source :-k

---

### Post by Didius Falco on 2009-05-04
> **Testrum said:**
> Can anyone tell me how to install Opera for Jaunty Jackalope? I can't seem to get the .deb file to work and have a hard time with compiling from source :-k

What is happening when you double-click the deb file? Have you tried right-clicking and choosing **open with "Gdebi Package Installer"**? 

I went to the Opera website and they don't have a Jaunty deb file listed for download yet. Which one are you using?

---

### Post by adriantsl on 2009-05-04
Take a look here [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04-p4](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04-p4)

---

### Post by freeman2000 on 2009-05-04
I just went to the Opera website and downloaded the Opera 9.64 Ubuntu version for Intrepid 8.10 (latest version) even though I am running Jaunty 9.04.  I downloaded the file (8.4mb) to my desktop, then I opened up "GDebi Package Installer" (in Applications --> System Tools) and dragged the Opera .deb file onto it and installed it.  It placed a link for Opera in Applications --> Internet.  If you don't have GDebi installed, go to Synaptics, search for "gdebi" and download it.  Opera is running real good in Jaunty with no problems.  Give it a try.  Good luck.

---

### Post by Sarai the Geek on 2009-05-04
You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```

Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Finally...
```
sudo apt-get install opera
```

---

### Post by Didius Falco on 2009-05-04
> **Sarai the Geek said:**
> You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```Finally...
```
sudo apt-get install opera
```

+1 on the repo install. I try to avoid installing deb packages whenever I can.

---

### Post by Sarai the Geek on 2009-05-04
> **Didius Falco said:**
> +1 on the repo install. I try to avoid installing deb packages whenever I can.

Repo installs are also significantly easier to uninstall...

---

### Post by binbash on 2009-05-04
There is a deb at opera's official download site, also a repository.YOu do not need to compile it.

---

### Post by Testrum on 2009-05-05
> **Sarai the Geek said:**
> You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```

Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Finally...
```
sudo apt-get install opera
```
Never mind got it to work :p tyvm.

---

### Post by aacs on 2009-05-12
How exactly do you try to compile a closed-source package? "Hard time compiling"?  ehh..

---

### Post by MontelEdwards on 2009-05-12
dude
just tell the guy to manually install the deb
```
wget http://www.augemedia.de/opera/linux/964/final/en/i386/opera_9.64.2480.gcc4.qt3_i386.deb
```
 thennn
```
sudo dpkg -i opera_9.64.2480.gcc4.qt3_i386.deb
```

---

### Post by Sarai the Geek on 2009-05-12
> **m.deonte said:**
> dude
just tell the guy to manually install the deb
```
wget http://www.augemedia.de/opera/linux/964/final/en/i386/opera_9.64.2480.gcc4.qt3_i386.deb
``` thennn
```
sudo dpkg -i opera_9.64.2480.gcc4.qt3_i386.deb
```

Well, technically it would be better to instruct him to download from the repos, because stuff installed via the repositories is updated automagically and also much easier to install...

---

### Post by peterx14 on 2009-07-25
> **Sarai the Geek said:**
> You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```

Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Finally...
```
sudo apt-get install opera
```

No longer works! :(

They seem to have changed their directory structure now so it lists various Debian releases... so is Jaunty most like Etch or Lenny?

---

### Post by SunnyRabbiera on 2009-07-25
> **peterx14 said:**
> No longer works! :(

They seem to have changed their directory structure now so it lists various Debian releases... so is Jaunty most like Etch or Lenny?

try the ubuntu installer again on the opera site, you can try the version for hardy as it really doesnt matter

---

### Post by LookTJ on 2009-07-25
> **SunnyRabbiera said:**
> try the ubuntu installer again on the opera site, you can try the version for hardy as it really doesnt matter
Jaunty Hardy and Ibex uses the same package.

peterx14, did you try ```
sudo apt-get update
``` to refresh the listings and install opera?

:)

---

### Post by SunnyRabbiera on 2009-07-25
> **LookTJ said:**
> Jaunty Hardy and Ibex uses the same package.

I forgot, I have not used Ubuntu in a while so I am bound to forget something :)
Maybe try the one for gutsy?

---

### Post by peterx14 on 2009-07-25
> **LookTJ said:**
> Jaunty Hardy and Ibex uses the same package.

peterx14, did you try ```
sudo apt-get update
``` to refresh the listings and install opera?

:)

Yeah - that's where I noticed the error:

```

pryan@kafka:~$ sudo apt-get update

....SNIP....

Ign http://deb.opera.com stable/non-free Packages                    
Err http://deb.opera.com stable/non-free Packages
  404 Not Found
Hit http://download.virtualbox.org jaunty Release.gpg
Ign http://download.virtualbox.org jaunty/non-free Translation-en_GB
Hit http://download.virtualbox.org jaunty Release         
Hit http://download.virtualbox.org jaunty/non-free Packages
W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
pryan@kafka:~$ 

```

Using a browser to check the URL does indeed show a 404 -- so like I say, the Opera folks must've been moving things around.

This is no biggie btw! I would just like to be able to keep Opera up-to-date via apt rather than have to download manually, but I'm not particularly desperate to have the latest Opera version or anything!! :D

---

### Post by LookTJ on 2009-07-25
peterx14, seems that it's stable should be replaced with lenny(or sid if you like)

---

### Post by peterx14 on 2009-07-25
> **LookTJ said:**
> peterx14, seems that it's stable should be replaced with lenny(or sid if you like)

Brilliant -- thank you!! :D

---

### Post by ssdt on 2009-07-25
Download the deb packagae from here [http://www.opera.com/browser/](http://www.opera.com/browser/) and then double click it. its a graphical installer which will take you all the way through.

---

### Post by strungoutfan78 on 2009-07-26
It appears to me after navigating the site that things have moved to:
[http://deb.opera.com/opera/pool/non-free/o/opera/]("http://deb.opera.com/opera/pool/non-free/o/opera/")
I haven't tried it yet but this may work instead?

---

