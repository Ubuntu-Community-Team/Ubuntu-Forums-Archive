---
title: "I have no idea what I'm doing"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-07-24
I just installed ubuntu, oh say, an hour ago. So I'm as absolute a beginner as one can get. My Windows machine was devoured by viruses, and I was forced to switch OS's without a lot of research, so I'm pretty lost.

My main concern right now is replacing all the stuff I used to have, mainly music. I managed to find the package that lets me play "restricted files", so I think that's good. Now I need a torrent client....or do I? I'm sort of getting the impression that there might be a default client that comes installed called Transmissions? Or is that just an ubuntu specific one? If this seems stupid, I'm sorry.

Also, if I need to download one (probably would take Vuze), how do I do that? I looked at a guide, and it was tossing around a lot of jargon I didn't understand. Things like roots and kernels and such.

---

### Post by michy99 on 2009-07-24
Transmission is indeed the bittorrent client that comes with Ubuntu, but you can use others. I like Deluge. Before you go looking for software to install, read over this page:

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

You will see that installing software is usually very easy in Ubuntu if you do it the right way!

---

### Post by Whiffle on 2009-07-24
Welcome!

Transmission is included under Applications > Internet > Transmission BitTorrent Client (near the bottom).

If you want to install something else, you can search through Synaptic, which you can access by going to System > Administration > Synaptic Package Manager.  If it is available in the default Ubuntu repositories, it will show up in a search.  All you have to do is right click it, click "Mark for Installation," and then click "Apply" on the toolbar.  

Don't be afraid to ask questions either, Ubuntu Linux is definitly not Windows and takes some time to get used to, and there are quite a few people here who are willing to help.

---

### Post by swoody on 2009-07-24
Hello rahrahmah, and Welcome to the Forums ):P

As the other's have said, yes Transmission is what you're looking for, and it does come with Ubuntu. There are still many options that you can explore though. That's one of the best things about Linux - just because the OS comes with certain applications doesn't mean that you have to use them or even keep them on your system! You're free to explore and learn what it is that suits you best!

For a *great* guide that should help you become more accustomed to Ubuntu and Linux in general, please check out the link in my sig! You can download the Beginner's Guide as a .pdf file, and read through it straight from your computer. It's very handy to have, and will probably answer quite a few questions I'm certain you're going to have.

And as always, feel free to post any questions you may have in these forums, there's always plenty of very helpful and knowledable people on at any given time :D

---

### Post by rahrahmah on 2009-07-24
thank you! I'm just really unsure of what comes with, and what I can download and use. But Transmissions seems to be working just fine. I have no doubt I'll be along to ask something else soon. Thanks!

---

### Post by swoody on 2009-07-24
Well, if you want to have a peek at just a part of what's available to you, you can check out the package managers to see what's out there. Go to Applications> Add/Remove Programs and you can search around for different applications in there. You can also go into System>Administration>Synaptic Package Manager and search through there.

There really is an endless plethora of programs out there that are available for Linux. A simple Google search on what you're looking for will be a great asset to your search as well :)

---

### Post by jmszr on 2009-07-24
rahrahmah,

Welcome aboard!

It appears that you have your torrent client need under control. You will want to add this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

For more information about using Ubuntu, I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

---

### Post by rahrahmah on 2009-07-24
I have another question this time about installation. I want a piece of software that counts calories and nutrition for you. I clicked the link to download the linux version of it, and it downloaded a little file that ended in .sh to my desktop. Now I don't know what to do with it. 

I've skimmed half of that Pocket Guide, and glanced through the official site's installing software thing and I'm afraid it's too technical and too all at once, and I don't think it's even covered what I need to know. If it did it went totally over my  head.

---

### Post by stlsaint on 2009-07-24
Welcome my fellow brethren!!! any questions on the system...in which you will have alot...this is def the place to find out what to use. also look up the "ubuntu pocket reference guide"! major help for me!

---

### Post by T-Train on 2009-07-24
The .sh file is a shell script. To run the script open Applications > Accessories > Terminal and follow the below commands.

*assuming you saved to your desktop and of course replace file with your filename
cd Desktop
./file.sh

---

### Post by magh-87 on 2009-07-24
Just take your time with it. Remember that Rome wasn't built overnight. Much the same, your knowledge with Ubuntu, or Linux for that matter, won't happen in one day. I've been using Ubuntu for months and there are still features about it that I look at and go "Woah. What?" Just be patient, do some homework, ask specific questions and be as helpful as possible to those who support who :)

It may be to your benefit to read a chapter of the guide a day, or week, and become used to what it's guiding you through until you become comfortable with it.

We're here to help :)

---

### Post by rahrahmah on 2009-07-24
I saved the file to my desktop, I didn't rename it anything. Do I have to do that? the name of the program is the name of the file right now: cronometer.sh What should I rename it? 

and when you say "follow the below commands" do you mean I have to type "cd Desktop
./cronometer.sh" (or whatever I have to rename it to)?

---

### Post by rahrahmah on 2009-07-24
please explain, I'm too scared to do anything without knowing if it's ok...

---

### Post by Arthur_D on 2009-07-24
> **rahrahmah said:**
> I saved the file to my desktop, I didn't rename it anything. Do I have to do that? the name of the program is the name of the file right now: cronometer.sh What should I rename it? 

and when you say "follow the below commands" do you mean I have to type "cd Desktop
./cronometer.sh" (or whatever I have to rename it to)?
Yeah, just click 'Applications' -> 'Accessories' -> 'Terminal' then write
```
cd Desktop
sudo ./cronometer.sh
```Then it will ask you for a password, and that should be the same as your login password. Type it, hit ENTER and follow eventual instructions.

---

### Post by rahrahmah on 2009-07-24
It says "command not found" I'm just cutting and pasting and pressing enter

---

### Post by rahrahmah on 2009-07-24
I read something that said I had to make sure that it was allowed to be executable, which I did. Then when I clicked it it gave me different options for running it. "run" did nothing "display" did nothing "run in terminal" opened something but it looked like a command prompt box and not the program at all. I'm afraid I'm going to wreck something clicking and opening things wildly like this...

---

### Post by Arthur_D on 2009-07-24
> **rahrahmah said:**
> It says "command not found" I'm just cutting and pasting and pressing enter
Could you try
```
sudo sh cronometer.sh
```
as well? This one should work I think, if it's a normal installation file.

---

### Post by rahrahmah on 2009-07-24
This worked better, as it got to the password prompt, but then I got:

cd: 9: can't cd to CRONoMeter.app/Contents/Resources/Java/
./cronometer.sh: 10: java: not found

---

### Post by Arthur_D on 2009-07-24
You seem to need Java. Install it by clicking 'Applications' -> 'Add/Remove...', search for Java, show all available applications, tick the first one, choose 'Apply all changes' and write your password.
Or, the fastest way:
Open the terminal, paste
```
sudo apt-get install sun-java6-jre
```and then write your password.

Then, try to sudo sh chronometer.sh again.

---

### Post by rahrahmah on 2009-07-24
well, I did that, and just for good measure I went into properties and made sure it was opening with java..and it still won't open. I looked at the error and there are instructions in the error. I don't know what that means. But it says (abreviated, since it won't let me cut and paste from the error window):

#!/bin/sh

Instructions:
1)install java
2)download Mac OS X Version and unzip in desired location
3)place this launcher script next to the application bundle
4)execute script to launch cronometer (the program)

Now, I downloaded the one that said it was for linux, why is it mentioning macs? and the rest of it is a total mystery as well.

---

### Post by rahrahmah on 2009-07-25
bump...

---

### Post by llamabr on 2009-07-25
Where did you save this file?  Make sure that you're running it in the same folder that it's saved.  In the previous explanation, the instructions tell you to cd Desktop.  Is that where it's saved?

---

### Post by Arthur_D on 2009-07-25
Deleted my writings; wrong context.

---

