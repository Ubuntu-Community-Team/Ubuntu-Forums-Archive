---
title: "Installing Java SDK"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by osullic on 2010-01-07
I'm new to Ubuntu (and not very experienced with Linux in general).
 
I'm trying to install the Java SDK, and I'm following the instructions at [http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#self-extracting)
 
This might be a silly question (so hopefully this is the right place for it!), but the instructions say, "Change directory to the location where you would like the files to be installed". Well, I'm not sure where I should want the files to be installed! In Windows, it would be Program Files, but as I said, I'm not very experienced with Linux.
Could someone give me some pointers?
Thanks

---

### Post by Methuselah on 2010-01-07
Open a terminal

```

sudo apt-get install sun-java6-jre sun-java6-jdk

```

If you need something like an IDE try Netbeans or Eclipse.
You can browse for them in Applications->Software Center.

As a rule in Ubuntu, downloading software from vendor's site is a last resort.
If the software is gratis it can usually be obtained using the Ubuntu software installation tools.

---

### Post by donato roque on 2010-01-07
There's an alternative to sun java and I do recommend it.  You can also find it in synaptic.  Type search openjdk.

Use the following methods to search for software within Ubuntu:

Terminal.  Type code:  sudo apt-get install (software name)

Synaptic Manager.  Go to System-->Administration

Software Center.  Go to Application-->Software Center

---

### Post by Mighty_Joe on 2010-01-07
> **Methuselah said:**
> 
As a rule in Ubuntu, downloading software from vendor's site is a last resort.


Sun Java is a special case.  It is not going to be updated in the Karmic repository, even for security updates (see [this bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") for some discussion).  [OpenJDK]("http://openjdk.java.net/") is the default Java implementation for Ubuntu going forward but it is anyone's guess how well that release will track with Sun's.  
osullic, [Here]("http://sites.google.com/site/easylinuxtipsproject/java") are instructions for installing the Java Linux binary on Ubuntu.

---

### Post by Methuselah on 2010-01-07
> **Mighty_Joe said:**
> Sun Java is a special case.  It is not going to be updated in the Karmic repository, even for security updates (see [this bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") for some discussion).  [OpenJDK]("http://openjdk.java.net/") is the default Java implementation for Ubuntu going forward but it is anyone's guess how well that release will track with Sun's.  
osullic, [Here]("http://sites.google.com/site/easylinuxtipsproject/java") are instructions for installing the Java Linux binary on Ubuntu.

OK, cool.
I didn't know that since I used OpenJdk.

---

