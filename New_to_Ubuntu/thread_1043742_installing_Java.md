---
title: "installing Java"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by colsandurz on 2009-01-18
I need to install Java to use smartSVN.  When I run smartSVN for the first time it tells me that it can't find /bin/java (it's not there, I did a ls | grep java with no results).  I tried to install Java using ```
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-bin
``` 
and there is still no /bin/java... I'm not really sure what to do here.

EDIT: added the in the 6 to sun-java6-bin

---

### Post by metallicamike on 2009-01-18
try getting sun java 6 runtime from add/remove

---

### Post by spcwingo on 2009-01-18
Try:

```
sudo apt-get install sun-java6-bin
```

instead of

```
sudo apt-get install sun-java-bin
```

Let me know if that works or not.

---

### Post by colsandurz on 2009-01-18
oh, my mistake I used ```
sudo apt-get install sun-java6-bin
``` the whole time, I just forgot to type in the six.

---

### Post by metallicamike on 2009-01-18
or try getting it from synaptic, there is a sun-java6-bin  in there

---

### Post by colsandurz on 2009-01-18
yeah, I am going to remove everything related to java and then try to reinstall.  Do you have any idea why it wouldn't create the /bin/java directory the first time.

---

### Post by metallicamike on 2009-01-18
nope not really :lolflag: mine isnt there either, but everything app wise that i have that requires java works perfectly.

---

### Post by albinootje on 2009-01-18
> **colsandurz said:**
> yeah, I am going to remove everything related to java and then try to reinstall.  Do you have any idea why it wouldn't create the /bin/java directory the first time.

/bin/java ?

You mean /usr/lib/jvm/java-6-sun-1.6.0.10/bin/ or something like that ?

---

### Post by albinootje on 2009-01-18
I just checked on Ubuntu Hardy (I didn't have java installed) :
The java binary is in here /usr/lib/jvm/java-6-sun-1.6.0.07/bin/
So.. to satisfy the "needs" of the application you want to run, for Hardy you can do this :
```

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/bin/java /bin/java

```
And run your application again.

Again, this is for Hardy, check where your java binary is exactly, and adjust the above command to your needs.
I admit that this is an ugly solution, but it could work right away.
Better is to check the documentation of the application, maybe it's possible to define some JAVA_HOME (or something) environment variable.

---

