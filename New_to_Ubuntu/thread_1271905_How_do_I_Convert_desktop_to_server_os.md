---
title: "How do I Convert desktop to server os"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by slvfx on 2009-09-21
Bought a tower to Run ubuntu server. Store installed desktop instead of server. How do I replace the desktop with the server?

---

### Post by mjwalfredo on 2009-09-21
You can go to [www.ubuntu.com](www.ubuntu.com), download the server install CD, wipe the desktop OS and then install the server edition from server install media.

---

### Post by slvfx on 2009-09-21
How do i wipe the desktop os?

---

### Post by ks07 on 2009-09-21
To put a long story short, just install using the server CD over the top of the desktop installation. You shouldn't need to do anything else, although you may have to reformat the disk in the installer's partitioner to make sure all desktop files are removed.

---

### Post by SlugSlug on 2009-09-21
> **slvfx said:**
> How do i wipe the desktop os?


you do know server is purely command line don't you?

---

### Post by mjwalfredo on 2009-09-21
I have not personally installed Ubuntu server but there should be an option to reformat your partitions during installation.  This will effectively wipe the hard drive if you choose to reformat everything.

How you reformat and install will depend on how your partitions are currently set up and how you want them to be set up.

---

### Post by slvfx on 2009-09-21
yes

---

### Post by mjwalfredo on 2009-09-21
> **SlugSlug said:**
> you do know server is purely command line don't you?

Yeah, it crossed my mind as to whether or not he is ready to take on installing Ubuntu server based on the questions.

I don't mean to scare you away, as it's not really all that hard but you need to make sure that you do your research before taking this on.

Also, the Desktop version should be able to do absolutely anything the Server version can.  Are you absolutely sure you want to run Server?

---

### Post by slvfx on 2009-09-21
I am just starting out. I like the desktop. I want to set up the apache webserver, my sql etc. Do I just do it with the terminal with the desktop or do I do something special?

---

### Post by SlugSlug on 2009-09-21
stick with desktop that way you have firefox ;)

[http://www.google.co.uk/search?q=ubuntu+lamp&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+lamp&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a)

---

### Post by slvfx on 2009-09-21
Perfect..thank you very much. Did the first exercise with the apache and it works.

---

### Post by chrisinspace on 2009-09-21
The only difference between the desktop and server versions are the packages installed.  If you want to set up apache and mysql, just go to the package manager and install them.  You can also do this from the command line using the 'apt-get install' command.

---

