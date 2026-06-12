---
title: "Synergy not working."
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Flavian on 2007-03-26
Hi guys.
I got the following problem:
I already managed it to connect from Windows to my Linux box via synergy and it worked fine!
I also managed it to connect from Linux to Linux.
But it won't work connecting from LINUX to Windows.
I always get the following error on the windows machine: 

> ERROR: server refused client with name "chopper"
ERROR: failed to connect to server: server refused client with our name.
NOTE: stopped client

Here is my LINUX configuration file, for the synergys Server.
> 
section: screens
chopper:
octavius:
end
section: links
chopper:
left = octavius
octavius:
right = chopper
end


Octavius is the linux machine which is on the left side and is the server which shares the keyboard and mouse.
Chopper is on the right side of Octavius :)

Thanks for your help!
Flo

---

### Post by airtonix on 2007-03-26
you mean you cant use the mouse connected to the linux box to control the windows box?

i can get htis working both ways fairly easy. my problem latley is that synergy cuts out eery so oftern and create mouse lag on the synergy-client.

really annoying.

---

### Post by Flavian on 2007-03-27
> 
you mean you cant use the mouse connected to the linux box to control the windows box?

Yepp, exactly.
I start the synergy server on my linux box with "synergys" and then I want to connect the windows client... and if I hit "Test" it just gives me the ERROR messages listed above :(

Maybe you can help me...
maybe it's just a little "bug" or whatever. Maybe a missconfig.

Thanks in advance.
Flo

---

### Post by eXisor on 2007-03-27
Try using the IP for the windows box.

---

### Post by Flavian on 2007-03-27
I already tried using the IPs for both of the computers... doesn't work either :(

---

### Post by airtonix on 2007-03-28
your config is fine.

try running the windows client in debug mode 2.

and the run the server with synergys -f

this should give you more info on why things are happening the way they are

One thought...... have you created a rule in firestarter or similar to allow all incoming connections from the ip of the windows box?

also try editing this file :  c:/windows/system32/drivers/etc/hosts

it is the equivilant of the linux file : /etc/hosts

in that put this : 

xxx.xxx.xxx.xxx chopper
xxx.xxx.xxx.xxx octavius

replace xxx with the ip address of each machine accordingly.
the n save and if you have the network icon in your systray, then right click that and click repair
failing that disable it and re-enable it, 

further more if you cant access the linux box via the machine name you just put in that file restart the windows machine.

put the same info in your /etc/hosts file on linux machine too.

sorry for cryptic replies.

---

### Post by Flavian on 2007-04-25
I now completely formated my laptop and set up a nice and fresh install of Feisty :) 
Here's the deal:
I did set the Ip adresses in the "hosts" files of both computers and now I get a different error message from the windows client

> 
ERROR: failed to connect to server: The attempt to connect was forecfully rejected


I do NOT use a firewall on liunx
AND the funny thing is that when I set up the WINDOWS box as the SERVER and the Linux box as the client, IT WORKS!! - I can share the windows machine's keyboard and mouse but not the Linux machine's one.
So there IS a connection, but only the way I don't want it to be :(

Can someone please help me?
Thanks
Flo

---

### Post by jbhutch on 2008-05-16
I had this same problem.  I found that another computer on my network had the same ip address and had a synergy server running.

---

