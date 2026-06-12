---
title: "Gaim MSN/Yahoo workaround for proxy!"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Flavian on 2006-10-04
Hi guys!
I had some problems with the university Network as posted in my first post here: [http://ubuntuforums.org/showthread.php?p=1579173#post1579173](http://ubuntuforums.org/showthread.php?p=1579173#post1579173)
But now it's solved, and I face the next problem.
Since the University uses a crappy proxy (I didn't figure out any benefit of a proxy yet, the cons overweigh the pros!) Anyways...
I got ICQ working through setting the normal ICQ Port (5190) to 110 which is the POP3 port. That works flawlessly :) hehehe...

But MSN and Yahoo don't. Using the Proxy server doesn't work.
And using Port 110 does not either (maybe because ICQ uses it already?) Is there any workaround to my problem. I hate not being able to do everything I want and then pay for my Internet connection!

Thanks in advance
Flo

---

### Post by Flavian on 2006-10-04
Here is a little update!
I found out that the freakin network does not allow me to send stuff over the SMTP port!!! ](*,)  That is SO freaking STUPID!
Cause pop3 is allowed. What do I use pop for if I can't use smtp as well...
If anyone of you guys knows a work around on this I would be more then glad!!!

Thanks so much in advance
Flo

---

### Post by weiersc on 2006-11-19
My problem is very similar. I cannot connect with GAIM/aMSN client even though I know that the Windows messenger on the Windows box in the room next to me is able to connect through the same proxy (10.0.0.35:3128).

I was able to get Google-Earth to connect by editing /etc/bash.bashrc. (But only when I run it from the command-line, not from the menu).

But still no luck with GAIM/aMSN.

I would also love to know if there is a way to solve this.

---

### Post by Flavian on 2006-11-22
Any help?

---

### Post by huwnet on 2006-11-23
> My problem is very similar. I cannot connect with GAIM/aMSN client even though I know that the Windows messenger on the Windows box in the room next to me is able to connect through the same proxy (10.0.0.35:312

This is because Windows Messenger supports a http protocol for firewalled clients

In GAIM goto Accounts > Choose edit on an MSN client > Advanced tab > Tick http method

---

### Post by Flavian on 2006-11-27
That brings up an error:
> 
Unable to authenticate: Unable to connect


:(

---

