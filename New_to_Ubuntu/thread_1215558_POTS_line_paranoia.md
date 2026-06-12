---
title: "POTS line paranoia"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by mamut0o1 on 2009-07-17
Hello I would like for someone to explain this to me. I have a pots line which I'd like to use to dial in into a PC that's in my LAN (VPN connection). How secure would it be to send data across the POTS line? I'm wondering if "analog to digital" signal could be captured?

thanks alot!
Mamut

---

### Post by bryceowen on 2009-07-17
I'm no security expert, but I have been reading a lot on the subject.

Your question was a little vague, so I will attempt to answer the different aspects of it.

First, the 'analog to digital' conversion does nothing to protect or expose the data. It is simply changing the method of transmission to match the medium. Second, yes, the data can be intercepted over the POTS system (probably easier than other mediums). Third, how secure the data is is totally dependent on what security you implement in your VPN. You can lock the connection down like Fort Knox if you like, but keep in mind the overhead for the encryption/decryption at both ends.

tl;dr: Data security depends on your VPN configuration, not necessarily the transmission medium.

---

### Post by jonobr on 2009-07-17
If your in the US, Internet service providers and telephone operators are 
mandated by law to be able to identify a target and 'tap' what they are doing.
This is called CALEA and is a law designed by Congress, the DoJ and telecom department

In effect there are a couple of things, they can target your traffic on foot of a warrant, they can tap you based on what you do in your sessions, IM, Chat, web traffic etc. and do content filter and so called, deep packet inspection to trigger certain words, phrases or expressions.

Other countries are at varying degrees along the Lawful intercept road.
Western Europe have some similar requirements, Asia are developing their own.

If you setup a VPN, that too needs to be trackable and from a vendor perspective, that traffic is typically unaltered in that it is usually passed to law enforcement unaltered and untouched.

The mechanism used, (Pots, frame relay, ATM etc) is irrelevant,
the providers must be able to track regardless of protocol.

---

### Post by mamut0o1 on 2009-07-17
Thank You both for your reply; I have a better understanding now.

thanks!
Mamut

---

### Post by bryceowen on 2009-07-17
jonobr:
I was thinking more of a malicious third-party observer, not so much the gov't. But, in either case, they would still need to crack the encryption you place on the data.

---

### Post by jonobr on 2009-07-17
Hello


Agreed,

From a 3rd party perspective, the chances if you use encryption are minimal.

---

