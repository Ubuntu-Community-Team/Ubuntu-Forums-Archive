---
title: "NEWBIE HOWTO: Get Firestarter to work the FIRST TIME"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by ckrueger on 2005-10-13
Ok, after screwing around with Firestarter and DHCP several times on Ubuntu, I figured I'd write up my experiences on how to get it working correctly on the first try (with DHCP, I might add, as that's where most of my problems came in).

[LIST=1][*]**Install the required packages.**
Install "dhcp3-server" and "firestarter", either through Synaptic or the terminal:
```
$ sudo apt-get install firestarter dhcp3-server
```
[*]**Configure your internal network card.**
Make sure that your internal network card is assigned a static IP address in a range that you will use for you internal network.  To do this, go to *System* -> *Administration* -> *Networking*.  Once there, go into the properties for the network card you will use for your internal/routed network (it will quite likely be disabled) and set it up as you deem necessary.  As a basic example, set the IP address to 192.168.0.1, and the subnet mask to 255.255.255.0.  Leave the gateway empty.

[*]**Fix the problem where Firestarter cannot locate the DHCP daemon init script.**
From within a terminal, and run the following command (creating a symbolic link to fix the mis-reference; this is a simple alternative to editing Firestarter's init script):
```
$ sudo ln -sf /etc/init.d/dhcp3-server /etc/init.d/dhcpd
```
This fixes the problem where Firestarter will sometimes say something along the lines of "An unknown error occured" when DHCP is enabled within its configuration.  Sometimes the firewall will start anyway, but DHCP will remain off.


[*]**Configure the interfaces on which DHCP will be listening.**
Edit your /etc/default/dhcp3-server file (using a text editor running as root, or by logging in and running "sudo vi /etc/default/dhcp3-server").  The only variable in there by default is "INTERFACES", which will have a null value.  Set it to your internal network interface.  For example:
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```
Write the file and exit.

[*]**Run Firestarter.**
If this is your first time running Firestarter, the wizard should appear.  If not, simply click *Firewall* -> *Wizard* from within Firestarter.  Select your external (Internet-connected) device when it asks, and make sure to specify whether or not the address is obtained via DHCP.  Click the "Forward" button, check the "Enable Internet connection sharing" box, select your internal network card, and check the box for "Enable DHCP for local network".  Drop down the "DHCP server details" and enter the range of IPs you would like for it to dynamically assign.  **Make sure they are in the same range as the static IP you set for your internal network card**.  Also, for the DNS server field, you **MUST** supply an address - "<dynamic>" will *NOT* work.  Simply look at your /etc/resolv.conf file if you need inspiration.  Click "Forward", check the "Start firewall now" box, and click "Save".
[/LIST]
**DONE!**

It took me a while to pinpoint the causes of various small problems I was having getting it to play nicely with DHCP, but I finally got it down and figured I'd share my experiences.  Please let me know if you have any suggestions (I know I clumped everything together for that last step, but c'mon, it's a wizard...  It's pretty freaking simple).

Regards,
Campbell Krueger
[http://www.flargen.com](http://www.flargen.com)

---

### Post by mit on 2005-10-13
Thanks for the advice, i am going thinking about installing Firestarter. So, it is best to set a static IP then?

---

### Post by ckrueger on 2005-10-13
On the internal network interface, it's the only way.

---

### Post by pseudonym on 2005-10-20
Brilliant! I was tearing my hair out over this - the Firestarter documentation is a little outdated and unspecific in parts. But when I came across this howto my problems were solved. Thanks! :)

I used this on Debian Testing. For some reason, the Debian Firestarter package seems to only want to work with the 'dhcp' package, rather than 'dhcp3-server' (I tried out both). So step 3 becomes - ```
# ln -sf /etc/init.d/dhcp /etc/init.d/dhcpd
```

Also, the <dynamic> name server option works in Debian.

My secondary PC has now just finished downloading the latest Ubuntu .iso on the now shared internet connection. Wunderbar! :)

---

### Post by puelly on 2005-12-21
Thanks for the howto.  That dhcp problem had me stumped and frustrated.

Thanks again.

---

### Post by ace2005 on 2006-02-02
Thanks, the dhcp error has been driving me up the wall

THANKS \\:D/

---

### Post by xmastree on 2006-02-06
Hmm... :-k 

I'm having trouble with the DHCP server. Using the wizard the option is greyed out. Using firestarter's Preferences > Network settings I can enable it but get the unknown error thing.

What's step 3 supposed to do, how can I check that I did it right (I cut&pasted from here) and how can I edit Firestarter's init script if this simple alternative doesn't work?

FWIW, what I'm trying to achieve is to allow another computer to use this one's net connection. To that end, I added another NIC in addition to the built-in one which I am using to connect to the Internet.
The new one became eth0 and the original one moved became eth1 so I had to tweak a couple of settings but that's all working AFAIK. At least, the net is ok, and the new NIC (eth0) now has a static IP address.

At this time there's nothing connected to it, but I can't see that having an effect.
:confused: 

Another (possible stupid) question: Now that I have installed firestarter, does it mean that **this** computer's connection is also passing through it?

---

### Post by theolster on 2006-02-06
Hi, this thread is a breath of fresh air!  I have finally managed to share my internet connection with an XP box.

However, before setting up firestarter, I used to be able to view the webpages on the apache server on ubuntu by typing in the ip address from the windows box. e.g 192.168.0.2

But now I can't access anything from the windows machine on the ubuntu one, just the internet!

Does anyone have any ideas on how to fix this? (Help!)

---

### Post by xmastree on 2006-02-06
Well, I suspect it's a proxy thing. Is the XP box using a proxy? I guess it's looking 'out there' for the address first. Disable it for cetain addresses, namely the 192.168.0.2

Mine now works! I followed the instructions in the ubuntu guide about editing /etc/dhcp3/dhcpd.conf and that fixed it.

[http://www.ubuntuforums.org/showpost.php?p=710125&postcount=77](http://www.ubuntuforums.org/showpost.php?p=710125&postcount=77)

---

### Post by NLFSoftware on 2006-02-08
Hello all

I a litlle canfuse whit all this stuff, and my network sharing is not working....

This is a description of my network:

1 Ububtu box that connect directly to internet
2 windows computers

What I want is to have the linux box whit a DHCP server and share the internet and if possible files.

This is what I have done to try share my internet and files:

1º in the begining I have a windows box sharing the internet so in the ubuntu box I only install samba and everithing works fine.

2º after some time I reallise that for many reasons I have to connect the ubuntu box directly to internet and share the connection whit windows pc's

3º I install other NIC in the ubuntu box for the internet connnection and works fine. Then I start to looking for information to configure ubuntu to share the connection.

4º after a while i install firestarter and the dhcp for it, and read this topic:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

about share the internet, the problem is I have to do it every day becouse when I start the ubuntu box the eth1 (NIC connected to internet) doesn't connect so after start I have to go to System->Administration->Network Setup (is not the corret name becouse I using a portuguese version of ubuntu ;) so is the app that let us config the NIC's and to activate then )

Well this was working more or less... some times after one hour of tryings the internet works on all the pc's...other times , not...

5º I decide to put this working proprely and since yesterday I unable to share the internet connection, so I have the firestarter installed but the firestarter is unable to recognize the DHCP3 Server, even after I follow the 3º point of this topic, The DHCP3 server is working becouse the windows box have the ip but when I try to ping google from the windows box, returns an error message saying that is unable to resolve the host name.

this is my /etc/resolv.conf

> search netvisao.pt
nameserver 213.228.128.99
nameserver 213.228.128.6

where netvisao.pt is my internet provider

this is my /etc/dhcp3/dhcpd.conf (only the uncomment lines)

> ddns-update-style none;
log-facility local7;
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 213.228.128.99, 213.228.128.6;
  option domain-name "cassiopeia.netvisao.pt";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

I have installed Bind9 in trying to put this name like a DNS in a desperated hope of share the internet but doesn't do anything... aperently.

6º When I open System->Administration->Network Setup and then close it, the internet stop working on ubuntu box, I have to open it again and then deactivate and activate the eth1 and let it open, otherwise the internet connection go off.:confused: ...bizarre...

7º I not having file sharing yet, but I guess that is for the same problem that I don't have internet shareing... 

Well some more info about the ubuntu box:

eth0 - NIC connected to the local network

configuration:
ip - 192.168.0.1
Mask 255.255.255.0
gateway -192.168.0.1

eth1 - NIC connected to internet 
configured by DHCP (from ISP)

just a litller reminder, when I ping 192.168.0.1 from windows pc's it works fine.

well I hope some one can tell me were is the bug of this...

Thanks in advance for your help.

---

### Post by cudaboy on 2007-05-28
Thanks, this guide helped me a lot with Edgy and now with Feisty also. In case it helps someone, what i did on Feisty to share internet with an XP box on the other side of the LAN was what it says in the original post, except that i left the <dynamic> server name, and after doing all that, I added:

"net.ipv4.ip_forward = 1" to /etc/sysctl.conf

to edit just type on terminal: 
$ sudo gedit /etc/sysctl.conf

and paste at the end of file:
net.ipv4.ip_forward = 1
 
Before adding that line on /etc/sysctl.conf, i had connection, but no internet.

---

### Post by JC Denton on 2008-06-16
Thank you, it _finally_ works.

---

