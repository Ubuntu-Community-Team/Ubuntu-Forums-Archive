---
title: "Hamachi VPN for file sharing - total confusion!!!!"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by herger on 2008-10-08
Hi all.
I have just installed hamachi on my Ubuntu laptop and my WinXP office desktop.  
I NEED to do file sharing between these two. I set up the hamachi lan, the two pc's see each other (green stars) and they can ping to each other, 
[COLOR="Red"]**BUT**[/COLOR]
I haven't found anywhere how I can do file sharing: I tried to access via ssh to both of the computers via the ip given by hamachi, but when I put the password, ssh doesn't recognise it and says it's wrong.
There are NO routers and I usually ssh via both from my laptop and my desktop to different computers.
I do NOT have firestarter or any other firewall on Ubuntu and WinXP has the firewall perimission for hamachi (I put it manually).
I have also installed VNC with the howto in this site, but it's not what I do need...
Can anybody help me, please?   :confused::confused::confused:
Thanks in advance and the best regards

Herger

---

### Post by superprash2003 on 2008-10-08
ensure that openssh is listening to the hamachi interface..

---

### Post by herger on 2008-10-09
Hi. Thanks for Your reply.
How can I ensure that?
Thanks again and excuse me, I don't have much experience... :oops:

Regards

H

---

### Post by herger on 2008-10-09
Sorry, I have realized there is one more problem: the win desktop can ping on my Ubuntu laptop, but my laptopo can't ping: it says destination unreachable.....
:confused:
Thanks and regards

H

---

### Post by superprash2003 on 2008-10-09
try this.. setup samba server in ubuntu and try accessing from windows desktop.. since windows can ping ubuntu it should work..
reference : samba setup [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by chapon on 2009-03-12
Hi all,

I want to share some files with my friends in my hamachi network. Can I do this over http? 
What I want to do is:

My friends can go http://<my.hamachi.ip>:<port> and download the file I have configured. 

We have successfully configured hamachi network but we couldn't do the above mentioned configuration 

any help would be appreciated

chapon.

---

