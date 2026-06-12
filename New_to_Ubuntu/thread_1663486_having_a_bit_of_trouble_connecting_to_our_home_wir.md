---
title: "having a bit of trouble connecting to our home wireless network :)"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by laura22 on 2011-01-09
hi, i am new to all things linux, so be easy on me...
so just downloaded ubuntu 10.10 on my samsung netbook, and i can't connect to our router using the wireless passcode thingy - the ethernet cable works to the same box, the wireless works when i set it on no encryption, and i can find the wireless network name on network manager. I have typed and re typed the password a few times now... and the same password work for other computers in the house...
i think the encryption is AES... 
should i get this wicd that ive heard so much about? how do i delete network manager after i have got wicd?

cheers :)

---

### Post by TeoBigusGeekus on 2011-01-09
What's your wifi chipset?
```
lshw -C network
```

---

### Post by Phillip Spencer on 2011-01-09
Just a thought but some wireless router / modems (such as my Orange LiveBox in France) require a button to be pressed on the modem at the time you are trying to initiate a new wireless connection otherwise it refuses to recognise the new connection despite the correct password / phrase being entered.

Be nice if it that easy, he said hopefully!
Cheers
Phillip

---

### Post by isee on 2011-01-09
Just some more info, but I had to put wicd into my laptop, NetworkManager kept dropping the connection, and wicd solved that problem.

I also think wicd has a better GUI and seems to give a more accurate signal strength.

I recently banished NetworkManager from my desktop because I was having trouble with dropped connections when using torrents, so now I have wicd on my desktop too, although a wired wicd connection will only connect to a router, so to be plugged in to my ISP's modem directly i used pppoeconf.

Hope that helps.

---

### Post by Eternal_Light on 2011-01-09
I am also aware of a situation on netbooks where owners of ralink wifi cards couldnt get them to work properly because the os was using the wrong driver as active. I had the same problem but cant remember the solution all that well. I remember putting the false driver in the blacklist and the os selected the correct one by default after that. Before solving the problem I had the exact same issues as u. It took the manager a veeeery long time to respond and try to establish a connection with the wifi router and after a few minutes had passed it asked me for the password again. Couldn't connect no way.

If you do a little search on the info center of gnome (Im on kubuntu i have Kinfocenter) and find the chipset of your card, if it is something like RaLink3090 here is the solution:

according to post #103 : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/+index?comments=all)

Steps to the solution:
 open your Terminal and first type in this: sudo modprobe rf rt2800pci
 Then afterwards type in this: sudo modprobe -rf rt2860sta
 As the next step follows this command in your terminal: sudo modprobe rt2860sta
 Just as you type in this, your networkmanager connects automaticly and comes back to work!!!
 But to close the whole thing up, you need tot ype in this command, for finishing up:
 echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
 Then you are d one and your networkmanager will work for you again.
 



All credit for this goes to Linuxexperte
Hope it was helpful

---

### Post by egossett on 2011-01-09
I am new to this as well. I will have to learn more from this post. I will look for my chipset and post here as well.

A lot to learn for sure.

---

