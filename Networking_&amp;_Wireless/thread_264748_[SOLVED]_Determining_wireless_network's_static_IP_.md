---
title: "[SOLVED] Determining wireless network's static IP range"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2006-09-25
Hello Ubuntu Team, 

Does anybody happen to know a tool/way that helps determine the IP range of wireless networks that use static IPs?

The reason why I am asking is that a lot of wireless network around me deemed "open" seem to use fixed local IP addresses, so I cannot hook up via DHCP. So in order to speed up the process of connecting to those alien networks, a tool would be nice that reveals the gateway's IP address.

TIA...

---

### Post by Sarisar on 2006-09-25
First and formost.  This is illegal in some countries!  Just because someone has left a wireless port open does not mean you can use it, just like leaving your front door open doesn't mean people can come in and use your house.

Having said that, try searching for wardriving or looking up airsnort or similar programs.

Yes I have tried to hack my own wireless networks to see how secure it was, but haven't done so under linux because of crappy broadcom drivers I can't quite get working.  So I can't recommend anything specifically for linux.

Another thought occurs.  If these are people just setting up their machines and not putting any security on them then they may have the default, which would probably be the router being 192.168.0.1 or 1.1 and running for 50 addresses or 100 which are the defaults I've seen.

Hope that helps, and remember it may be illegal so if you get arrested do not blame me!

---

### Post by wieman01 on 2006-09-25
> **Sarisar said:**
> Hope that helps, and remember it may be illegal so if you get arrested do not blame me!
I am more than aware of it because IT security is part of my job. :-) That's exactly why I am asking because we're about to assess my company's network security.

No, Airsnort, etc. won't help. And the default settings usually don't help either, because static IP is not default so if somebody has gone from DHCP to Static IP there is a pretty good chance that this person has changed the default IP range as well.

BTW: It's not deemed illegal to make use of a network if somebody leaves the network open. Some do that on purpose so as to let others have a "free ride". Which countries are you referring to?

---

### Post by Sarisar on 2006-09-25
The US and the UK I believe.  Probably Canada and Australia also.  My understanding of it was that if you log onto their open wireless you are going onto their network which is trespassing, basically (well the techie version of).
Oh and [here]("http://www.sptimes.com/2005/07/04/State/Wi_Fi_cloaks_a_new_br.shtml") is a story of someone being busted for connecting to an open wifi connection (though it doesn't say he was doing anything illegal on it).

---

### Post by NetworkGuy on 2006-09-25
Once you are on one of these networks, you can use Ethereal to determine source and destination IP addresses.  I'm not sure if you need to change to monitor mode however..

---

### Post by wieman01 on 2006-09-25
I was more talking about finding out about their IP range without having to connection to it. Is there any way?

Sarisar, 

It's definitely not illegal in Europe. There are public wireless networks & people (also restaurants, etc.) leave the open on purpose so that others can take advantage of it. I don't think it's illegal to use them, this would defeat the purpose of open networks.

Breaking into someone's network by cracking the keys is definitely a different story though.

---

### Post by Sarisar on 2006-09-26
[It's illegal in the UK according to the beeb]("http://news.bbc.co.uk/1/hi/technology/4721723.stm")

I'm not trying to argue with you, honest :)

---

### Post by wieman01 on 2006-09-26
> **Sarisar said:**
> [It's illegal in the UK according to the beeb]("http://news.bbc.co.uk/1/hi/technology/4721723.stm")

I'm not trying to argue with you, honest :)
Ok, this is also not the point of this thread. In all honesty I was more looking for a tool that helps me with my work (IT security auditing).

So I think we're on the same page. Any idea?

---

### Post by Sarisar on 2006-09-26
Well some programs (I should point out most of these I've not tried) are:
Ethereal, ettercap, airsnort (as mentioend before), snort.

For windows there is a nice program called cain.

I'll see if I can find out any more and let you know but I'm wireless-less (i.e. I do not have a wireless connection here) so I can't try any of these out.

Let me know what programs you find useful - it's a kind of hobby of mine to know how to break into networks, and therefore by extension know how to protect yourself against those attacks.

---

### Post by wieman01 on 2006-09-26
> **Sarisar said:**
> Let me know what programs you find useful - it's a kind of hobby of mine to know how to break into networks, and therefore by extension know how to protect yourself against those attacks.
Great, I am talking to the right person. A paranoid just like me.

I use WPA(2) which is PSK with AES (CCMP, RSN). Thought about EAP instead of PSK, but I think that's a bit over the top for personal use.

I'll let you know how it goes. Will try some of these tools.

---

### Post by tagra123 on 2006-09-26
Wouldnt a simple ping script help?

Ping 192.168.1.1 through 192.168.1.255

Any that answer are used any that do not are open.

Would this be a simple way to check?

---

### Post by wieman01 on 2006-09-26
> **tagra123 said:**
> Wouldnt a simple ping script help?

Ping 192.168.1.1 through 192.168.1.255

Any that answer are used any that do not are open.

Would this be a simple way to check?
Yes, if you are connected. But I am looking for a solution that detects the IP range without having to connect to the network. That's because if you don't know the range, you just CAN'T connect in the first place. :-)

---

### Post by tagra123 on 2006-09-26
This grabbed my attention I may need to follow this thread.

I have a couple of questions for my own education.

1. FOR DHCP doesnt a request need to be sent to the router/dhcp server?
2. Don't most routers/servers send an error when two IPs try to connect to the same ip?

3. Is the range broadcasted?

---

### Post by tagra123 on 2006-09-26
I found this page;

Maybe an answer is here:

[http://www.wardrive.net/wardriving/tools](http://www.wardrive.net/wardriving/tools)

---

### Post by wieman01 on 2006-09-26
> **tagra123 said:**
> This grabbed my attention I may need to follow this thread.

I have a couple of questions for my own education.

1. FOR DHCP doesnt a request need to be sent to the router/dhcp server?
2. Don't most routers/servers send an error when two IPs try to connect to the same ip?
3. Is the range broadcasted?
Welcome!

1. Yes, the client needs to send a request but does not need to know the exact IP range. The DHCP server is waiting for such requests and releases IP addresses/connects when asked.
2. Do you mean two clients with the same (fixed) IP address trying to connect to a server? Yes, they could not. But this cannot happen with DHCP because the server/router controls the IP range.
3. That's exactly my question. I would think yes, it should be found in package headers that you should be able to capture somehow.

---

### Post by wieman01 on 2006-09-26
> **tagra123 said:**
> I found this page;

Maybe an answer is here:

[http://www.wardrive.net/wardriving/tools](http://www.wardrive.net/wardriving/tools)
Fantastic! If they don't have a solution, nobody else will I reckon. Thanks for that terrific link. Nice repository.

---

### Post by tagra123 on 2006-09-26
I found this too:

[http://sectools.org/tools2003.html](http://sectools.org/tools2003.html)

On this page this one looks real interesting

[http://www.packetfactory.net/projects/firewalk/](http://www.packetfactory.net/projects/firewalk/)

---

### Post by Sarisar on 2006-09-26
Oooh.. got me some reading to do :P

Cheers for the links people :)

---

### Post by wieman01 on 2006-09-28
I think I've found the right tool thanks to you guys: KISMET. It's in the respositories and even detects IP block/ranges. Unluckily I am not on a business trip and have not wireless networks around me so I can only confirm if this thing works when I get back home.

Give KISMET a try. :-)

---

### Post by Sarisar on 2006-09-29
> **tagra123 said:**
> I found this too:

[http://sectools.org/tools2003.html](http://sectools.org/tools2003.html)

[They have a 2006 one out now]("http://sectools.org/") and kismet is number 7!

---

### Post by seekyrr on 2006-09-29
I use Kismet my self and it works well for what you are asking.

In windows you can use a free wireless packet analazyer called Omnipeek personal

[http://www.wildpackets.com/products/omni/omnipeek_personal/overview](http://www.wildpackets.com/products/omni/omnipeek_personal/overview)

Seek

---

