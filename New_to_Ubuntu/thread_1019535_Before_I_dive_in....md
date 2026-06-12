---
title: "Before I dive in..."
date: 2008-12-23
forum: New to Ubuntu
---

### Post by ohwhynot on 2008-12-23
Hi all,

early next year I'm going to be working on a hobby project which basically comes down to introducing a server into a small Windows workgroup. Since there's no real rush behind it I figured this might be a good opportunity to take the plunge and give Ubuntu a shot.

My total Linux experience to date: zero :lolflag:

I've been reading up on things (without getting into much detail) and I'm confident that with all the info available online I'll be able to figure most things out. At the same time it's all a bit overwhelming and I'm afraid that at some point I'm going to hit a wall, only to find out something like "Oh that? Nope, can't do that with Ubuntu, sorry." :(

So what I'm looking for at this point is to figure out if what I have planned is going to work at all (or is realistically too hard for someone with zero Linux experience). Otherwise I'll just forget about the whole thing, set up a Windows Server and be done with it :) I would appreciate any input, sorry for the length of this but I'd rather be specific than forget something that later turns out to be crucial...


**Workstations**
It's six total, four are running Windows Vista Ultimate SP1 (front office) and two are running Windows XP SP3 (machine room). None of the users have admin privileges. Additionally, the owner brings in a laptop from time to time that connects to the network (wireless). I'm not 100% on what that laptop is running, but it has internet access and full access to the network shares.

**Server**
Nothing too spectacular but it would do the trick in a Windows Server setup, it's a 2.4 Ghz DualCore with 4 GB of RAM on a [Wolfdale1333-D667 R2.0]("http://www.asrock.com/mb/overview.asp?Model=Wolfdale1333-D667%20R2.0") motherboard. I should also mention that the 500 GB HDD is a SATA drive, since I read that can complicate installation a bit? Just for clarity: that machine is currently not in use, it has a Windows XP installation on it that can go.

**Internet**
The internet cable is hooked up to a [Linksys WRT54G Wireless-G Broadband Router]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper"). The wireless internet (WPA2) is provided so employees can browse the internet on their own laptops during breaks. They have no network access otherwise. There's also the owner's laptop (see above) that does have access to the shared folders.

**Network setup**
The Linksys router is connected to a [Dell PowerConnect 2708 switch]("http://www.dell.com/content/products/productdetails.aspx/pwcnt_2708?c=us&cs=555&l=en&s=biz") (owner's quote: "We bought the black box 'cause the blue box didn't have enough holes"). All workstations have a wired connection to the switch, giving them access to the internet and the network shares. The server would be added to either the router or the switch, plenty of free holes in both :)

**Network shares**
There are two virtual drives that are available to all six workstations and the owner's laptop. They physically reside on one of the Vista machines but would move to the server. At the moment there is no restriction to what machine or user has access to which files and folders, but that would change once the server is in place.

**Printer sharing**
There is a single shared printer hooked up to one of the Vista machines. That would stay like that, but I want to be able to add shared printers to either another workstation or directly to the server.

**Roaming profiles**
I want to introduce roaming profiles for the four Vista machines only.

**Remote access**
[LIST]I need to be able to access the server from my home.[/LIST]
[LIST]The owner needs access to the shared folders from his home. Ideally, he should have access to his roaming profile so he could log on from home as if he was sitting at his desk at the office.[/LIST]
[LIST]I need some sort of Remote Assistance capability, allowing me to take over any workstation from my home.[/LIST]
[LIST]Users need a way to make files available to business clients on the server. So a user would put a file on the server, contact the client with a URL for the file and the client downloads it.[/LIST]
[LIST]All of this obviously needs to be secure as hell :)[/LIST]

**Backups**
There's an external HDD (USB) that needs to be hooked up to the server every day to run a full backup of the shared folders and user folders. The backup process is done by a regular user so it should be as straightforward as can be.


That's all I can think of at the moment. Again, I'm not looking for help on any particular item (useful links are always welcome of course) but just trying to hear if there's anything in the above list that's going to cause me serious headaches if decide to go with Linux.

Thanks for your help!

---

### Post by nerdking on 2008-12-23
let me be the first to say, welcome to ubuntu. The idea you have should run smothly and if any thing unexpected happends just come back here and ask for help. :)

---

### Post by Titan8990 on 2008-12-23
I would like to start by saying, don't start your Linux adventure with servers.

The first thing that happens everytime is people say "where is the GUI?" Without prior experience of the terminal and how basic UNIX based systems operate it is next to impossible to go from being a Windows administrator straight into a Linux server.


Install Linux on your desktop at home. Play with it without using GUIs to administer the server. Set up some servers on your desktop OS to test and play around with. Compile your own kernel or two.

Once you have some knowledge of BASH and how UNIX systems operate, then you can consider implementing it in your production environment.


> Roaming profiles
I want to introduce roaming profiles for the four Vista machines only.


This is the only thing I see as questionable. But why roaming profiles when you only have 4 machines to make users on??? Roaming profiles were created for admins who had to deal with 100s of users with 100s of computers.


Edit: Why use Windows workstations at all?

---

### Post by halitech on 2008-12-23
> **ohwhynot said:**
> Hi all,

early next year I'm going to be working on a hobby project which basically comes down to introducing a server into a small Windows workgroup. Since there's no real rush behind it I figured this might be a good opportunity to take the plunge and give Ubuntu a shot.

My total Linux experience to date: zero :lolflag:

I've been reading up on things (without getting into much detail) and I'm confident that with all the info available online I'll be able to figure most things out. At the same time it's all a bit overwhelming and I'm afraid that at some point I'm going to hit a wall, only to find out something like "Oh that? Nope, can't do that with Ubuntu, sorry." :(

So what I'm looking for at this point is to figure out if what I have planned is going to work at all (or is realistically too hard for someone with zero Linux experience). Otherwise I'll just forget about the whole thing, set up a Windows Server and be done with it :) I would appreciate any input, sorry for the length of this but I'd rather be specific than forget something that later turns out to be crucial...
Linux is set up primarily to run as a server so this should not be hard to do at all
> 
**Workstations**
It's six total, four are running Windows Vista Ultimate SP1 (front office) and two are running Windows XP SP3 (machine room). None of the users have admin privileges. Additionally, the owner brings in a laptop from time to time that connects to the network (wireless). I'm not 100% on what that laptop is running, but it has internet access and full access to the network shares.

as far as the server goes, a computer is a computer so shouldn't matter to it what the computers run for an OS. Setting up shares might be tricky with Vista but thats Vista's issue, not Linux.

> **Server**
Nothing too spectacular but it would do the trick in a Windows Server setup, it's a 2.4 Ghz DualCore with 4 GB of RAM on a [Wolfdale1333-D667 R2.0]("http://www.asrock.com/mb/overview.asp?Model=Wolfdale1333-D667%20R2.0") motherboard. I should also mention that the 500 GB HDD is a SATA drive, since I read that can complicate installation a bit? Just for clarity: that machine is currently not in use, it has a Windows XP installation on it that can go.

SATA can be tricky but its getting alot easier as time goes along. The system should certainly run Linux with no issues (other then maybe the drive)

> **Internet**
The internet cable is hooked up to a [Linksys WRT54G Wireless-G Broadband Router]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper"). The wireless internet (WPA2) is provided so employees can browse the internet on their own laptops during breaks. They have no network access otherwise. There's also the owner's laptop (see above) that does have access to the shared folders.

unless you want to change the routing work over to the server, everything should be fine here as well

> **Network setup**
The Linksys router is connected to a [Dell PowerConnect 2708 switch]("http://www.dell.com/content/products/productdetails.aspx/pwcnt_2708?c=us&cs=555&l=en&s=biz") (owner's quote: "We bought the black box 'cause the blue box didn't have enough holes"). All workstations have a wired connection to the switch, giving them access to the internet and the network shares. The server would be added to either the router or the switch, plenty of free holes in both :)

**Network shares**
There are two virtual drives that are available to all six workstations and the owner's laptop. They physically reside on one of the Vista machines but would move to the server. At the moment there is no restriction to what machine or user has access to which files and folders, but that would change once the server is in place.

since you are running Windows on most machines, look into SAMBA for this

> **Printer sharing**
There is a single shared printer hooked up to one of the Vista machines. That would stay like that, but I want to be able to add shared printers to either another workstation or directly to the server.

same here, use samba

> **Roaming profiles**
I want to introduce roaming profiles for the four Vista machines only.


not sure exactly how to set this up but probably looking into setting up linux to act as a domain controller

[/quote]**Remote access**
[LIST]I need to be able to access the server from my home.[/LIST]
[LIST]The owner needs access to the shared folders from his home. Ideally, he should have access to his roaming profile so he could log on from home as if he was sitting at his desk at the office.[/LIST]
[LIST]I need some sort of Remote Assistance capability, allowing me to take over any workstation from my home.[/LIST]
[LIST]Users need a way to make files available to business clients on the server. So a user would put a file on the server, contact the client with a URL for the file and the client downloads it.[/LIST]
[LIST]All of this obviously needs to be secure as hell :)[/LIST][/quote]

multiple options here, ssh, vnc, vnc over ssh, etc. You will need to configure the router to forward the connection to the server

> **Backups**
There's an external HDD (USB) that needs to be hooked up to the server every day to run a full backup of the shared folders and user folders. The backup process is done by a regular user so it should be as straightforward as can be.

I believe rsync can be set up to do backups with a cron job

> That's all I can think of at the moment. Again, I'm not looking for help on any particular item (useful links are always welcome of course) but just trying to hear if there's anything in the above list that's going to cause me serious headaches if decide to go with Linux.

Thanks for your help!
welcome to the board and good luck with your endeavor :)

---

### Post by LowSky on 2008-12-23
Just to throw it out there Canonical (ubuntu's developer) does offer business support at a fee. there is also other distro like Redhat and Suse that have been arond for years that may offer better backend support. If you want to go free ubuntu/opensuse/fedora can all work but you are on your own for help. Something many companies would never like. I'm not try to scare you or tell you Windows is better or worse but as an IT manager you should really use what you are familiar with.

---

### Post by Malalo on 2008-12-23
> **LowSky said:**
> as an IT manager you should really use what you are familiar with.

I'm 50-50 on this one, since ohwhynot mentioned it was only a project. I think it's great that ohwhynot's willing to try out a Linux solution for his network. 
My advice to the ohwhynot would be to try the server features (available on the desktop environment as well, so you wont lose the GUI) on the free machine you have and if possible, get another machine to be a temporary workstation for testing purposes. Once your server is up and running as you want it, then add it to your network.

---

### Post by Titan8990 on 2008-12-23
> Once your server is up and running as you want it, then add it to your network.


After you install the server kernel and remove the GUI, of course.

---

### Post by Malalo on 2008-12-23
> **Titan8990 said:**
> After you install the server kernel and remove the GUI, of course.

Of course :)

---

### Post by ohwhynot on 2008-12-23
Wow, these boards move quickly :) Thanks for the replies so far.

Titan8990:

I spend a lot of time without GUI's (mainframes) so I'm not too worried about that aspect. But you are absolutely right about getting my feet wet first and I plan to do so. I just want to feel confident beforehand that in the end that's going to get me where I want to be and be more than just a fun leaning exercise. That's the main point of my post.

As for this:

> **Titan8990 said:**
> But why roaming profiles when you only have 4 machines to make users on??? Roaming profiles were created for admins who had to deal with 100s of users with 100s of computers.

Roaming profiles are beneficial in a situation where users don't always work at the same workstation. The actual number of users is irrelevant.

I'll certainly be reading up on that part though before I decide to do this or not.


halitech:

> **halitech said:**
> Setting up shares might be tricky with Vista but thats Vista's issue, not Linux.

You're probably right, but either way that makes it MY issue ;)

> **halitech said:**
> The system should certainly run Linux with no issues (other then maybe the drive)

Well having a working HDD is pretty high on my wish list :) But I guess it will be the very first thing I run into so if I can't get that part working that will be the end of that. I assume any issues I might run into installing the desktop version are similar to the server version regarding the SATA drive?

> **halitech said:**
> Samba

Yeah I've already been reading up on that, looks like that can take care of a lot of the things I need.

> **halitech said:**
> welcome to the board and good luck with your endeavor :)

Thanks! Your reply was very helpful.


LowSky:

> **LowSky said:**
> as an IT manager you should really use what you are familiar with.

Ture, but where's the fun in that :lolflag: Besides, if you want to broaden your horizon you have to start somewhere.


Finally, this:

> **Malalo said:**
> try the server features (available on the desktop environment as well, so you wont lose the GUI) on the free machine you have and if possible, get another machine to be a temporary workstation for testing purposes. Once your server is up and running as you want it, then add it to your network.

> **Titan8990 said:**
> After you install the server kernel and remove the GUI

was exctly what I had in mind so I must be on the right track :D

---

### Post by Titan8990 on 2008-12-23
> Well having a working HDD is pretty high on my wish list But I guess it will be the very first thing I run into so if I can't get that part working that will be the end of that. I assume any issues I might run into installing the desktop version are similar to the server version regarding the SATA drive?


The only time I have had issues with SATA drives was when compiling my own custom kernel in Gentoo. Other than that, never had an issue in the 10-20 machines I have installed Linux on.


You have the mindset that you need to accomplish your goals in Linux and I think you will be successful.

---

