---
title: "Sharing files on a network"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by eman245 on 2007-06-28
My desktop and laptop are both running Ubuntu Feisty Fawn, and I want to share my desktop files over the network so that I can get all my documents etc. on my laptop easily. What is the best way to do this? I have tried to set up a ssh server with no luck. I have also tried to share the folder without any luck. I dont want to download any 3rd party software if its possible to do it without it. Sorry, because I know this is a dumb question, but i'm a noob.

---

### Post by benanzo on 2007-06-28
Why doesn't right-clicking the folder and selecting **Share Folder** work?  Does it not appear on the other machine?  That would be the easiest way to do it I believe.

---

### Post by Threbus5 on 2007-06-28
Hi,

Right click to share as already described then make sure to use the same domain throughout the network.
Often in a mixed Windows-Ubuntu network WORKGROUP seems acceptable for a network domain name.
My network has Mac's, Ubuntu, & Windows wired and wireless. Sharing should be fairly easy.

Take care

---

### Post by eman245 on 2007-06-28
I've tried to click share folder many times. I've tried to share it through Unix networks and Windows networks. In the Unix networks, i've tried to share it by specifying ip address and computer name. None of this works. When I go to Places, Network on my laptop, it comes up with my desktop machine, but inside, there is nothing. It also has a windows network folder, which is also a dead end. There are no files being shared. I dont understand why it doesnt want to share it like this. Is there another way to share / transfer files on a lan?

---

### Post by gigaferz on 2007-06-30
[http://ubuntuforums.org/showthread.php?t=444691](http://ubuntuforums.org/showthread.php?t=444691)

look at this post

so far i can ping my computers, scan ports and even do a remote desktop connection however im still stuck to share files like in windows,

click network places,click on network, click on computer and so on,,,,,
when i go to network, there is only windows network and nothing, 

Hope you have better luck
so far the best I get is on a web browser is an index with apache default and myphpadmin thing...

like you i also went to the sahred folders options, added host with ip address and even tchanged the network settings  specified network and net mask etc...

I just did it, but with something  called ssh

go to places conec to server, and enter the ip address of the other computer, and log in with the user and password of that computer,

---

