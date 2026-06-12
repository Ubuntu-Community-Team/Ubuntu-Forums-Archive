---
title: "Installing VLC player from source."
date: 2009-06-05
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-05
Upon installing the source of VLC player, this message comes:
> 
configure: error: Please install GL development package. Alternatively you can also configure with --disable-glx.
Please help me continue.

---

### Post by eeeandrew on 2009-06-05
why are you installing from source? VLC player is available from the repositories. Type in terminal:

> sudo apt-get install vlc

---

### Post by melrokz on 2009-06-05
My friend is running Ubuntu 9.04 with a ATI mobility radeon hd 2600 card + 2 gb RAM. VLC player does not work properly when installed through the repos. It displays the video in a new window called 'xvideo' The video output setting is 'opengl'

---

### Post by theluddite on 2009-07-02
I had this same problem and fixed it by installing libglu1-mesa-dev and mesa-common-dev.

---

### Post by sadaruwan12 on 2009-07-02
It's there in the VLC web site how to install it in Ubuntu I have it go it directly from the repository and it works like a charm.

---

### Post by reeseslover531 on 2009-07-02
That is an issue with the version of VLC in the repos, you can install a later version from a ppa [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

---

### Post by juanoleso on 2009-07-02
> **theluddite said:**
> I had this same problem and fixed it by installing libglu1-mesa-dev and mesa-common-dev.

+1

Also try:

```

sudo apt-get build-dep vlc

```

if you haven't already.  That will download most, if not all, the packages necessary to build VLC.  If ./configure gives you more errors, do a search in synaptic for the *-dev of that package.  Here is a link to VLC's wiki instructions for building from source.

[[COLOR="Blue"]UnixCompile - VideoLAN Wiki[/COLOR]]("http://wiki.videolan.org/UnixCompile")

They helped me.

---

