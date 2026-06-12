---
title: "how to set up a server in my desktop"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by cosine352 on 2009-03-26
Hi All,
I have a desktop and I want to use it as a server. Mainly to serve as a backup the data in the network computers. Also may be run some applications from it by remote login. 
I have no knowledge about set up a server. I even do not know if a desktop can be used as server. 
If anyone know any good and easy tutorial for this purpose, please let me know. 

Thanks :guitar:

---

### Post by Coreigh on 2009-03-26
A computer is a computer. Calling it a desktop or a server or a workstation or whatever really only refers to its *primary* role or purpose.

With Ubuntu (or any Linux distro) especially it is easy to have the computer perform multiple roles. With small networks like home networks or single offices there is little problem doing this. Simply install the software that does what you need done. Web pages? Apache, and probably php and maybe MySQL or postgres. Share files with Windows? Samba. 

Backing up data in a small network is easiest done by making the "server" a file server by creating a shared folder (Samba if other computers are Windows) and then having each computer copy its data to the file server on a schedule. You could expand on this by creating folder shares on each computer and then telling the "server" to go get the data on a schedule. Then you can get more advanced and incorporate the ability for the backup to delete data older than a given time period. And so on as you skills and understanding grow.

Much of the information you may have seen that "frowns on" having a server do "dual-duty" comes from common practice for a "dedicated server" where there are more than a small number of computers and to have even a small period of the server being unavailable is a big and expensive problem.

Remember you have to start somewhere and if you are on your own and on a budget it is easier to start small... usually.

---

### Post by stone@bruti on 2009-03-26
As said above, a computer is a computer. A server genraly means that it is dedicated to one big task and enabling other computers to use its power or specific programs. [wikipedia might be a bit clearer than I am]("http://en.wikipedia.org/wiki/Server_(computing)"). they tend to not have a graphic interface to save on resources (well all but windows servers ... Flame on ^^).

right, back to the problem. A "Desktop" can easaly take care of backups and run remote apps. if you're just using Linux computers, have a look at these links :
[sbackup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")
[grsync]("http://www.opbyte.it/grsync/") (a better link probably neaded but google only gives me french pages ... try "grsync ubuntu howto" on *google.your_country*)
[X over SSH]("http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html")
or if you wan't to get your hands dirty with nice long scripts, rdiff and rsync are nice for backups.

if you have windows machines, SAMBA is going to be necessary and a remote access with VNC will give you the easiest way to execute remote progs. if not CYGWIn will give you access to X over SSH from windows.

Hope that sounds clear, been a long day :s

good luck

Stone

---

### Post by ibuclaw on 2009-03-26
Yes, you can make a Server out of your Desktop, you just need to install the right packages, and get your network/machine security setup as appropriate.

For data backup, you'll probably want to look at the HOWTOs on file servers. :)

How you go about setting it up will depend on what Operating Systems are running on your network. If you have Windows machine, then have a look at the HOWTO for [installing and setting up a samba fileserver]("http://ubuntuforums.org/showthread.php?t=202605").

For running applications remotely from it... I'm not sure what you are expecting from this, but a file server may offer this functionality (if the file has execute permissions). But, just for similarity sake, you could achieve running applications remotely by also using Remote Desktop, there is a cool [HOWTO on RD using Firefox]("http://ubuntuforums.org/showthread.php?t=541656").

Lastly, there is the subject of security...
If you are just wanting to use the server as a local server in your home network, then ensure that you are behind a router, and it doesn't port forward any ports to any computers. :)

Else, check out [The Ubuntu Security HOWTO]("http://ubuntuforums.org/showthread.php?t=510812") for good tips and info for locking down your server from the outside world.

Regards
Iain

---

### Post by albandy on 2009-03-26
The main difference between desktop and server is not the gui or the applications, is the kernel.

server uses no preemption  Deadline I/O and PAE.

---

### Post by cosine352 on 2009-03-26
thnaks guys

---

### Post by nothingspecial on 2009-03-26
My desktop`s now under the stairs acting as a "server" but I haven`t changed it (yet). 

If I access it using vinagre (remote desktop) there`s my wallpaper and everything still there - not very efficient, but I haven`t bothered to turn it into a superfast cli only server yet.

Plus because it still runs X and gnome I can run graphical apps on it remotely, if I want.

Have a good look at ssh [ssh]("https://help.ubuntu.com/community/SSHHowto"). That`s the best tool to get you started.

---

### Post by shane2peru on 2009-03-29
What is the best way to go about this with Linux - Linux file server.  I don't need/want Windows to access this?  Would it be the same howto that was referenced above?  Is there a more specific one for Linux?  Would it be the same as setting up NFS (Network File System)?  Thanks for the info.

Shane

---

### Post by MrWES on 2009-03-29
> **shane2peru said:**
> What is the best way to go about this with Linux - Linux file server.  I don't need/want Windows to access this?  Would it be the same howto that was referenced above?  Is there a more specific one for Linux?  Would it be the same as setting up NFS (Network File System)?  Thanks for the info.

Shane

I just set this up a couple of weeks ago, and I used the following guide from howtoforge:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

Bill

---

### Post by shane2peru on 2009-03-29
> **MrWES said:**
> I just set this up a couple of weeks ago, and I used the following guide from howtoforge:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

Bill

Yeah, I seen that guide, I was kind of hoping for a simpler solution just converting my existing desktop.  I don't want a server for outside access, I have set that up before, and it takes a lot, plus security setup after that.  Thanks for the info though.  Any simpler solutions would be welcomed.

Shane

---

### Post by TideMan on 2009-03-29
> **nothingspecial said:**
> 

Have a good look at ssh [ssh]("https://help.ubuntu.com/community/SSHHowto"). That`s the best tool to get you started.

Thanks nothingspecial.  This is very good advice.
I just tried it and by following the instructions in the link, I can now log into my Ubuntu machine either from my Xubuntu machine or my Win XP machine (using putty).  It was very straightforward.

The only strange thing is that on Xubuntu, it works using the IP address, but it will not log on using joe@computer.  It says it cannot resolve the hostname.  Win XP works with either IP address or joe@computer.

---

### Post by shane2peru on 2009-03-29
> **TideMan said:**
> Thanks nothingspecial.  This is very good advice.
I just tried it and by following the instructions in the link, I can now log into my Ubuntu machine either from my Xubuntu machine or my Win XP machine (using putty).  It was very straightforward.

The only strange thing is that on Xubuntu, it works using the IP address, but it will not log on using joe@computer.  It says it cannot resolve the hostname.  Win XP works with either IP address or joe@computer.

Yes, I have used ssh quite a bit and am fond of it for updating/maintaining the other boxes in the network, however I want an easy graphical server so that they(misc non-tech users) can access the files in a very easy format once it is setup.  Sharing files would be very easy, but yet outside my network would not be allowed in.  More ideas are always appreciated!

Shane

---

### Post by MrWES on 2009-03-29
> **TideMan said:**
> Thanks nothingspecial.  This is very good advice.
I just tried it and by following the instructions in the link, I can now log into my Ubuntu machine either from my Xubuntu machine or my Win XP machine (using putty).  It was very straightforward.

The only strange thing is that on Xubuntu, it works using the IP address, but it will not log on using joe@computer.  It says it cannot resolve the hostname.  Win XP works with either IP address or joe@computer.


Add the IP to /etc/hosts

```
192.168.1.101	ubuntu

```

Edit to fit your needs.

Bill

---

### Post by TideMan on 2009-03-29
> **MrWES said:**
> Add the IP to /etc/hosts

```
192.168.1.101	ubuntu

```



Yes, that fixed it, thank you.

---

### Post by cosine352 on 2009-04-04
ssh is really great. I am now using [this]("https://help.ubuntu.com/community/FreeNX") and it makes my life so easy. Now I can do work in my 'work computer' from my home securely.

---

