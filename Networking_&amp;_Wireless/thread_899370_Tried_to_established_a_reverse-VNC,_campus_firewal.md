---
title: "Tried to established a reverse-VNC, campus firewall blocked it"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-08-24
Someone recently asked me to conduct a remote VNC session with them to help troubleshoot a video problem they were having with their Ubuntu system.  I typically use a reverse VNC connection to do this, where my PC listens for an external request from their PC to connect.  This takes the worry of port-forwarding out of the equation.

Unfortunately, the campus this person is staying at (ENMU to be precise) seems to have some pretty stiff firewall settings.  He was never able to successfully connect to me.  Fortunately, I got all his problems solved blind over the telephone.

What are some ways I could have gotten a connection established; to go around their port restrictions?

---

### Post by SpaceTeddy on 2008-08-24
mhm - i can think of three. but most of the involve running some server on your side that can mask the traffic as something else.

Option 1.) run the vnc on a standard port that is usually used for something else. As most firewalls will let http and https pass, i would say run the vnc on port 443 (https) - then (if no proxy is in the way) the firewalls will not be able to distinguish between a normal ssl request and a vnc connection request

Option 2.) run an ssh server somewhere (even at your place) that runs on 443. Let the remote person connect to it via putty (if they use windows) or ssh client (if they are on linux) with port forwarding enabled (in the commandline this would be something like *-L 5900:localhost:5900*). The advance over option one is that the traffic will look exactly like an ssl session - so even a proxy cannot figure out that you are doing something that is actually not allowed. The disadvantage is that the person to be helped needs some ssh client and needs to set it up properly.

Option 3.) this is overkill for a onetime help - but i use this for difficult clients. I have an Openvpn server running that always listens on port 443. The client gets a cert-based connection installed on their laptop/computer that they don't even know about. As soon as they boot their computer and have internet their laptop/computer will automatically connect to my server - thus giving me direct access to their laptop as soon as i join the vpn myself. As i said, this is pretty heavy overkill and you need to get your hands onto their computer one time to set this up (believe me, they cannot do that alone). But once it is set up it works totally automatic and independent without any interaction from the person needing help...

hope it helps :)

---

### Post by ilrudie on 2008-08-25
+1 for ssh tunneling.  If memory serves me correctly vnc is in no way secured and leaves its security 100% up to a)trusting the network or b)secure the connection somehow.
Since this is over the internet a is not an option leaving you with option b.  An ssh tunnel is probably the easiest way to do this.

---

### Post by diablo75 on 2008-08-25
> **SpaceTeddy said:**
> mhm - i can think of three. but most of the involve running some server on your side that can mask the traffic as something else.

Option 1.) run the vnc on a standard port that is usually used for something else. As most firewalls will let http and https pass, i would say run the vnc on port 443 (https) - then (if no proxy is in the way) the firewalls will not be able to distinguish between a normal ssl request and a vnc connection request

Option 2.) run an ssh server somewhere (even at your place) that runs on 443. Let the remote person connect to it via putty (if they use windows) or ssh client (if they are on linux) with port forwarding enabled (in the commandline this would be something like *-L 5900:localhost:5900*). The advance over option one is that the traffic will look exactly like an ssl session - so even a proxy cannot figure out that you are doing something that is actually not allowed. The disadvantage is that the person to be helped needs some ssh client and needs to set it up properly.

Option 3.) this is overkill for a onetime help - but i use this for difficult clients. I have an Openvpn server running that always listens on port 443. The client gets a cert-based connection installed on their laptop/computer that they don't even know about. As soon as they boot their computer and have internet their laptop/computer will automatically connect to my server - thus giving me direct access to their laptop as soon as i join the vpn myself. As i said, this is pretty heavy overkill and you need to get your hands onto their computer one time to set this up (believe me, they cannot do that alone). But once it is set up it works totally automatic and independent without any interaction from the person needing help...

hope it helps :)

Re Option 1:  I kind of had the idea of doing this when we were trying to connect, but I couldn't figure out the syntax for getting the port number to connect.  I've been using x11vnc on the client side, and vncviewer (in listen mode) on my end to establish reverse vnc connections.  When I tried the "-listen (insert port number here)" it would ADD that number to the number 5500, giving me a result that was WAY off from what I was trying to get...so that didn't seem to work.  So... just throwing this out in case someone knows how to get the listening port number on vncviewer to something like 443 if I wanted to do it like this.

Re Option 2:  An SSH tunnel is something I've always wanted to learn how to setup.  It's an advanced technique that I don't have a crystal clear understanding of, especially when it comes to the software.  I have a windows-based vnc launcher (a small program that runs Tightvnc server for them and makes it as easy as one click for the user to start a remote session with me), and I'd like to figure out a way to make using SSH a standard protocol.  I guess I'll have to do some reading about Putty and ssh client and see how they work.  It wouldn't take much to make my own computer an SSH server, right?

Option 3:  Sounds pretty advanced, but very secure.  I'd go for it if I had a clue about doing this.  Maybe some other day :)

---

### Post by SpaceTeddy on 2008-08-25
Ok... i am taking this as a hint to explain ssh forwarding... 
Well - i don't really think i will explain it all too thorough - just the nutshell.

the basic idea is that you utilze the ssh connection to pass non-ssh traffic through it. The way this works is that ssh opens a port on one side of the connection and sends the packets on the specified ip on the other side. 

Lets consider this setup (i am assuming that DNS works and will not assign IPs to the Computers):
Comp1 <---> Comp2 <---> Comp3

now - lets say that you are sitting on Comp1 and want to access something on Comp2 that cannot be access directly (let's say it's a webpage)

> ssh Comp2 -L 8080:localhost:80
Now the Synatx here is localport:DestinationIP:DestinationPort
And what does it mean ?
Well - on Comp1 there is now a port opened (8080) which will be forwarded to the other side of the ssh connection and then try to connect the specified ip (localhost) on the destination Port (80). In other words - by accessing port 8080 on your computer you are acctually connection to port 80 on Comp2.
                   
So the Connection actually looks like this
Comp1 (127.0.0.1) sshd_server (port 8080) -> Comp2 (127.0.0.1) port 80

Now - let's make this a little trickier... lets use this command:
> ssh Comp2 -L 8080:Comp3:80
This would forward the port 8080 on your computer from comp2 to comp3. So, by connecting to localhost:8080 you'd actually be looking at comp3 port 80.

ok... this is pretty confusing. The best way to figure this out is to actually try it. 

Hope it helps (a little) :)

---

