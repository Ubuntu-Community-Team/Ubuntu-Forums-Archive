---
title: "Calcurse will not import .ics"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Peacefulpieofdeath on 2009-11-01
Calcurse wont import my .ics file... I wanted to use it in conky but its not working since I upgraded to 9.10.

> 
eric@eric-desktop:~$ calcurse -i ~/School/Home.ics
mem.c: 176: xfree: null pointer


Thanks for the help in advance!

---

### Post by Brandon Williams on 2009-11-01
There are a couple of bugs in calcurse-2.6 for the particular use case. I ran into them myself a few days ago, so I downloaded the latest calcurse release (2.7), fixed one of the bugs that is still present in that version, and updated the packaging. Since reading your post, I uploaded the source packages to [my ppa](https://launchpad.net/~opensource-subakutty/+archive/ppa) and it's building now.

Even with this version, there's still a bug that affects this use case: attempting to load an ics file will fail due to missing directories. You can prevent this by creating the necessary directory structure first:
```
mkdir -p ~/.calcurse/notes
```

---

### Post by Peacefulpieofdeath on 2009-11-01
I can't add your source... i have added the key and the source itself...
Also im not sure what "building" on the package means but i take it its not done...

If i am doing something wrong, or anything can you please explain.

Also I tried adding the notes directory but it did noting.

Thanks for trying to help at least.

---

### Post by Brandon Williams on 2009-11-01
Building means that the binary package isn't ready yet. It doesn't normally take so long for the build to start. It should be there eventually.

What do you mean when you say that you can't add my source? Is it giving you an error when you try to update? Did you list karmic or jaunty as the release. I uploaded for a jaunty build. I'll upload for karmic later if the jaunty build doesn't work on my karmic machine. I would just download the deb (when it's ready) and install it using dpkg if I were you.

EDIT: The builds for i386, amd64, and lpia are all ready. Despite being built for jaunty, the software can be run and installed on karmic, too.

---

### Post by Peacefulpieofdeath on 2009-11-02
Ok i beleave the calendar is now working... but i downloaded as deb...

Your source on the other hand is still not working... after update it gives me this.

> W: Failed to fetch [http://ppa.launchpad.net/opensource-subakutty/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/opensource-subakutty/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found


---

### Post by Brandon Williams on 2009-11-02
I'm glad you get it working.


> **Peacefulpieofdeath said:**
> Your source on the other hand is still not working... after update it gives me this.

As I noted above, I uploaded it for jaunty, not karmic, so if you want to install directly from my ppa, you have to specify jaunty is the release in your sources.list file. It will look like this:
```
deb http://ppa.launchpad.net/opensource-subakutty/ppa/ubuntu jaunty main
```

I might upload it for karmic at another time, but only when I update all of my packages for karmic. It's probably best for you to stick with the manually installed deb for now.

---

### Post by Peacefulpieofdeath on 2009-11-02
Ok, well thanks a lot for your help...

---

