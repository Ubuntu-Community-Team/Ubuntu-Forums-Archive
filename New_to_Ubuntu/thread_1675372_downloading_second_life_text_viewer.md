---
title: "downloading second life text viewer"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by twitchn on 2011-01-25
Hi. I switched to ubuntu netbook edition a couple hours ago. I have everything fine. I am enjoying the system. The only problem i have had is there is one more program i want on my computer. I play second life often. I need to use a text viewer however, and  i can not figure out how to get it installed. I am not so good with any programs. I need help. Explanation on how i can download it, and make it work! lol please :p

---

### Post by twitchn on 2011-01-25
I figured out the program. It says i need something called mono? The program i found is called radegast. But i can not get it to install.

---

### Post by cariboo on 2011-01-25
The mono libraries you need, should be installed by default, if you haven't removed tomboy.

---

### Post by Nytram on 2011-01-25
Unzip the file you've downloaded (may need to install an unzip package) and navigate to the directory in a terminal, then type:

> mono Radegast.exe

(Has to be a capital R.)

---

### Post by purplemonster on 2012-05-24
I'm a complete newbie to Linux and installed Ubuntu 11.10 on an old laptop a few days ago, and tried to install Radegast in order to get into Second Life, but couldn't get it to work.

From reading various help threads I assumed that the necessary mono files would have been installed by default, but it seems not. So for anyone searching for the solution to this problem in the future, I thought I should comment with what fixed it for me!

In terminal:

sudo [SIZE=2]apt-get install mono-complete

Then after that had installed, going to the directory I'd unzipped the Radegast files into and typing mono Radegast.exe worked.

[/SIZE]

---

