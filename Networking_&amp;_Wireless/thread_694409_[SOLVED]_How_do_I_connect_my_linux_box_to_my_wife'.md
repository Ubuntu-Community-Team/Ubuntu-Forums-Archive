---
title: "[SOLVED] How do I connect my linux box to my wife's linux box?"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by BobLand on 2008-02-12
I have an ubuntu only box that I can connect to my wife's dual boot - (xp & gutsy).  I can get to xp in a variety ways but so far cannot see the ubuntu box.  All systems work as expected on their respective computers.

I've shared the linux folders using nfs and specified my computer name.  Can't see either box either way.
We're wired through a lynksys router connected to a cable modem.  We both can get to the internet with no problems.  No wireless in use at this time.

I've got some old pentium boxes I'd like to install ubuntu on and connect them as well so all advise is appreciated.

Suggestions?

bobland

---

### Post by Ek0nomik on 2008-02-12
> **BobLand said:**
> I have an ubuntu only box that I can connect to my wife's dual boot - (xp & gutsy).  I can get to xp in a variety ways but so far cannot see the ubuntu box.  All systems work as expected on their respective computers.

I've shared the linux folders using nfs and specified my computer name.  Can't see either box either way.
We're wired through a lynksys router connected to a cable modem.  We both can get to the internet with no problems.  No wireless in use at this time.

I've got some old pentium boxes I'd like to install ubuntu on and connect them as well so all advise is appreciated.

Suggestions?

bobland

SSH.  You can use SSH in multiple fashions, *and* it's encrypted.

You can install by doing the following:

```
sudo apt-get install openssh-server
```

You can login by doing the following:

```
ssh wife@her.local.ip
```

Now you are able to access the computer via the terminal and can copy files, update your computer, etc.

You can also run programs installed *only* on *your* computer by using the -X flag while logging in via SSH.  This is a really cool way of controlling things graphically without having to use VNC.  As an example, I sometimes I run Exaile (a music program) on the computer next to me, even though it isn't installed on that computer.  Exaile is only installed on this machine, but I can run Exaile from this machine on any other computer I wish, and it acts as if I were running it locally.

Now, what I think will be exactly what you originally have in mind, you can also access SSH graphically to transfer files between one another.  Open your file browser (nautilus) and go to File/Connect to server.  Select SSH, put in the IP, the port (default is 22, but you can change it in /etc/ssh/sshd_config) and the directory you wish to visit (/home/wife)).  If you want to transfer files graphically in Windows you can use WinSCP which is a great piece of software.

If you have any more questions, feel free to ask.

---

### Post by BobLand on 2008-02-12
Gave this a try and got the following error
```
ssh: connect to host <ip> port 22: Connection refused
```
Do I need to do something on her side?


bobland

---

### Post by Ek0nomik on 2008-02-12
> **BobLand said:**
> Gave this a try and got the following error
```
ssh: connect to host <ip> port 22: Connection refused
```
Do I need to do something on her side?


bobland

You are using a Linksys router which means you probably have a firewall built in and it's blocking it.

I presume you know how to open ports on the firewall?  The steps following something like this:

1.  Type 192.168.1.1 into your web browser of choice.
2.  Enter your password (admin by default)
3.  Look for a tab called 'Port Forwarding' or something of the like.
4.  Make sure you know the internal IP (ifconfig in the terminal) of the computer you are trying to connect to so you can open the port on that computer.

Feel free to ask more questions... I'll check back after my lectures are done for the day.

---

### Post by bernied on 2008-02-12
> **BobLand said:**
> Gave this a try and got the following error
```
ssh: connect to host <ip> port 22: Connection refused
```
Do I need to do something on her side?

boblandYou need the openssh-server package installed and running on the machine that you are ssh-ing to.

For ease of use you probably want to have fixed IP addresses on all machines that you want to have easy access to, configure this in /etc/interfaces (or there is a GUI in a control panel somewhere - look for 'network'). You might also want the IP addresses translated to machine names, the file for this is /etc/hosts, but again there is a GUI somewhere, probably the same one you used to configure your IP address.

You might also want to investigate samba for file sharing. Samba shares look like windows shares and can be easier to use than nfs.

In my experience, most router firewalls don't block traffic inside their own LAN, generally they only block incoming (from the internet) traffic.

---

### Post by Ek0nomik on 2008-02-12
> **bernied said:**
> You need the openssh-server package installed and running on the machine that you are ssh-ing to.

For ease of use you probably want to have fixed IP addresses on all machines that you want to have easy access to, configure this in /etc/interfaces (or there is a GUI in a control panel somewhere - look for 'network'). You might also want the IP addresses translated to machine names, the file for this is /etc/hosts, but again there is a GUI somewhere, probably the same one you used to configure your IP address.

You might also want to investigate samba for file sharing. Samba shares look like windows shares and can be easier to use than nfs.

In my experience, most router firewalls don't block traffic inside their own LAN, generally they only block incoming (from the internet) traffic.

Since he wants to go between both computers I presume installing openssh-server on both computers would be beneficial.  Anyways, my Linksys router back home would always block LAN-LAN traffic.

---

### Post by BobLand on 2008-02-12
On the router, I tried user admin with all my "common" passwords.  Then I tried all the user names with same passwords.  None worked so I guess that's out unless there is a way to physically reset the router.  

No idea where the manual is.  I'll give their site a look.

I'll try installing the openssh server on the other box and let you know what happens.

I appreciate these responses.
Thanks guys,
bobland

---

### Post by BobLand on 2008-02-12
After installing openssh-server on the other computer I was able to connect to it.

I tried scp thisfile [email]user@local.ip[/email]
Didn't get an error but didn't get the file either.  Tried it both ways to no avail.

At the moment, this has some urgency as I need to get files from my linux box to her new linux box.  Once that is done I'd like to explore other possiblites of using ssh as I now have 2 "junk" boxes to play with.  I'd like to set one up as a backup server with the other to use to play with distros.

Your help is greatly appreciated!
bobland

---

### Post by jabeez on 2008-02-12
I have used Samba to share from Linux>Linux, although it isn't as easy as Linux>Windows or vice-versa. It still isn't too hard, search the forums for Samba sharing and you should be up and running in no time. I've tried NFS, as that's supposedly easier for Linux>Linux, but never managed to get it working (although I didn't really try much). I've never understood why Linux>Linux is so much more difficult than Linux>Windows.....

---

### Post by BobLand on 2008-02-12
Finally am able to copy files from mine to hers.  Had to set the authentication keys up.  

What's a good reference for the various things I can do, such as having a graphical interface and the like?

bobland

---

### Post by BobLand on 2008-02-12
OK!  Got it all figured out.  I had bad syntax when copying both files and directories.  Now I have everything copied to her computer.

Thanks for all the help!!!!!
bobland

---

### Post by Ek0nomik on 2008-02-12
> **BobLand said:**
> OK!  Got it all figured out.  I had bad syntax when copying both files and directories.  Now I have everything copied to her computer.

Thanks for all the help!!!!!
bobland

Do you still have questions about what you can do with SSH?  Remember, you can transfer files graphically or through the terminal.  You can also run software from a computer that has SSH on any other computer in the world.  It just needs an X environment (so, any linux box can run the software fine, and you can get "X emulators" for Windows)

---

### Post by BobLand on 2008-02-13
Well, now that you mention it, how would I view a machine graphically that has X on it?

bobland

---

### Post by rahul_bhise on 2008-02-13
> **BobLand said:**
> On the router, I tried user admin with all my "common" passwords.  Then I tried all the user names with same passwords.  None worked so I guess that's out unless there is a way to physically reset the router.  

try user name=admin  password=admin

---

### Post by Ek0nomik on 2008-02-14
> **rahul_bhise said:**
> try user name=admin  password=admin

By default you leave the user name blank and just type admin in for the password.  This works on nearly all routers, including Linksys and some European ones.

> **BobLand said:**
> Well, now that you mention it, how would I view a machine graphically that has X on it?

bobland

So you have SSH working properly on both computers?  Transferring files should be a breeze if you do it graphically.  If you want to use software graphically you can use VNC (unsecure), you can tunnel VNC through SSH (secure), or you can load a program for a session in SSH.

Here is an example of how to do the last one I mentioned, being done from a different computer than your own:

ssh -X [email]BobLand@your.ip.goes.here[/email]

Now try running a program that is installed on your computer, but not on the computer you are currently using.  (You can run a program that is installed on the one you are using, but this just proves the point a bit more).  It should appear on your screen within seconds because you used the -X flag, which allows the X environment to be tunneled over SSH.

There is a lot of information about VNC and VNC through SSH, so you will be able to find plenty on these forums alone.  You may not have to worry about security though, so just a plain unsecure remote desktop could fit your needs.

[http://ubuntuforums.org/showthread.php?t=279069](http://ubuntuforums.org/showthread.php?t=279069)

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by BobLand on 2008-02-14
EkO

That is VERY COOL!!!

I'll bookmark those urls and check it all out.

Many, many thanks to you for making this so easy!  You ought to write a wiki and submit it.

bobland

---

### Post by Ek0nomik on 2008-02-14
> **BobLand said:**
> EkO

That is VERY COOL!!!

I'll bookmark those urls and check it all out.

Many, many thanks to you for making this so easy!  You ought to write a wiki and submit it.

bobland

You're welcome.  If you have any more questions feel free to shoot me a PM.

---

### Post by BobLand on 2008-02-15
What's your take on VNC vs SSH.  I've noticed a few posts that think that VNC is more useful.  What's your opinion in general?

bobland

---

