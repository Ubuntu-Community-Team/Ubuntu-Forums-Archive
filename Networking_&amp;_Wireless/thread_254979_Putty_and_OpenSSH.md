---
title: "Putty and OpenSSH"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by finferflu on 2006-09-10
Hi all,

I'm trying to get a friend of mine (who uses Windows XP) to connect through PuTTY to my Ubuntu box running the OpenSSH server, but everytime she tries to connect to my IP, she receives the following error: 

> Network error: Connection timed out 

I went around searching and found this:

> This error means that the network connection PuTTY tried to make to your server received no response at all from the server. Usually this happens because the server machine is completely isolated from the network, or because it is turned off.

Check that you have correctly entered the host name or IP address of your server machine. If that fails, consult the administrator of your server. 

So I guess I need to change something on the server side, and I guess I need to put the IP of my system in on port 22, but I don't know how I am supposed to do that.

Any hint would be appreciated.

Thanks for your time. :)

---

### Post by Iowan on 2006-09-10
Is there a direct connection between your friends computer and your server - or is there a router between them that needs to forward port 22 to your server?

---

### Post by cstudent on 2006-09-10
A lot of ISP's block ports for residential customers too.

---

### Post by finferflu on 2006-09-11
Well, I am connected to the internet through a router, and my friend, I think, is using a proxy server (she's connected to the internet through another machine).

So, I guess I should forward port 22 on my router, right?

When I tried to connect to another Ubuntu box through ssh, I had no problem, even though this is the first I try the other way round (i.e. people connecting to my machine).

Thank you.

---

### Post by tbonius on 2006-09-11
If your Ubuntu computer is behind some sort of router/firewall/NAT.. then yes.. of course you would forward TCP port 22 (assuming you left SSH listening on port 22) to your [COLOR="DarkRed"]INTERNAL[/COLOR] IP of the Ubuntu computer.

She would then connect to the [COLOR="DarkRed"]EXTERNAL[/COLOR] IP address of your router.. which would forward it to the Ubuntu computer.

Now that is assuming that she does not need any special type of Proxy client software on her side to access services on the outside of her network.

T

---

### Post by finferflu on 2006-09-11
Well, yes, I've configured my router to forward port 22 on my internal IP address, and I gave my friend the external one.

> assuming you left SSH listening on port 22

I don't know anything about that, I've just installed the OpenSSH server, and it auto-configured itself, so I guess 22 is the default port...

I haven't tried yet with my friend, but I tried today to connect from another computer connected to the same router. When I tried to connect to my PC using the external IP I received a refusal of connection, but it obviously worked fine when I used the internal one. 

But I don't know whether that test was a valid one..

---

### Post by tbonius on 2006-09-11
I assume you mean that you tried to connect to the external IP address from inside the network, thus having it redirect from the external IP address to the internal IP address.  Some routers will not let you do this.. it can cause an infinite routing loop.  Test from a computer outside your internal network.  Only then will you know if the port forwarding on your router works correctly.

T

---

### Post by finferflu on 2006-09-11
Yes, I meant that, but right now I tried with my friend again and it didn't work. Also: what should I put when forwarding the port, TCP, UDP or both?

Thanks

---

### Post by tbonius on 2006-09-11
If it didnt work then either your port fowarding isnt working.. or your friend cant get to alternate services outside of his/her network anyways.

Try forwarding TCP port 22.  You only should need TCP.

Also.. why not just use Linux as your firewall instead of whatever router you are using?

T

---

### Post by finferflu on 2006-09-11
I'm sorry, it actually did work, I put both, and it worked.. there's been some mistake earlier.

Thanks a lot for your help! :D

---

