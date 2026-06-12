---
title: "Trying to set up a Linux network... (file sharing, user logins, etc.)"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2007-11-08
I volunteered myself to set up, configure, and run a local Linux network for one of my teachers for a small class he's teaching.

The only problem: I'm fairly new to networking. My knowledge extends to setting up my Linux box at home to work with wireless, and that's about it. The way we want it set up is far more advanced that just a local wireless network to get internet, and I don't know where to start.

I've already gotten some help from a different forum, but since I've run into a few more problems than I thought I would, I figured I'd post my dilemma here for faster responses and more in-depth thought. 

What we're trying to do is set up a network that will allow for users of client machines to log into user accounts stored on a server. Basically, everything is done and stored on the server. Kind of like how schools set up their Windows network. You log in with your student ID and password-pin, and all your stuff is stored on a centralized server rather than the client machine. New users are added to the server, user files are stored on the server, etc.. Let me explain a bit how our network is set up.

The Ubuntu server is connected to the schools network via eth0 (this allows it to have internet), and to a 24-port switch via eth1. The server's eth1 is at a static 192.168.123.1. We then have 4 Ubuntu boxes set up to serve as clients, and are also connected to the same switch at eth0 (there's only one eth port on these boxes). The clients start at a static 192.168.123.11, and go up from there. Currently, we only have one client that's able to ping the server, and vise-versa. We'll be configuring the other clients to work once we get the one that pings completely working to do what we want it to do...

Here's a picture (that I shamelessly edited from [this]("http://aboutdebian.com/sharing2.gif") :)) that shows our network configuration:
[IMG]http://i82.photobucket.com/albums/j255/XtremeGamer99/network.gif[/IMG]

The whole idea is to have the server store the information from the clients. I'm not sure how to explain this, so bear with me. If the server has user 'Rachelle', then she will have a home directory of /home/Rachelle on the server. We want Rachelle to be able to log on from one of the Ubuntu clients, and have her files and everything in her home directory on the server available on her client machine. She will be able to work on her files from the client machine, use programs that are on the client machine, and save files to her home directory on the server.

We're using NFS to mount the servers /home directory to the clients /home directory so that the client machine can work with user files and whatnot. This is where the problems are starting. First off, it's not mounting at boot time, and I'm not sure why. This is what I have as the servers /etc/exports (192.168.123.11 being the client that we're working with):

```
/home 192.168.123.11(rw,no_root_squash,async)
```

And this is what I have as the clients /etc/fstab:

```
192.168.123.1:/home    /home    nfs    rw,hard,intr    0    0
```

Like I said, it's not mounting at boot: I have to manually mount the servers /home to the client by using [FONT="Courier New"]mount /home[/FONT] to further test whats working and what's not. Once the servers /home is mounted, we're having problems logging into the machine. Lets say that the server has the user 'servertest' with a password of '123qwe'. The user's home directory shows up in /home on the client machine, however it won't let us log into the machine using that user, saying that we provided an "Incorrect username or password" when using the GNOME login; "Unknown id: servertest" when using [FONT="Courier New"]su servertest[/FONT] in the terminal. I'm guessing that there's another file that's required to log in; something like a user database that I need to mount. I dunno. =/

I'm new to networking, and I'll admit that I'm still a newb at Linux (which is one of the reasons I took up this challenge -- to learn). Can someone help me out? Thanks!

PS: I'll also be using this thread, once I get this set up and functional, to ask questions I may have or run into, such as setting up a user's quota (so they don't flood the HDD), routing internet access to the client machine (currently only available to the server unless I manually connect the client to the internet), and some other things. =D

---

### Post by BoneKracker on 2007-11-08
[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by Lem on 2007-11-09
I'd have a good look at LTSP (it's integrated with Edubuntu or downloadable for Ubuntu)
The downside is that the documentation is a bit of mess with lots of outdated information. Many new features and major changes have taken place (esp. moving to LTSP5).

However, it's pretty easy to get running and you can use any old tat for you thin clients. It solves a lot of issues for setting up samba shares, PAM authentication etc.
You'll need a reasonably beefy server, but it uses far less grunt and memory than virtualisation. I'm involved in a project with a company working with virtualisation servers. However, early tests indicate that on one of their entry level core2duo servers, I could run 50 LTSP clients, rather than 15-20 virtual machines!

Resource-wise, you're looking at 50Mb memory capacity on your server per user over an above what the server needs to run.

---

### Post by XtremeGamer99 on 2007-11-09
Okay, I'll look into LTSP.

Any other suggestion are more than welcomed!

EDIT: I've scanned some articles about it, and it seems that 'thin-clients' run completely off the server, including applications and user logins and everything. I was hoping more for just user logins. I would like applications to be on a client-based basis (0_o), so that we can eventually set up different client machines for different purposes, while user's and related things stored on the server.

---

### Post by SpiritIsReality on 2007-11-09
howdy
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
trails

---

### Post by BoneKracker on 2007-11-10
If you don't want the thin-client architecture then here are some other things you could consider.

The clients can use NFS to mount a partition that's on the server as though it were local (e.g. a common /home directory, a common /usr directory, etc.).  That way, no matter which of the clients a student logs into, the machine they're logging into has their home directory "on" it.  Common /usr directory is a way to avoid having to install most of the user-specific applications to each-and-every client.

You can use authentication architectures such as LDAP or Kerberos to centralize user login processing to the server.

Personally, I think LTSP is a brilliant architecture for schools.  But there are many ways to accomplish what you've said you want to do

It might be a good idea for either you or the eductator to whom you are reporting to become a bit more familiar with Linux before you roll this out to students.  One of the nice thing about thin client is how it makes normal student antics harmless.  

If you do something else (like NFS mounts and LDAP auth), I suggest you take a disk image of your standard client machine so you can reinstall them from scratch regularly -- because they will be hacked, deleted, messed up, and monkeyed with in ways you couldn't even imagine.

---

