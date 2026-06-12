---
title: "[SOLVED] Router problems"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by LeadHop on 2008-09-02
Hello - I looked around the forums but simply couldn't find a question that was like mine! 

I'm having trouble connecting to the router, wireless or wired.  It was working fine, then suddenly stopped transmitting any information.  I don't have problems directly connected to the cable modem when i plug in, but when it goes through the router, it stops sending any information.  I didn't fiddle around with anything, it just suddenly stopped working.  I've checked the modem, connections, wires, and the router. 

Edit: the problem seems to be coming from the router - i can connect to every other source (school wifi, directly from modem, etc.) except from the router.  what can i do?  is there a way i can check for the password to the router?  thanks!

---

### Post by jigsaws on 2008-09-02
What model of router? Is it works when you replug the UTP? Any log entires? Does other computer still connected when it happend?

Try:
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling
from root (i.e. after "sudo su")

---

### Post by Dark Hornet on 2008-09-02
have you tried a different router...the router you are using could simply be bad.  I have had it happen to me in the past.  To answer your other question...usually there isn't a way to check for the password, but to get to the log in screen, usually you need to go to 192.168.1.1, or .10.1 in your address bar.  You can try reseting the router...on some models that will reset the password back to the default of "admin", or "linksys", etc...Good luck!

Darkhornet

---

### Post by LeadHop on 2008-09-02
thanks everyone!  I am using a linksys model.  Not sure on the specifics because i'm currently away from home right now, but i'm pretty sure it's not a hardware problem on the router's end, as my roommates are fine with their connections, hence my befuddlement :).  I'll look into my router via that 129 code once i get home.  Hopefully i can get it taken care of - my windows was having a problem as well!

---

