---
title: "Local Network can't find it."
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by dareofficer on 2008-11-22
Hello, I'm trying to find my local network, but none of the other computers show up.  I can't even do a Windows Share, and enter the IP address.

My samba shares are working fin.  I can log in from my other PC's/Mac and share/move just fine.

I have a network hard drive, with TV Shows on it and would like to find it so I can watch it with MythTV.

I also have the 8.10 installed, with the ubuntu-desktop.


Thanks, for any help.

---

### Post by Iowan on 2008-11-24
Can you **ping** between machines?

Well, DUH... if the Samba shares are working. So the other machines can see this one, just not vice-versa?

---

### Post by dareofficer on 2008-11-24
Right, when I go to look up other servers, via, nothing shows up.

---

### Post by cariboo on 2008-11-24
Install nmap on one of your Ubuntu computers and run the following command:

```
sudo nmap -PR -sP 192.168.1.0/24
```

This assumse that your ip address are between 192.168.1.1 and 192.168.1.254. If not change to suit your network.

Namp is in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Last time I ran the above command it found a computer that I had forgotten about, my Mac G3 was stuck away in a corner in my shop and I had turned it on and had forgotten to turn it off after using it, it had been running for at least 3 weeks.

Jim

---

### Post by dareofficer on 2008-11-24
I had to install nmap.  After I did that it showed all my computers.  Now how do I connect to them?  I would like to ssh, or Windows connect to them with a gui?

Thanks

---

### Post by Iowan on 2008-11-25
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

Give credit where due...
Not a solution, but maybe it's progress.

---

### Post by dareofficer on 2008-11-26
Thanks,I was able to get it going.  I found the IP address, as you were describing, then I smb:// the ip, and it is working just fine.

---

