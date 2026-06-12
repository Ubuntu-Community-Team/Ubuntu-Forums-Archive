---
title: "Wireless connects to internet but won't load web pages properly"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by epibas79 on 2008-06-12
I am a new ubuntu user with very little knowledge of how it works. The wireless hardware I'm using to connect to the internet is a Netgear WGT624 v3 wireless router and the wireless card in my laptop is an Intel PRO/Wireless 2200.  I am able to connect to the internet through the wireless router, but many of the webpages I try to access don't load properly or don't load at all when I am connected wirelessly. It just sits there as if it was loading indefinitely.  Some sites work flawlessly and others have this problem.    
      When I connect my laptop directly to the modem I have no problems downloading any web pages so I know it's an issue with one of my wireless components.  Has anyone else had similar issues?  Also, I don't have any problems connecting to the internet or any web sites from the windows partition on the same computer.              
      I really want to convert over to ubuntu because I am sick of Windows but if I can't resolve this issue I think I'll have a hard time switching.Could someone help me???

---

### Post by rlzyoner on 2008-06-12
Have you tried pinging both the probem sites and the router whilst the issue is occuring.
Example, you cannot load [www.google.com](www.google.com)
Open a terminal and type the following
ping -c 4 [www.google.com](www.google.com) (-c 4 is the number of pings)
ping -c 4 192.168.1.1 (replace the 192.168.1.1 with the gateway address of your router)

If you are not getting replies, this means that your computer cannot contact the destination (router or website, depeding on which you have attempted pinging)

Also, check your firewall configuration (if any)

---

### Post by epibas79 on 2008-06-12
I tried pinging a few sites and the router and they all worked except for one website.  Usually what happens is it will load the opening page of a website, but then when I click a link to another page in the website it will not connect.  The one site that didn't respond when I pinged was facebook. However, if I clear my cache, cookies and other private data then the first page of facebook will open and it will let me sign into my account, but then when I click on other links it will not connect any further.  There are a couple of other sites like this, but most sites work fine.  Like I said, all the sites work flawlessly when the computer is either connected directly or if I connect through windows.  Any other suggestions??

Update:  I had to post this reply from windows because my computer wouldn't load the message wirelessly from ubuntu. (It just kept loading indefinitely like with the other sites.)

---

