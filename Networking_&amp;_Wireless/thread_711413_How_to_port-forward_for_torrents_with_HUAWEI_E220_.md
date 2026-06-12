---
title: "How to port-forward for torrents with HUAWEI E220 3.5G modem?"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Extreme Coder on 2008-02-29
So I was surprised I got my new Vodafone E220 working so easily with the driver Vodafone made, but I have one major issue: torrents.
I download a lot of torrents, so this is a big issue for me.

I can't find any port that is open for torrent programs to use, and I looked around the net for solutions, and I can't find any.

Anynone knows which ports are open on Huawei E220s or how to open one?

Also, I just wonder, but how good is your modem for online gaming? I get pings from 100-300, so I'm just wondering ;)


Thanks!

---

### Post by anaconda on 2008-02-29
The e220 doesn't have a firewall, so it doesn't close any ports!!

BUT many ISP:s have closed most ports. I have the Huawei E220, and I just found out that my ISP has closed almost all ports!?!?!?!?##? 

PS. My InternetServiceProvider is Sonera, hope you have better luck with Vodafone.

You can use some porttesters to find out which ports your ISP has left open for you eg:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Select the option to scan 
"All service ports"
when the scanning has been done the report will also have instructions on howto detect which ports are closed by the ISP:

Oh, I decided to copy it here anyway...

> Detecting Ports Blocked by Your ISP

Internet service providers often block specific traffic entering their network before it reaches their customers, or after leaving their customers before it exits their network. This is sometimes done to block the exploitation of common security vulnerabilities, and sometimes to prevent their customers from offering proscribed Internet services.

As a customer, it can be useful and interesting to know which service ports, if any, an ISP has chosen to preemptively block in order to restrict their customers' global Internet traffic.

ISP port blocking can be easily tested, often quite rapidly, by arranging to allow the ShieldsUP! probe to have access to an unprotected computer. Since all non-stealth machines will respond to every open request &#8212; either affirmatively or negatively &#8212; ports appearing as STEALTH will be those blocked by your ISP, corporate firewall, or other external agency.


	 	If your system is unprotected, without any personal firewall or NAT router, any ports showing as stealth are being blocked somewhere between your computer and the public Internet. This is probably being done by your ISP. Internet traffic directed to your computer at the stealth ports will be dropped before reaching your machine.
 

	 	If your system has a personal firewall that can be instructed to "trust" a specific remote IP, you can temporarily instruct it to trust the ShieldsUP! probe IP of [4.79.142.206]. If, after doing so, most of the service ports change to either open or closed , you have succeeded and any which remain stealth are being blocked by your ISP.
 

	 	If your system is operating behind a residential "NAT" router, the router will be acting as a natural and excellent hardware firewall. But that's not what you want for the moment. You can temporarily remove your NAT router and connect an unprotected computer directly to your cable modem or DSL line. Or, if you are comfortable reconfiguring your NAT router, you may be able to point the router's "DMZ" at one of your computers which has been instructed to "trust" our probe IP of [4.79.142.206]. If, after doing so, most of the service ports change to either open or closed , you have succeeded and any remaining stealth are being blocked by your ISP.
 

	 	Finally, if your Internet security system, NAT router, personal firewall, or whatever, can produce detailed logs of incoming Internet packets, you could leave your existing security in place, clear your log, run the service ports scan, then carefully inspect your log for any consistently missing port probes. We send out four sets of probing packets because individual packets are sometimes dropped along the way. Therefore, it won't be unusual to see occasional missing packets from your logs. What you're looking for is a complete lack of packets bound for a specific port. A careful and detailed examination of your log will reveal any missing ports which are being blocked before they reach your logging tool. (Note that this technique is not quite as foolproof as the other approaches since ISPs could be blocking outbound packets from their customers, which the other approaches would detect but log-watching would not.)

After completing the experiments above, remember to return your system to its previous tight security and verify that everything is safe again by re-running any of our tests. 

---

### Post by Extreme Coder on 2008-02-29
Ok, thanks! I will try that now!
BTW, do you mean you don't have any open ports at all?

Also, how's the ping and lag with online gaming?

Thanks!

---

