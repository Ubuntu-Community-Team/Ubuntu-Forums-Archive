---
title: "Installation mechanism"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by xachu4u on 2010-04-15
I am new to ubuntu. So far I have liked everything about it.

But I still don't understand many things..:confused:


[LIST]
[*]Most basically, I have no idea how to install a new application.:KS
[*] I ran into this trouble while trying to install [SIZE=3]**"xchm"**[/SIZE] (to read .chm file)
[*]I know you have to go to the terminal and type in commands starting like:
[*]sudo apt-get install ........
[/LIST]

_*but whenever I tried this I get an error of missing package.*_:(

If you can help me, then plzzzzzzz...:)


[LIST]
[*]I have ubuntu 9.04 installed using the "within windows option", the one which does not allow hibernation..
[*]As far as xchm is concerned i have downloaded xchm-1.17.tar.gz file from net.
[*]I have no idea what to do with it.
[/LIST]
[FONT=Garamond][SIZE=4]**I would be very happy if SOMEONE could explain the installation mechanism in Debian - based OS.**[/SIZE][/FONT]

---

### Post by Elfy on 2010-04-15
Hi and welcome.

Make sure that you have the repos enabled in software sources (System > Admin > Software Sources) - pay attention to the 4 options on the first Ubuntu Software tab - don;t worry about the sources.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Use Software Centre, Add/Remove or synaptic to install software.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I would not worry about compiling from tarballs just yet - certainly xchm is available in the repos.

---

### Post by Paqman on 2010-04-15
> **xachu4u said:**
> 
[LIST]
[*]I know you have to go to the terminal and type in commands starting like:
[*]sudo apt-get install ........
[/LIST]


You don't have to use the terminal. Take a look at System > Admin > Synaptic. For desktop applications (as opposed to little packages like xchm) you can go to System > Ubuntu Software Centre.

---

### Post by m4tic on 2010-04-15
Go to System>Administration>Synsptic Package Manager
On the search bar on the top, type the name of the application you want to install. Look down on the list and choose the best that suits you accordinf to the discription provided. Check on the box next to your app and select the (green "tick" i think) on the top to apply

---

### Post by aeiah on 2010-04-15
> **xachu4u said:**
> 
sudo apt-get install ........



people have mentioned synaptic, and you can think of apt-get as basically the underlying command line that synaptic uses. people will often tell you a command rather than say 'use the menu to open synaptic, then search for package 'xxxx', then tick the box then apply changes, then close synaptic' because its a hell of a lot easier just to give you the apt-get command. 

in truth when you're installing stuff yourself you may find synaptic easier than the command line, and the software center easier still (although the software center doesn't list everything in the ubuntu repositories like synaptic does)

as a rule always try and get stuff from the ubuntu repositories through the methods mentioned already. if it isn't available, or the version is too old, then you may have to deal with compiling it yourself from a tar.gz (like you tried to). but its a lot easier to rely on the repositories when you can (and the repo is massive, so you can almost always rely on it to have what you want).

---

### Post by xachu4u on 2010-04-16
Thank you for your time, but I don't understand what is "repos"
I checked out Synaptic Package manager and I understood what it is for.

But regarding Software Center , sorry I have no idea what it is for, I have no idea what it is trying to say.(please forgive my lack of knowledge, do you know any books that may help?)

The point is I don't know how to use Software Center.

Hoping for your ans........

(Have you heard of complains of people unable to install packages? I am asking because I am suffering from it. I think it is because i have installed Ubuntu within Windows. I believe i should use VMware to use both XP and Ubuntu.)

---

### Post by xachu4u on 2010-04-16
Can you tell me how to use the Software center....?
And what are these Ubuntu Repostries..?

---

### Post by wojox on 2010-04-16
> **xachu4u said:**
> Can you tell me how to use the Software center....?
And what are these Ubuntu Repostries..?

The repo's are where you download your applications and such from. Open synaptic and search for chm. It will give you a bunch of diffrent choices. 

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Elfy on 2010-04-16
ubuntu help on installing

[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

---

### Post by grifonas on 2010-04-16
> **xachu4u said:**
> 
The point is I don't know how to use Software Center.


As far as I remember there was no Software Centre in 9.4 yet. It only appeared in 9.10, and it's in the "Applications" menu.

---

### Post by Sef on 2010-04-16
> Quote:
 	 	 		 			 				 					Originally Posted by **xachu4u** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9130680#post9130680") 				
 				*The point is I don't know how to  use Software Center.*
 			 		 	 	 
As far as I remember there was no Software Centre in 9.4 yet. It  only appeared in 9.10, and it's in the "Applications" menu.

That is correct.  The software center first appearance was in Koala Karmic, 9.10.

---

### Post by DM was on fire! on 2010-04-16
Well, if you want to get technical, there was a software center in older versions; the one available in the Applications menu, plus Synaptic. (I'm reaching faaar back here, to Dapper [6.06 LTS].)
Synaptic was always slow as hell for me and froze up, so I typically just used apt-get to install. 

What exactly do you mean by having Ubuntu installed within Windows, xachu?

---

### Post by xachu4u on 2010-04-17
Sorry I mistook Software Sources with Software Center.

What are your comments on Ubuntu Package Search ?

It was really helpful(regarding xchm)

In the Synaptic (for 9.04) i couldnot find anything for "chm".
Thanks to all for sharing your info.

---

