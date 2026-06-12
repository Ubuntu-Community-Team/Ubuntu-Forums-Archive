---
title: "Actually connecting to wireless network"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by walkingbeard on 2007-11-18
Hi,

I am using a Netgear WG111T to connect to a wireless network.  I have used ndiswrapper to successfully get my Windows driver working.  The card seems fine and can see the networks in my area, but no matter what I do, I don't get web browsing or anything else working.  The key is in the following format: L000l0l00, where L is a capital letter, l is a lower case letter and 0 is a numeral.  I'm thinking that the capital doesn't matter and it's a hex key.  The network's 'secured' by Open WEP.

I have tried changing the authentication settings in the network manager, but nothing works.  I can't ping the router.

Please can someone help?

Thanks.

---

### Post by rustybronco on 2007-11-18
[http://ubuntuforums.org/showthread.php?t=574474&highlight=WG111T](http://ubuntuforums.org/showthread.php?t=574474&highlight=WG111T)

and see kevdogs finest in my signature.

---

### Post by walkingbeard on 2007-11-18
Cheers dude, but that post wasn't really about my problem.  I did search for relevant posts earlier, but the only ones with my problem suggested using an alternative tool to connect, wifi-radar.  But that too has its problems, because it won't let me change the settings for any existing network. :-|

---

### Post by rustybronco on 2007-11-18
> **walkingbeard said:**
> Hi,

 I have used ndiswrapper to successfully get my Windows driver working.  The card **seems ** fine and can see the networks in my area, but no matter what I do, I don't get web browsing or anything else working.  
Thanks.  some people are having problems being able to see networks but are unable to connect because of the wrong driver being installed, 
as an example in kevdogs post that I have as a link in my sig.
>  How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line
In setting up their wireless connection for the first time, Im discovering many individuals having problems connecting through Network Manager or other GUI wireless connection tools. In fact my Network Manager is intermittently buggy, connecting sometimes and not others. This guide benefits all users in case the GUI tools are not working, and is useful for **testing a wireless connection** during initial installation of wireless drivers since it provides for good debugging output.
cheers, Dale

---

### Post by rustybronco on 2007-11-18
> **walkingbeard said:**
> Hi,

I The key is in the following format: L000l0l00, where L is a capital letter, l is a lower case letter and 0 is a numeral.  I'm thinking that the capital doesn't matter and it's a hex key.  The network's 'secured' by Open WEP.
Thanks. I use wep and I can use lower case or upper case, but I have never tried a combination of both.
***edit*** I just tried it with my network and yes it works using both upper and lower case at the same time.

---

