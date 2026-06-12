---
title: "FacebookPlugIn-1.0.0.tar.gz"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by nevabry on 2009-12-27
HELP!

I am running Ubuntu 9.04, and Firefox 3.0.

I am trying to get the Facebook Advanced Photo Uploader to work.

The website keeps directing me to download a tar.gz file called:

FacebookPlugIn-1.0.0.tar.gz

I've downloaded it to my Desktop, and have no idea what to do with it from here. 

Seriously, I need simple terms here. Any help would be AWESOME.

---

### Post by taurus on 2009-12-27
Unpack it.  Then, see what does it say to do next, probably have to build and install it on your machine.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf FacebookPlugIn-1.0.0.tar.gz
```
There should be a new directory, probably called FacebookPlugIn-1.0.0, so change to it and look at either the README or INSTALL.

```
cd FacebookPlugIn-1.0.0
more README
```

p.s.  But if you tell me where you downloaded it, I can have a quick look on my machine.

---

### Post by django0909 on 2009-12-27
Wouldn't 

./make

make install

run it from there?

---

### Post by taurus on 2009-12-27
> **django0909 said:**
> Wouldn't 

./make

make install

run it from there?

Not for all.  Some of them would have a script that you install it directly.  Some require you to run the ./configure first before make and **sudo** make install.  Some don't even require you to do anything since there is already a binary so you can just run it from there or move it somewhere else on your path.

---

### Post by nevabry on 2010-01-21
Sorry it's taken so long to get back to everyone. 

I extracted the tar.gz file onto my Desktop and it created a folder called "FacebookPlugIn-1.0.0"

The README file states:

"Installing the plugin is achieved by copying the included libnpfbook_1_0_0.so file
into the .mozilla/plugins folder in your home directory. For example,
if your username were "jzoidberg" you might copy the plugin to
"/home/jzoidberg/.mozilla/plugins". For your convenience, we have
included a script, "install.sh", that can be executed in lieu of
this rather technical operation.

Example:
  $ ./install.sh"


The "install.sh" file is literally called "FacebookPlugIn_Install.sh"

so when I type ./FacebookPlugIn_Install.sh into the command line it says 

"Permission Denied"

So I tried to manually move the .so file to the .mozilla/plugin folder, which appears to have been successful. 

But still no luck. I try to use the Facebook Advanced Photo Uploader and it continues to prompt me to download "FacebookPlugIn-1.0.0.tar.gz"

I can still use the Simple Facebook Photo Uploader - but the whole point is to get the ADVANCED Uploader to work.

I can't understand why it worked fine before my Upgrade to Ubuntu 9.04, and now it doesnt. I'm using Firefox 3.0.17 by the way.

---

### Post by ajamaja on 2010-01-30
Run FacebookPlugIn_Install.sh file with sh like...

sh FacebookPlugIn_Install.sh 

that worked for me 

for more information visit [http://www.cyberciti.biz/faq/run-execute-sh-shell-script/](http://www.cyberciti.biz/faq/run-execute-sh-shell-script/)

Chaoo

Questions are obvious but Answers are not :D

---

### Post by Excedio on 2010-01-30
There is also the option of using F-Spot. It comes with an extension that allows for bulk upload to Facebook.

---

### Post by knighthaq on 2010-01-30
or you could just update your install to 9.10

upload all my pics no problem.................

---

### Post by isee on 2010-02-14
ajamaja

Thanks very much!  I needed to know how to do that also.  Worked for me!

Cheers! :KS

---

### Post by Autumn7 on 2010-03-16
Please note the new FacebookPlugIn-1.0.2.tar.gz (vs the old FacebookPlugIn-1.0.0.tar.gz) does not work with ubuntu 9.10.

see discussion: [http://www.facebook.com/topic.php?uid=184826119663&topic=12994](http://www.facebook.com/topic.php?uid=184826119663&topic=12994)

---

