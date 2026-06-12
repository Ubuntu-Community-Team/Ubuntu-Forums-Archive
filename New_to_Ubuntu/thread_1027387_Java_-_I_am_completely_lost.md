---
title: "Java - I am completely lost"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Pollik on 2009-01-01
I am a total beginner in Linux, although I am failry literate in Windows.

I am running Ubuntu 8.10 Intrepid Ibex.

I am trying to instal Java - I have tried to read round the subject, and I have tried to install and have run into so many brick walls that I am going round in circles. :(

None of this helps anyone to be able to help me, but I just wanted to explain the ditzy blonde that I feel like at the moment.

For somewhere to start - [https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation) .  I didn'tunderstand the comments about universe and multiverse.

In the terminal window, "openjdk-6-jre" returns "bash: openjdk-6-jre: command not found"

In the terminal window, "sun-java6-bin, sun-java6-jre" returns "sun-java6-bin, sun-java6-jre"

"openjdk-6-jdk" returns "openjdk-6-jdk"

I am completely clueless as to where I go from here.  In Windows, I am literate enough to find solutions from existing pages published on the web, but in Ubuntu, people might as well be speaking Cantonese. :(


(Ditzy) Polly

---

### Post by MattBD on 2009-01-01
You should be able to install the Java runtime environment with this command:
```
sudo apt-get install sun-java6-jre
```
However, I tend to install the ubuntu-restricted-extras package, which is a metapackage - it pulls in a number of things including Java, MP3 support and extra fonts at the same time. You can install this as follows:
```
sudo apt-get install ubuntu-restricted-extras
```
Hope that helps!

---

### Post by .Maleficus. on 2009-01-01
What you should do is just go to Java's website and download the Linux version for your arch (either i386 or x86_64, depending on if you're using 64 bit).  Save it to an easy place, like Desktop.  Then, what you'll want to do is open a terminal and type:
```
cd Desktop
chmod +x *the_filename_you_downloaded.bin*
./the_filename_you_downloaded
```
And the installer should start up.  You may need to ad the .bin in the last command but I can't remember right now.  Also, replace the_filename_you_downloaded with the actual filename.

Good luck!


Edit:  Actually, do what the above poster said.  It's easier if you haven't played with the terminal much :).

---

### Post by Malta paul on 2009-01-01
Hi Welcome,

An easy way to install Java is to go to 'Applications>Add/remove, In the box 'show' change to 'All available applications' then type in 'Java' in the Search box. Tick the box for 'Sun Java 6 runtime' press the Apply Changes button and it will install for you.

Have fun:D

---

### Post by oilchangeguy on 2009-01-01
why do all of this command line stuff, and downloading from the website, when you can go to the synaptic package manager or add/remove and get it from there? people try to make linux way too hard.

---

### Post by fooman on 2009-01-01
have you tried synaptic?

go to system > administration > synaptic package manager

in synaptic's toolbar, click settings > repositories

on the "ubuntu software" tab....put a check mark next to the first 4 items (main-universe-restricted-multiverse)

click "close" and you will see a warning saying that the repos have changed...close that box.

click the "reload" button...then click on "search"

in the search box type: sun-java6 

click "search"

in the results that pop up...right click on:

-sun-java6-jre

and choose "mark for installation".

press "apply" in the toolbar.

that should do it.

---

### Post by Pollik on 2009-01-01
> **MattBD said:**
> You should be able to install the Java runtime environment with this command:
```
sudo apt-get install sun-java6-jre
```
However, I tend to install the ubuntu-restricted-extras package, which is a metapackage - it pulls in a number of things including Java, MP3 support and extra fonts at the same time. You can install this as follows:
```
sudo apt-get install ubuntu-restricted-extras
```
Hope that helps!

Thanks for the response. :)

"sudo apt-get install ubuntu-restricted-extras" returns "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

"dpkg --configure -a" returns "dpkg: requested operation requires superuser privilege"

'Polly' is the only user of this PC and booting launches straight in, without going through a log in screen.

At one point, I did try installing JDK but got stuck on the JAVA EULA (at least, I think that is what it was...it was a couple of hours ago, now.



Polly

---

### Post by fooman on 2009-01-01
open a terminal and type or copy/paste:

```
sudo dpkg --configure -a
```

then try:

```
sudo apt-get update
```

should be ok to continue installing java after that.

---

### Post by SuperSonic4 on 2009-01-01
```
sudo dpkg --configure -a
``` (sudo gives you superuser privileges)

```
sudo apt-get update
``` (to update the repos)

When you get to the EULA press tab and then return

---

### Post by MattBD on 2009-01-01
> **fooman said:**
> open a terminal and type or copy/paste:

```
sudo dpkg --configure -a
```

then try:

```
sudo apt-get update
```

should be ok to continue installing java after that.

Just beat me to it!

@oilchangeguy - It's easier to cut and paste it into the terminal.

---

### Post by jboy012000 on 2009-01-01
Hi Pollik,

Open a new terminal window (APPLICATIONS>ACCESSOROIES>TERMINAL and enter the following code, or just copy and paste.

To Install Java version 6 use the line of code below.

sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

You will be asked to enter your password because you used the sudo command which basically allows you to make changes to your system i.e install java.

Hope this helps you out.

Thanks

John

---

### Post by Pollik on 2009-01-01
> **.Maleficus. said:**
> What you should do is just go to Java's website and download the Linux version for your arch (either i386 or x86_64, depending on if you're using 64 bit).

Another fast response...thank you

How would I determine which I need?

Polly

---

### Post by fooman on 2009-01-01
> **Pollik said:**
> Another fast response...thank you

How would I determine which I need?

Polly

follow the instructions to use synaptic....it is ubuntu's package manager and the preferred method for installing software.

---

### Post by oilchangeguy on 2009-01-01
> **Pollik said:**
> Another fast response...thank you

How would I determine which I need?

Polly

you've already been given the answer (several times). and the answer is not visiting java's website. read the replies to your post.

---

### Post by frank002 on 2009-01-01
Open  Synaptic and in the search field type    sun-java. Mark the following for installation:
   sun-java6-bin
   sun-java6-jre
   sun-java6-plugin
   Hit Apply and let the installation begin.  It's that easy.

---

### Post by sadaruwan12 on 2009-01-01
Other wise you can just go to Systems -> Administration -> Synaptic package manager. Then scroll down till you see Openjdk-6-jdk or Openjdk-6-jre select one of these and click on the check box now you'll get a pop up menu from that select mark for installation now click on apply. Now Ubuntu will download and install JDK your on to your PC.

---

### Post by Pollik on 2009-01-01
I just want to say how overwhelmed I feel at all of the responses....thank you so much!

Where I am now...using the code offered by fooman and supersonic, JRE6 seems to have gone in OK.  Still not working fully in Firefox and Opera, so I am going through the process of enabling, installing plug ins, clearing cache...I am at least moving again, which is great.

I have not had a chance to read every post (which is why I asked a daft question, oilchangeguy) , but I will come back and do it...Synaptic looks like something else I need to look at.

But, I have to go out now...I will come back to this as soon as I can.

And thanks again. :) :)




Polly

---

