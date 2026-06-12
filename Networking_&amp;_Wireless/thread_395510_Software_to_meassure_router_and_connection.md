---
title: "Software to meassure router and connection"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by timmahhny on 2007-03-28
In a nutshell. 
 For the past three years we have had problems with our "highspeed" internet connection. The local hick company has been here well over a dozen times, and in that period had tried to convince us that the constant low speed, the dropping of the internet, both wired and wireless, was due to a virus or something on our end. 
 
 Six months or so ago a new tech came out and changed the line between the house and pole due to a very bad connection at the pole. This did not solve the problem.

 They claim we are the only ones on this road that are having a problem. I know for fact two other people are also experiencing the same problems we are.

 Their provider is Parasun whom I talked to along with the co-owner of our internet service provider on the phone. I have been researching this for three years and it comes down to maybe- Parasun DNS service. 

 I would like to get some sort of software installed on my Linux machines that can measure the amount of times my router attempts to get an IP address. This is the problem according to Parasun- the router or modem is sending out 100 requests per day for an IP Address.

 From what I understand, if the "signal" is weak or interrupted the router, which is a Linksys Wireless 54G, will request a new IP Address. 

 I have replaced the Linksys with a D-Link and that made things even worse. I would be off line for days and even the wired connection to one computer would lose connection. At least with the Linskys I would have limited connection, like dial up speed. 

 I am writing this is a hurry. The local company placed a laptop on our line in the house and will be here sometime today to pick it up. They have a program that I guess measures how many attempts the router is requesting an IP address. I would like to verify this and add any additional information, so I can remove our house from the equation. (Not for today but for future reference)

 Any information, suggestions, or help would be greatly appreciated. 

Thanks 
Timmahh

---

### Post by Scunizi on 2007-03-28
How 'bout using someone elses DNS services?

---

### Post by Mr. C. on 2007-03-28
I'm reading this as your router is frequently dropping its link with the provider, and when it regains its link, it of course must request an IP address.  So the number of IP requests is being used to estimate lost connections.

The modem establishes a link with the hardware at your provider's end.  Once that link is established, the modem is free to transmit its request for IP information.  This is greatly simplified, but that's the basic idea.

A lack of a DNS server will not cause your modem to drop link.

I am confused - you indicate your neighbor has Parasun for broadband, but it sounds like you do not.  It would therefore not make much sense to use their issues as a basis for measurement of your own issues, unless the unless the carriers are the same.

Without the proper technical background, and without creating a piece of hardware/software that can monitor the signal between your router and your line, there will be little you can do.  You cannot measure the WAN side of your link with your LAN hardware. 

DSL and cable providers are notorious for oversubscribbing a line, and advertising higher speeds than customers actually get.

Hope this helps a little,
MrC

---

### Post by timmahhny on 2007-03-29
> A lack of a DNS server will not cause your modem to drop link.

According to [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) Speak Easy a slow DNS server will simulate loss of connection and very slow speeds. 

> I am confused - you indicate your neighbor has Parasun for broadband, but it sounds like you do not. It would therefore not make much sense to use their issues as a basis for measurement of your own issues, unless the unless the carriers are the same.

 Yes we all are provided internet connection by the same hick provider, who in turn gets their connection from Parasun. Parasun in the past has had many problems with their DNS service. 

Since this tech guy from Hickville did not show up today, I will attempt to clarify what is going on a little better. 

 The tech placed a second router in our house, after he replaced the line from the pole into the house and replaced the old Motorola with a new Motorola Surfboard router. The second router is a Linksys router. The Vonage line is hooked up to the Motorola router and everything else is hooked up to the Linksys router, and we still have problems. 

> Without the proper technical background, and without creating a piece of hardware/software that can monitor the signal between your router and your line, there will be little you can do. You cannot measure the WAN side of your link with your LAN hardware.

Is there not some software that I can get a log of what is going where, how often the router asks for an IP address, et..? I don't want to "measure" the signal per say, just figure out how often something is connecting and what might be the cause of it. 

 Just because I don't think I have a virus, and I know I don't as all machines in the past three years, and these past three months have all been securely wiped and new OS installed on them, even the one Window Machine. So I am pretty confident it is not a virus, but something else. 

This leads me to what the tech from Parasun was saying: Something about microfractures, which is caused by a slightly damaged cable, which will cause "feed back". He mentioned something about a signal taking 30 ns when it should be no higher then 20 ns. I don't know what he was talking about and never have I ever heard of a "microfracture". I guess some body from Japan stumbled upon this theory. 

 This post is getting too long.
Thanks for everyone's input and quick replies. I have never been on a forum where people post so quickly and with very poignant information. 

Thanks for everything
Timmahhny

---

### Post by Mr. C. on 2007-03-29
Yes, slow DNS servers will cause problems with name lookups, and uses will experience intermittent internet connectivity, slowness, or believe that the internet is gone.

But DNS failures will *NEVER* cause your cable or DSL modem to lose its link connection with your provider.  You gave us data that there are 100+ requests for IPs, indicating a possible loss of link.

This has nothing to do with DNS.

A Windows virus will  not cause your cable or DSL modem to lose its link connection.

The "tech" you talked with may or may not understand the physical properties and requirements for DSL or Ethernet.  Nonetheless, they exist and are very real.  Some areas are simply unable to obtain satisfactory broadband, essentially due to hardware that is outside of specification.  Crimped or lengthy (greater than 300'ish ft) Ethernet cables will cause problems.  Wire pairs improperly twisted will cause feedback problems, improperly connected RJ45 plugs will cause problems, etc. etc.  In fact, much of the Ethernet, Cat-5, Cat-6 specs are all about the electrical properties, tolerances, and physical requirements.

There is a very easy way to determine how often your connectivity drops, packet loss occurs, and time taken for packet delivery to remote sites.  Its called "traceroute".  You simple run periodic traceroutes to a remote site, and monitor the loss, time, and connectivity over time.

If your modem provides a web interface, and logs, you may be able to glean some information from it.

I feel for you - poor internet connectivity can be worse than none at all.

MrC

---

### Post by timmahhny on 2007-03-29
Mr. C thank your for your thoughts and inputs.
 It gives me a new insight to what it takes to deliver "highspeed" to remote areas or for that matter anywhere. I have a new appreciation, I guess, for these people.
 As most people, we don't think of how it works, just as long as it does. 

 I have been told that our internet provider will be leaving Parasun for another provider so maybe that will help. 

Mr. C thanks for explaining the DNS in a way that anyone can understand it. 

 I will just have to deal with this until well, we switch to satellite, if we do. We went with Vonage because the normal phone bill here was 80 dollars a month and if we do go to satellite we will not be able to use Vonage. 
 
If we someone down the road and across the street that was considered long distance. We would routinely have phone bills as high as 120 dollars and is just too much. Cell phone is not too great up here either. 

 With that said, it still beats living in the "city". 

 Thanks for all of the input.

 Timmahhny

---

