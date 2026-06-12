---
title: "Entirely frustrated! - XDMPC"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by twignation on 2009-03-19
Ugh!

XDMCP between two Ubuntu computers. Worked fine yesterday, why doesn't it work today?!

I would like the ability to log into a computer remotely, XDMCP seems like the most obvious choice for a secure LAN.

It worked absolutely fine yesterday - today I go to log in and it will find the machine I want, I click - and it will just sit there with a blank screen and the mouse as an X.

This is giving me a headache now.

I have tried:

Disabling all firewalls
Disabling ESD Sound (on both client and server)
SSH works (I think)
Switching the remote screen to plain face (It doesn't get that far)
I know the machines can see each other because I am listening to music from the remote machines music folder

Please could someone run me through the steps I require to have XDMCP working or tests in case I have inadvertently done something that prevents XDMCP from connecting?

AFAIK the only change I have implemented is setting up NFS and Samba on the remote computer - 

Please 'elp!!

Twig.

---

### Post by ivanvajar on 2009-03-19
It's amazing how many problems you can solve by restarting computer :-)

---

### Post by twignation on 2009-03-19
:) true

Shame this isn't one of 'em :P

---

### Post by twignation on 2009-03-19
ssh won't connect via console. 
but it is working connecting through putty.
no console with ssh no port forwarding with VNC right?
xmdcp just doesn't work. 
I've tried it on another pair of computers. 
It doesn't work.
however I can connect to all my folders using smb://
Although I have to go in through 'location..' because nothing shows up under network.

](*,)

---

### Post by twignation on 2009-03-22
Last try at getting help...

Lets try this another way

I do this [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564) and at this point:

vncviewer localhost:1

If I try locally: 'Connection to Host is Closed'

If I try to remote in: 'Connection to Host is Closed'

In my network tools, I can port scan and see the port is open. I don't have a firewall. This has worked before. 

Why doesn't ANY remote access thing work?

---

### Post by sim-value on 2009-03-22
Samba ?

Try disabling it again ...

---

### Post by twignation on 2009-03-22
Nope, not samba, disabled it and no connection even on local host.

---

