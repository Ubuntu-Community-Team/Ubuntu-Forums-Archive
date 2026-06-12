---
title: "adsl troubles with ubuntu6.1"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by gudy1024 on 2006-12-09
Men, :) I'm quite new to ubuntu but got some linux
(rh5.0) experience in the past,now quite a while ago..

this is the situation :
I have a home network with 4 pc's, connected to a 4
port adsl router
On my own pc(1 of the 4(the 3 others have win2k and
xp)) I've just installed ubuntu(6.10)from the "life
cd" on a brand new harddisk,well partioned and so on

startup of ubuntu very smooth :) I can't see any
trouble,applications running well and so on

BUT internet acces..I can't get it right
I get a message, "there are 25 updates available" so
that means ubuntu has connected to a server somewhere,
but the download fails always
Also if I start firefox, I can't load any page
(timed out every time)

the point is I don't know where i must find the
solution to this problem,bc the other pc's connection
to internet are good

is ubuntu(6.10) using differend protocols in compare
with windows? how do I debug my system? where must I
look and for what?


Thank you so much for your help

Gudy

---

### Post by bscbrit on 2006-12-09
What error message do you get when you try to update?

What fault finding have you already done?  Can you ping your own IP, your named computer, another computer on your network, your gateway, and outside IP?

If you are not sure what to do, we can always start at the beginning.

---

### Post by handy on 2006-12-10
Hopefully [**_this how-to_**]("http://ubuntuforums.org/showthread.php?t=282034") will solve your problem.

---

### Post by gudy1024 on 2006-12-11
Thank you so much Handy :) the trick with firefox about:config was really  the solution :) firefox runs fine now

Downloads from Synapsis are still giving errors of "cant connect" ,wel I see the number of available downloads increasing, but downloading....nothing :) 
I will search in other posts for this trouble... (maybe IPv6 is also disabled in the synapsis configuation, but I could not find it out yet)

Thanks, your help was very much appreciated
Gudy

---

### Post by handy on 2006-12-11
I'm glad it was some help to you. :) 

Did you try prepending your isp's DNS addresses?  That may still be a solution for your existing problem...

All the best!

---

