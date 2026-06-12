---
title: "Active Directory Authentication and Share Questions"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by Bpope on 2008-06-01
Hi, 

I'm pretty new to linux, but very much enjoying it so far. Right now my company is considering using linux servers as file servers to save some costs and add stability.  I've been asked to "play around" and see if I can come up with something viable. So I'm going to post our hypothetical network layout here and see if I can get some help from the community to get things up and running. 

Right now, We have an Active Directory network with an exchange server and 2 primary domain controllers.  we'll give the domain controllers the following hypothetical IPs:  

1st domain controller (1DC): 1.2.33.1
2nd domain controller (2DC): 1.2.33.2
Our Domain Name will be Example.local

We also have our current file server which is Win Server 2k3:

Win server 2k3 File server (FileServ): 1.2.33.3

Then there's our exchange Server:

Exchange Server (Exch): 1.2.33.4

And of course, our Linux file server.  I've created an reservation in DHCP for the linux box, so it's always given the same IP address on the network.

Linux Server (LinServ):  1.2.33.5

For all intents and purposes I'll be wanting to authenticate as a domain admin to the linux machine for pretty much everything. We'll say my administrator log-in as as follows

Domain admin login: Scoobydoo
Domain admin Pass: Ih34rtShaggy

So far I've installed ubuntu 8.04 the client version and I'm working on authenticating users at log in.  So far, I'm able to see the files and mount windows shares by going to Places --> Connect to a network.

From there I put in the name of our file server (FileServ) set it as a windows share and navigate to the appropriate directory on the file server and it works and the scoobydoo login and pass when prompted.  There are some problems (it tells me it cannot mount the share, but does anyway, and puts two icons on my desktop to do so) but it still works.

My understanding is that this isn't really authenticating with samba, but just using smbfs to see shares on the network. 

I've tried the opposite, sharing a folding from the linux server home drive across the network, but it won't share.  I used the standard, default, "Video" folder contained within the home folder since some of the files we want to share are media files for marketing, I right click, go to properties go to share, I get a prompt that sharing services are not installed, so I choose "install services" then I go click "create share" and I get an error that lock directory /var/run/samba does not exist, also pid director /var/run/samba does not exist. 

Fair enough, I can take a hint, ubuntu.  I go to command prompt and type sudo apt-get install samba.  It tells me that the package is unavailable, but may be referred to by another package, meaning it may be obsoleted, but that the following clients are available as a replacement:  smbclient and samba-common.  I run a sudo apt-get on both of those and have the newest and latest version. 

I'm kind of stuck here.  And so here are things I'd like to accomplish with the communities help.

The first two goals are the major ones.

1)  I'd like to authenticate on the domain on linux box as my AD domain admin account Scoobydoo instead of authenticating as a local user on the linuxbox then authenticating the domain windows shares as the AD domain admin individually. 

2)  I'd like to share my /home/Video folder across the entire network to any authenticated Active Directory user. 

The rest of my goals are completely secondary, but if it's at all possible, I'd like to achieve them as well. 

3) I'd like to set up evolution mail to work with Scoobydoo's exchange account

4) I'd like to share a network printer on the example.local domain, I'm assuming this will be done through CUPS, but I have no idea how to even get started here. 

Also, I'm running the client version of ubuntu 8.04.  I only installed this version because it looked easy to get up and running with.  If I need to start again by installing ubuntu 8.04 server and setting things up from there.  I'll gladly do that. 

thanks for all the help on the front end, and the way it's looking, if I can get this set up here, I'll be switching to ubuntu on all my home PCs and laptops as well.

---

### Post by Bpope on 2008-06-01
anybody?

---

### Post by Kileli on 2008-07-11
> **Bpope said:**
> anybody?

it doesn't look like anyone will answer this did you resolve the issue? i have a very similar problem

---

### Post by carlo bolzonello on 2008-10-27
Hello guys,

i have tried the following, so i am going to tell you what i have found. The evolution cleint is not stable with exchange at all, if you send mail via evolution though the exchange server, go and open a seperate machine session with outlook and you will see no mail in your sent folder using the same mailbox. This is a issue i dont know how to resolve :( and its keeping me on windows. Secondly, eveoltion authentication to AD keeps dropping, you can run it via IMAP, but thats also unstable.

i will post more as i test

---

### Post by brown.hornet on 2008-12-09
Bpope –

I to wanted to get my Ubuntu box on my Windows Domain and have ran into all sorts of issues.  Unfortunately as I am sure you have discovered getting help when it comes to working with Windows is for all piratical purposes next to impossible at best to get.  After some digging around I found the following post (link below) on how to get a Ubuntu server into a Windows Domain.  Using this I was able to get my Ubuntu server on the domain as well as my workstation (Requirement 1).  Once the systems were in the domain I was able to create shares and access them from my Windows XP workstation, SBS 2003 server, and iMac (10.5.4) (requirement 2).  I was able to get Evolution working; however, I am also having problems with Exchange tracking messages that I sent using Evolution.  Currently I am using Crossover ([www.codeweavers.com](www.codeweavers.com)) on my Mac and I run Office 2003 Pro and use Outlook without any problems.  According to Codeweavers’ website you can use Crossover on Ubuntu. (Kinda meets Requirement 3).  I have not tried to share a printer from either my Ubuntu server or workstations; though, I have successfully attached a Windows printer to my Ubuntu workstation (Requirement 4?). 

[http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html]("http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html")

Some parting thoughts –

- If you are planning on storing media files then I suggest building the server as it seems much more agreeable with working in a Windows Domain.
- Though Ubuntu has some neat features I truly don’t believe that it is really ready for full and easy integration into Windows.  I don’t consider editing numerous .conf files as easy and simple Windows integration.
- As far as for your business I would not consider either Server or Workstation a viable solution unless you are willing to dump Windows.  As you can see within the post on this as well as other forms on the Ubuntu site getting the two systems to easily work together is not that straight forward.  As such any perceived benefits/savings would most likely be lost by the amount of time required to get the system working in harmony.  Not to mention you have not even addressed Exchange and from what I have found again there is not a straight forward solution to replace Exchange within the Linux world.

---

### Post by Raphaeld on 2008-12-18
Bpope,

Just did the move from XP to Ubuntu 8.10 on my corp laptop.
I had the same concern and I found this very good article
[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

just did the 3 first steps and that's it. 
Thanks to Vide for sharing this.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]
hope this will help you.
Enjoy

---

