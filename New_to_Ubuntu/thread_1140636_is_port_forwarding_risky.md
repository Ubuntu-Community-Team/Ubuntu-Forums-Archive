---
title: "is port forwarding risky?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-04-27
I installed apache on my ubuntu computer to host a website, but I can't access it outside of my home network. so I will try using virtual server in my router and forward port 80 under my computer's static i.p so that people can access my website from outside my network. Is this risky to my computer and other computers on my network? (by the way, my computer is the only ubuntu/linux computer in our network, and all the rest are windows computers) i'm just not sure to enable it bacause i'm worried that some one could enter our network and steal credit card information and files etc... and also, every computer in the network exept for this ubuntu one has an inbound firewall with norton internet security 2009.

---

### Post by amingv on 2009-04-27
Every new service you open adds a new risk, no computer is protected 100%.

However this shouldn't be an impediment to use the services you *need*, after all if you can't use your computer for what you need to use it, what's the point of having it? As long as you configure everything OK, don't open unnecessary services and *don't* use this computer for daily work (optional, but I promote the "servers are not PCs theory), everything should be fine.

If you're really concerned about this, though, and if your router allows it, you may "divide" (so to say) your network and put your server in what's it's called a [demilitarized zone (DMZ)]("http://en.wikipedia.org/wiki/DMZ_(computing)"), leaving the rest of the computers with sensitive data under an additional layer of security; if your concern requires you to go this far I suggest you get counseling from someone specialized in network security, so he can study your particular case and decide what might work for you.

Hope that's of any help...

EDIT:
Is this a home or an office/business network, if it's the former case the DMZ may be a bit excessive.

---

