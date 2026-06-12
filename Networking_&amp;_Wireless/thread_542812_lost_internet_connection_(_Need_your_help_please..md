---
title: "lost internet connection :( Need your help please."
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by ROUBOS on 2007-09-04
Hi all,
Well I had my Ubuntu Box at home working fine on the ADSL Router.
I closed down that internet conneciton at home and moved the Ubuntu box to my office.
At the office I also have an ADSL connection with an ADSL Router and a 16port Switch.

the thing is that I hookup my lan cable and I get no network connection. I tried everything.

When I run the following command:

sudo pppoeconf

it finds my network card eth1

and then I get an error:

"Sorry I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reasong for the scan failure may also be another running pppoe process which controls the modem."

OK I'm a noob and I looked up for troubleshooting on google and got the pppoeconf command.

I tried setting a static IP etc. I cannot even ping the router.

Any help will be greatly appreciated as I need to get this ubuntu box on the network and set it up as a File Server in the next few hours :confused:

---

### Post by ROUBOS on 2007-09-04
Don't know exactly what I did. I managed to get it to detect eth0 now.
And I can get it to see the Router pages 192.168.2.1
but I cannot get on the internet though.

I think that the problem is that under Networks it shows loopback by default and no eth0.

Any thoughts?

---

### Post by eluzi on 2007-09-04
First of all:

# ps aux | grep pppoe

If this comes out with some process of pppoeconf, kill it with

# kill <PID> 

Where PID is the number of the process.

Ok, now u should check if the cable between the network card and the modem is well connected and if it is a direct cable 

Done this, run pppoeconf again...

When it recognizes the card, enter the correct info about your provider.

Then check if u get ip address from the router... If u do not, u can force your ip address and netmask to something in the router net, to be able to access it via browser and check its configs...

---

### Post by ROUBOS on 2007-09-04
thanks for the reply. I looked at the following:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html)

and some personal troubleshooting... as a noob I dont really know what I did, but I got it to work.

It's working now. Thanks....alot for your reply

---

