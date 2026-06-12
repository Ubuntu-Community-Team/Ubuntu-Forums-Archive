---
title: "Remote Access"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-02-26
This may not be the best place to ask this lol as its a windows question.  Yes sirs, I came to a linux forum to get help with windows... you can't beat that eh?

Remote Access in linux
--------------------------------
1) install ubuntu
2) setup nx from no machine
3) set up multiple linux accounts

From the above multiple ppl can use one system at the same time remotely interacting with say a database thru a client application which would provide all the goodies of record locking and update serailization, so that everything stays good and synchrnoized.


Remote Access on Windows XP Pro
--------------------------------------------
1) install windows
2) enable remote desktop
3) set up multiple windows account

BUT only ONE person can assess the system at a time??? Why cant i have it like the linux? When one person logs in remotely it tries to log the person currently logged in out.

Can anyone tell me how I can have multiple ppl logged into a windows machine (xp, server 2003) where multiple ppl can be in and using it at the same time.

Thanks.

---

### Post by dca on 2008-02-26
Didn't think you could do that using the RDP in WinXP.  Geez, if you could access multiples at one time there'd be no reason for MS charging so much for CALs and their server OSs...
 
The WinXP Remote Access function uses RDP versus VNC to make connection.  If someone is using the XP client your logged in to they can just log back in and kick you out, I don't know of any other way it works...

---

### Post by sefs on 2008-02-26
Which means that 2003 server/xp cannot support multiple logged in clients to one machine?

---

### Post by Eiríkr on 2008-02-26
I think this is the key:
> Geez, if you could access multiples at one time there'd be no reason for MS charging so much for CALs and their server OSs...
Remember, kids, MS is all about making *money*, not software, and not making things work.  That's why OSS is such a thorn in their side -- it's all about the tools and the ability to get things done.  

You could try googling around to see if there are any VNC possibilities for Windows that would work for you, but if you're stuck with RDP, I think that's it -- you're just plain stuck.  Happily, VNC does exist for the Windows platform.  For instance, from the [RealVNC website]("http://www.realvnc.com/vnc/how.html"):
> The system allows several connections to the same desktop, providing an invaluable tool for collaborative or shared working in the workplace or classroom...

Good luck,

Eiríkr

---

### Post by sefs on 2008-02-26
Thank you my good fellow!

---

### Post by sefs on 2008-02-28
Contacted RealVNC and they enterprise version does not even support multiple concurrent users of the same system.  This is a sad day in history.

---

### Post by Eiríkr on 2008-02-28
Then what the heck does that line on their website mean?  Sheesh.  No doubt something put together by Marketing with faint regard for reality.  Oh well.  Thanks for posting to let us know.  

Cheers,

Eiríkr

---

