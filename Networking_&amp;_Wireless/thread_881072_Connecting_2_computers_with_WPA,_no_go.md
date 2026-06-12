---
title: "Connecting 2 computers with WPA, no go?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by phenest on 2008-08-05
I have a wireless issue that by rights, should not happen (at least according to every 'expert' I've spoken to).

2 computers running either Ubuntu or Windows with a wireless connection to a modem-router. If encryption is not used, both computers can connect to the router together. Obviously, no encryption is not a wise choice, so encryption is set to WPA Personal. But now, only one computer can connect which is whichever computer is powered on first.  The other computer seems to be denied access. Individually, the computers connect successfully to the router, but the router does not like them both together. If the encryption is removed again, both computers connect fine.

I have seen this behaviour with several different computers, and several different routers. The encryption is set-up correctly, and yet only one computer is 'allowed access'.

Is their something I'm missing here?

---

### Post by jimv on 2008-08-06
Well this is an odd issue...hmmmm.

Does it happen with WEP or WPA2?  Perhaps try flashing the router with DD-WRT or Tomato firmware.
[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)
[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

What kind of router is it?

---

### Post by Tlingit on 2008-08-06
Have a look at the ip addresses. use the proper commands for renewing or changing them.

---

### Post by phenest on 2008-08-06
But isn't the router supposed to deal with ip addresses? And why is it ok when the wireless is not encrypted?

---

### Post by jimv on 2008-08-06
I'm thinking it could be a bug in your router, thus the idea to flash it with different firmware.

---

### Post by phenest on 2008-08-07
If it's a bug, then it's in 4 different routers. My old Belkin and my new Belkin (old one packed up), my sisters Belkin and my mums 3Com. I'd rather not do any flashing.

Could this be a setting that I've overlooked?

Perhaps someone could give me a rundown of how they set up their own wireless encryption for 2 laptops, so I can see if there's something I've missed. (Done as if the router is new and on factory settings.)

---

### Post by jimv on 2008-08-07
This is just weird then.  I have 2 laptops and my desktop on wireless that is secured with WPA, as well as another machine hardwired into the router.  Everything works fine, so your setup SHOULD work.

After some thinking...

The only thing different between mine and yours is that you are using two Ubuntu machines on the wireless, and I'm only using one.  When I get home, I'll install Hardy on my desktop and try connecting that and my Ubuntu laptop to the wireless and see what happens.

---

### Post by phenest on 2008-08-07
> **jimv said:**
> The only thing different between mine and yours is that you are using two Ubuntu machines on the wireless, and I'm only using one.  When I get home, I'll install Hardy on my desktop and try connecting that and my Ubuntu laptop to the wireless and see what happens.

No I'm not. This happens with any combination of Ubuntu/Windows.

---

### Post by jimv on 2008-08-07
Ah, I thought the problem only happened with the two Ubuntu machines hooked in.  So it happens anytime you use two computers, regardless of OS?

---

### Post by phenest on 2008-08-08
Could this be anything to do with the DHCP server and the Lease Time? If the lease time is set to forever, then each computer has a fixed IP address on the router. As I switch each computer on, shouldn't the DHCP server assign new IP addresses? I ask this, because the computer that won't connect says it's trying to obtain an IP address. Perhaps I could use static IP addresses instead?

---

### Post by phenest on 2008-08-11
I have decided to assume that all computers and routers in all of my above mentioned set ups are working correctly, as far as hardware is concerned. This leaves the possibility that a setting (either OS or router) needs to be tweaked. After some trial and error, I have discovered something that improved my mum's set up. They have 2 laptops that connect wirelessly. One laptop running Ubuntu and the other running XP. I found that by changing the channel setting on the router from 'auto' to '7', both laptops can connect with encrypted wireless, with only one issue. The issue being that if the XP laptop connects 2nd it takes 2 attempts before it connects. The Ubuntu laptop seems to have no problems.

---

