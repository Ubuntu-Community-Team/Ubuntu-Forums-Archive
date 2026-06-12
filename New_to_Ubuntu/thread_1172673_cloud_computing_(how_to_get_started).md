---
title: "cloud computing (how to get started)"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by djmh on 2009-05-28
so i have heard alot about cloud computing
and i would like to try it, but i dont know where to start or what programs to get...if anyone has links or programs to get i would appreciate it

---

### Post by spiceminesofkessel on 2009-05-28
Sign up for a Google account. That's a great cloud platform. You get e-mail, IM, voice and video communication, phone service, office applications, news reader, picture manager, blog, and much, much more.

It's all done from the Internet, or in the cloud, so all you need is a computer with a browser and an Internet connection.

---

### Post by Paqman on 2009-05-28
Yep, Google runs my whole life these days. Gmail, Calendar, docs, it's all good stuff.

---

### Post by djmh on 2009-05-28
oh,thats all cloud computing is ?
i already have all that lol .... i dont know what i was thinking it was,thanks anyways evryone.

---

### Post by juancarlospaco on 2009-05-28
You can build **[COLOR="Red"]your OWN Cloud[/COLOR]** with Ubuntu, a unique Feature *(Windows 7 or Snow Leopard can't do that)*

---

### Post by djmh on 2009-05-28
and how would you go about building your own cloud ?

---

### Post by Paqman on 2009-05-28
> **djmh said:**
> oh,thats all cloud computing is ?
i already have all that lol .... i dont know what i was thinking it was,thanks anyways evryone.

Yep. Cloud computing is a just a fancy way of talking about pushing some of the computation and storage normally done on your machine onto somebody else's servers over the internet.

Taken to it's logical conclusion you end up with a kind of thin client arrangement where all your hardware does is establish a connection and present the information. I can't really see that happening to any great degree myself.

---

### Post by ripeart on 2010-01-23
> **Paqman said:**
> 

Taken to it's logical conclusion you end up with a kind of thin client arrangement where all your hardware does is establish a connection and present the information. I can't really see that happening to any great degree myself.

I know this thread is old, however I wanted to reply that I'm gathering some hardware to set up a cloud cluster on my lan. Specifically, I'll soon have my hands on a few G4 PPCs on which I plan to run some things locally (print server, samba shares, firewall, dhcp/dns server,etc.). I can post a new thread if anyone is interested in my progress?

---

### Post by PenguinInside on 2010-01-24
Well, everyone has a different definition of cloud computing, like the 3 blind men and the elephant.

Rackspace offers [http://www.rackspacecloud.com/](http://www.rackspacecloud.com/)
Amazon offers [http://aws.amazon.com/](http://aws.amazon.com/)

Ubuntu offers [http://one.ubuntu.com](http://one.ubuntu.com) for cloud storage
Ubuntu One works with your Karmic. Applications > Internet > Ubuntu One

---

### Post by wcorey on 2010-05-24
It's way more than the people who have answered have addressed.

Yes, it's a way to toss all but your oldest PC in the trash and let Amazon host (for a fee) all your favorite Windows or Linux apps. Start them when you want to play, shut them down when you're done.

But, consider you want to run a mail server that is totally isolated from all of your other servers. You want to run an app server that is totally isolated from your other servers. Rather than having one gigundo server with everything but the kitchen sink on it you want to have small dedicated servers for specific tasks. Supposing you want to 'upgrade to U10.4 or 10.10 or Fedora 12 but don't want to risk it totally trashing your one server. Put up your own cloud and start and stop whole servers that run as virtual images in your cloud, for free, not Amazon's for $$$. 

Chances are really good the guy with the server in his bedroom isn't going to have much use for a cloud beyond saying he has one but if you are IT at work and want to kick the tires without the company spending serious bucks at Amazon, take a couple of idle servers and build a cloud.

For corporations, having a private cloud renders the 'where is my data' question moot.

---

### Post by Calash on 2010-05-24
> **wcorey said:**
> It's way more than the people who have answered have addressed.

Yes, it's a way to toss all but your oldest PC in the trash and let Amazon host (for a fee) all your favorite Windows or Linux apps. Start them when you want to play, shut them down when you're done.

But, consider you want to run a mail server that is totally isolated from all of your other servers. You want to run an app server that is totally isolated from your other servers. Rather than having one gigundo server with everything but the kitchen sink on it you want to have small dedicated servers for specific tasks. Supposing you want to 'upgrade to U10.4 or 10.10 or Fedora 12 but don't want to risk it totally trashing your one server. Put up your own cloud and start and stop whole servers that run as virtual images in your cloud, for free, not Amazon's for $$$. 

Chances are really good the guy with the server in his bedroom isn't going to have much use for a cloud beyond saying he has one but if you are IT at work and want to kick the tires without the company spending serious bucks at Amazon, take a couple of idle servers and build a cloud.

For corporations, having a private cloud renders the 'where is my data' question moot.


What is the point of setting up a cloud if you do not have the infrastructure to put it to good use?  Really is not much more than a server farm at that point.

---

### Post by bnsmith001 on 2011-07-21
> **wcorey said:**
> It's way more than the people who have answered have addressed.

Yes, it's a way to toss all but your oldest PC in the trash and let Amazon host (for a fee) all your favorite Windows or Linux apps. Start them when you want to play, shut them down when you're done.

But, consider you want to run a mail server that is totally isolated from all of your other servers. You want to run an app server that is totally isolated from your other servers. Rather than having one gigundo server with everything but the kitchen sink on it you want to have small dedicated servers for specific tasks. Supposing you want to 'upgrade to U10.4 or 10.10 or Fedora 12 but don't want to risk it totally trashing your one server. Put up your own cloud and start and stop whole servers that run as virtual images in your cloud, for free, not Amazon's for $$$. 

Chances are really good the guy with the server in his bedroom isn't going to have much use for a cloud beyond saying he has one but if you are IT at work and want to kick the tires without the company spending serious bucks at Amazon, take a couple of idle servers and build a cloud.

For corporations, having a private cloud renders the 'where is my data' question moot.

Sorry, coming in late.

So a cloud is nothing more that a "GoToMyPC" or "TeamViewer" tool?

I am an IT/IS guy... I've supported hardware/software/user interfaces and databases throughout my career... so I'm trying to figure out where I fit in this "cloud".  I don't see any birds, and I can't see any side of a mountain, and my gyroscope can't even tell me if I'm up/down/left/right or even my speed.

I'm trying to understand a recent news article that said companies will not be hiring any IT or IS people to work in-house, and be getting rid of the one's they have, because cloud computing will completely remove the need for an IT team/department... and that all app work now will be done in the cloud.

Great! So where are all of the "cloud companies" that are hiring all of the IT/IS people?

I'm almost to the point where I think that the person talking about the cloud is blowing smoke (you know the rest of that clause).

So, a "cloud" is just a web addressable ISO that users login to?

I guess that I need a mid-technical thread about what a cloud is.

Is there one of those?

Thank you.

---

### Post by haqking on 2011-07-21
store all your data on someone elses machine that is connected to the internet, and use someone elses apps to do your work instead of the ones on your machine.

Put your whole life out there for others to control and your in the cloud ;-)

---

### Post by NetoriusNick on 2011-08-10
I know this is most likely incorrect but I though cloud server was a way for creating a large pc from several separate smaller PC's. 
In my case I have some old PC's that I want to clump together to use as a server for a website, email and possibly a chat server. (some may be on separate PC's but I don't think some of the PC's will be able to take the load of the application just by them selves)
If I am being a complete twerp just say.

---

### Post by helzpain on 2012-03-01
I know this is an old thread, but I did not want to start a new thread based off of an old premise.

I would like to set up an internal cloud to distribute physical resources (such as hard drives, cpu's and ram) across my network. Basically build two virtual machines that utilize all the computers on my network. I want some of the computers to be ran as a server farm and the rest to be for workstations. Does anyone have any good resources for information on this concept, or am I heading in a new direction here?

---

### Post by Zill on 2012-03-01
> **helzpain said:**
> ...I would like to set up an internal cloud to distribute physical resources (such as hard drives, cpu's and ram) across my network. Basically build two virtual machines that utilize all the computers on my network. I want some of the computers to be ran as a server farm and the rest to be for workstations...
Is this not simply a [Local Area Network (LAN)]("http://en.wikipedia.org/wiki/Local_area_network")?

---

### Post by helzpain on 2012-03-01
Not the way I envision it in my head. The server farm portion is for load balancing. Basically with the workstations, I would like to set them up as they are one large machine that distributes resources on a per user call, rather than individual machines that are networked together. All the workstation resources are distributed, almost like they are one large server and  thin clients at the same time. Another way to describe it would be kind of like resource pooling between workstations. Not just hard drives though, all available resources (such as ram, cpu's, etc...). I guess a network operating system would be the best way to describe it.

---

### Post by psidjut on 2012-03-10
If you want to get help from a private cloud data center then clone systems will be helpful for you.[http://www.clone-systems.com/private-cloud-data-center.html](http://www.clone-systems.com/private-cloud-data-center.html)

---

### Post by audiomick on 2012-03-10
> **helzpain said:**
> ...I would like to set them up as they are one large machine that distributes resources on a per user call, rather than individual machines that are networked together..

Sounds like this to me
[http://en.wikipedia.org/wiki/Cluster_%28computing%29](http://en.wikipedia.org/wiki/Cluster_%28computing%29)

I'm guessing, but I am sure the technology is out there to do at least some of what you are thinking of.

---

