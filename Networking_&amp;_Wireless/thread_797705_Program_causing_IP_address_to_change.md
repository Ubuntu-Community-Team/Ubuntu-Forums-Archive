---
title: "Program causing IP address to change"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by nytefall on 2008-05-17
Hello, I was redirected to this forum for an issue I am currently having. When I run online gaming programs, after about a minute or so my IP address changes on me - disconnecting me from the game needless to say. It is not the particular program itself, it is not wine or the custom Linux launcher, and according to my ISP it is not them doing it so I can only guess it is something my OS is doing. Has anyone else had similar problems or know how I can go about not allowing my computer to change my IP address without my permission? It isn't only affecting my computer - it is affecting anyone hooked up to the router and the problem persists even if I disconnect the router. If someone could just tell me how I can go about locking my IP address into place I would be much appreciative.

---

### Post by Monicker on 2008-05-17
I have never experienced an issue like that running linux.  It sounds more likely that it could be something to do with the router itself.  You are using dhcp to get an ip address from the router?  I wonder if the router might be giving an extremely short dhcp lease time, which is what tells the client how long it is allowed to keep the ip address.  Usually when the lease is 50% over, iirc, the client will request a new ip address from the dhcp server.  

One option, supported by most home routers, is to use a dhcp reservation.  You would enter the mac address of the client into the router and associate it with a particular ip address.  The client still uses dhcp but the router always assign it the same ip address because of the reservation.  Dig around in your router's configuration options; the exact methods to do it will vary by vendor and model.

---

### Post by nytefall on 2008-05-17
I do not believe the problem has anything to do with my router. I tried using  the program with and without the router hooked up and the result was the same - played for about a minute or two and then changed my IP address.

---

### Post by Monicker on 2008-05-17
*shrug*  You won't get anywhere if you don't narrow down the possibilities.  The only thing at the os level which would do that is something telling it needs to get a new ip address.  DHCP uses a lease time to control how long a lease should be kept.  How are you testing without the router?  Once a dhcp address has been given, the client will still pay attention to the lease information that it was originally given.

Perhaps you could give more details about your setup.  What other machines are on the network, and what operating system are they?  You said it affected anyone who had connected via the router.  What does that mean exactly?

What program are you talking about which caused you to title this thread as you did?

The router is still the most likely cause of the problem, based on the limited information you have given so far.


EDIT: From a forum search, it seems that the program is LOTRO, and you are using some type of shell script to launch the application.

I would suggest trying to get some information about what is happening on the network when this program is running.

If it were me, I would start a tcpdump capture before launching the game, and then stop the capture after the ip address change occurs.  Then I would examine the dump file for anything which might show why machine would have changed its ip address.

```
sudo tcpdump -w lotro.cap
```

Use CTRL + C to stop the capture.  You could attach the lotro.cap file here.  That should give some indication of what might be going on in your situation.

---

### Post by nytefall on 2008-05-17
> **Monicker said:**
> *shrug*  You won't get anywhere if you don't narrow down the possibilities.  The only thing at the os level which would do that is something telling it needs to get a new ip address.  DHCP uses a lease time to control how long a lease should be kept.  How are you testing without the router?  Once a dhcp address has been given, the client will still pay attention to the lease information that it was originally given.

Perhaps you could give more details about your setup.  What other machines are on the network, and what operating system are they?  You said it affected anyone who had connected via the router.  What does that mean exactly?

What program are you talking about which caused you to title this thread as you did?

The router is still the most likely cause of the problem, based on the limited information you have given so far.

When I say I tested it without the router, I meant that I unpluged the router and modem, plugged only the modem back in, restarted my system, and attempted to use the program again. The result of this test was the same as my normal configuration.

Two machines use the network, mine that has Kubuntu and my room mate who has Vista. When I said it affected anyone that was connected to the router, I meant that everyone connected to the router for internet was being inconvenienced.

The program I am talking about is Lord of the Rings Online - I am running it via wine atm, but I do not believe it is the cause of this (the people that developed the .script to allow it to be ran on wine told me it wasn't).

I apologize for not being an easy person to help with this but I know very little about routers (for all I know they work by magic >.>) and while I am relatively computer literate I just switched to Kubuntu from XP about 2 days ago.

---

### Post by Monicker on 2008-05-17
Np.  Its an interesting issue, and it intrigues me.  Please see the edit to my earlier post.

Does the problem only occur when running this particular application?  Does it ever happen when you are not using LOTRO?

---

### Post by nytefall on 2008-05-17
Yes I am using a shell script to launch lotro. I don't exactly know what this tcdump is, I entered the line you gave me into the terminal but either I don't have the program installed on my system or I am completely wrong in my understanding of what it is. The error does only occur when I run the program but since it is the only program I have of its nature, I can't be sure it wouldn't happen with another program that was similar.

---

### Post by Monicker on 2008-05-17
Hrmm. It may not be installed by default.  One thing I just realized - I have no idea how that application handles authentication, so it may not even be a good idea to post a capture to these forums.  There is a chance your username/password are passed in cleartext.

Outside of actually looking at the network traffic, I don't see a good way for you to determine why this is happening.  It could be some kind of strange interaction with wine, the application, and the OS.  Debugging information at the application level is beyond me.

---

### Post by nytefall on 2008-05-17
Is there no way to simply prevent any program from changing my ip address? Is it possible to just put a lock on it or something?

---

### Post by Monicker on 2008-05-17
You can set a static ip address.  You should be able to do that via the Network Manager.  You will need to set the ip address, subnet mask, gateway, and dns servers to use.

ifconfig will give you what ip and subnet mask you are currently using.  netstat -rn will show you what the gateway is - denoted by UG in the flags columns.

/etc/resolv.conf will show your current dns servers.

EDIT: You can also do some manual editing at the console.  [http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html")

---

### Post by netztier on 2008-05-17
> **nytefall said:**
> Is there no way to simply prevent any program from changing my ip address? Is it possible to just put a lock on it or something?

A program that does not run with root priviledges has no means of changing an IP address - if it wanted to, it would have to call the ifconfig routine with sudo or from a root shell. 

Does Wine (in which you are running this game) run with sudo in your case? If at all possible, try to reconfigure Wine and/or the game software not to require root priviledges.

I suspect a DHCP problem here - which might always be there, but you might not notice it as long as you are only surfing the web or receiving/sending out emails. On the command line (aka terminal window), right after you notice the changing of the IP address, lookt at the output of the following command and post it's output here:

**cat /var/log/syslog | grep DHCP**

[COLOR="Gray"](this command displays the content of the file /var/log/syslog, but only shows lines that contain the string "DHCP".)
[/COLOR]


regards

Marc

---

