---
title: "wireless connection gets lost"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Snam on 2006-11-11
Hello,

I've got a Dell inspiron 6400 laptop with an ipw3945 wireless module and Ununtu 6.06 LTS Dapper Drake. And a D-Link DI-524 wireless router.

I use the Gnome NetworkManager Applet 0.6.2. to get a wireless connection with my router.

Ever since I've got the above configuration working the connection gets lost one in a while. Even when the connection strength is strong (4 or 5 out of 5 bars). When that happens it isn't possible to reconnect.
A workaround to this problem is to pull out the electricity plug. And put it back in again. So the D-Link-524 resets. Then I can reconnect.
Now I share a wireless connection with my neighbours. So the workaround to pull out the electricity bug isn't possible anymore. (Because I can't get into my neighbours house). Besides that, I never want to lose my connection anymore. I just want it to work.

I've got two questions:
1.How can I solve the problem that the connection gets lost once in a while?
2.How can I reconnect to the D-Link DI-524 without the need to pull out the electricity plug?

I don't know if this is a hardware, or a software problem. If you know a solution, please let me know.

Thnx,

Snam

---

### Post by Snam on 2006-11-21
The cause might be the PSP (Power Save Polling) feature of my Intel Pro Wireless 3945 adapter (ipw3945) in combination with my D-Link DI-524 wireless router. See: [http://www.intel.com/support/wireless/wlan/sb/cs-006205.htm]("http://www.intel.com/support/wireless/wlan/sb/cs-006205.htm")

A workaround is: manually set the adapter to CAM (continually aware mode), which disables the PSP capability.

But I don't know how to do this in Ubuntu Linux... So I contacted Intel. 
They asked me "What is the current version of the Intel(R) drivers installed?"
I don't know that, so I asked Intel how I can see that. Intel responed with "Please note that how to questions on Linux* are not part of the scope of our support.  
Support is limited to installation issues only.
We would suggest you to contact the Linux Community  through the available Online Forums for assistance  on  how to look for the driver version installed in your system."

Therefore I've got these questions:
1. How can I see what the version of the current installed Intel(R) drivers is?
2. How can I set the adapter to CAM (continually aware mode) / disable the PSP capability?
3. What are other causes that can my wireless connection getls lost once in a while?
3b. What are solutions to these causes?
4. How can I reconnect to the D-Link DI-524 without the need to pull out the electricity plug?

Thnx,

Snam

---

