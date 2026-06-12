---
title: "VPN in Ubuntu 5.04"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by agrinin on 2005-08-01
Hi!

I'm new to Linux in general, therefore please give me detailed instructions, if possible. So here's the question: at home I have a LAN, and Internet access through Virtual Private Network. LAN works perfect, BUT I don't know how to set up VPN access. What packages I need to install to enable it, and what to configure?

Thanks a lot :-)

---

### Post by varunus on 2005-08-01
You need to set up the "vpnc" program to use a vpn.  You should also use the resolvconf tool; this lets you switch from local network to VPN on the fly without having to issue any commands to change your routes.  Do the following in a terminal:
```
sudo apt-get install vpnc resolvconf
```

Then, type the following:
```
cd /etc/
mv resolv.conf resolv.conf.old
ln -s /etc/resolvconf/run/resolv.conf resolv.conf
```

Then, set up your vpn settings.  To do this:
```
sudo gedit /etc/vpnc/default.conf
```
This will make a blank file for you to add settings to.  There are example settings in /etc/vpnc/example.conf; you can also use google.  Here are my settings (I connect to Purdue University's network through VPN):
```

Interface name pal
IDE DH Group dh2
Perfect Forward Secrecy nopfs
IPSec gateway vpn.airlink.purdue.edu
IPSec ID vpnusers
IPSec secret vpnusers

```

After this, you need to edit your resolvconf settings:
```
sudo gedit /etc/resolvconf/interface-order
```
Make that file look like this:
```

# interface-order(5)
lo.inet*
lo.dnsmasq
lo.pdnsd
lo*
tun*
tap*
pal #Add the name of the interface you used in your vpnc default.conf here, I used pal
eth*
ath*
wlan*
ppp*
*

```

And you're done!  Make sure you have ethernet access, and open up a terminal, and type:
```
sudo vpnc-connect
```

To disconnect, type
```
sudo vpnc-disconnect
```
in a terminal.

I'm making a GUI frontend for vpnc and resolvconf, since i use them both too, so once I'm done, if you're interested, I can get you a copy.  (I plan to have it make an icon in your system tray letting you know of the status of the VPN, and to let you edit all your settings through GUI and connect through a GUI.

---

### Post by johnmcle on 2005-08-02
Hi I was searching for help on VPN setup & came acrros your posting. Could you please forward me your GUI when you have completed it?

Many thanks in advance.
 :)

---

### Post by johnmcle on 2005-08-02
Please forgive my ignorance, but where can I get vpnc resolvconf package?

Thank you :smile:

---

### Post by gruepig on 2005-08-03
'sudo apt-get install resolvconf'

---

### Post by agrinin on 2005-08-03
Thanks a lot, varunus, for your help. I appreciate this :-)

---

### Post by frogfromsaturn on 2005-08-11
Hi, I'm a student new to linux living at a hostel. 

In the hostel I have access to internet by connecting to a VPN using my account username and password. In windows its simple I just setup the connection and put in the hostname. I figured I could follow the instructions above and manage to do what is needed for ubuntu but I can't connect to the internet in the first place to get the packages needed. 

Could you tell me what I should do to allow ubuntu to install these packages, please? My USB storage device works so I can access the net from windows and copy files to ubuntu using the USB device.

Thanks in advance  :grin:

---

### Post by frogfromsaturn on 2005-08-19
Ok I guess it was pretty simple.

Just downloaded vpnc and resolvconf from one of the many repositories for Ubuntu. Then used dpkg -i vpnc and dpkg -i resolvconf. I still have to figure out how to configure the VPN but at least I have the tools :D

---

### Post by andrewsawyer on 2005-10-01
Hi all,

I *think* this is related - if it should be in its own thread, I appologise.

I am at home on broadband with Ubuntu 5.04.  I access the net with adsl (no vpn needed).  Now, if I want to access certain resources at Uni, I have to vpn in.

so:

```
sudo vpnc
```

Then the host name, in my case access-gw.jcu.edu.au, then all the other stuff until I have to type in my password.  After this, it just sits - it doesn't go back to a prompt.

I assume this is ok, and it is running the vpn??? Edit: After about 5 minutes, I get a message saying:
```
/usr/sbin/vpnc: no response from target
```

So, how do I now route programs through the vpn rather than just having them going directly through the internet?  Loading up a program that tries to connect to a server at the uni results in it refusing to connect, as it is not going via the vpn.

As always, any help would be greatly appreciated.

P.S.

Trying the info given by Varunus gives the following message:

```
andrew@ubuntu:/etc$ sudo vpnc-connect
Enter IPSec ID for access-gw.jcu.edu.au:
Enter IPSec secret for @access-gw.jcu.edu.au:
Enter username for access-gw.jcu.edu.au: jc146578
Enter password for jc146578@access-gw.jcu.edu.au:
/usr/sbin/vpnc: unknown host `access-gw.jcu.edu.au'
```

Please note that there is no IPSec ID or secret for this server that I'm aware of, so I ommited it from the default.conf file.  I do not get this error when going drect with vpnc, and manually entering the info.  Am I doing something wrong?

---

### Post by andrewsawyer on 2005-10-01
Ok, 

I've read back over my post, and I've edited it one too many times.  There is a guide [here]("http://www.library.jcu.edu.au/InfoHelp/Guides/remoteaccess/vpn.shtml#first") that shows both Windows and Mac users how to get a vpn connection from home into the uni system.  So the question is, how do I do this in Ubuntu?

Using access-gw.jcu.edu.au in vpnc gives an error after about 5 minutes of hanging saying that there has been no response from target.

Any help would be much appreciated.

---

### Post by Balachmar on 2005-10-11
I have a similar problem.
I have done everything in this manual.
But after I enter all the info either manually, or using the config file. It just doesn't do anything. It doesn't come up with the message that a vpn connection was created.
And if I do ifconfig, it doesn't show up.
Shouldn't I change something in the interfaces or something like that?

---

