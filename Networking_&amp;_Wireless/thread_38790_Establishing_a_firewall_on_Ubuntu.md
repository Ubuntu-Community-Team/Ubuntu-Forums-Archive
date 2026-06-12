---
title: "Establishing a firewall on Ubuntu?"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by Paul Panks on 2005-06-02
How do I establish a firewall on Ubuntu? Does Ubuntu come with a built-in firewall?

Paul

---

### Post by Seti on 2005-06-02
You may want to check out the instructions for setting up the Firestarter firewall frontend for iptables. 
[Firestarter](http://www.ubuntuguide.org/#firestarter)

---

### Post by doomchild on 2005-06-05
I'm going insane.
sudo apt-get install firestarter doesn't find anything. I just installed Kubuntu 5.04 for AMD64, and used Firestarter quite succesfully in the previous Kubuntu 32-bit I had.

I tried to download the tarballs from packages.ubuntu.org, packages.debian.org and even from Firestarter's homepage. I went through the required packages list, apt-get installing each one of them. FIrestarter 0.9.3 config ends to

"configure: error: Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them."

and firestarter 1.0.1 configure ended in complaining about missing XML::perl parser.

**So please someone tell me what rows to add to /ect/apt/sources.list so I can install firestarter with apt** . I had to comment some rows from current sources.list, since those repositories don't work, and some of us.* repositories have been changed to working ones here in finland (eg fi.archive...).

My sources.list looks like this:

## Uncomment the following two lines to fetch updated software from the network
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by Strife on 2005-06-05
See [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by doomchild on 2005-06-05
I've tried that before, but I tried it again. The result is still quite horrible. After doing as the link suggests, and then trying sudo apt-get install firestarter, I get the following errors:

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages( /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-a
md64_Packages) - stat (2 No such file or directory)

< And here's tons of these couldn't stat this-and-that errors >

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d                                                            ists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package firestarter

---

### Post by berdoo on 2005-06-05
The problem is your repositories are not set up properly. 

If you copy and paste the repositories from http://www.ubuntuguide.org/#extrarepositories then replace all the repositories that have "us.archive.ubuntu.com" with "archive.ubuntu.com", then update, it will  work for you.

---

### Post by doomchild on 2005-06-06
Oh.
I forgot to do the update... did as you said and it worked like a dream  :oops: 
So thank you so very much!

---

