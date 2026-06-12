---
title: "Image Uploading Problem"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by maerceci002 on 2009-05-04
I just installed Ubuntu 9.04 on my computer Tuesday (coming from Windows). I've been trying to upload a set of about 50 pictures to a website but for some reason it won't work. I've tried just uploading a zip file of the whole set, and I've also tried uploading just a single picture at a time, on both my computer and a friend's Mac. On my computer the whole site just freezes and I don't see the percent there, on the Mac the percent does increase, it just takes 20 minutes to reach 100%, and then the images don't even come onto the screen. It doesn't do anything. I've done some Google-ing, and not had any luck. I've asked my boyfriend for help (since he made the switch months before me) and I've searched the forum, I could just be missing it and if so, please direct me to the right thread, but does anyone know what's wrong? 

Thanks in advance :D

---

### Post by nhasian on 2009-05-04
by any chance are you talking about facebook?
i had the same problem until i changed the default version of java.

open a terminal by going to Appliations->Accessories->Terminal and type:

```
sudo update-alternatives --config java
```

try switching it to:

/usr/lib/jvm/java-6-sun/jre/bin/java

for more info take a look at [http://www.openguru.com/2009/04/ubuntu-changing-default-java-version.html](http://www.openguru.com/2009/04/ubuntu-changing-default-java-version.html)

---

### Post by maerceci002 on 2009-05-06
No, I'm actually talking about suicide girls :D I tried doing that, and it said I had no alternatives?

---

### Post by lyttelmonkey on 2009-05-08
Ha! I'm having the same problem with SG myself, and I came on here for some answers. If anyone has any advice, I'd really appreciate it.

---

### Post by nhasian on 2009-05-08
can you go to System->Administration->synaptic Package manager and make sure you have installed sun-java6-jre ?  if it wasnt selected, install it then run that "sudo update-alternatives --config java" command

let me know how it works

---

### Post by lyttelmonkey on 2009-05-14
I did that, and it said I already had it installed. Any other ideas? Thank you.

---

### Post by nhasian on 2009-05-15
you can have several different implementations of java installed at the same time but to tell the computer which one to use by default you need to use the terminal command:

```
sudo update-alternatives --config java
```

if that doesnt work try copy pasting this one in a terminal:

```

ln -s /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins
```

---

### Post by lyttelmonkey on 2009-05-23
Hello again,

I tried copying and pasting that last thing, and this came up

ln: creating symbolic link `/home/das/.mozilla/plugins': File exists 

I have no idea what this means... I might just try uploading the images from a friend's computer, but thank you for all your help.:)

---

### Post by rob2uk on 2009-05-23
So two people using three different machines are having exactly the same problem at the same time...

Are you sure it's not a problem at the site's end rather than yours?

---

### Post by nhasian on 2009-05-24
well i wanted to test an upload to SG myself but didnt see where to do it without having to pay to join.  am i missing something?  Or if you need an account maybe someone can msg me a temporary username/password to troubleshoot it.

---

### Post by lyttelmonkey on 2009-06-07
You have to either have a paid account or a model account (and you need to send in some photos of yourself to get one of those ;)) to upload photos. I'm pretty sure it isn't a problem with the site. Maybe it just isn't compatible with Ubuntu.

---

### Post by nhasian on 2009-06-12
actually it could be due to bad coding of the website but it is far more likely that its just a java problem if your using the wrong version.

> **lyttelmonkey said:**
> You have to either have a paid account or a model account (and you need to send in some photos of yourself to get one of those ;)) to upload photos. I'm pretty sure it isn't a problem with the site. Maybe it just isn't compatible with Ubuntu.

---

