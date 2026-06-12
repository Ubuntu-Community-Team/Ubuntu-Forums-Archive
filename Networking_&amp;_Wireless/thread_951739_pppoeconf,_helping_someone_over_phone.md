---
title: "pppoeconf, helping someone over phone"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by chaslinux on 2008-10-18
Hi all. I'm trying to help someone set up their Linux box for a Bell Sympatico connection in Ontario. I thought Bell was now providing people with hybrid modem/routers, but this person doesn't appear to have one. I've guided them how to set up their connection using:

sudo pppoeconf

The problem is they seem to have to do this every time they shut off the computer. I thought once pppoeconf was run once you didn't have to set up the connection again?

Cheers,

C.:popcorn:

---

### Post by Rosycode on 2008-10-19
Dear Team,
          I am with Ubuntu since 2 day. I am trying to connect with pppoeconf. I am setting the same password and username that I use in Windows. However, I get CHAP and PAP failure. I checked the CHAP and PAP secret files and they have the "username" * "password".

I am using Ehthernet modem. I am getting connected as it correctly detect IP and DNS. But its during my user verification that causes the problem. 

Is my ISP not using CHAP verification and uses some other handshake protocol ? Please help as I cant breathe without internet !!! 

Regards
Rosy

---

### Post by superprash2003 on 2008-10-19
to connect and disconnect you need to type pon dsl-provider and poff respectively..

---

