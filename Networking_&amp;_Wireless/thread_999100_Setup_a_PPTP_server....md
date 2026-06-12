---
title: "Setup a PPTP server..."
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by pzhukke on 2008-12-01
Yo!

I'm sitting here and having some trouble getting my Poptop server to work.
You see, I can't connect to it and I don't really know if I've configured it correctly since I havn't found any good guide on the internet...

Anyway, here's is the scenario:
I want a VPN server running on my Ubuntu server which allows Windows XP machines to connect.
My server runs on a wireless connection.
There should be user / password authentication.

So do you have any good guide or tip or anything that maybe could be helpful, please respond! :)

//Eric

---

### Post by HermanAB on 2008-12-01
Hmm, sorry can't directly help you.  I'm just wondering why you want to set up an insecure VPN.  PPTP is broken and even Microsoft recommends that it should not be used.

I would use SSH (on Cygwin) or OpenVPN (cross platform).

Cheers,

Herman

---

### Post by pzhukke on 2008-12-02
Oh, I didnt know that...

Well you see, the reason I don't want to use OpenVPN is because you can only connect to a OpenVPN server via the OpenVPN software on your machine, I was kind of searching for some program where I could connect just via the regular VPN connection thing Windows have...

But if that's not possible I guess I'll return to OpenVPN then...

---

