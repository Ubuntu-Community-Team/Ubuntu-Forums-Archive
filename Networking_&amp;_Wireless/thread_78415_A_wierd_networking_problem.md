---
title: "A wierd networking problem"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by ramba on 2005-10-18
I installed Ubuntu just a couple of days ago and I'm new to linux. Well, anyway, I have this really wierd network problem, my ethernet and wireless cards are working okay but if I want to browse the net I have to ping the address manually before I can enter the site.

My connection is a broadband (Elisa ADSL) and I use a HW router. Normally in windows I just plug it in and it works through DHCP right away with default settings.

I had similar problems when I tried Mandriva... If you need more description, tell me. Thank you ;J

---

### Post by mips on 2005-10-18
Your problem seems DNS related in some way.

Please post the following info:

1) Router Make & Model.
2) Did you buy it or was it provided by the ISP.
2) Connection type, Ethernet, USB or Wireless.
3) Running in Bridged or Routed mode. Do you configure PPPoE on the client or router.
4) Country you live in.
5) Your ISP and/or Broadband provider.
6) What service are you sucribing to from them.

Please provide links where possible to the above questions.

---

### Post by ramba on 2005-10-18
1) A-Link RR24AP [http://www.a-link.com/uk/RR24AP.html?id=cipkhVhM]("http://www.a-link.com/uk/RR24AP.html?id=cipkhVhM")   I bought it myself
2) Ethernet (it does the same with wireless connection, but I'm using ethernet now)
3) I think this is on routed mode. This doesn't use PPPoE. (I'm not sure about this, but a good guess)
4) Finland [http://uncyclopedia.org/wiki/Finland]("http://uncyclopedia.org/wiki/Finland")
5) Elisa [http://www.elisa.com/en/index.cfm?t=1&o=3]("http://www.elisa.com/en/index.cfm?t=1&o=3")
6) See the link above

---

### Post by ramba on 2005-10-18
Ah, It says the router should have support for RFC Routed/Bridged Ethernet over ATM Protocol.

Router settings:
VPI 	0
VCI 	100
Protocol 	RFC 2684 Bridged
Framing 	LLC/SNAP
Linetype 	Multimode (G.DMT tai ANSI T1.413)

---

### Post by mips on 2005-10-18
[QUOTE=ramba]Ah, It says the router should have support for RFC Routed/Bridged Ethernet over ATM Protocol.

Router settings:
VPI 	0
VCI 	100
Protocol 	RFC 2684 Bridged
Framing 	LLC/SNAP
Linetype 	Multimode (G.DMT tai ANSI T1.413)[/QUOTE]


Does it work in Windose ? How is windows setup to use this device ? I'm trying to establish if you are running PPPoE/PPPoA on the PC or whether it is configured on the router in which you would be in routed mode.

For now please upgrade you routers firmware to the latest version, [http://support.a-link.com/rr24ap/upd.htm](http://support.a-link.com/rr24ap/upd.htm)

Look at: [ftp://ftp.a-link.com/rr24ap/suositeltavat_asetukset.pdf](ftp://ftp.a-link.com/rr24ap/suositeltavat_asetukset.pdf)
and   [ftp://ftp.a-link.com/rr24ap/ISPManual_FIN.pdf](ftp://ftp.a-link.com/rr24ap/ISPManual_FIN.pdf)

I cannot read Finnish, it doesnt seem to resemble a Germanic language ?

We want to configure the device as a router so it handles the PPPoE/PPPoA stuff. Your PC should just require DHCP setup on the LAN cards TCP/IP settings.

---

### Post by mips on 2005-10-18
You can also try manually configuring the DNS settings from your ISP in Ubuntu's Network configuration.

If you do have windows and it works please open a command prompt and type "ipconfig /all" and paste the output here.

---

### Post by ramba on 2005-10-18
Windows IP Configuration

        Host Name . . . . . . . . . . . . : t
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-04-61-71-84-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.0.2
        DHCP Server . . . . . . . . . . . : 10.0.0.2
        DNS Servers . . . . . . . . . . . : 10.0.0.2

Btw. my connection doesn't need username and password so I doubt it has to use PPPoE or -A to connect. Thank you for your effort! :D

---

### Post by fheinsen on 2005-10-18
Hi -- I've had the same DNS problem with cheap routers when using DHCP.  These two solutions work for me:
 
1. Go to Applications -> Accesories -> Terminal and type "sudo install resolvconf pump dnsmasq" (see [http://www.ubuntuforums.org/showthread.php?t=5690](http://www.ubuntuforums.org/showthread.php?t=5690))

2. Follow the instructions here: [https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29)

---

### Post by mips on 2005-10-19
Also look at Option3 in this link  [http://ubuntuforums.org/showthread.php?p=425483&posted=1#post425483](http://ubuntuforums.org/showthread.php?p=425483&posted=1#post425483)

---

### Post by ramba on 2005-10-19
Okay It's working, I called my ISP to get the dns servers and edited the resolv.conf. Now I just have to lock it so it doesn't change...

Thanks for your effort! :J :cool:

---

