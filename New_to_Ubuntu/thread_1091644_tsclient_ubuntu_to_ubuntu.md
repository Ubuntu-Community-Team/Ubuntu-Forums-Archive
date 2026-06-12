---
title: "tsclient ubuntu to ubuntu"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by rhconcepts on 2009-03-09
I just got done setting up my server with ubuntu. Now I have another pc with ubuntu and xp and would like to remote connect to the server. The server is in my crawl space so I don't want to keep getting up to try something. Im going to test things out on my pc and if it works then set it up on the server. I would like to use ubuntu to connect to the server. I tried tsclient but don't I need something on the server side to be running? Im very bad with commands but Im learning, so if anyone could point me in the right way that would be great.

---

### Post by Nxion on 2009-03-09
Well you say you setup a server. Did you actually install Ubuntu Server or did you install Ubuntu Desktop and is using it as a server?

Either way, to answer your question yes you have to have a Xserver running on the server to be able to connect to it with tsclient. It isn't like Windows when you can just click an option and then you have remote access via a GUI. there is a little bit to get it setup. Most of the time the command line is used to administer the machine. SSH is most commonly used to accomplish this. 

In fact you can even open a remote desktop connection with SSH. The reason for this is because then you are tunneling remote desktop overs ssh and therefore all the traffic is encrypted. If you went bout it the normal way and didn't use SSH, then the connection is NOT encrypted.

---

### Post by rhconcepts on 2009-03-09
Ok im going to start over. I installed the desktop not server. Now after I get it back up could I then connect to the server using tsclient?

I found this [http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html) and it looks easy to setup. Is that what I should do.

---

### Post by Nxion on 2009-03-09
There are other ways to do what you are asking but I believe in your case, follow that guide. It is a good one. That should be fine for what you want to do.

---

### Post by mlentink on 2009-03-09
Are you sure you installed Ubuntu Desktop? If so: go to System>Preferences>Remote Desktop
enable this, it will start up a VNC server on your 'server'. This you can access with ts, using the VNC option to connect.

Personally, I administer my server with ssh and WebMin... a breeze

Wups. the thread mentioned does just that... with a windows box. In ubuntu you can connect with either Terminal Services Client (be sure to specify VNC as the connection type) or Vinagre (Applications>Internet>Remote Desktops)

---

### Post by rhconcepts on 2009-03-09
> **mlentink said:**
> Are you sure you installed Ubuntu Desktop? If so: go to System>Preferences>Remote Desktop
enable this, it will start up a VNC server on your 'server'. This you can access with ts, using the VNC option to connect.

Personally, I administer my server with ssh and WebMin... a breeze

Wups. the thread mentioned does just that... with a windows box. In ubuntu you can connect with either Terminal Services Client (be sure to specify VNC as the connection type) or Vinagre (Applications>Internet>Remote Desktops)

If I use ts all I can connect with is RDP or RDPv I cant use VNC how do I get that to turn on?

---

### Post by Nxion on 2009-03-10
> **rhconcepts said:**
> If I use ts all I can connect with is RDP or RDPv I cant use VNC how do I get that to turn on?

Just follow that guide you found and it will show you how to enable VNC on your machine.

---

### Post by rhconcepts on 2009-03-11
OK I installed the server version and I dont think I can do it. Does the server version have a graphics side to it or is it all commands? I can do a few thing with the terminal but not much.

---

### Post by mlentink on 2009-03-11
Hmmm.
Well, I administer my server with terminal (ssh) and Webmin. Highly recommended.

If you really insist on a GUI, you can install through:
```
sudo apt-get install ubuntu-desktop
```
or, if you want a more light weight desktop
```
sudo apt-get install xubuntu-desktop
```

Please also see [here]("http://ubuntuforums.org/archive/index.php/t-186298.html") e.g.

Althought running a server from terminal only (or with a management interface like Webmin) may seem daunting at first, after you get the hang of it will work a lot faster. And be more easy on your server's resources.

---

### Post by rhconcepts on 2009-03-13
Im sure I could take it out once I get up and running right? But if I do a remote link to it will I then have a gui interface to it with terminal (ssh) and Webmin. Or is that just terminal no GUI.
I can connect to the ubuntu desktop using vnc/windows pc but no luck from my ubuntu computer.

---

### Post by zeronothing on 2009-03-13
if your using a GUI interface with your install, download and install [[COLOR="Blue"]nomachine[/COLOR]]("http://www.nomachine.com/"). I use nomachine on my ubuntu desktop install. its really simple to install. if you go to their website, you can download the .deb packages. with the .deb packages you can just double click install nomachine. then you just use the client software to access you machine. the client software is available for linux, windows, and mac. also make sure you install openssh server from synaptic because nomachine uses ssh protocol to securely connect to your machine.

---

### Post by danrche on 2009-03-13
rhconcepts


what are you trying to do with your server? If you're not well versed in command line you may want to install the desktop version instead of the sever ver. With your current install you're only going to get a term window with vnc connected, and if this is all you're looking for, use SSH, it's much better and easier. 

If you are not comfortable in command line, you can use the desktop, which comes with a GUI, and then install all the server peices you're looking for. They run just as well on the desktop....

If your goal is to become well versed in command line, I recommend you still use the Desktop insatll, and ssh everything you do, until you're tired and angry, then open the vnc connection, see the pretty desktop environment, and within a few clicks your done... :) at least that way you go to bed satisfied. 

So what are your plans for the box in the attic? I run Ubuntu on my desktop at home, and use it as a file serv and have installed the child time games for my kids (who love it). My work runs a linux vm solution as well that's pretty cool too. I also use Fedora on my thinkpad and have had a lot of success with that as well as a work PC.

---

### Post by rhconcepts on 2009-03-15
Thanks for the help guys. 
I have 3 web sites running on apache. I would like to get my ftp up and going now. ftp will only be for working on the pages. I will make the page with web page maker and that has a one click upload using ftp. so each site needs it own file and its own login. I started a post for help with the ftp but no luck. right now I have the desktop ubuntu running and may stay with that. I need to find out more info on the ssh I have no clue what that is.

---

### Post by MrWES on 2009-03-15
ssh is the way to go. I just installed 8.04 server for a file and print server -- also with transmission daemon running. I simply use ssh to connect and maintain my server. IMHO, using ssh forces you to learn command line and you'll be very thankful down the road. If you decide to forward port 22 for ssh from the outside world, I'd recommend you install Denyhosts for some added security. 

Bill

---

