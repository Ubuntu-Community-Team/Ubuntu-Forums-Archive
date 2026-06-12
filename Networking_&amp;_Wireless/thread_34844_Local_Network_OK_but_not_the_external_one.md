---
title: "Local Network OK but not the external one"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by gyhelle on 2005-05-16
Hello,

I have a problem with my network with Hoary. I configured it correctly (IP, name, mask, DNS)  I think, because I can have  access to my local network, but the problem is that internet is out of access.

I have a Win XP partition, and it's working well under windows. Before my Ubuntu, I had a Suse 9.2 and it was working well too (but I didn't configuring this one). Sadfully I delete this Suse installation, hopefully I still have the /etc directory. 

Does anyone have an idea of the problem ? can I use some files from the Suse /etc ?

many thanks for your help,

gyhelle

---

### Post by dave9191 on 2005-05-16
So you can ping IP on the local net, but you cant access the internet? 

Try pinging google.com. If that fails, try pining 216.239.36.10 . That ones of googles servers. 

If the google.com fails and the IP succeedes, then your name servers arent configured properly. Try that

Dave

---

### Post by gyhelle on 2005-05-17
>Try pinging google.com.
> If that fails, try pining 216.239.36.10
 >If the google.com fails and the IP succeedes, then your name servers arent configured properly. Try that


It's OK now, thanks a lot 


gyhelle

---

### Post by dave9191 on 2005-05-17
Cool :)

---

