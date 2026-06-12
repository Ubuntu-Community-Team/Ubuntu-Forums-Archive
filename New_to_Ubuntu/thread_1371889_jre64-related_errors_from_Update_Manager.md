---
title: "jre64-related errors from Update Manager"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by watchpocket on 2010-01-03
My recent wholesale move to Ubuntu has been kicking me hard.

For the last few days -- maybe a week -- it seems I can't successfully download software. 

I just tried to install some updates recommmended by the Update Manager and got the following, which I've seen before over the last week or so:

"Not all changes and updates succeeded.  For further details of the failure, please expand the 'Details' panel,"  which had this:

```
update-alternatives: using /usr/bin/jvm/jrel.6.0_14/bin/javaws to provide /usr/bin/javaws (javaws) in manual mode.

Can't call method "slave" on an undefined value at /usr/sbin/update-alternatives line 1017.

dpkg: error processing jre64 (--configure):
    subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
jre64
```Also got this application error message (I don't know what the app was that gave it):

```
Wrapped Exceptions:  java.io.FileNotFoundException: 1 (No such file or directory)
       at java.io.FileInputStream.open(Native Method)
       at java.io.FileInputStream.<init>(Unknown Source)
       at java.io.FileInputStream.<init>(Unknown Source)
       at com.sun.javaws.Main.launchApp(Unknown Source)
       at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
     at com.sun.javaws.Main$1.run(Unknown Source)
     at java.lang.Thread.run(Unknown Source) 
```Clearly this is to "jre64" and the 64-bit java installed, but I have no clue what to do about it.  Help, anyone, please.
I'm running karmic on a 64-bit System76 Wild Dog Performance desktop unit.

---

### Post by theschles on 2010-01-04
I am having the same problem on karmic with the Sun JDK 5 amd64 just downloaded from Sun's website:

```

$ sudo update-alternatives --set java /usr/lib/jvm/jdk1.5.0_22/bin/java
update-alternatives: using /usr/lib/jvm/jdk1.5.0_22/bin/java to provide /usr/bin/java (java) in manual mode.
Can't call method "slave" on an undefined value at /usr/sbin/update-alternatives line 1017.

```

---

### Post by tom.swartz07 on 2010-01-04
I would suggest removing all java related stuff on your computer and start again.

Follow this guide step by step all the way through and it will get you up and running in no time. I literally just did it a few minutes ago and now Facebook photo uploader works great! :popcorn:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
If you have any questions related to it, or if it works- let us know here and we could help.

Good Luck!

---

### Post by watchpocket on 2010-01-04
Fantastic -- I'll definitely follow the step-by-step you linked to for a java removal-and-reinstall process tonight when I get home.  Looks like a great guide.  Thanks for posting it and for introducing me to the "Easy Linux tips project"  

I can really use something like that right about now as I seem to have about a half-dozen other puzzles to solve with Karmic (this one being the most serious.  Thanks -- I'll post the results.

---

### Post by theschles on 2010-01-04
> **tom.swartz07 said:**
> I would suggest removing all java related stuff on your computer and start again.

Follow this guide step by step all the way through and it will get you up and running in no time. I literally just did it a few minutes ago and now Facebook photo uploader works great! :popcorn:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
If you have any questions related to it, or if it works- let us know here and we could help.

Good Luck!

Sweet -- it worked!  Thanks :)

---

### Post by watchpocket on 2010-01-04
I do have one question about the 64-bit Java install:  

When we go to get the "Linux x64" Java, at the page where we get it, <http://www.java.com/en/download/manual.jsp> , there is an asterisk beside the link to "Linux x64" -- the corresponding text just below the link says:

"* Please use the 32-bit version for Java applet and Java Web Start support."

I'm guessing that this can be ignored since nothing was said about it on the "Easy Linux tips project" page where the instructions are.

Am I guessing correctly?  

Thanks.

---

### Post by tom.swartz07 on 2010-01-04
> **watchpocket said:**
> I do have one question about the 64-bit Java install:  

When we go to get the "Linux x64" Java, at the page where we get it, <http://www.java.com/en/download/manual.jsp> , there is an asterisk beside the link to "Linux x64" -- the corresponding text just below the link says:

"* Please use the 32-bit version for Java applet and Java Web Start support."

I'm guessing that this can be ignored since nothing was said about it on the "Easy Linux tips project" page where the instructions are.

Am I guessing correctly?  

Thanks.

when you see the x64 in the list, just right click and hit save as. Save it to your home folder, and keep on truckin with the instructions.

---

### Post by LuisGMarine on 2010-01-04
Awesome website, never knew it existed.

---

### Post by tom.swartz07 on 2010-01-04
> **LuisGMarine said:**
> Awesome website, never knew it existed.

Dontcha just love it? :D

Glad I could help!

If there arent any more questions relating to the installation, please mark this thread as read, so that others could jump right to this as a guide!


Happy New Year!

---

### Post by watchpocket on 2010-01-05
This is one weird "do not pass go" signal:

```
[rj-home:/opt]  [v4.3.10]  zsh  569 --> cd java 
cd: permission denied: java
[rj-home:/opt]  [v4.3.10]  zsh  570 --> sudo cd java
sudo: cd: command not found
```I could cd easily enough into /opt.  Why in the world can't I cd into the newly-created java folder?

```
[rj-home:~]  [v4.3.10]  zsh  572 --> ls -la /opt 
total 20
4 drwxr-xr-x  5 root root 4096 2010-01-05 13:31 ./
4 drwxr-xr-x 23 root root 4096 2010-01-05 13:22 ../
4 drwxr-xr-x  3 root root 4096 2009-12-28 01:44 Adobe/
4 drwx------  2 root root 4096 2010-01-05 13:31 java/
4 drwxr-xr-x  3 root root 4096 2009-11-02 10:50 system76/
```Help.

---

### Post by watchpocket on 2010-01-05
Sorry for the alarm.  I changed the permissions for the java folder:

```
4 drwxr-xr-x  2 root root 4096 2010-01-05 13:31 java/
```

---

### Post by Methuselah on 2010-01-05
> **watchpocket said:**
> This is one weird "do not pass go" signal:

```
[rj-home:/opt]  [v4.3.10]  zsh  569 --> cd java 
cd: permission denied: java
[rj-home:/opt]  [v4.3.10]  zsh  570 --> sudo cd java
sudo: cd: command not found
```I could cd easily enough into /opt.  Why in the world can't I cd into the newly-created java folder?

```
[rj-home:~]  [v4.3.10]  zsh  572 --> ls -la /opt 
total 20
4 drwxr-xr-x  5 root root 4096 2010-01-05 13:31 ./
4 drwxr-xr-x 23 root root 4096 2010-01-05 13:22 ../
4 drwxr-xr-x  3 root root 4096 2009-12-28 01:44 Adobe/
4 drwx------  2 root root 4096 2010-01-05 13:31 java/
4 drwxr-xr-x  3 root root 4096 2009-11-02 10:50 system76/
```Help.

```

cd /opt
sudo chmod 0755 java 

```

EDIT: I see you changed it already.

---

### Post by watchpocket on 2010-01-05
This went off without a hitch. I did a download test after the java installation to make sure there were no more error messages.  Thanks loads.

---

### Post by tom.swartz07 on 2010-01-06
> **watchpocket said:**
> This is one weird "do not pass go" signal:

```
[rj-home:/opt]  [v4.3.10]  zsh  569 --> cd java 
cd: permission denied: java
[rj-home:/opt]  [v4.3.10]  zsh  570 --> sudo cd java
sudo: cd: command not found
```I could cd easily enough into /opt.  Why in the world can't I cd into the newly-created java folder?

```
[rj-home:~]  [v4.3.10]  zsh  572 --> ls -la /opt 
total 20
4 drwxr-xr-x  5 root root 4096 2010-01-05 13:31 ./
4 drwxr-xr-x 23 root root 4096 2010-01-05 13:22 ../
4 drwxr-xr-x  3 root root 4096 2009-12-28 01:44 Adobe/
4 drwx------  2 root root 4096 2010-01-05 13:31 java/
4 drwxr-xr-x  3 root root 4096 2009-11-02 10:50 system76/
```Help.
EDIT: didnt see second page :X

Glad you got it working!

Dont forget to mark the thread as solved! Thread tools at the top of the page.

Thanks! Happy New Year!

---

