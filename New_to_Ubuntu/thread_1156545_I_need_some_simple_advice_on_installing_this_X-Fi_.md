---
title: "I need some simple advice on installing this X-Fi driver"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by nogoodreason on 2009-05-11
Hi guys,

I'm sure this has a reeeeally simple solution, but I am an absolute beginner when it comes to Linux so would appreciate it if someone could tell me exactly what to do before I screw this up again. :S

I've downloaded the only available 64-bit Linux drivers on the Creative site for my X-Fi soundcard.  I've saved the file to my desktop and extracted it there.

Inside are a bunch of files and a readme, which says:

[B]Quick install
=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install[/B]


I realise I sound like a total and utter n00b by asking this, but what exactly do I do??  Do I copy and paste these instructions directly into terminal?  I get the feeling they're instructions rather than simple commands, but as I said I really am a total beginner and clueless. :oops:

I've attached a screenshot which probably explains things better than I did.



PS: On a similar note, you will notice the latest nvidia drivers are also on my desktop.  If possible, could someone also tell me how to:
a) uninstall the old nvidia drivers
b) install these new ones


I would be extremely grateful if someone could find the patience to explain this to me.

---

### Post by doctorbighands on 2009-05-11
The instructions in the Readme want you to perform the following in a terminal:

Step 1: Go to source directory
```
cd ~/Desktop/<name of folder containing driver files>
```

Step 2: Execute make command as root
```
sudo make
```

Step 3: Execute make install command as root
```
sudo make install
```

If the Readme is accurate, you should now have your driver installed.

---

