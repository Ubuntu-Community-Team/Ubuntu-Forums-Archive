---
title: "Need guidance with server-client authentication..."
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by dxtremeb on 2008-02-06
Hey, I'm new to posting, but have been a long time reader. I'm debuting with a question that I've been trying to find the answer to for days. I don't know how much information you'll need to help me, so I'll just start giving it out.

Here's my set-up:
I have a server that has three ethernet ports. eth0 isn't assigned to anything (I might assign it to a network printer later on), eth2 goes to the internet, and eth1 is assigned the IP address 192.168.123.1. This connection goes directly to a 12-port switch, and this address acts as a gateway to the internet (I have a script running on start-up to route the internet from eth2 to eth1).

From the switch, four computers (clients) are connected, each given a network address from the server via DHCP. The range is 192.168.123.10 to 192.168.123.30.

Now, what I want to do:
At the moment, the clients are only able to log in locally from the users on that machine. I don't want this. The only local user that I want on the clients is root. What I want is for the users to be stored on the server; their home files and everything. I want them to be able to put in their username and password, and for the client machine to fetch their personal files and whatnot from the server and display them on the screen as if they logged in locally. This would mean much easier management of users (having them all stored in one place), and having their files available from whichever computer they log in from, as opposed to having it available only on one computer.

How would I be able to achieve this? BTW, I'm using Ubuntu for both the server and the clients.

Thanks!

---

### Post by dxtremeb on 2008-02-07
Up to the top...

---

### Post by dxtremeb on 2008-02-08
Anyone know? I'd like to get a workable answer by Monday, so if anyone knows any way...

=D

---

### Post by CRYPTKEEPER on 2008-02-08
I have the same problem. I believe you can not access root from a remote user/desktop. I may be wrong but i have not find a way around this yet.

---

### Post by dxtremeb on 2008-02-09
Er, I'm not wanting to access root remotely. Quite the contrary -- the only local user (that is, the only user on the client machine) that I want available is root, and only use the root to set up that individual machine. I'm wanting the regular users stored on the server, along with their personal files and such, and have them able to log in via the client machine and work on their files from there.

---

### Post by DarbCal on 2008-02-09
I believe what you are wanting is a nis server.   A google search returns a few nis tutorials.  The only Ubuntu tutorial I found is at [https://help.ubuntu.com/community/SettingUpNISHowTo]("https://help.ubuntu.com/community/SettingUpNISHowTo")  

I haven't tried it, but it should give you a nice starting point.

Good Luck!

---

### Post by DarbCal on 2008-02-09
another link to get you started:  [http://www.linux-nis.org/]("http://www.linux-nis.org/")

---

### Post by cdtech on 2008-02-09
Package download........

[[COLOR="DarkRed"]NIS[/COLOR]]("http://packages.ubuntu.com/dapper/net/nis")

---

### Post by dxtremeb on 2008-02-09
Thanks all! I'll look into NIS.

Anymore suggestions are appreciated.

---

### Post by dxtremeb on 2008-02-09
Okay, yeah. NIS does seem to be what I'm looking for.

So, should I use NIS or NIS+? Or is there any difference?

---

### Post by DarbCal on 2008-02-09
NIS.  The linux-nis.org website says "There is no NIS+ server for Linux and it doesn't look like that there will ever be one."  

I have used nis in the past and it is in use at my work, but I don't know much about it.   I do plan to set it up on my home network in the near future.

---

### Post by rome-NY on 2008-02-20
Nis is what you want. I have a nis server up and running for 5 years now. It is fantastic. I have seven systems on my network and all running suse nis clients. But if you plan on running kubuntu on the client I don't think  you can use NIS. I have been trying to setup my system as a nis client running kubuntu but no go. I can ypcat my passwd.---- files and see them but kubuntu wont allow me to login. If you find a way let me know because i would really like to use kubuntu, but without nis support I can't use it....so sad

---

