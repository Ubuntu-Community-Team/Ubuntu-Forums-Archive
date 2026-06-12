---
title: "Installing files using apt-get"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Volume on 2009-07-26
So, I have a question.  Where do all of the files go after I use "apt-get install"?  How can I find out what directory they go to, and can I change that directory?

Thanks

---

### Post by philcamlin on 2009-07-26
[http://www.howtogeek.com/howto/ubuntu/see-where-a-package-is-installed-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/see-where-a-package-is-installed-on-ubuntu/)

and you cant change the directory because it installs in more then one :popcorn:

---

### Post by Volume on 2009-07-26
Nice link.  However, what does it mean to know where the .conf file is?  What type of power do I have with the knowledge of the location of that file--really I guess I'm asking what good does that do me?

Is that sort of the synonym to the windows *.exe file?

---

### Post by llamabr on 2009-07-26
It has nothing to do with an exe file.  It's a configuration file, where you can change where they go.  But I wouldn't.  They go to /var/cache/apt/archives/

cd there, and have a look.

---

