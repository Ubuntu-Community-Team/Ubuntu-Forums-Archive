---
title: "Windows Shares are Invisible??"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2008-08-07
I just installed Ubuntu Server, installed gnome and went to connect to a windows share. I click places->network-> Windows Network -> Workgroup and there's nothing there, it's empty. 

Previouly I was testing CentOS. It saw the windows shares straight off, but it was heavily lacking in repositories so I decided to try ubuntu. I like it's repositories but now I am unable to connect to my network machines, which I used to use rdesktop for (it doesn't connect either) 

Anyone have a fix?

---

### Post by Sammi on 2008-08-07
Does any other kind of networking work on the machine?
Does it have an internet connection?

Does it get an ip address from DHCP (dynamic ip supplied from a router)?

Have you tried a simple ping to the computer you want to connect to? Does it respond? You just write "ping <targets ip address>" in a terminal. replace <target ip address> with the ip address of the computer you're trying to connect to.

---

### Post by davethewave83 on 2008-08-08
> **Sammi said:**
> Does any other kind of networking work on the machine?
Does it have an internet connection?

Does it get an ip address from DHCP (dynamic ip supplied from a router)?

Have you tried a simple ping to the computer you want to connect to? Does it respond? You just write "ping <targets ip address>" in a terminal. replace <target ip address> with the ip address of the computer you're trying to connect to.

Thanks for the reply :) The internet works on the machine, it does have an IP and Ping did successfully find it. I did a system restart which fixed the rdesktop problem, however, it still will not see the windows shares in network.
If I do a smbclient -L 192.168.1.34 it lists the windows shares in the terminal, but they will not list in the network browser.

---

### Post by davethewave83 on 2008-08-08
Also, it may be interesting to note that it does know the "workgroup" name for the windows shares, in the network file browers I open "windows network" it sees "WORKGROUP" which is the linux, and it sees "WIN" which is the name of the workgroup I gave to my windows machine, opening WIN up displays nothing, however, as stated before this worked in centos just yesterday. :confused:

**edit**
If I go into pyNeighborhood and turn off "always use anonymous login" it displays the windows machines, but will not mount them. 

If I use the "connect to server" and choose windows share, type the server name in (the pc name) and connect, it opens a folder "Windows shares on <mypc>" but the directory is blank.
I will continue probing around :) if anyone knows my problem feel free to blurt it out, thanks!

***Edit2**
Well I tried being more specific with the connection, I clicked "connect to server" and chose windows share, then entered the Server name, and folder name, it asked for my windows username and password, and domain so I entered all that, which then it added a mount to the desktop *cheers* It is a bit more work than I am used to, since I used to just browse the network and click to open it, but at least it's working this way :) 

Still, if anyone knows how to get the network browser to work let me know, it would be great help!

---

