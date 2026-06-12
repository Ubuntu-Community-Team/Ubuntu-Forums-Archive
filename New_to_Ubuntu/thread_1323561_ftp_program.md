---
title: "ftp program"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by wordmaster on 2009-11-11
Hi Y'all,

Is there a graphical ftp program similar to wsftp available in Ubuntu? If so, how do I get it and start it?

If not, what do I use for ftp in Ubuntu?

Thank you kindly for your help.

---

### Post by Zyro11 on 2009-11-11
I use a FTP add on in Firefox called FireFTP, works good enough for me.   sadly I don't know of any FTP programs that work Ubuntu.

---

### Post by coronacolada on 2009-11-11
Go for Filezilla! I use it and it works great. Additionally, you can connect to servers from the "places" dropdown on your top bar,  though I sometimes have trouble connecting to SSH sites with that. 

```
sudo apt-get install filezilla
```

-tom

sic luceat lux

---

### Post by itsbrad212 on 2009-11-11
use a program called filezilla:

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by dragonboss on 2009-11-11
There are several in the ubuntu software center just type in ftp and they'll be listed.

---

### Post by Dude-PWB- on 2009-11-11
gftp is a simple and decent ftp client, it's in synaptic package manager.

---

### Post by falconindy on 2009-11-11
Nautilus integrates the ability to connect to an ftp server. On the main menu under Places, click 'connect to server' and select 'ftp with login'. Fill in your details and you'll be prompted for your password on connecting.

---

### Post by greyebeard on 2009-11-13
I have used FileZilla in both xp and ubuntu since 8.04 and would happily go back to the windoze version if it was still on the system.  The version on the repo hangs, does not follow the default file exists settings, etc.  Ver 3.3.3 (stable) has just been released.  
Would someone PLEASE tell me how to install the tar.gz files

---

### Post by camaron1 on 2009-11-13
> **greyebeard said:**
> I have used FileZilla in both xp and ubuntu since 8.04 and would happily go back to the windoze version if it was still on the system.  The version on the repo hangs, does not follow the default file exists settings, etc.  Ver 3.3.3 (stable) has just been released.  
Would someone PLEASE tell me how to install the tar.gz files

Acording to Filezilla site the last stable release is 3.3.0. you can get a deb. package from [here]("http://www.getdeb.net/updates/filezilla") . When it finishes downloading you'll be ask your password and will be installed automatically

---

### Post by Iksf on 2009-11-13
$ ftp {domain}
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> get
(remote-file) file.txt
(local-file) file.txt


Or just use FireFTP, or Filezilla, KDE's one is quite nice too, forgotten what its called though. Begins with a K :D

Personally i always use FireFTP or CLI

---

### Post by durand on 2009-11-13
> **Dude-PWB- said:**
> gftp is a simple and decent ftp client, it's in synaptic package manager.

GFTP is great. I also use the file manager's built in ftp client a lot. Just go to Places > Connect to Server.

---

### Post by XCan on 2009-11-14
GFTP is nice, but it doesn't support FTPS. I find Nautilus' built in client very slow for some reason. Thus I use gftp for local transfers or SFTP, and filezilla for FTPS.

---

### Post by Paqman on 2009-11-14
I just use Nautilus. It's a little slow, but what FTP isn't?

---

### Post by andrew.46 on 2009-11-14
Hi XCan,

> **XCan said:**
> GFTP is nice, but it doesn't support FTPS.

If you definitely mean [FTPS ]("http://en.wikipedia.org/wiki/FTPS"), or FTP over SSL, gFTP does in fact support this, I attach a screenshot to demonstrate this.

Andrew

---

### Post by XCan on 2009-11-14
oO! Perhaps that support was added in the version provided in Karmic? I'm on Jaunty and I just checked on my machine and I can't select FTPS as protocol. :( Please share how you enabled it if you managed to get it working in Jaunty as well. :)

---

### Post by andrew.46 on 2009-11-15
Hi XCan,

> **XCan said:**
> oO! Perhaps that support was added in the version provided in Karmic? I'm on Jaunty and I just checked on my machine and I can't select FTPS as protocol. :( Please share how you enabled it if you managed to get it working in Jaunty as well. :)

I have enabled FTPS under Karmic Koala but this should also work for Jaunty except the filenames for gFTP will be different. It is interesting to note that ssl connections with gFTP has been specifically removed from the gFTP build for a licensing problem but easy enough to *rebuild* the package so ssl connections are available. One mini-guide coming up :).


First create a build directory:

```

$ cd $HOME/Desktop
$ mkdir build
$ cd build

```

Then install the build tools:

```

$ sudo apt-get install build-essential fakeroot dpkg-dev

```

Then add the build dependencies for gFTP as well as the *new* dependency of the ssl library:

```

$ sudo apt-get build-dep gftp
$ sudo apt-get install libssl-dev

```

Next grab the source and unpack it, remember if you are using Jaunty the filename for the .dsc file will be different:

```

$ apt-get source gftp
$ dpkg-source -x gftp_2.0.19-1ubuntu1.dsc

```

Now to adjust the debian rules, this use of sed is a little crude so hopefully no sed purist will read this post :). Remember again that the directory name will be different under Jaunty :

```

$ cd gftp-2.0.19/
$ sed -i '/\-\-disable\-ssl/d' debian/rules
$ sed -i 's/\-\-enable\-textport\=yes \\/\-\-enable\-textport\=yes/' debian/rules

```

And now build the package, install it and clean up the mess:

```

$ fakeroot debian/rules binary
$ sudo dpkg -iR ../
$ fakeroot debian/rules clean	

```

It looks a little complex but this will give you the functionality removed by the packagers :).

All the best,

Andrew

---

### Post by wordmaster on 2009-11-15
Thank you all very much!

---

### Post by XCan on 2009-11-15
> **andrew.46 said:**
> Hi XCan,



I have enabled FTPS under Karmic Koala but this should also work for Jaunty except the filenames for gFTP will be different. It is interesting to note that ssl connections with gFTP has been specifically removed from the gFTP build for a licensing problem but easy enough to *rebuild* the package so ssl connections are available. One mini-guide coming up :).


First create a build directory:

```

$ cd $HOME/Desktop
$ mkdir build
$ cd build

```

Then install the build tools:

```

$ sudo apt-get install build-essential fakeroot dpkg-dev

```

Then add the build dependencies for gFTP as well as the *new* dependency of the ssl library:

```

$ sudo apt-get build-dep gftp
$ sudo apt-get install libssl-dev

```

Next grab the source and unpack it, remember if you are using Jaunty the filename for the .dsc file will be different:

```

$ apt-get source gftp
$ dpkg-source -x gftp_2.0.19-1ubuntu1.dsc

```

Now to adjust the debian rules, this use of sed is a little crude so hopefully no sed purist will read this post :). Remember again that the directory name will be different under Jaunty :

```

$ cd gftp-2.0.19/
$ sed -i '/\-\-disable\-ssl/d' debian/rules
$ sed -i 's/\-\-enable\-textport\=yes \\/\-\-enable\-textport\=yes/' debian/rules

```

And now build the package, install it and clean up the mess:

```

$ fakeroot debian/rules binary
$ sudo dpkg -iR ../
$ fakeroot debian/rules clean	

```

It looks a little complex but this will give you the functionality removed by the packagers :).

All the best,

Andrew

Awesome, it worked great for one of my newly upgraded Karmic machines, going to try it on a Jaunty soon. Thanks for sharing!

Sorry for the partial stealing of the thread wordmaster. :oops:

---

### Post by andrew.46 on 2009-11-15
Hi XCan,

> **XCan said:**
> Awesome, it worked great for one of my newly upgraded Karmic machines, going to try it on a Jaunty soon. Thanks for sharing!

Great news :). This technique can be used, with usually significant variation, to reshape most of the Ubuntu packages.

> Sorry for the partial stealing of the thread wordmaster. :oops:

My apologies as well!!

Andrew

---

### Post by FreedomOverdose on 2010-07-25
> **camaron1 said:**
> Acording to Filezilla site the last stable release is 3.3.0. you can get a deb. package from [here]("http://www.getdeb.net/updates/filezilla") . When it finishes downloading you'll be ask your password and will be installed automatically
That package is outdated... synaptic and ubuntu software center both have an outdated (3.3.1) version, meanwhile the current version is 3.3.3, released more than a month ago. How do I update from 3.3.1 to 3.3.3?

---

