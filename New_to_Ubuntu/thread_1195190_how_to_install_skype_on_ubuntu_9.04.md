---
title: "how to install skype on ubuntu 9.04"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by savvavas on 2009-06-23
I am getting an error message: Wrong architecture 'i386'

---

### Post by scrooge_74 on 2009-06-23
First, what version of Ubuntu you are using? 32 or 64 bit.

---

### Post by savvavas on 2009-06-23
how do i figure this out.  I was given a system 76 computer with ubuntu 9.04 already installed for my birthday. I am a complete computer amateur. Could you please help me find out this information?

---

### Post by Troll_the_Great on 2009-06-23
It if says "wrong architecture i386" it means that you are trying to use a 32 bit program on a 64 bit system. Search for Skype 64 bits and it should work. I think the easiest way to install it is via Synaptic Package Manager from System - Administration - Synaptic.
Cheers!

PS: you can find out what system version you are using by typing 
```
lsb_release -a
``` in a terminal (Applications - Accessories - Terminal)

---

### Post by LowSky on 2009-06-23
open a terminal, run these two commands, once done you wil  have skype

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install skype
```


it should install

---

### Post by savvavas on 2009-06-23
I tried these two codes and I do not think skype has installed.  Help I need skype to work.:(:(:(

---

### Post by savvavas on 2009-06-23
According to the Synaptic Package Manager skype is already installed. Now, I guess, it is a matter of finding it.  How would one find it through the terminal for example?

---

### Post by synapsys on 2009-06-23
Did you look under Applications >> Internet ?

Or in terminal type > which skype

Or just > skype

for that matter

---

### Post by savvavas on 2009-06-23
This is the message I get from synaptic Package Manager:


A VoIP software - Medibuntu package

Skype is a proprietary peer-to-peer Internet telephony (VoIP) software.
The Skype communications system is notable for its broad range of features,
including free voice and video conferencing, and its ability to use peer to
peer (decentralized) technology to overcome common firewall and NAT problems.

This package is in Medibuntu because it is not freely redistribuable.

This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!

Please report any bug to our bug tracker instead:
 [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)

This package contains the "standard" Skype variant.


What could this mean?

---

### Post by synapsys on 2009-06-23
That's just the description of the package... try what I said before.....

> Did you look under Applications >> Internet ?

Or in terminal type  	Quote:
 	 	 		 			 				which skype 			 		 	 	 
Or just  	Quote:
 	 	 		 			 				skype 			 		 	 	 
for that matter 	

---

### Post by savvavas on 2009-06-23
When I typed in which skype i got a location of:  /usr/bin/skype.
But how do I access and open this file?

---

### Post by 3rdalbum on 2009-06-23
```
skype
```

---

### Post by savvavas on 2009-06-23
thank you very much [synapsys and all other helpful users]("http://ubuntuforums.org/member.php?u=850688").  I think I successfully installed skype.:P:P:P

---

### Post by savvavas on 2009-06-23
now how do I end this thread with this solven question?
thanks again all helpful users:P:P:P

---

### Post by synapsys on 2009-06-23
Thread tools >> Mark this thread as solved

---

### Post by savvavas on 2009-06-23
okay cool , but can I ask questions about my installed skype?  Or should I start a new thread?

---

### Post by magh-87 on 2009-06-23
Try searching the forums for what you may want to learn about using Skype on Ubuntu. Google is also a very good resource, as are the people on this forum. For specific questions, creating a new thread would probably be the best option since you are no longer having any issues with the installation.

---

### Post by savvavas on 2009-06-23
when i go to thread tools I do not get a thread solved option.  Why is the solved button not showing up?

---

### Post by Sef on 2009-06-24
It has not been enabled because of problems with it.   Instead you have to go to your first post and click on edit, then go advanced and add [solved] to the top left of the title.

---

### Post by Nick Brohman on 2009-10-24
> **LowSky said:**
> open a terminal, run these two commands, once done you wil  have skype

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
``````
sudo apt-get install skype
```it should install

LowSky

I thank you for this post.

I have been getting hot under the collar because every download (&that is many), would not install due to corruption or permissions. All this because I've had to re-install 9.04.

I'm now going to make a call to check audio.

Once again, many thanks.

Cheers...Nicko

28/10/09

I have now made several calls & have some minor problems, but am not too fussed about those.

I don't get my video window but my video is transmitted - minor prob. as I know what I look like. 

I have some audio echo thru' my speakers but audio is fine at the other end - also minor as it doesn't cause any problem for whom I'm calling. 

[COLOR=Red]All in all, I am quite pleased as calls made so far would cripple my meagre funds.[/COLOR]

Thank you all for helping this novice.....Nicko

---

### Post by nikoszax on 2009-10-30
i am a new ubuntu user as well - i followed the said directions to a point - now (assuming that it is installed),when i type on the terminal "which skype" i get ...nothing, when i type just "skype" i get "bash: skype: command not found" - how should i proceed?

---

### Post by manoriax on 2009-10-30
> **nikoszax said:**
> i am a new ubuntu user as well - i followed the said directions to a point - now (assuming that it is installed),when i type on the terminal "which skype" i get ...nothing, when i type just "skype" i get "bash: skype: command not found" - how should i proceed?

I think you did not install it, yet.

> **LowSky said:**
> open a terminal, run these two commands, once done you wil  have skype

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
``````
sudo apt-get install skype
```it should install

Running this should solve your problem, otherwise go to [www.skype.com]("http://www.skype.com") and download the latest version there and install it manually.

---

### Post by Nick Brohman on 2009-10-30
> **nikoszax said:**
> i am a new ubuntu user as well - i followed the said directions to a point - now (assuming that it is installed),when i type on the terminal "which skype" i get ...nothing, when i type just "skype" i get "bash: skype: command not found" - how should i proceed?

Hello nikoszax, 

Press enter/return after each command line.

You will have to enter your password after the first command & then y (when asked) to proceed with the second command line.

It will take about 30 mins. to install.

The Medibuntu repositories gives you 2.0.0.72 but you get everything req'd to have Skype up & running.

You might want to add Restricted Ubuntu from Synaptic Pkg. Mgr.

Best of luck

Nicko

---

