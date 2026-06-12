---
title: "Trying tomake a fileshare network with Vsita"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by Omnios on 2008-01-15
Hi I have beeb trying to set this up for a bit now.
 
 After varios how to's I used the one on Ubuntu guide for a set up.
 
 Anyways trying to conect today and things seem a bit wierd in that the other day I could see my Ubuntu box and now I can not. However I could not open the fileshare. 
 
 I have been playing around with this a bit now and canot figure out how I saw it the other day.
 
 I should be able to connect to it if I can see it in Vista.
 
 Any suggestions.

---

### Post by mimada on 2008-01-16
There seems to be an issue with samba and the iptables firewall. Try disabling iptables and see if you can access your shares.

---

### Post by Omnios on 2008-01-16
K weirdest thing. Been playing around with it for a few days now. Anyways last night I read and used [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Servers") to set up Samba. 

 Now I have been battling all day in this building pertaining to internet connections  routers and wireless. Getting connection and disconnections. I kept getting locked out of my firewall admin page so I ended up pulling the plug on the router a few times today. Problem was Id get kicked and when trying to reconnect I got a "The router page was already getting Administrated by someone else"

 Anyways kept it disconnected for a while and tried again and could not log into the router page. After trying to fix it I finally used the router reset to change it to factory defaults. Reinstalled the firmware and played around with it. Anyways realized the lan ip was still the router default so changed the lan and lan ranges to something else. This always seemed to F,U when I would get my wireless secure. Anyways so far so good.

 K now the problem I am having is that Vista can see the home directory and I mean I can brows and view that directory without logging and pass. I also have my download folder set up as a share. When I try to get into the download share  It prompts for user-name and pass. Another problem here I tried using the user and user-pass from the set up and it will not let me into the folder.

 K first off not sure about the /home directory but in the config it has my Vista name as user.

 As for the download share I am stumped so far.

 What I want to accomplish not have all my /home viewable.

 I want to set up specific folders on in my /home directory and also set up shared on my "My Documents drive which is shared with Ubuntu as documents.

 Anyways so far I managed to connect and play a song from ty server  using Samba.

 Any help will be appreciated.
I also think I am going to have to do some heavy security stuff for my shares, know of any good reads?

---

### Post by mimada on 2008-01-19
Your problem with the router sounds like either a hack attempt or some malicious program trying to keep you from locking it out. It could also be some corrupted packets in the network gumming things up. I don't know what your setup is like so I can't be sure.

If you want to troubleshoot on your own, I suggest browsing the [**samba.org**]("http://samba.org") site. You should at least get to know the smb.conf file stuff and how to check it using testparm.

Otherwise, if you need more online help, you ought to describe your network setup and post your smb.conf file. Be careful to remove anything that might compromise your security from any files you decide to post.

Good Luck!

---

### Post by Omnios on 2008-01-20
K got it to work. Now I want to secure it. 

 I am thinking of using something on the lines or a mac address filter to varify the machines on the network.

---

