---
title: "Need help with remote desktop solutions"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by gyzer on 2008-05-27
I am wanting to know the differences in usability for all the different remote desktop solutions there are for a linux system.

The ones I know of are ssh, vnc, and nx.

I have tried using freenx server, and I kind of got it working then it stopped after awhile. I kept getting error messages that the server had timed out.

My setup is this. I've got an Ubuntu 8.04 desktop which I want to be the host server. I've got a laptop that I want to be the client. They are both on my wireless network at home.

All I'm wanting to be able to do is view my desktop's desktop on my laptop. The laptop is running Xubuntu 8.04 with IceWM. 

Obviously I am new to this so something that is also the simplest to configure would be the best option.

---

### Post by gyzer on 2008-05-28
Also what are the disadvantages to each one of the different solutions?

---

### Post by RottenBananas on 2008-05-28
Hey,
Check out these links (2 methods)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) -- the forwarding X section(after you have regular ssh setup and working)

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

I use the method in the first link
hitting CTRL+ALT+F1 and typing
```
xinit -e ssh -XCT yourusername@your.host gnome-session -- :1
```
its pretty slow though over the internet...but more secure than just vnc

If you wanna go through just your LAN it'll be much quicker

Hope this helps

---

### Post by gyzer on 2008-05-28
>  
If you wanna go through just your LAN it'll be much quicker
 

 
Do you mean using the way described in the first link or just doing VNC?

---

### Post by RottenBananas on 2008-05-28
I mean if you connect through your LAN(local area network)

If your laptop is on ur home network with your desktop it'll be quick

Say you go to australia and wanna connect to ur home computer in the U.S youd have to go through the internet which makes it slower...but not unbearable.

Im a newbie to the remote desktop stuff myself, so far I like the forwarding X method better, with vnc you have to be running a vncserver on the desktop and be logged in(i think). Forwarding X you dont need to log in on the desktop, as long as its on you're good

---

### Post by gyzer on 2008-05-28
So then this in effect "sharing" the desktop session, so that any programs that I brought up on the desktop at the comp will show up when I remote in with the laptop, right?
 
Yes I'm primarily using the laptop over my LAN.
 
So this same method can be used over the internet? Is it pretty secure? How would you do this over the internet with dealing with your router/firewall?

---

### Post by RottenBananas on 2008-05-28
> **gyzer said:**
> So then this in effect "sharing" the desktop session, so that any programs that I brought up on the desktop at the comp will show up when I remote in with the laptop, right?
 
Yes I'm primarily using the laptop over my LAN.
 
So this same method can be used over the internet? Is it pretty secure? How would you do this over the internet with dealing with your router/firewall?

Haha thats the thing, I actually made a thread in the forums with that problem. I can connect and everything but i cant control...so i see my desktop...can access all the files on it, but if i open up firefox on the desktop it wont show on the laptop when im connected. Still hoping someone will help me with that eventually

Im fairly certain ssh is one of the best ways to go in terms of security. You can even setup rsa/dsa keys

Yep that method works over the internet. You need to forward the right ports(22 for ssh and maybe one more??) on your router. I went over to dyndns.org and setup a network name to match my dynamic ip. so instead of bananas@111.111.23.4 i use [email]bananas@mynetworkname.net[/email]

Try gettin just ssh to work so you can get a commandline to your desktop
and then you can run that command to see the desktop

---

### Post by gyzer on 2008-05-28
Yeah I will try that. It seems alot more straight forward then using nx. I might eventually do VNC through SSH tunneling if I think ssh is too slow with forwarding the entire desktop. 
 
So as of right now with using ssh and forwarding the entire desktop you are having the same problem that I was having with nx? 
 
If firefox was opened on the desktop, I couldn't open it up on the laptop, if it was opened via the laptop, it wouldn't work on the desktop. Strangly though when pidgen was minimized to the task bar, it would show up on both with some minor problems. 
 
> xinit -e ssh -XCT [email]yourusername@your.host[/email] gnome-session -- :1
 
So that command is used on the console for the client or the console of the host computer?

---

### Post by RottenBananas on 2008-05-28
> **gyzer said:**
>  
If firefox was opened on the desktop, I couldn't open it up on the laptop, if it was opened via the laptop, it wouldn't work on the desktop. Strangly though when pidgen was minimized to the task bar, it would show up on both with some minor problems. 


I dont think that was my problem. Everything worked on both normally, just the laptop couldnt control the desktop. Meaning if i move the mouse on my laptop when im connected you cant see it move on the desktop.

Yeah that command looks good to me, you need to switch to console with ctrl alt f1 on the client computer and put it in

Use ctrl alt f7 to switch back

---

### Post by gyzer on 2008-05-29
Alright I can get ssh to work perfectly, but I cannot get the x session forwarding of the gnome-session to work. I get this error message:

Waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/x11/misc"
refcount is 2, should be 1; fixing

and it doesn't get any further then that. I did make sure to turn on x session forwarding and I restarted the ssh-server after that so that shouldn't be a problem. 

Any help I can get would be appreciated.

Thanks

---

### Post by gyzer on 2008-05-29
I was able to forward firefox over and that worked just fine.

---

### Post by RottenBananas on 2008-05-30
Whats the command ur trying to use look like? using -XCT options??

---

### Post by gyzer on 2008-05-30
I'm issuing that command you told me to.

```
xinit -e ssh -XCT [EMAIL="yourusername@your.host"]yourusername@your.host[/EMAIL] gnome-session -- :1
```I did some searching for this problem and found alot of refrences to the xorg.conf file and refrences in it to fonts. Neither of my host or client computers have any font refrences in their xorg.conf file.

Also the directory that is refrenced in the error message "/usr/share/fonts/x11/misc" does not exsist on either of the computers either.

---

### Post by gyzer on 2008-05-30
I just tried taking off options -C and -K and it still produced the same error.

---

### Post by RottenBananas on 2008-05-30
Try this
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

Add those lines listed to the etc/vnc.conf file

---

### Post by gyzer on 2008-05-30
Would that even do anything seeing as I'm not using vnc right now? 
 
I probably will switch over to using VNCOverSSH.
 
Is there some other similar file for ssh that might need to be altered like this one?

---

### Post by RottenBananas on 2008-05-30
Yeah I dunno if thatll fix anything i forgot we're workin with ssh.

The ssh server config file is /etc/ssh/sshd_config

---

### Post by fhmanas on 2008-06-05
Your original FreeNX setup seems to me the faster amongst the solution, I've tried VNC, and definitely it is much slower than NX.  I have also used XDMCP or the X route, and still I found it slow.  The NX solution was the best I've had over the internet.  For added security, I decided not to do port forwarding as it opens my network to the internet, instead I installed hamachi and I use the private hamachi network I created to connect to the system, worked great for me, SSH on hamachi VPN and NX for fast response time.

BTW, if you are having trouble with FreeNX, you can use NoMachine's NX Server free, I believe this would be more stable, although it will only allow 2 sessions at a time.

---

### Post by linux6994 on 2008-06-05
Krdc is real easy and works fine.

---

### Post by gyzer on 2008-06-05
The problem I had with NX was that it was completly unreliable and that I wasn't able to see the current session on the desktop. I know I was logged into the current session, but if a web browser window was open up on the desktop where the nx server was, the nx client couldn't see that web browser window, but if I tried to open up firefox with it open on the nx server, it will give me an error message saying that it is already open.
 
I've had some good sucess with ssh, and I've only run into a few minor problems with VNC. Sadly though I haven't had the time to work out those VNC problems yet.

---

