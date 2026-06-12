---
title: "msn.com is the ISP - can it work?"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Bartender on 2007-08-05
Good morning!
Some friends are using msn.com as their dial-up ISP.  I'd like to lug a Feisty PC over to their house and show them what Linux looks like.  I'd really like to go online from their house.  

I've searched on the Ubuntu Forum and googled it, but all I come up with is hundreds of threads about instant messaging.
I don't care about IM, I just want to know how hard it is, or if it's even possible, to dial in to msn from Ubuntu.

Can anyone please tell me so I don't look like a dope in front of them?   :)

EDIT: I've been bugging them for months to drop MSN, but you all know how people are resistant to change...

---

### Post by HereInOz on 2007-08-05
Unless microsoft deliberately block log-ins from Linux machines, you should be able to head over there, with your modem attached, and something like GnomePPP installed, get the phone number for the connection and make it happen.

You will need to install a dialler (like GnomePPP) first, if you haven't already done that, and then run setup in GnomePPP to detect the modem, and the rest should be fairly straightforward.

I have never dialled up to msn, so no idea if there are any special requirements, etc, but a PPP dial up connection is the same regardless of what OS it comes from.

---

### Post by _duncan_ on 2007-08-05
I just looked up the MSN dial-up web page. The thing that worries me is the presence of the MSN dial-up accelerator. This is probably some sort of windows-based compression technology a dial-up user will have to use to connect to their service.

Unless there is a linux equivalent for this accelerator software, or if they allow users to dial-up using the default dial-up utilities in windows without the accelerator software, then it's probably a no-go for ubuntu.

---

### Post by Bartender on 2007-08-05
Hmmm, yeah, the website doesn't say anything about paying more for "accelerator".  Just like MSN to offer something free if the freebie keeps everyone else off their playing field.

Oz, I've got gnome-ppp installed. Will just wipe the previous entries, type in the new, restart the PC (that seems to make a big difference) and try it...

---

### Post by HereInOz on 2007-08-05
Hmm, yes the Accelerator could be a problem.  Perhaps it is a Windows only application which does the dialling and connection.  

If you are able to, I would check it at home first to avoid the proverbial egg on the proverbial face if it doesn't work :-)

---

### Post by Bartender on 2007-08-05
Hi, Oz -
I hadn't thought of that.  If they trust me with their username/password, then stay offline, I could take a shot at it from home.  I'd be able to think more clearly without people hovering over my shoulder.

Good idea!

---

