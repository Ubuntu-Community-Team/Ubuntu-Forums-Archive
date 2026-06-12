---
title: "really need help"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by longardino on 2011-07-17
i have had other versions of java but recently downloaded java 6 and it is not running properly and tells me the package or something is broken so i am trying to remove it completely and start over w/ a new download but it will not permit me to remove. when i go to add/remove and try to unclick the java 6 option it is not clickable....anybody...please help as i need java to run stuff for work...eeeeeeeekkkkkkkkkkkkkk

---

### Post by Bucky Ball on 2011-07-17
I can't help you with this, but I advise descriptive thread titles in future will improve your chances. Many ignore non-descriptive titles like 'Help' or 'Issues'. The majority of users here 'really need help' so that bit we know already. ;)

Good luck fixing your probs and welcome.

---

### Post by Mr.Kappa on 2011-07-17
From where are you trying to remove java? Synaptic?

---

### Post by Rex Bouwense on 2011-07-17
Go to Synaptic Package Manager and use the Broken Custom Filter.

---

### Post by Brushstroke on 2011-07-17
Try to run: 

```
sudo apt-get install -f
sudo apt-get update
```That'll attempt to fix any broken dependency problems.

After that, try reinstalling Java.

---

### Post by corncob on 2011-07-17
If all the above fail, try removing it with Computer Janitor.

---

### Post by mikejonesey on 2011-07-17
dunno what your unix experience is, but if you grabbed a install.sh of java the likeley hood is it won;t be in synaptic, it would have just installed the files required to run java.

I too use java at work, what i did was installed the default open java from package manager, i then downloaded a few jdk's from sun, i extracted these to;
/usr/lib/sun/jdk...

I then use an environment variable in my .bashrc file;
export JAVA_HOME="/usr/lib/sun/jdk1.5.0_22/jre"

this enables me to use this jre as my default;

I also installed my jre's to the update-alternatives;

* 0            /usr/lib/sun/jdk1.6.0_25/jre/bin/java      1102      auto mode
  1            /usr/bin/gij-4.4                           1044      manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  3            /usr/lib/sun/jdk1.5.0_22/jre/bin/java      1100      manual mode
  4            /usr/lib/sun/jdk1.6.0_21/jre/bin/java      1101      manual mode
  5            /usr/lib/sun/jdk1.6.0_25/jre/bin/java      1102      manual mode

this enables me to conveniently switch between them depending on what i'm working on...

I reccomend you just download the correct jdk and set it up this way...

also to find where your current jdk was installed to (asuming you installed a jdk, not a jre)... you could run something like...

```
sudo find /usr/ -type d -wholename */jdk*/jre
```which will find all jdk dirs that contain a jre dir...

hope this helps...

ps check your alt configs too maybee is installed in there and you can temp switch to your old 1;

```
sudo update-alternatives --config java
```

---

