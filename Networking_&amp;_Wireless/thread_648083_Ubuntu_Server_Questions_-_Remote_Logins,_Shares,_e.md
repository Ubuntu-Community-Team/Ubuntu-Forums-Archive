---
title: "Ubuntu Server Questions - Remote Logins, Shares, etc..."
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by redwolf3 on 2007-12-23
Hey guys, I did some searching but couldn't find anything related to what I was specifically looking for.

For about 6 months, I have been running my main system and file/printer server under Ubuntu desktop. It works very reliably and I am very happy overall, but there are some applications, etc, that prevent me from going to a strictly linux environment.

Right now, I'm planning on turning my existing desktop into a dedicated file and printer server. I have about 4 primary goals that I would like to achieve with this re-install, but I'm not sure of the best way to accomplish them (or if they are event possible):

[LIST=1]
[*]Remote Profiles: I would like to maintain a consistent, network maintained user profile (ideally, one that is semi-transparent whether logging in using a Windows or Linux client. The biggest factors here would be the use of a single "My Documents" folder on all systems.

[*]File Server: I would like to make a set of 3 folders on the server accessible as network shares to all users equally (I have accomplished this before, but now in conjunction with the user profiles).

[*]Automated SMTP/IMAP Server: I would like to setup a simple local server that basically checks my SMTP every, say, 10 minutes, and downloads it to a local box on the server that I can then later connect to and sync. That way if my mail server goes down or I lose connection, I still have my most recent email from, at most, 10 minutes ago.

[*]X Serve Server: At work, I regular use an X Client to connect to our dedicated remove servers for coding and performing other tasks. One of my goals with this setup would be to setup a good X Serve environment so I could connect to my dedicated server through an X Client for any of my larger personal project needs. That way they are maintained in one place.
[/LIST]

From the searching I've turned up, none of these seem to be too tall an order (most of them I have working presently). The 2 items that are going to be most important that I have the least information on is the user profiles and the X Serve end of things. I know I can setup an active directory like system in Linux, and then connect via Windows boxes, but I always see this referenced in conjunction with a master AD server that's on windows, which I won't have. 

Thanks for any help/suggestions you can give me. I hope to do a re-install in about 2 - 3 weeks, so I have some time to plan and prepare. And please, let me know if you have any questions.

---

### Post by karl0sglover on 2007-12-26
I did look at this a while ago, in the end came to not having enough time i was using Samba as the domain controller i got a windows client connected and thats about it gave up.

---

