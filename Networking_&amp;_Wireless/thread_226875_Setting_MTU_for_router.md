---
title: "Setting MTU for router"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by dgermann on 2006-07-31
Hi--

I have a Linksys router, WRT54G, and having trouble connecting to get my compuserve POP3 mail (pop.compuserve.com).

I am suspecting the MTU setting in the router.

How can I test for the right MTU setting?

In Windows, the procedure is to use ping pop.compuserve.com -f -l 1462 --but I suspect that for linux we'd need to use -M somehow.

Any ideas?

Thanks!

---

### Post by gunderwood on 2006-07-31
man ping 

will tell you all the flags that you need.

I think it's -s to set the size, but check it out for yourself just in case ;)

---

### Post by dgermann on 2006-07-31
gunderwood--

Thanks!

Already checked that out, but it does not make sense to me. Any idea where I can get an English translation? ;) 

Thanks, gunderwood!

---

### Post by gunderwood on 2006-08-01
ping -M do -s 1462 pop.compuserve.com

Is the linux equivilant of the windows command

ping pop.compuserve.com -f -l 1462

This instruction sends a ping 1462 bytes in length (I think there may be some other header data too, but I'm not really sure. If anybody else could confirm that'd be great :) )and the '-f' (in windows) or '-M on' instructs ping to not allow the ping packet to be fragmented.

Hope this helps. Learning how to understand Man pages and Usage statements will really help you if you plan on using the command line regularely.

Greg

---

### Post by dgermann on 2006-08-01
Greg--

Many thanks! That helps.

Here is what I did, but not sure I am going about this correctly. I think I need to keep going up in commands, right?

Do I run this against the pop.compuserve.com address or against the router address, 192.168.0.1?

Did your command at 1462 and no packet loss, 1472 no packet loss, 1473 and above "Frag needed and DF set"--which all says to me that I need to use 1500 MTU, which is where the router is set.

But I cannot connect to pop.compuserve.com to get my e-mail. I suspect the router, because with it out of the mix, I can connect to get the e-mail reliably. Not sure what else to try other than mtu.

> Learning how to understand Man pages and Usage statements will really help you if you plan on using the command line regularely.


Yup, I agree. It has sure helped me. I prefer command line to gui usually. But in this case, the man pages are a little more greek (geek?) than I was able to decipher. I am glad to have someone like you who has been through it more than I have. Thanks, Greg!

:- Doug.

---

### Post by dgermann on 2006-08-09
The saga continues:

Monday the Linksys tech told me to try a firmware upgrade. I did and lost all connectivity. After working with it for 3 hours till 1:20 am or so, the tech gave up, gave me an rma to return it.

Today I bought a new one, the same model WRT54G, but version 6 instead of version 5. Same problems, not quite as severe: can connect to CIS via telnet or mail client about one in 8 tries.

It might be easier for me to dump CIS entirely and go through the pain of notifying all my correspondents of my new address than to continue this pain. I do not seem to have difficulty getting Comcast e-mail.

One guy over in PC Hardware forum of Compuserve writes--

===clip

The problem lies in the CIS network and how CIS does load balancing. It's been a problem ever since CompuServe first exposed it's mail servers to the Internet and opened up to POP3 in addition to its proprietary old mail system.

The load balancing servers aren't always successful in directing your connection to an available host inside the network. My suspicion for various informal tests over the year is that the CIS internal network is overly congested.

I can duplicate Doug's poor connection record with mail clients on Linux, OS X and Windows XP.

===you are whole

I don't know what to do. But I am getting hints, huh?

Thanks for all your help!

---

