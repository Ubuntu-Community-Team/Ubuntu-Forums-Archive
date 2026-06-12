---
title: "help with getting latest seamonkey"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by racerrandy on 2010-03-19
Hi, I just loaded ubuntu 9.10 on my laptop and so far am loving it. I was able to get the wifi to work and get the proper things to be able to watch dvds. I had trouble with the last time I tried ubuntu (8.04 on an older comp.) even watching movies. 

Anyway, I went to my software center and loaded seamonkey but found out it was the outdated version. I went to the website and downloaded the newest version, but just can't grasp how to install it. I read the read me file and it had some instuctions but I am just having trouble getting started. 

Can someone walk me through it? I have done a lot of reading in the help guides, but I am a 43 year old newbie who has just started to get comfortable with windows! :)

Thanks for the help.





Randy

---

### Post by wjm on 2010-03-19
This will answer ALL of your questions - [https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by lyall on 2010-03-19
wjm is right on the mark

to find out more about Ubuntu see the Community Documentation
titleindex
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")

good luck and have fun learning

---

### Post by ankspo71 on 2010-03-19
Hi,
I see some good advice was already given, but I already typed this out  so I'll post it anyways... ;) Maybe someone will need it.

I found a link to Seamonkey 2.0.3 PPA .
[https://launchpad.net/~joe-nationnet/+archive/ppa-seamonkey2]("https://launchpad.net/%7Ejoe-nationnet/+archive/ppa-seamonkey2")
You can download a deb package from that page to install seamonkey  directly, but only installing the deb package by itself wont give you  any updates to that version in the future. So I would recommend installing it through the PPA system, which will  involve adding sources to your sources list, but it would give you the  updates later.

Using that link above, it gives us the two source lines and a signing  key.
First we'll add the sources:
So go to Applications > Accessories > Terminal
Open the terminal and type the following:
```
gksudo gedit /etc/apt/sources.list
```Enter your password
Now add these lines to the bottom of the list:


```

# Seamonkey
deb http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu karmic main 
deb-src http://ppa.launchpad.net/joe-nationnet/ppa-seamonkey2/ubuntu karmic main 
```Click save and exit the text editor.
Next we want to add the signing key:
Go back to the terminal and type the following:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8F0C7B7
```you will probably need to enter your password again.

Almost done.

Next we will go System > Administration > Synaptic Package Manager.
Open Synaptic Package Manager.
Click on the "Reload" button near the top left.
Search for seamonkey-2.0.
Select to install it by clicking on it and say "Mark for Installation"
Click on the "Apply" button

All done :D

---

### Post by racerrandy on 2010-03-19
Thank you all very much. I now have the latest version of Seamonkey of my laptop. I did cheat and copy and paste everything but its a start. 

The links you guys gave me also allowed me to backtrack where the info came from amd helped a bunch. Sometimes its hard to know where to look when there is so much info available. 

I am sure this won't be my last dumb question. :D





Randy

---

### Post by SlappyPappy on 2010-04-04
Ah, dude, check your work:

Enter your password
Now add these lines to the bottom of the list:
Code:

# Seamonkey
deb [http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu](http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu) karmic main  
deb-src [http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu](http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu) karmic main

That's not going to fly.

---

### Post by ankspo71 on 2010-04-04
> **SlappyPappy said:**
> Ah, dude, check your work:

Enter your password
Now add these lines to the bottom of the list:
Code:

# Seamonkey
deb [http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu](http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu) karmic main  
deb-src [http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu](http://ppa.launchpad.net/joe-nationn...monkey2/ubuntu) karmic main

That's not going to fly.

it's fixed now... The automatically shortened hyperlinks messed it all up. Thanks.

---

