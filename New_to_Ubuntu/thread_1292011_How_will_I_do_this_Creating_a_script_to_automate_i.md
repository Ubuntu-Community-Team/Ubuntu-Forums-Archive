---
title: "How will I do this? Creating a script to automate installation"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by realskinner on 2009-10-15
Hey everyone this is my first thread here. And hope I am in the correct section for this.

And also I'm very new to linux and ubuntu and I will be very glad if someone can help me with this one.

Anyway this is my problem.

I am creating a script to install this 2.

sudo apt-get install libgtk2.0-dev
sudo apt-get install libcurl4-gnutls-dev

and my script looks like this
> #!/bin/bash
sudo apt-get install libgtk2.0-dev
sudo apt-get install libcurl4-gnutls-devbut the problem is that every time these 2 
sudo apt-get install libgtk2.0-dev
 sudo apt-get install libcurl4-gnutls-dev

gets executed I get this message in the terminal

> The following packages will be upgraded:
  libfreetype6 libglib2.0-0 libxcb-render0 libxcb1 libxi6
5 upgraded, 59 newly installed, 0 to remove and 245 not upgraded.
Need to get 20.8MB of archives.
After this operation, 68.6MB of additional disk space will be used.
Do you want to continue [Y/n]?So, I am wondering if there is a way that I can include my "Y" answer on my script so that I won't be inputing "Y" every time I run the script.

Guys I really appreciate any of your time...

Thanks a lot in advance....

---

### Post by rampageoberon on 2009-10-15
> **realskinner said:**
> Anyway this is my problem.

sudo apt-get install libgtk2.0-dev
sudo apt-get install libcurl4-gnutls-dev

and my script looks like this
but the problem is that every time these 2 
sudo apt-get install libgtk2.0-dev
 sudo apt-get install libcurl4-gnutls-dev

So, I am wondering if there is a way that I can include my "Y" answer on my script so that I won't be inputing "Y" every time I run the script.


Hi, You can use the -y flag to answer yes to the question. For example:

```
sudo apt-get install -y libgtk2.0-dev
```

---

### Post by petersohn on 2009-10-15
Another suggestion: You can do the following:
```
sudo apt-get -y install libgtk2.0-dev libcurl4-gnutls-dev
```

---

### Post by realskinner on 2009-10-15
Wow that was FAST... awesome bro... It works...

Thank you very much...

By the way I would just like to add...

Is there also a way that I can launch a message box from the script?

---

### Post by rampageoberon on 2009-10-15
> **realskinner said:**
> Is there also a way that I can launch a message box from the script?

Erm, you might find 'zenity' useful for message boxes.

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

---

### Post by realskinner on 2009-10-15
Thank you very much guys....

petersohn and rampageoberon I really appreciate the BIG help...

Thanks

---

