---
title: "Where did the package for amarok 2 go?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-03-05
I've followed the guide that has you add the "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main" line to your third-party repos.  It says that Synaptic/Adept will then provide a package for amarok 2 but no such thing happens.

Interestingly enough, I've used this method before and it worked - but only once.

Did the package get removed...?

---

### Post by zvacet on 2009-03-06
Dis you refreshed your source list after adingg new repo?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by InfectedWithDrew on 2009-03-08
> **zvacet said:**
> Dis you refreshed your source list after adingg new repo?

```
sudo apt-get update && sudo apt-get upgrade
```
Yes.

---

### Post by markbuntu on 2009-03-09
You can just go to the http and find the debs and install them yourself.

---

### Post by InfectedWithDrew on 2009-03-11
> **markbuntu said:**
> You can just go to the http and find the debs and install them yourself.All I could find were tarballs... do those contain debs?

----------------
Now playing: [Strung Out - Velvet Alley](http://www.foxytunes.com/artist/strung+out/track/velvet+alley)

---

### Post by markbuntu on 2009-03-12
The debs are here

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/)

---

### Post by InfectedWithDrew on 2009-03-13
> **markbuntu said:**
> The debs are here

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/)

Which .debs should I go for?  I'm using Ubuntu Intrepid.

----------------
Now playing: [Within Temptation And The Metropole Orchestra - All I Need](http://www.foxytunes.com/artist/within+temptation+and+the+metropole+orchestra/track/all+i+need)

---

### Post by llyshon on 2009-03-15
I had this same problem.

I was able to install from a terminal by typing:

sudo apt-get install amarok-kde4

It installed even though synaptic didn't show the package.

Good luck!

---

### Post by Lord_Dicranius on 2009-03-16
> **llyshon said:**
> I had this same problem.

I was able to install from a terminal by typing:

sudo apt-get install amarok-kde4

It installed even though synaptic didn't show the package.

Good luck!

Same here.  I couldn't find it through Synaptic, but when I did "sudo apt-get install amarok-kde4" from the CLI, it showed the package in the "NEW packages that will be installed" section.  Now I just need to fix these couple of errors I'm getting...

---

### Post by markbuntu on 2009-03-16
You should hit the reload button on synaptic regularly because if the packages have been updated they will not show up until you reload.

---

### Post by Lord_Dicranius on 2009-03-17
> **markbuntu said:**
> You should hit the reload button on synaptic regularly because if the packages have been updated they will not show up until you reload.

Hitting "reload" didn't work for me.  It still wouldn't show up in Synaptic.

---

### Post by InfectedWithDrew on 2009-03-17
> **llyshon said:**
> I had this same problem.

I was able to install from a terminal by typing:

sudo apt-get install amarok-kde4

It installed even though synaptic didn't show the package.

Good luck!

Thank you, this was successful.

----------------
Now playing: [The Tragically Hip - When the Weight Comes Down](http://www.foxytunes.com/artist/the+tragically+hip/track/when+the+weight+comes+down)

---

### Post by samuraitor on 2009-04-01
> **InfectedWithDrew said:**
> Thank you, this was successful.

----------------
Now playing: [The Tragically Hip - When the Weight Comes Down](http://www.foxytunes.com/artist/the+tragically+hip/track/when+the+weight+comes+down)

I tried to install amarok 2 through CLI and synaptic. No luck, I keep getting the same message from CLI and synaptic when tried to install amarok2.

This is the only message I get : amarok-kde4:  Depends: libqt4-webkit but it is not going to be installed

How do I go about to fixing this ?

---

### Post by abn91c on 2009-04-01
> **samuraitor said:**
> I tried to install amarok 2 through CLI and synaptic. No luck, I keep getting the same message from CLI and synaptic when tried to install amarok2.

This is the only message I get : amarok-kde4:  Depends: libqt4-webkit but it is not going to be installed

How do I go about to fixing this ?
add the repos mentioned before then sudo apt-get update then try the sudo apt-get install amarok-kde4

---

### Post by hyper_ch on 2009-04-02
the packages version in that repo is quite old. Much better to use the Amarok 2 Neon Project - see my repo generator in my sig.

However if you want to be truly up-to-date you can compile amarok2 from svn yourself. I wrote an extensive guide on that for intrepid (won't work on jaunty).

---

