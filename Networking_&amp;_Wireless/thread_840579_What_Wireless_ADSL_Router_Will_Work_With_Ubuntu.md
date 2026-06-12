---
title: "What Wireless ADSL Router Will Work With Ubuntu?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by joshdudeha on 2008-06-25
Hello there.

I normally use a Speedtouch 330 to connect to the internet with Ubuntu.
But, after my hard drive breaking and re-installation of Hardy, I can't get it to work again.
  I am now using Mandriva, as it fully supports this modem without extra installation. But I really hate Mandriva, i'm waiting for the nearest opportunity to get back to Ubuntu, because it is amazing.

So...
I want to buy a wireless ADSL router, wireless because i'll be getting a new computer soon.

All I want to know is **_what router shall I get? _**

As I don't know whether it will be compatible with hardy or not.
Plus, I don't have a big budget to spend (£20-£35-ish)
And, how do you set-up a network with a Router on ubuntu?

And it has to be ADSL, as we have that kind of broadband.
Thank you for your help in advance

---

### Post by rickyjones on 2008-06-25
> **joshdudeha said:**
> Hello there.

I normally use a Speedtouch 330 to connect to the internet with Ubuntu.
But, after my hard drive breaking and re-installation of Hardy, I can't get it to work again.
  I am now using Mandriva, as it fully supports this modem without extra installation. But I really hate Mandriva, i'm waiting for the nearest opportunity to get back to Ubuntu, because it is amazing.

So...
I want to buy a wireless ADSL router, wireless because i'll be getting a new computer soon.

All I want to know is **_what router shall I get? _**

As I don't know whether it will be compatible with hardy or not.
Plus, I don't have a big budget to spend (£20-£35-ish)
And, how do you set-up a network with a Router on ubuntu?

And it has to be ADSL, as we have that kind of broadband.
Thank you for your help in advance

I'm not sure how your ISP has it all configured but in my neck of the woods (Michigan, USA) most of the ISPs use PPPoE for authentication to bring up the DSL line. They also usually provide a simple modem/gateway with a single ethernet port that usually takes care of this authentication (once it has been configured). 

For example: AT&T gives me this black box that I plug my computer and my phone line into. I connect to it over the web interface and type in my DSL username/password. It then connects me to the internet and I never have to touch it again.

I can then plug a router into the ethernet port and plug my computer into the router and have it "just work." 

Does your ISP operate like this? If so then you should be able to pick up a standard DSL modem and use the same configuration that I do.

To answer the wireless question: I use the ISPs modem/gateway to get the initial DSL which is then plugged into a wireless router. The router's WAN side gets the true public IP address from the DSL provider and provides internet to my laptop and desktop via NAT.

I really hope this helps!

Sincerely,
Richard

---

### Post by joshdudeha on 2008-06-25
Well, I configured my ADSL usb modem over PPPoA.
As it plugs into the phone line.

But, the router will plug into the ethernet on my computer, then down a phone line.
Not through like a cable box.

Hmm :]
Tjhanks for the help

---

