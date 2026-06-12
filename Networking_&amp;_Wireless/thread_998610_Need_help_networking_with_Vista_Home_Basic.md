---
title: "Need help networking with Vista Home Basic"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by smurfier on 2008-12-01
So I'm new to ubuntu 8.10. I've been a windows man all of my computer related life. I wanted some fun and to expand my experiences so I used Wubi to install ubuntu on my laptop. So far its working great once I've figured out a few basic things. The big problem is that I have a rather large hard drive sitting on my fathers desktop I would like to have access to while I'm using ubuntu. I have tried configuring samba to the best of my ability. I installed a gui interface since the coding is out of my league. I've read several how-to's and lots of forum pages but am completely lost in the coding. When i go into the network, I can see the workgroup but nothing is listed when I open it. I'm actaully starting to prefer ubuntu over windows, but if I can't figure this out I may have to stick with vista.

---

### Post by darco on 2008-12-01
Yes Samba can be pain to get it working. Not knowing what you have done, have you tried connecting via the IP address? Can you ping the ip? Are you on the same WORKGROUP?
Try this link

[http://www.linux.com/articles/58593](http://www.linux.com/articles/58593)

good luck 

darco

---

### Post by smurfier on 2008-12-01
I have no idea how to connect via the ip address. and is this something that can be done automatically when i login?

I know that I have the right workgroup because I can see my laptop on my desktop, but after logging in I still can't access my files.

---

### Post by Iowan on 2008-12-01
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

As if you need more reading... [this]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To for mounting shares automatically.

---

### Post by smurfier on 2008-12-02
Well, I tried that. It doesn't ask for my user name and password, nor does it show my shared folders. I did a ping which was successful.

---

### Post by recon69 on 2008-12-02
Well, I'm no expert, but you could try set the Wrokgroup/Domain setting on both computers. They should match. look in ubuntu under "system->admin->network->general" and in windows using "My Computer->properties->not sure where". also a firewall on the windows machine might be blocking your connection. 
  You can also go to irc.freenode.org and join the #ubuntu channel and ask for help there as well.

hope this helps.

regards

---

