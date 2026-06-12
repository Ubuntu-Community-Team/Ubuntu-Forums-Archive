---
title: "New to linux and tryin to get some networking help"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by jodesama on 2007-04-17
I'm very new to these forums I am a student, and i have a project that i'm doing for my Unix class on whatever i want to do within Linux, i chose Ubuntu after being referred to it, but i want to use the ssh feature, can i use this with he desktop version, or should i use the server version and get a GUI? 
I've searched a bit through this forum but i have not found an answer to this particular question.

also my computer is a 1 gb k6  with 128 MB of RAM i was told it should be able to handle Ubuntu but i'm just making sure that i was at least ok with it from ppl that use it and have exp.

oh...and does ubuntu support cisco routers? the wrt models...if anyone knows by chance....thanx

---

### Post by dfreer on 2007-04-17
> **jodesama said:**
> i want to use the ssh feature, can i use this with he desktop version, or should i use the server version and get a GUI?

```
sudo apt-get install ssh
```
There is NO difference really between the desktop and server edition, other than the packages installed by default. Same thing with Kubuntu, Xubuntu, Edubuntu, etc.

> **jodesama said:**
> also my computer is a 1 gb k6  with 128 MB of RAM i was told it should be able to handle Ubuntu.

should be fine, although it might run a little slow when using the desktop. more than enough for a server install :D

EDIT: 
> **jodesama said:**
> oh...and does ubuntu support cisco routers? the wrt models...if anyone knows by chance....thanx
ummm... not sure what you mean here? I believe you configure most enterprise-class cisco routers by telnet, which should work fine.

---

### Post by joft on 2007-04-17
> **jodesama said:**
> but i want to use the ssh feature, can i use this with he desktop version, or should i use the server version and get a GUI? 


Well, wether you chose Server or Desktop version really doesn't matter if you just want use ssh. There should be no problem installing the ssh daemon (ssh server) on the Desktop version. (I assume you want to run a ssh server or what du you mean by "ssh feature"?)

> **jodesama said:**
> 
also my computer is a 1 gb k6  with 128 MB of RAM i was told it should be able to handle Ubuntu but i'm just making sure that i was at least ok with it from ppl that use it and have exp.


Hmmm, I think it doesn't hurt having a little bit more RAM (256 MB), if you want to use GNOME - at least this is my experience. It works with 128 MB, but your swap partition might be quite active. Perhaps Xface is the better alternative to Gnome (as GUI).

> **jodesama said:**
> 
oh...and does ubuntu support cisco routers? the wrt models...if anyone knows by chance....thanx

What do you mean? Ubuntu certainly does not run an WRTs. Connecting to it _as a client_ is no problem. BTW: There is a free firmware for WRTs: [www.openwrt.org](www.openwrt.org) .

---

### Post by jodesama on 2007-04-17
when u say as a client what do u mean?

and when i say ssh feature basically i wan to be able to remotely access my files from anywhere  ( i believe thats what ssh does)

as for the RAM i will try to get more for this system b4 i install it with this 128, this PC was originally built for Windows ME (yes ppl bought ME) and i now have P running on it, but its slow as hell.  if the ubuntu will use resouces the same way then i will try either the RAM route or the Xbuntu route...i believe thats what u mean by Xface.

When i say cisco routers i mean the linksys routers...they're made by cisco rite?
does the above reply mean that i have to update my firmware for it to work? if so would my other devices be affected by this...it says that my model router is a Work in progress (WiP)

---

### Post by joft on 2007-04-17
> **jodesama said:**
> when u say as a client what do u mean?

By client I mean, a PC which connects to an access point (e.g. such a WRT box).

> **jodesama said:**
> 
and when i say ssh feature basically i wan to be able to remotely access my files from anywhere  ( i believe thats what ssh does)


Well, yes, but ssh does more than that (stands for secure shell => encryption, shell access/virtual termnial and of course file access).
So you want an ssh server/daemon.

> **jodesama said:**
> 
When i say cisco routers i mean the linksys routers...they're made by cisco rite?
does the above reply mean that i have to update my firmware for it to work? if so would my other devices be affected by this...it says that my model router is a Work in progress (WiP)

Yes, by Cisco. No, you don't have to replace your current firmware. And it seems that you have new WRT device (=> WiP).

---

### Post by jodesama on 2007-04-17
thank you very much. i think tat smost of my questions have been answered. I have already gotten the desktop version of ubuntu. to get the ssh server/daemon where to i get it. where do i get all these extra programs? i kno they all open source, is it that theres a way to get them from the OS? cause i believe thats wat i read on the documentation.

---

### Post by dfreer on 2007-04-17
If you are just wondering if your ubuntu box will hook up to the router, the answer is yes.

---

### Post by dfreer on 2007-04-17
the command I gave above will install the server, which runs as a daemon.

---

### Post by jodesama on 2007-04-19
when i have my ubuntu up and running, i kno that i have to use a special program (cant remember the name right now) that i have to use to get to my ssh from windows, but what about from another ubuntu system? can they run it straight from the OS, or do i have to get a program to access it from there as well?

---

### Post by askreet on 2007-04-19
SSH is primarily a method of accessing a Shell from another computer.  You can also use secure file access (WinSCP is a common program in Windows).  In Ubuntu, you can install any SCP/SFTP client to retreive files from another Ubuntu PC.  You can also use the commandline program **scp**, which is included by default.

- Kyle

---

### Post by jodesama on 2007-04-21
i currently have the XUBUNTU (feisty fawn) installed. but i dont see a places menu for me to link so an ssh server, can anyone help this one?

---

### Post by joft on 2007-04-23
Open a terminal window (I think in Applications -> Accessoires) and call ssh :
```

ssh <hostname or ip>

```
Then you'll get a remote shell and you can type commandos like you were infront off that specific PC.

---

### Post by jodesama on 2007-04-24
ok, i am now on a windows computer, and im trying to log on to my linux system from winscp, im putting in my hostname and my username and password that i use to login normally. would the fact that i am still logged in on my linux system cause a problem? its telling me that the host does not exist...does it matter that the windows and the linux are pulling internet from the same router in my home?...also does the port number matter? if so where do i go to set the port and what about my host name where is that listed? cause i thought that it was what comes up in the terminal promt.

---

### Post by dfreer on 2007-04-24
on a windows computer you will need to use putty or (my favorite) the official SSH client. it should default to using port 22, so unless you've changed that it should be fine. First, ping the linux machines IP address (not the hostname), to make sure that you can connect to it. Then try using the client to connect. You will need to enter the same username and password that you use on the linux machine (again, make sure to connect by IP address and not hostname). If you can connect via IP address, THEN try doing it by hostname (depends on how your network is set up, you may not be able to use the hostname)

lol this is linux, not windows. You can log in with the same account 10 times and/or have 10 different people logged in at the same time.

---

### Post by jodesama on 2007-04-25
thanx much...so i got my ssh to work while im connected to my router at home, using the internal IP, but i'm now in a different network, and trying to get to my ssh using the foward facing IP since we all kno that the internal address is worthless outside of the network. Now i cannot connect to my linux machin from this other network, nor can i ping my routers foward facing IP, any suggestions?

i also tried using my hostname, that didnt work either.

---

### Post by dfreer on 2007-04-25
hmmm. so now you want to ssh from the internet to your local machine? several things you'll need to check out:

Do you have a static IP at home? If not, check out dyndns/no-ip

Does your ISP block port 22 (my university did)?

Do you have your home router's Firewall and port forwarding set up to allow ssh?

---

