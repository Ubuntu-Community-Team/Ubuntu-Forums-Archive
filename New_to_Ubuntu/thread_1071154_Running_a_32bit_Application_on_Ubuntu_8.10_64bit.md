---
title: "Running a 32bit Application on Ubuntu 8.10 64bit?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by esender on 2009-02-15
I just downloaded the Eclipse Zend PDT for Linux which I believe was designed for the 32bit framework.

I try to execute the file with the "./eclipse" command, but it keeps failing.

How can I execute a 32bit application in the 64bit Ubuntu environment? 

[http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)

---

### Post by handy on 2009-02-15
You need ***32bitLibs***.

Try a search in Synaptic package manager, I think you will quickly find what you need there.

---

### Post by esender on 2009-02-15
> **handy said:**
> You need ***32bitLibs***.

Try a search in Synaptic package manager, I think you will quickly find what you need there.

Well, I just did that. I actually installed everything under "ia32"

Now, the "./eclipse" command does execute, but absolutely nothing happens...

Heh, so what do I do now?

---

### Post by halovivek on 2009-02-16
you can try some from [here ]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/")how to install.

---

### Post by stumbleUpon on 2009-02-16
> **esender said:**
> I just downloaded the Eclipse Zend PDT for Linux which I believe was designed for the 32bit framework.

I try to execute the file with the "./eclipse" command, but it keeps failing.

How can I execute a 32bit application in the 64bit Ubuntu environment? 

[http://www.zend.com/en/community/pdt](http://www.zend.com/en/community/pdt)

Eclipse is in the universe repositories for 64-bit ubuntu. So you can directly install from there. In a terminal do

```
sudo aptitude install eclipse
```

---

### Post by esender on 2009-02-16
> **stumbleUpon said:**
> Eclipse is in the universe repositories for 64-bit ubuntu. So you can directly install from there. In a terminal do

```
sudo aptitude install eclipse
```

Thanks, but I was looking for a specific version of Eclipse with Zend's PDT.

What I ended up doing was scrapping my 64bit and installing anew with 32bit. Now it seems to work :) 

But I am new linux and every step of the way I am coming across random problems haha, I'm glad this is a 3 day weekend.

---

### Post by joey-elijah on 2009-02-16
> **esender said:**
> Thanks, but I was looking for a specific version of Eclipse with Zend's PDT.

What I ended up doing was scrapping my 64bit and installing anew with 32bit. Now it seems to work :) 

But I am new linux and every step of the way I am coming across random problems haha, I'm glad this is a 3 day weekend.

That was extreme, you could've just forced installed it with the --force architecture command.

---

### Post by esender on 2009-02-16
> **joey-elijah said:**
> That was extreme, you could've just forced installed it with the --force architecture command.

Hmm, I didn't know about that command. Either way, I'd rather everything run smoothly and standardly, especially now as I am a total newbie to this.

And honestly, scrapping and reintalling a new Ubuntu took less than 40 minutes from downloading the new ISO to being back to right where I was before.

---

### Post by Vico Vicario on 2009-02-16
Just for future reference: 32bit Eclipse uses swt-gtk toolkit, so it needs a 32bit java. You can install ia32-sun-java6-bin to run java apps that link to native 32bit libs. Just dont forget to point JAVA_HOME to the correct version before running Eclipse, or edit the startup file.

V.

---

