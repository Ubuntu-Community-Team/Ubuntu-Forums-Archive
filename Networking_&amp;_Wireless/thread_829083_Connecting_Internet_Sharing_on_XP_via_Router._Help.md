---
title: "Connecting Internet Sharing on XP via Router. Help Please."
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by getanner on 2008-06-14
Hi there,

I'm new to the Ubuntu system and would like to migrate over.

My problem is that as I currently have no access to a hardwire landline, my only access to the internet is with a 3G USB dongle and that of course has on Windows Drivers. It's a Huawei E220 HSDPA USB Modem from T-Mobile (UK).

What I would like to do is set up a small network using redundant kit.

I have a Netgear Cable Router, Netgear Ethernet Printer Server, PC Box with XP and a laptop with Ubuntu installed.

If I can get the laptop and the XP Box to share the internet, I'll invest in a wireless AP to replace the current CAT5 cable used with the laptop.

I have the Laptop connect to port 1
The XP Box is connect to port 2
The Printer Server is connected to port 4.

I can see the Windows shares in Ubuntu, but I can not access the internet.

I have enabled Sharing on the T-Mobile Dial-up but this is beyond my current skills set.

Any advice or help would be very gratefully received.

Running XP Pro and 8.0.4 LTS.

Many Thanks,

Guy

---

### Post by dacorr on 2008-06-14
so, are you saying that all the computers are connected to the netgear router and they share the internet connect through the XP box using the T Mobile 3G modem?

Or is the modem connected to the router and they connection is sheared via the router?

---

### Post by getanner on 2008-06-14
Thanks for your reply, i will try to clarify further.

I have a Netgear RP114 Router. A Netgear PS110 Print Server. An XP Box running Pro with the T-Mobile Modem attached. A laptop with 8.0.4.

I have the laptop connected via ethernet cable to port 1 on the router.

The XP Box is attached to port 2 via ethernet cable and the print server is attched to port 4.

The WLAN side of the router is empty.

The T-Mobile USB modem is attached via USB to the XP Pro box.

I can see the windows shares displayed on the ubuntu laptop but not the shared T-mobile internet.

I have set in the XP Network connections via Properties>Advanced to share the T-mobile connection.

Not sure what to do now.

Guy

---

### Post by dacorr on 2008-06-14
ah ok

so the Linux box will get an IP by DHCP from the router so you can access the LAN.

The router will be the DNS also.

You will need to set on the linux via System>Administation>Network. for the default gateway use the XP box IP.

That should work

Strange way to do it but should be ok

let me know how it goes

Dac

---

### Post by jones139 on 2008-06-14
I think dacorr is correct that setting the XP box as your default gateway will let you see the internet, but I think you will have trouble with DNS - you will be able to use IP addresses (216.239.59.147), but not normal addresses ([www.google.co.uk](www.google.co.uk)).
This is because your router is not connected directly to the internet (as far as I can tell from your description) - it sounds like you are using it more as a network hub than as a router?
This means that the router will not know what DNS servers to supply to the Linux box when it connects via DHCP.
It might be possible to program the router via its configuration page to set the DNS servers automatically, but personally, I am a luddite and for a simple network like yours I would configure the computers manually using static IP addresses and other configuration things rather than try to teach the router how to configure them for you.
I might be wrong though - it might just work as suggested!

---

### Post by getanner on 2008-06-15
Thanks for both your replies,

I will try your suggestions tonight when I get home.

I agree it's a strange way setup a network but alas with no ubuntu (or Linux in general for that matter) drivers for the T-Mobile Mobile Broadband dongle, I'm limited to using either Windows XP or Vista for my internet access.

I only have the one XP licence but 3 computers therefore a solution is needed that would allow 2 Ubuntu latops and a PC box to connect to the internet around the house.

You are right in the I'm using the router as a Network Hub and not as the internet gateway simply because my internet is USB based and the router only has ethernet ports (1xWLAN and 4xLAN).

Many thanks again for you help and I will try the solutions out this evening.

Kind regards,

Guy

---

