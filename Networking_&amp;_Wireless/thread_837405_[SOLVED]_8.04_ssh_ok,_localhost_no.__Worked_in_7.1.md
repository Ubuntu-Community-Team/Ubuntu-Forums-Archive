---
title: "[SOLVED] 8.04 ssh ok, localhost no.  Worked in 7.10"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by AquaNature on 2008-06-22
Hello everyone!

I wasn't able to find anything with my specific problem.  I'm not too familiar with ssh and such, just followed the forums (thanks everyone)!

I setup a mythbuntu server, and I usually connect via ssh and then type in firefox "localhost/mythweb" to see the recordings and such.

This has been working perfectly for me in both windows and ubuntu 7.10.  For some reason, on a 8.04, (fresh install), the localhost doesn't work.  I am able to ssh to my server, via "ssh [email]user@domain.net[/email]"  and log in, but typing localhost in any program doesn't work (firefox/vinagre/xtightvncviewer)

I used to be able to login ssh and type localhost for VNCviewer also, and that doesn't work either now.  I tried it in my windows machine via putty, and it works perfectly, both vnc and firefox.

I installed putty in ubuntu, thinking I setup my ssh wrong or something, and it still didn't work.  I'm able to ssh, but not use localhost. :confused:


Is there something I'm missing?

---

### Post by jetsam on 2008-06-22
Could you post the output of 
```
cat /etc/hosts
```
and
```
cat /etc/nsswitch.conf | grep hosts
```

---

### Post by AquaNature on 2008-06-22
sure, here goes.  room is the name of my computer

127.0.0.1 localhost
127.0.1.1 room

cat /etc/hosts
```

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


cat /etc/nsswitch.conf | grep hosts
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

---

### Post by jetsam on 2008-06-22
> 127.0.0.1 localhost
127.0.1.1 room
So, wait... those two lines are in your /etc/hosts file or no?

They need to be if they aren't.

The whole thing should read like so:
```
127.0.0.1 localhost
127.0.1.1 room

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Your nsswitch.conf looks good.  

It's also possible your loopback interface isn't defined.  Does
```
ifconfig lo
```
show something like this?
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33200 (32.4 KB)  TX bytes:33200 (32.4 KB)

```

---

### Post by AquaNature on 2008-06-22
oops, yea, the 127.0.0.1 localhost and 127.0.1.1 room are in my /etc/hosts.  just didn't quote it right. doh!

I think I have the same thing you get when I do ifconfig lo:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137104 (133.8 KB)  TX bytes:137104 (133.8 KB)

```

---

### Post by jetsam on 2008-06-22
mmmm...  I was expecting to have found the problem by now, but everything looks good.  

So you can **ping -c3 localhost** when you log in to the command line with ssh, but the problem is restricted to when you use x11 forwarding?

...afraid I may be swimming out of my depths at this point.

---

### Post by AquaNature on 2008-06-22
yea, I login to my server via ssh... and I am able to ping localhost from my command line (new terminal).  I don't know what x11 forwarding is, but if that means things like vnc and firefox, then that's my situation.  

Thanks for your effort, jetsam.  I appreciate the quick response.  

I'm wondering if I'm the only one or if others ave the same problem.  I guess I might have to switch back to an older version.

---

### Post by jetsam on 2008-06-22
There are others, because I have the same problem.  :)

---

### Post by jetsam on 2008-06-22
OK!

Figured it out with Firefox anyway-- assuming your problem is the same as what I was seeing.

Run Firefox like this when you're in your ssh session:
```
firefox -no-remote
```
Otherwise, it will detect an already running instance of Firefox on the local machine and use it.   
Here's the bug report that led me to this.  The solution is in the last comment:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/214829]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/214829")

I got quite confused when I realized the problem only happened if I already had Firefox running on the local machine.  

Not sure about vnc.  Maybe there's something similar?

---

### Post by AquaNature on 2008-06-23
Thanks for the link.  I tried doing firefox -no-remote in ssh, but didn't get it to work unless I put -X in the command ```
ssh -X [email]user@domain.com[/email] firefox -no-remote
```

It works, like you said!  Thanks, but for me, it's a bit slow.  Firefox would get dark as if it's going to freeze, and then go back to normal and work, and then get dark again, and then back and forth.  It's a bit too slow for me.  Are you using firefox 3?

I found something that would get vnc working though, it was located here:
[URL="https://help.ubuntu.com/community/VNCOverSSH"]
https://help.ubuntu.com/community/VNCOverSSH[/URL]

Basically, it said to do this: ```

vncviewer -via user@domain.com computername:1
```


**Heads up:** when I searched for vncviewer via apt-get, it has been updated to **xtightvncviewer**.  


I guess this will be a temporary solution for me.  But I still would like to get firefox working without having to run another instance through the ssh connection.

Thanks again!

---

### Post by jetsam on 2008-06-23
> It's a bit too slow for me. Are you using firefox 3?

Yes.  Firefox 3-- whatever the official package is at this point.  It says 3.0 in the about page, but I think it's based on rc1 or rc2, as Firefox hasn't officially released yet.  

It's bound to be a bit slow running remotely like you are.  It's noticeably slower for me than running a local copy, but not to the point where I'm getting the gray screen of catatonia.  

It seems like what you want to do is run your browser locally, and have mythweb serve the content to it.  I don't know mythTV really at all (haven't used it), but if you don't need the ssh tunnel, it may work to just put
[http://domain.com/mythweb](http://domain.com/mythweb)
or
http://[COLOR="Blue"]<server_ip_address>[/COLOR]/mythweb
...into Firefox running locally.  You might need to configure mythweb to serve the content to your machine though.  

----------------------------------

If you do need the ssh tunnel for encryption, is this link helpful?  
[http://www.mythtv.org/wiki/index.php/MythWeb_ssh_tunnel_howto]("http://www.mythtv.org/wiki/index.php/MythWeb_ssh_tunnel_howto")

I can get this setup tunneling web content from apache running on my server with almost no fuss.  On the client machine, I run this in a terminal:
```
ssh -L 8080:localhost:80 [COLOR="Blue"]user[/COLOR]@[COLOR="Blue"]server_hostname[/COLOR]
```
...and sign in to authenticate the ssh session.
Then, again on the client machine, I run Firefox (locally-- not in the ssh terminal!) and point it to
```
http://localhost:8080/
```
...and my apache server on the remote system comes up, except it's serving the content through the encrypted tunnel.  Magic!

...hope that was more helpful than confusing.  It can make your head spin a bit figuring out which connection goes where and what localhost is pointing to in these different contexts...

---

### Post by AquaNature on 2008-06-24
That was exactly what I was looking for! Thanks a million!  Works perfectly!  I was just surprised when I updated to 8.04 that things weren't working as before.  Oh well, things for the better I guess.  

Thanks once again for all your help!

---

### Post by jetsam on 2008-06-24
Sure thing.  Glad you got it working!  :)

If you get a chance, can you mark this one solved in the thread tools drop-down?  It has three (relatively) obscure solutions in it, including your vnc fix.

---

