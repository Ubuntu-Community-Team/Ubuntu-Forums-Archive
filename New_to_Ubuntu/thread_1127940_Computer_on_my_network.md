---
title: "Computer on my network"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by sanubie on 2009-04-17
I am somewhat new to linux and networking in general. I have 4 machines running off the same Linksys wireless router. And I am interested in setting up a file server so I can share files between computers. 

2 computers run Linux, one runs Vista, and the other is an old powerbook Mac 10.3.1.

My research lead me to a few tutorials and it says I should be able to ping each computer by name or IP. I am not entirely sure what each machine's IP is. Is there a terminal command to pick up on the machines connected to my network?

PS: I tried going into my web utility for my router, but it won't even let me through. So I can't set up port forwarding or anything. The default password should work but it isn't. Maybe I tried the wrong password too many times. Who knows... anyway, any advice would be greatly appreciated.

---

### Post by jbrown96 on 2009-04-17
nmap is the best tool for this. Install with ```
sudo apt-get install nmap
``` To run a basic ping scan that will give you the address and name of each computer run the following scan ```
sudo nmap -sP 192.168.1.*
``` Your router may use a different ip range, so you may need to use 10.0.0.* instead. You can figure out which ip range to use by checking your ip in network manager (top right). Right click on it and select connection information.

---

### Post by Iowan on 2009-04-17
Can't help with the Mac, but Linux boxes should reveal their IP via *ifconfig* in a terminal. Vista uses **ipconfig** from the Start>Command Prompt.

---

### Post by halitech on 2009-04-17
MAC uses the terminal as well so the same command that works in Ubuntu should work there (from what I can remember at least)

---

