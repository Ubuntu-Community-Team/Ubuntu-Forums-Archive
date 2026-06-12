---
title: "setup tunnel vnc via cml"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Sir Jake on 2008-03-24
Hello there, I have my server setup in a colocation. I have access to it via putty, still new to linux and would like to be able to use remote desktop with vnc. I spent the last day looking up ssh tunneling vnc
for some reason I still cannot get anything working. If I could get some help on this that would be great. I am using ubuntu 7.10 server 64bit with gnome installed.  I cannot access my remote desktop when I type in the ip address in ultra vnc.  I get "failed to connect to server"
Sorry for the limited info I have, if you need more please let me know and I will try to get it.

---

### Post by SpaceTeddy on 2008-03-25
when using port forwarding with ssh (putty ?), you do not connect to the remote ip - you connect to yourself... 

so, lets say you forward the standard vnc port from your computer to your remote host (i only know the commandline commands :( )

ssh -L 5900:127.0.0.1:5900 user@remotehost

this will forward port 5900 from your local machine to the localhost on the remote machine (also port 5900) - note that the 127.0.0.1 applies **on the remote machine **.

in fact - now you connect to yourself in order to connect to the remote host (this sounds insane... but it is that way)

so run vnc on host 127.0.0.1
and you should see the remote host

the conection you acctually do here is

vncviewer <--> your computer (5900) <--> ssh client (your computer) <--> ssh server (remote computer) <--> vnc server (5900)

hope this is understandable :)

---

### Post by Sir Jake on 2008-03-25
Okay, somewhat understand also lost. :(
On my server I type "ssh -L 5900:127.0.0.1:5900 user@remotehost"
in the command line? Or to I need to replace the "user@remotehost" with my user name or leave it that way.


Or does "ssh -L 5900:127.0.0.1:5900 user@remotehost" 
do I setup that in putty on my local computer.
Sorry for being so new at this.

---

### Post by SpaceTeddy on 2008-03-25
slowly... open then putty on your machine - type in the hostname of the remote machine - before you go on connect choose SSH->Tunnels from the side menu, put in 5900 as source port, and as destination you type in 127.0.0.1:5900

screenshot of what it should look like is attached.
then go on open and log in normally. 

once the command shell is open, open vncviewer and connect to 127.0.0.1  - you chould get then get the connection to the remote server.

---

### Post by daflame on 2008-03-25
You could also use FreeNX since it automatically tunnels over SSH if you have root access to the machine.  The instructions are in the link below.

---

### Post by Sir Jake on 2008-03-27
Thank you very much Teddy, works great  :)

---

