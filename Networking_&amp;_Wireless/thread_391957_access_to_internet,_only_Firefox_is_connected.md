---
title: "access to internet, only Firefox is connected??"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by flashbuntu on 2007-03-23
Hi, 
I've just installed Ubuntu 6.10 and have a D-Link DSL-502T ADSL Modem/Router via ethernet. 

Install went great but had no internet connection. 
The system worked fine with WinXP. 

After looking at these forums I found I had to disable ipv6 on firefox using about:config.

Things were looking good, I can access internet via Firefox, good speed to.

I then opened Evolution and put in the required email details, including gmail.
Unfortunately Evolution tries but no connection is made. Error, No route to host

I tried the Synaptic Package Manager and get the same response. Error, No route to host

But Firefox works???
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Would appreciate some ideas or be pointed to an appropriate forum post.

Cheers

---

### Post by bobhawkes on 2007-03-25
I have just posted the exactly the same problem to the newbie board. For some reason I missed this thread when I searched.  The only difference is that I am using the D-Link 504T router. Could this be a D-Link setting problem?

Bob

---

### Post by HereInOz on 2007-03-25
This is perhaps a DNS problem.   I have had problems with the 504s not passing the DNS addresses to Ubuntu correctly.  Firefox works but not the updates.

If you go in to System > Administration > Networking and then the DNS tab, and enter the DNS addresses given to you by your ISP, and then go back to the Connections tab, select properties for the active connection, set the IP address as a static IP, and enter your gateway IP which is the internal IP address of the 504, then it might work.

From memory, the 504 uses 10.1.1.1 as its default internal address, but I can't be sure, and it may have been changed.

---

### Post by bobhawkes on 2007-03-25
I found the solution (for me any way). As in the previous post its a DNS issue.

Here's what I did:

Go to System -> Admininstration -> Networking
Select the DNS tab
Delete the router IP address from the DNS table
Add your ISP DNS address to the table.

All works fine now.

Bob

---

### Post by flashbuntu on 2007-03-25
Thanks for the replies,

I tried the same and all is good now, cheers.

Firefox and updates all work, although having trouble with Evolution sending emails, hopefully my ISP can help me with settings.

again cheers for the reponses.

---

