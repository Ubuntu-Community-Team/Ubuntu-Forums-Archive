---
title: "Simple networking and remote access"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by 50words on 2008-04-22
Two questions:

1. I am trying to network two Ubuntu computers. They are hard-wired to the same router. I can ping either computer from the other (they are static IPs 192.168.0.40 and .50), but when I use shares-admin to share a folder (say, the "~/Audio folder), I cannot see the shared folder from the other computer.

I am trying Samba, as I have been told it is easier. Any ideas?

2. I want to set up remote access to one of the computers (.50). The other is a laptop. I want to be able to share and sync files from home to the desktop in my office. My router is behind a another router. I have forwarded a port (I randomly selected 8181) from the Qwest Actiontec router to my Netgear router, but I cannot get in using remote desktop access. Assuming I configured all the IP addresses right, can anyone guess what the problem might be?

---

### Post by SpaceTeddy on 2008-04-23
> **50words said:**
> Two questions:

1. I am trying to network two Ubuntu computers. They are hard-wired to the same router. I can ping either computer from the other (they are static IPs 192.168.0.40 and .50), but when I use shares-admin to share a folder (say, the "~/Audio folder), I cannot see the shared folder from the other computer.
I am trying Samba, as I have been told it is easier. Any ideas?

Yes!
i find the easiest way of getting ubuntu computers to "talk" to each other is ssh. Install the openssh-server on both computers with this command
```
sudo apt-get install openssh-server
```
after that, open a nautilus (filebrowser) windows on one of them and simply go ssh://IP in the address bar. That should give you a warning about an unknown host (will only come up once) - then enter the username and password as you would on the other machine and your in. Works on any computer that runs the ssh-server.
Sidenote: i don't like samba... 

> **50words said:**
> 


2. I want to set up remote access to one of the computers (.50). The other is a laptop. I want to be able to share and sync files from home to the desktop in my office. My router is behind a another router. I have forwarded a port (I randomly selected 8181) from the Qwest Actiontec router to my Netgear router, but I cannot get in using remote desktop access. Assuming I configured all the IP addresses right, can anyone guess what the problem might be?

mhm... you are sure that the pakets acctually reach your internal host ? also, i would start of with a simple test (guess what - use ssh :) ) to make sure basic connectivity is given and take it from there. BTW, file sync and vnc/rdp can be tunneled over ssh... just an idea. But as for setting up vnc/RDP i am the wrong person - i only know networks.

can you describe the setup in a little more detailed, including the internal ips and your set forwarding on the routers ?

hope we can figure this :)

---

### Post by randlieb on 2008-05-13
> **SpaceTeddy said:**
> Yes!
i find the easiest way of getting ubuntu computers to "talk" to each other is ssh. Install the openssh-server on both computers with this command
```
sudo apt-get install openssh-server
```
after that, open a nautilus (filebrowser) windows on one of them and simply go ssh://IP in the address bar. That should give you a warning about an unknown host (will only come up once) - then enter the username and password as you would on the other machine and your in. Works on any computer that runs the ssh-server.
Sidenote: i don't like samba... 

I want to set up a shared network between 2 ubuntu machines also. Am using a Linksys router and the internet connection is working for both machines.

Did what you suggested to get them to 'talk' to each other and got this window. Same from both computers.

[B]"Couldn't display "sftp://ip/", because the host could be found.

Check that the spelling is correct and that your proxy settings are correct."[/B]

I thought seting up a home network on Ubuntu was supposed to be a no brainer, even for none geeks. I have yet to find a "do this - do this - do this - done!' HOW TO.

---

### Post by Iowan on 2008-05-13
@randlieb:
You are using the actual IP address of the machine - not literally **ssh://IP**?

---

### Post by randlieb on 2008-05-13
Well almost....

I was using the Cox.net ip address. I went into the "Network Settings" window and found the localhost ip address, typed that into the nautilus address bar and clicked. I got a window that asked for my username and password (yeah!), but when I typed in the other computer's name/pw it just popped up the same window again. If I typed in the name/pw for the computer I'm on it went to my root folder.

Does it matter that I have my Home and Root in separate partitions on this computer but not my second one?

My Network configuration is set up as DHCP on both machines.

---

### Post by randlieb on 2008-05-14
This is what I have set up:

Hardware
My cable plugged into my Linksys cable modem.
The cable modem plugged into my Linksys router with 4 port switch.
One ethernet cable going from the router to each of  2 home computers.

Internet connection is working on both computers.

Software
openssh server and client installed on each computer.
the wired connection is configured for dhcp on both machines.

Using the ip address:
Do I use the localhost address, the address for the name of my computer (which I set up upon installation of Ubuntu), or the adress I get from my service provider Cox cable (none seem to work!)?

What am I missing?

---

### Post by 50words on 2008-05-14
localhost is 127.0.0.1 for every computer. It means the computer that you are working on, and will not go to another computer.

If you want to know your IP address, open a terminal and type [code]ifconfig[code]. Under your connection to the local LAN--assuming you are using a router--(wlan0, in my case), it will give you a "inet addr," which is your computer's local IP address.

If you are not using a router, you can also use ifconfig, or else just go to whatismyip.com to figure out where you are.

---

### Post by 50words on 2008-05-14
I will try ssh today. I was without a second computer for a while, so I did not have an opportunity to play with networking.

In the long run, however, it does not sound like ssh is as convenient for sharing folders, which is what I need to do. I will have three staff (which includes me) who will need to access the same files on a server, both locally and remotely.

---

### Post by mapes12 on 2008-05-14
I am trying to configure my 2 Ubuntu boxes the same as you guys. I hadn't heard of OpenSSH until I read this thread. There is a Ubuntu Document that covers it in more detail here:

[https://help.ubuntu.com/7.10/server/C/openssh-server.html](https://help.ubuntu.com/7.10/server/C/openssh-server.html)

I'm new to Linux and thought (incorrectly as it appears) that a simple Workgroup (as in up to 10 clent machines in Windows) would be easy to configure. It isn't  :(

From what I have read I need to set one box up as a server and then place the files to be shared just on that machine. That's not ideal for what I need.

---

### Post by 50words on 2008-05-14
OpenSSH worked like a charm on the local network! Hopefully rsync is as easy to configure.

We are getting a new internet connection this afternoon, and I will make sure to forward a port so I can try accessing remotely.

---

### Post by Iowan on 2008-05-14
> **mapes12 said:**
> From what I have read I need to set one box up as a server and then place the files to be shared just on that machine. That's not ideal for what I need.It's possible to setup a pseudo peer-to-peer Samba network - it just involves setting up each machine as a server via  **/etc/samba/smb.conf**.

---

### Post by randlieb on 2008-05-14
I started a fresh thread here [http://ubuntuforums.org/showthread.php?t=793308&goto=newpost](http://ubuntuforums.org/showthread.php?t=793308&goto=newpost) and got a great how to for setting up a simple network with just Ubuntu on my computers using openssh server.

---

### Post by hardtofindausername on 2010-09-10
I know this post is from 2008, but I would just like to indicate (or, perhaps, remind [sorry if this has already been written in another forum thread]) that autofs can also be used together with NFS.  The Ubuntu documentation explains how to use autofs.  The URL to the help page is:

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

For Linux-Linux folder-shares, this is perhaps a simple or simplified (meaning: not too much work or configuration) way to access folders from one computer to the other in the same local network.

---

