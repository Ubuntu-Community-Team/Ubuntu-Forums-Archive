---
title: "Resolved-- problems connecting to  vpn (pptp) server with Gutsy"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by stevieP on 2008-05-31
I was having newbie problems setting up a VPN connection to my employer network from a Ubuntu Gutsy laptop, and was going to submit this post as a question. However I seem to have resolved all my problems, so I thought I would still submit this as an informative post, (hopefully), for newbies. 

I have a Dell XPS M1530 laptop.
System->About Ubuntu gives:
"Thank you for your interest in Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007"

Following the directions on:
[http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/](http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/)

I have installed network-manager-pptp using synaptic package manager.
(I don't know how to check that it has been probably installed however, but I assume it is)
I rebooted my machine.

If I click on the "Network Configure network devices and connections" icon, I see no options for a VPN connection. Only Wireless Connection, Wired Connection, and Modem Connection. So I cannot configure VPN from there. 

The only place I found I could configure VPN from was the icon giving my wireless network connection bars (It says 'Wireless network connection to network_name (68%)').

If I click on that and go to VPN Connections -> Configure VPN
I get a window saying "Manage virtual private network connections"
I click "Add". A "Create VPN connection" window opens. 
I click forward, then "Connect to PPTP tunnel", then click forward.
I'm in a "connection" tab of the "create VPN" GUI. (other tabs are Authentication, Connection and Encryption, PPP options, and Routing).
I'm asked for a connection name and make one up. The only type of network I'm allowed in the window is Windows VPN (PPTP), which is what I want.
Then I'm asked for Gateway, and I have no idea what to enter. 
There are no fields for "Server name" and "Username" and "Password".
So I guess what they want for Gateway is the Server name, I enter that, and  go forward. 
I find on the next tab that PPTP Server is set to what I entered for Gateway so I guess that worked. 
I see a list of specs for the VPN network, but I still don't know where I'm supposed to enter my Uname/Passwd. I click OK and the network appears to be added. 
I click again on my wireless connection bars icon and go to VPN connections. 
Lo and behold I'm asked for my username/password, which I enter. 
I found that a little lock icon appears on my Wireless network connection icon, and I'm able to access journals, websites, etc. particular to my employer. 
Great success.

---

