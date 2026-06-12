---
title: "XP or Vista Computer needs to see Ubuntu Computer"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by BuntuFreak on 2008-01-26
All right, so I have made the switch too Ubuntu for good. Problem is a family member still needs to keep a windows box. That box is running XP and Vista dual booted. So either is okay.

Now I want the XP / Vista box to be able to read / write from a folder on my Ubuntu computer. To be clear we are not talking about a XP / Ubuntu dual booted computer trying to see Ubuntu from XP. We are talking off separate computers.

I saw some postings of using ssfsh whatever, but they went over my head. Right now, I can select "Network" on Ubuntu, which provides me a link to Windows Network, I can then simply open it up and have access to any Windows boxes on my network. I now need the reverse. In Vista, I want my Network to list all computers : Windows and Ubuntu and be able to read / write from / to the Ubuntu computer.

I'm not sure if this is possible. I hope it is. Please advise. The Vista user is not as sophisticated as me :), so it is important they can accomplish this using Windows Explorer.

Many thanks for any help.

---

### Post by GuiGuy on 2008-01-26
> **BuntuFreak said:**
> All right, so I have made the switch too Ubuntu for good. Problem is a family member still needs to keep a windows box. That box is running XP and Vista dual booted. So either is okay.

I'm not sure if this is possible. I hope it is. Please advise. The Vista user is not as sophisticated as me :), so it is important they can accomplish this using Windows Explorer.


Have you configured Samba on the Ubuntu PC. [Google]("http://www.google.com.au/search?hl=en&q=Vista+ubuntu+samba+configure+guide&btnG=Search&meta=") will show a number of guides on the topic. 

There are also several threads in these forums, [notably this one]("http://ubuntuforums.org/showthread.php?t=650520"). There's a guide around here somewhere as well. 

In vista ensure Network Discovery is on.

Just a tip- once you get set up and if you get "Network Path Not Found" errors on the vista box, reboot the router & repair the network connections before you panic. :)

After that it's only a matter of setting permission on the Linux shares. 

NB: I find SWAT the best for sorting out SAMBA. 


regards.

---

### Post by BuntuFreak on 2008-01-26
All righty then. Now I actually know what Samba is :)

I googled as  you suggested and added word Samba to the search string. Presto! Several articles telling me what to do.

So now my Vista computer can see my Ubuntu computer. Now I'm not ungrateful, but I still have a small problem. I have a Laptop that also has Vista. When I try to go to my Ubuntu box thrrough the Laptop, Vista gives me a 10 line error message box that effectively says "You have already logged on using this username to Ubuntu, use another".

So do I need to create another user account on Ubuntu just so I can have two separate Vista boxes connect to it simultaneously?

---

### Post by GuiGuy on 2008-01-27
> **BuntuFreak said:**
> 
So now my Vista computer can see my Ubuntu computer. Now I'm not ungrateful, but I still have a small problem. I have a Laptop that also has Vista. When I try to go to my Ubuntu box thrrough the Laptop, Vista gives me a 10 line error message box that effectively says "You have already logged on using this username to Ubuntu, use another".


Are you using "Simple file sharing" in ubuntu?

---

