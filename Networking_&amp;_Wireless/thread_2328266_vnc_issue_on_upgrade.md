---
title: "vnc issue on upgrade"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2016-06-19
since I upgraded to ubuntu 16.04 I can only connect via vnc once then I need to reboot the remote computer to connect again. There was a fix for this before but I can find it anywhere. I tried a few things but nothing works. To be clear I need to repeatably connect to the current users vnc desktop to do remote support. I am connecting through a LAN so security beyond the vnc password is not an issue. Thank you.

---

### Post by steeldriver on 2016-06-19
What VNC server are you using, and how are you starting it? after the first client exits, does the server quit? or does it stay running but refuse connections?

---

### Post by cmcanulty on 2016-06-19
I have tightvncserver and x11vnc I can always connect to either user with rdp. vnc I can connect once then have to reboot to connect to it again. Remmina gives error "failed to connect to server" How would I make the server keep running after I exit the vnc once? System monitor shows x11vnc and vino-server still running. I need to login to the actual live desktop several times a day for support.
So I edited the .x11vncrc to look like this and now I can't vnc even with a reboot but can still rdp OK. I did save the original.x11vncrc file though it wasn't working

```
display :0
shared
forever
localhost
rfbauth /home/user/.vnc/passwd
```

---

### Post by steeldriver on 2016-06-19
tightvncserver **and **x11vnc **and **vino-server? VNC **and** RDP? sorry - I have no experience with such a setup

---

### Post by cmcanulty on 2016-06-19
I use rdp to access the systems silently and vnc to do live support. Should I get rid of all the vnc except one? If so which one? It all worked fine with the same pkgs before the upgrade to 16.04.

---

### Post by steeldriver on 2016-06-19
Well I guess it's OK to have all of them - as long as you're clear which you are connecting to with each client, which port(s) each one is listening on, how each one is configured etc.

---

### Post by cmcanulty on 2016-06-19
I think this is a better explanation of the issue. From win 7 I can reach all machines with rdp or vnc any time. From ubuntu I can only reach vnc the first time, then a reboot is needed to reach it by vnc again. I can always reach by rdp.I have tried commands to list all services but they don't work in 16.04

---

### Post by steeldriver on 2016-06-19
I don't have access to a 16.04 system, but I would think netstat and/or lsof would allow you to see the listening ports (regardless of whether the servers are running as 'services' or not)

```

sudo netstat -nltup | grep LISTEN

```

```

sudo lsof -i :5900,3389

```

etc.

---

### Post by cmcanulty on 2016-06-20
OK here is another piece of the puzzle. If I go to the librarian account via rdp and type in terminal

```
sudo x11vnc start
```

then I can again connect via vnc _once_ without a reboot. So the issue is make x11vnc keep running after one connect and disconnect. It is in my startup apps but it needs some command to keep it always running.It may also be relevant that I only connect to the non sudo user  via vnc. The weird thing is one machine allows me to connect multiple times  via vnc but I can't find any difference in the apps installed or the setup as I always try to keep all the public machines with identical setups. I also uncommented the -forever option in .x11vncrc but that had no effect. Now I tried removing all vnc servers completely and reinstalled x11vnc. Then I did the
```
x11vnx  -storepasswd and -forever 
```
in terminal and rebooted but get the same behavior. It connect once then won't connect again until I reboot the server.

---

### Post by cmcanulty on 2016-06-21
OK so it is definitely an issue of x11vnc not keeping running after one connect. When I go into a terminal on the remote machine and type x11vnc then I can again connect one time via vnc. I also thought I had x11vnc configured to keep running by running this command, but apparently something is wrong with the command as it only allows one connection.

```
x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/USERNAME/.vnc/passwd -rfbport 5900 -shared 
```

also I enter a

```
 x11vnc -storepasswd
```

 command and verify it yet always get an error that I am running x11vnc with out a password. And I found out vnc4server is a requirement for x11vnc and that is why I have both installed.

---

### Post by cmcanulty on 2016-06-21
OK I finally after a week of trying got the x11vnc to reconnect without a reboot and had to set up a .x11vncrc file which I never found in the manuals. That was why the -forever option wasn't saved, without a .x11vncrc file for every user x11vnc never saved any options. I got this info from this web page.

[http://anonymouse-journey.blogspot.com/2010/02/configure-x11vncrc.html]("http://anonymouse-journey.blogspot.com/2010/02/configure-x11vncrc.html")

---

