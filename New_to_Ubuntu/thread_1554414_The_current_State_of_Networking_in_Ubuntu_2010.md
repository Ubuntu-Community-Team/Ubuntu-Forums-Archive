---
title: "The current State of Networking in Ubuntu? 2010"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Nick_Jinn on 2010-08-16
So its 2010.


       So what is the current state of home networking in Ubuntu? What can we do and what are the limitations? I am yet to try it, but its been on my to do list. Can we access each others files via the router on different machines? How about watch a video hosted on their machine? Can we plug an external hard drive into a wireless router and access those files from any computer in the house?

---

### Post by bodhi.zazen on 2010-08-16
> **Nick_Jinn said:**
> So its 2010.


       So what is the current state of home networking in Ubuntu? What can we do and what are the limitations? I am yet to try it, but its been on my to do list. Can we access each others files via the router on different machines? How about watch a video hosted on their machine? Can we plug an external hard drive into a wireless router and access those files from any computer in the house?

We can do all that and more, have been able to do so for many years, where have you been ?

---

### Post by Nick_Jinn on 2010-08-16
Under a rock getting high.

No seriously, I was pretty sure you could do all those things but I brought it up a couple of months ago somewhere else and nobody knew about plugging in an external hard drive to a wireless router. I figured the rest would be easy enough.


Is there an easy tutorial?



Ive been a point and click Ubuntu user for years, but its just the last few months that I decided to really study it.

---

### Post by bodhi.zazen on 2010-08-16
Tutorial for what ?

Networking ? Samba ? NFS ? HTTP ? SSH ? Autofs ? Kerberos ?

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

Otherwise you are going to need to be more specific.

---

### Post by Nick_Jinn on 2010-08-16
Im going to read that page and get back to you. Some of it I am semi-familiar with. Some of it is new to me.

---

### Post by Nick_Jinn on 2010-08-16
hmmmm.


So if I make a small re-branded ISO for a group I am working with, can I have them prepped for 'read only' access to a specific partition on a PC already to go from live CD?

---

### Post by bodhi.zazen on 2010-08-16
Probably , depends on your knowledge of remastering the live CD ;P

---

### Post by beastrace91 on 2010-08-16
> **bodhi.zazen said:**
> We can do all that and more, have been able to do so for many years, where have you been ?

Unless you have something setup with multiple workgroup or any number of other configurations that make samba take a dump.

In the three years I've been using Linux as my sole operating system I can count on one hand the number of times I've successfully accessed a network share without having to mount it via CLI.

Hopefully you will be more lucky than I :-/

~Jeff

---

### Post by Paqman on 2010-08-16
> **Nick_Jinn said:**
>  I brought it up a couple of months ago somewhere else and nobody knew about plugging in an external hard drive to a wireless router.

To do that you'd have to have a router that supports it. Some do have a USB port on them for this exact reason. Basically it turns the router into a mini-NAS.

---

### Post by bodhi.zazen on 2010-08-16
> **beastrace91 said:**
> Unless you have something setup with multiple workgroup or any number of other configurations that make samba take a dump.

In the three years I've been using Linux as my sole operating system I can count on one hand the number of times I've successfully accessed a network share without having to mount it via CLI.

Hopefully you will be more lucky than I :-/

~Jeff

There are several ways of configuring and managing samba, some graphical, some command line.

If you are interested in learning the graphical tools, start a new thread. In general, you can configure and mount a samba share out of the box with the graphical tools, I have done so many times, although I prefer the command line.

In fact, I prefer autofs (client side).

[http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)

And I prefer managing a samba server via the command line, so, I do not find the lack of graphical tools a downside. If you want them, they are available, and they work.

If you need assistance, ask for help.

---

### Post by beastrace91 on 2010-08-16
> **bodhi.zazen said:**
> If you need assistance, ask for help.

[http://ubuntuforums.org/showthread.php?t=1534728](http://ubuntuforums.org/showthread.php?t=1534728)

](*,)

~Jeff Hoogland

---

### Post by Nick_Jinn on 2010-08-16
I am not really competent with the CLI yet. Graphical is pretty much the way I need to go for the time being, until I hon my CLI-Jitsu.

---

### Post by bodhi.zazen on 2010-08-16
> **beastrace91 said:**
> [http://ubuntuforums.org/showthread.php?t=1534728](http://ubuntuforums.org/showthread.php?t=1534728)

](*,)

~Jeff Hoogland

That is not a simple samba problem, it involves mixed clients and multiple work groups.

I can not tell from your post if the server you wish to connect to is a Windows server and you did not give any information as to how authentication is performed on your Windows Workgroups.

There is no GUI on either windows or linux that will solve that problem, there are too many variables to know where to begin.

I advise you start with a network administrator that is willing to solve the problem and that you will need to provide much more information then on that thread.

From Linux -> Linux for mixed windows/linux environments, using a basic (default) workgoup it will work out of the box. But if you start adding in things such things as kerberos and windows authentication, yes it will get complex.

---

### Post by beastrace91 on 2010-08-16
> **bodhi.zazen said:**
> There is no GUI on either windows or linux that will solve that problem, there are too many variables to know where to begin.

Really? On Windows I crack open "My Network Places", click on the file server, enter my user name, and poof! There are my shares :-/

I also got a 3 to one vote [here](http://ubuntuforums.org/showthread.php?t=1519548) that they are a pain... Not trying to start an argument just sharing that they indeed still have many issues. You should know what you are getting into as the OP wanted to find out.

Just saying.

~Jeff

---

### Post by uRock on 2010-08-16
> **beastrace91 said:**
> Really? On Windows I crack open "My Network Places", click on the file server, enter my user name, and poof! There are my shares :-/

I also got a 3 to one vote [here]("http://ubuntuforums.org/showthread.php?t=1519548") that they are a pain... Not trying to start an argument just sharing that they indeed still have many issues. You should know what you are getting into as the OP wanted to find out.

Just saying.

~Jeff
So now you have your issue fixed?

BTW, having the opinion of 4 people in one thread is useless for real world statistics. Post it on a server page and you will get the exact opposite replies.

---

### Post by TXpaniolo on 2010-08-16
As a total newb I was able access my son's Windows machine on our home network and transfer photo and mp3 files to my machine as basically one of my first tasks after initial Ubuntu setup.  Then set it up to auto mount that computer and set my daily backups to save on a 2nd hard drive in my computer with a mirror to his computer over the network.  It wasn't drop dead simple, but it didn't take a lot of time either.  

Setting his Windows computer up to backup onto my 2nd harddrive is on my to do list just isn't real high on priority, but is the some thing I want to work on.

---

### Post by beastrace91 on 2010-08-17
> **uRock said:**
> So now you have your issue fixed?


No. The issue is accessing the share from Ubuntu. Which still is not resolved, but to be honest I only spent an hour pouring of guides trying to make it work.

~Jeff

---

