---
title: "Why do they do this? :("
date: 2010-09-26
forum: New to Ubuntu
---

### Post by CornerSquid on 2010-09-26
I know this is kind of like a spam thread, but why do they make program installation so ridiculously hard? (compared to windows)

I was trying to install java, and it gave me same random .bin file.

So i went and found a tut on how to install .bin files, to no avail.

After fumbling around in the terminal for 20 minutes i finally got it working (although i had to move the .bin file to another directory)

But all that happened was the .bin was extracted to a folder, no installation or anything.

I looked in the .bin folder for a second, and saw all these files all over the place, and thought "Why do this when i can just go Nxt --> Nxt --> Nxt --> Finish in windows 7?"

So why do they make it so hard? I'm sure many people dont like crapping around in a console typing in "sudo" every 5 seconds, when they could just be clicking on a next button.

---

### Post by mick222 on 2010-09-26
Open a terminalthen copy paste code below.
```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

 or use synaptic and enable the partner repository .then install from there.

---

### Post by CharlesA on 2010-09-26
There is no need to mess with bin files. You can install Java from software center or Synaptic (or apt-get or aptitude).

Just do a search.

---

### Post by coffeecat on 2010-09-26
> **CornerSquid said:**
>  why do they make program installation so ridiculously hard? (compared to windows)

Actually, they make it ridiculously easy (compared to Windows).

Go to Applications > Software Centre. Search for java. Select the packages you want - click, click - done.

If you want the Sun java stuff, go to System > Administration > Software Sources > Other software tab and tick the first (partner) line. Do a reload when prompted and then open Synaptic or Software Centre to select your Sun java packages - click, click - done.

---

### Post by CornerSquid on 2010-09-26
*Sigh*

I give up on linux, i'll just go back to the easy ways (spamming a "next" button and smiling)

---

### Post by ibizatunes on 2010-09-26
the funny thing is there is less steps installing application in linux (ubuntu), then there is in window lol
Go application > accessiories > terminal
paste ```
sudo apt-get install ubuntu-restricted-extras
```
and hit enter
that will install java + flash + mp3 codec etc,
one command install install load of usefull programs cant do that with windows

Just post questions and people will help, it seems hard but it gets easier trust me

---

### Post by Diametric on 2010-09-26
Later, homie - but you're really missing out on a cool way to operate a computer.  Linux DOES take some learning (or unlearning if you're coming from Windows) but  after a little work and effort, you get a stronger, more robust more secure OS than Windows could ever hope to be.

Good luck!

---

### Post by Lateralis on 2010-09-26
Indeed.  Learning anything new takes a bit of time.  If you've only ever used Windows, and used Windows for many years, you become set in your ways.  Like anything though, you will learn how to do things and eventually discover that installing things in Linux is ***far*** easier than in Windows.  

But Ubuntu is easy.  As a pertinent example, take my mother.  She's someone that doesn't know her kernel from her command line but is quite happily using Ubuntu.  If she can do it, *anyone* can do it. 

But whatever.  If you want to use Windows, go right ahead.  No one here will stop you. ;)

---

### Post by bobbob1016 on 2010-09-26
I'm guessing this was a joke.  But either way, why don't we include a "How To" or "What to do now" video that plays after install?  Like "Go to Applications, Software Center, then do this to install flash and java and whatever else."

---

### Post by Chris1274 on 2010-09-26
> **bobbob1016 said:**
> I'm guessing this was a joke.  But either way, why don't we include a "How To" or "What to do now" video that plays after install?  Like "Go to Applications, Software Center, then do this to install flash and java and whatever else."

Mint has a welcome screen with various "Getting started" links, maybe Ubuntu should think about including something like that, if not the video you suggested.

---

### Post by honeybear on 2010-09-26
> **CornerSquid said:**
> I know this is kind of like a spam thread, but why do they make program installation so ridiculously hard? (compared to windows)

I was trying to install java, and it gave me same random .bin file.

So i went and found a tut on how to install .bin files, to no avail.

After fumbling around in the terminal for 20 minutes i finally got it working (although i had to move the .bin file to another directory)

But all that happened was the .bin was extracted to a folder, no installation or anything.

I looked in the .bin folder for a second, and saw all these files all over the place, and thought "Why do this when i can just go Nxt --> Nxt --> Nxt --> Finish in windows 7?"

So why do they make it so hard? I'm sure many people dont like crapping around in a console typing in "sudo" every 5 seconds, when they could just be clicking on a next button.

apt-get install sun-java6-bin 

I guess that mozilla and java for youtube are posisble too to be installed from apt-get ... but i am not sure

---

