---
title: "Connection &quot;hanging&quot; problems"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by kurraider on 2006-12-23
I am having some problems with my web connecting seeming to “hang” for 10 to 20 sec when I try to access any website.  For example, if I was to try to access ubuntu.com in firefox I would see “Looking up www.ubuntu.com” for about 20 seconds then the page would load like normal and when I visit any further subpage of ubuntu.com the page would load in normal time (but if I would try to visit a different site like ubuntuforums.org, the connection would hang again).  This occurs both I'm using wireless and when I'm connecting via Ethernet and I do not have this problem when I'm using any Windows OS (so it's not an ISP problem).  My ISP is Verizon DSL and I'm using  Actiontec GT704WG wireless router.

Thanks in advance,
-kurraider

---

### Post by geekygreen on 2006-12-23
I had a similar problem, except my system would not communicate with the internet at all.  I have a windows based laptop which worked fine on both wireless and Cat5, so it was not a DSL or router issue.](*,) 

My problem kept appearing after about 24 hours being on....and after resting overnight, would work fine for another 24 hours.  

I was able to log onto both the router and the DSL modem using the Ubantu machine, however.  

If you can log onto the router and/or the modem, the problem may be the syustem is forgetting the DNS server address, and has to reacquire it.  After doing so, things work fine.

I solved my problem by adding a DNS server address in Network settings for my network card in Ubantu.

First, log onto your modem or router and browse around until you find the DNS servers being used.  Some sort of STATUS command should give you that info. 

I use the Gnome desktop.  

Choose System/Admin/Networking.  Select the DNS tab.  

Manually enter the DNS servers you found here using the ADD button.

I do in fact have a dynamic setup, but I am making  a gross assumption that the DNS server wont change very often.:confused:   It seems to have fixed my system from hanging.  If someone has a better fix, I would be glad to try that out also!

Updated:  you might look at this[ posting]("http://www.ubuntuforums.org/showthread.php?t=323747&highlight=firefox+2.0"), also.

---

