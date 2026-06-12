---
title: "wired home networking problems / 2nd NIC"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by stlouisubntu on 2008-07-03
New to ubuntu and forums and have tried to resolve this via
other postings and responses, but frankly I need some hand
holding.

Currently my main box is a is a Micron ClientPro 766Xi
Pentium II 333 Mhz with 320 MG RAM which also act as a 
router for file/print/DSL internet sharing via Win 98 SE
(dual boot with a cli Ubuntu 8.04 install -- was trying 
Fluxbox for the gui and have now traded it for Ubuntulite
/ LXDE.)  

Naturally for the sharing, this box has two NICs
eth0 to DSL ISP is a 3Com Fast EtherLink XL 10/100Mb TX Ethernet NIC (3C905B-TX) (works fine)

eth1 to home network for file/printer sharing and internet connection sharing is a D-Link DFE-530TX+ PCI Adapter.

This setup works fine under Win98, and I need to boot to Win98 (on the dual boot side) in order for this to work.  I would prefer to boot to Ubuntu, but need to resolve this first so my 
home network will function.

Tried Firestarter and WICD. Firestarter fails to start at every boot and in the GUI says fail to start as eth1 is not ready.

Both NICs use different interrupts.

Have tried playing with interfaces file and manually bringing eth1 up. Modifying interfaces did not help and neither NIC functioned after I manually brought eth1 up.

Thanks for reading and thanks in advance for thoughts, suggestions, and assistance.

---

### Post by superprash2003 on 2008-07-03
try disabling the dhcp server in firestarter.. the "not ready" error may disappear

---

### Post by stlouisubntu on 2008-07-03
> **superprash2003 said:**
> try disabling the dhcp server in firestarter.. the "not ready" error may disappear

Thanks for the suggestion, but frankly it does not seem helpful.
Eth0 receives a dynamically assigned IP from the ISP DSL Modem and
I need eth1 to dynamically assign NAT / IPs to the other boxes
in my home network.  The reason I installed Firestarter was not for
the firewall feature, but for the dchp feature for internet sharing.

Perhaps the type of assistance I am looking for is for someone
to advise me on exactly how my interfaces file should look for this desire configuation.  Or whatever I need to do to make this work.  I also was using PPPoE on Win98 so I was trying to make that work, too.  I could try disabling dchp on Firestarter (or uninstalling it
completely, but again, I need the NAT internet sharing capability.

Thanks.:confused:

---

### Post by superprash2003 on 2008-07-03
is this what you are looking for [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by stlouisubntu on 2008-07-07
> **superprash2003 said:**
> is this what you are looking for [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

Thank you!!  Thank you!!

This link is gold.  Well worth copying into an OpenOffice Writer
file (or ABI) printing and saving.

I did make it completely through the step by step instructions (had
to do it twice before it appeared to work with no errors.)  Now I can
ping the host/server, and the server has an internet connection through
eth0, but the client still does not have internet access.

Questions:

Since this is dhcp3 server, I assumed I would no longer need firestarter
so I unintalled it.  (Should I reinstall?)  The new plan was to use ufw on top of dhcp3 server (ufw is still disabled for testing purposes of dhcp3.)

The line to uncomment in sysctl.conf is slightly different in my file than the instructions (I didn't change what was in my file other than to 
uncomment the noted line to enable packet forwarding for IPv4
Is that okay? (I thought the instructions might be for an earlier 
version.)

In dhcpd.conf under option domain-name "SOMENAME";

Do I just make up my own .com domain name for
my local LAN?  How much does this matter?

Thanks so much for the assistance.  Problem is not solved, yet, but
it seems progress it being made.  Further advice would be
much appreciated.  (I'll read your blog.)

Thanks again.

---

### Post by stlouisubntu on 2008-07-26
Although I never received a reply from my last few questions,
through further web searching using both google and ask.com and
trial and error, I finally did get a dhcp home server going with 
dynamic ip / NAT assignments to the client boxes and packet
forwarding.

For anyone who had the same problem, the final two things I tried
were to apt-get install ipmasq dnsmasq.
Then it worked but only after I do a
sudo /etc/init.d/networking restart followed each boot up.
Until I do that, I have no internet access at all.

My latest struggle it to get ufw operating correctly.
After enabling, I do a 
sudo ufw allow from 192.168.10.0/24 to any
and it shuts off all internet access to the clients
until I do a ufw disable.
I do not get it, but I will keep on trying until
it works.  Any thoughts, suggestion, or recommendations
would again be much appreciated.  Do I need to add 
ports and/or protocols to it.  If so what ports 
(the ports concept puzzles me frankly.)  Also, 
which protocols?  TCP?  UCP?  SSH?

Tried installing gufw, but it will not even launch
(maybe because I am trying to run it on a low 
end LXDE/Openbox ubuntulite installation and it
might need gnome or something.)

Thanks.

---

