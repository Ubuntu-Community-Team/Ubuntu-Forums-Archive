---
title: "How to remote desktop?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Cloud Wolf on 2010-01-30
Hey,

I have Ubuntu 9.10 running on my HP Compaq 311c, and I would like to remote desktop to my main desktop, which runs Linux Mint 7 (amongst Ubuntu 8.10, and an unused version of 9.04 as well - I would like to specifically access my Linux Mint desktop for my user on it).

I am connected to my home wireless network, and my main pc is connected to the router via LAN cable.

How would I go about making it so I could remote access the main Pc from my netbook? I know there is a tool in *Applications > Internet > Remote Desktop Viewer* on my netbook.

Gui methods preferred, but I am not averse to using the terminal.

---

### Post by Psumi on 2010-01-30
Is the desktop PC setup to receive Remote connections in the first place? (By default, ubuntu is not (which linux mint is based off of), even though it has the software to do so. Which is a GOOD idea, we don't want attackers having another opportunity.)

---

### Post by Cloud Wolf on 2010-01-30
I went onto the remote desktop settings and selected to allow viewing and control of the desktop, and set a password. anything else I need to do?

---

### Post by nothingspecial on 2010-01-30
No, just go to remote desktop viewer on your netbook.

What do you want to remote desktop into your pc for. ssh is a lot quicker for most purposes.

---

### Post by Cloud Wolf on 2010-01-30
On the main pc it says I can access it via 'Mint1.local' or '192.168.1.3'.
I go onto the remote desktop viewer and click connect.

It does not matter which one I use ('Mint1.local' or '192.168.1.3') it doesn't connect, just stays as a black screen.

Any help?

---

### Post by nothingspecial on 2010-01-30
Again, I ask, what do you want to do on your remote machine?

I`ve always found vinagre(the remote desktop program) buggy and slow. Hence I don`t use it and don`t have the answer. From what you`ve said you seem to have entered everything correctly.

Like I said you can probably do this better through ssh, if what you want to do is start a program on the remote computer.

The only thing I can think of that vingre would do better would be to view what someone else is doing on that computer.

---

### Post by Cloud Wolf on 2010-01-30
I want to be able to access the files and programs on my main pc, and transfer them to my netbook easily. I don't know what ssh is, but I actually would like to use remote desktop, merely because I know what it is.

Brainwave, is it the firewall on either machine?

---

### Post by nothingspecial on 2010-01-30
> **Cloud Wolf said:**
> 

Brainwave, is it the firewall on either machine?

Could be, are you running a firewall.

If you want to access files on the other machine, this is what I would do. Either search for openssh-server and openssh-client in synaptic and install them on both machines. One or both of them may already be installed, depends on the version of ubuntu and I don`t know about mint, or

```
sudo apt-get install openssh-server openssh-client
```

Then on your netbook, go places > connect to server

in the top box select ssh

in the next box put user@192.168.1.3 (substituting user for your username)

check the add bookmark box

Give desktop a name 

Now anytime you want to access your desktop just click on the name you gave it in your places menu.

You will then have access to the file system and your netbook will treat any file as one of it`s own - so if you click on a movie it will open in totem etc etc.

---

### Post by Cloud Wolf on 2010-01-30
it just says that the connection timed out. it doesn't work :(
Any idea why?

---

### Post by nothingspecial on 2010-01-30
Switch the firewall off on both machines. The one in your router should be fine.

If you must have a firewall on your actual machine, look into firewall rules, just switch them off first, to see weather that is the issue.

Also, from the command line (on the netbook) type```
 ssh user@192.168.1.3
```

Does it let you log in or give an error.

---

### Post by Cloud Wolf on 2010-01-30
How do I switch off the firewall? (tell me how to do it in Ubuntu and I can do it in mint).

Also, the command you gave me to try does not do anything, it just hangs for ages.

---

### Post by nothingspecial on 2010-01-30
Did you install ssh

I took 192.168.1.3 from one of your earlier posts, is this the correct ip address? Check your desktops ip by right clicking on the network icon and choosing connection information. Modify tho command and the settings in connect to server accordingly.

If you haven`t turned the firewall on you don`t need to switch it on.

---

### Post by Cloud Wolf on 2010-01-30
I installed ssh on both, and the IP is 198,162.1.3, the '2' was a typo.

I believe at one point I put a firewall on mint, how would I disable it. (ubuntu fixes work on mint)

---

### Post by nothingspecial on 2010-01-30
If you used the default one
```

sudo ufw disable
```

---

### Post by Cloud Wolf on 2010-01-30
I remember I used firestarter, so i disabled it through that. Now, instead of timing out, it just says the connection was closed. Why?

*Edit:* This is on the remote desktop software, ssh now works fine

---

### Post by quinnten83 on 2010-01-30
on ubuntu install xvnc4viewer
hen in terminal type xvnviewer xxx.xxx.xxx.xxx
which is the IP address you want to connect to.
that is not gonna allow you to share files, as VNC is not like windows RDP.
You can share files using samba.
Right click on the folder you want to share and select sharing option. Select, share this folder and allow ubuntu to install the samba software.
On the other computer, go to places, windows network, the name of the computer and doubleclick, you should see all shared folders.
this is more or less what it is, I am on windows right now, so don't know from the top of my head all the steps you have to take.

---

### Post by Cloud Wolf on 2010-01-30
ignore my last post, it was me being stupid. I forgot to set up remote desktop access to my desktop, as I was using a different user (on Mint).

ssh and remote desktop work perfectly now!

---

### Post by nothingspecial on 2010-01-30
Excellent.

Like I said earlier, I`ve always found shh to be a lot faster than remote desktop.

If you NEED to see the desktop use the remote desktop ...... if you want to access/copy/run  the files use ssh.

If you`re ever interested in the more interesting things ssh can do through the cli, just ask.

---

### Post by pastir on 2010-01-30
Does SSH only work on a network or can I use it over the internet?

---

### Post by nothingspecial on 2010-01-30
You can use it over the internet. This involves having a static ipaddress and extra security.

See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/SSH") and [[COLOR="DeepSkyBlue"]here[/COLOR]]("http://www.dyndns.com/")

Once you`ve set it up, you can start a process running on your remote pc, fly half way round the world then check the progress 10,000 mile away.

---

### Post by tom.swartz07 on 2010-01-30
> **pastir said:**
> Does SSH only work on a network or can I use it over the internet?

Yep!

I ssh to my computer from my iPhone all the time! haha


Just edit your router to 'port forward' port number 22 and 5900 to the ip address of the computer youre looking to ssh into. When you forward port 5900, you could also vnc in also.

---

