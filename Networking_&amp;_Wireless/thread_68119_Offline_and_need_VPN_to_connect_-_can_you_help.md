---
title: "Offline and need VPN to connect - can you help?"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by Bigglez on 2005-09-22
Hello. 
This is the story:
I am on Fedora. I have a friend that wants to try Linux. We are both connected to the net via the same ISP who uses VPN with MPPE.
I want to install Kubuntu 5.04 on her machine as I think it's the easiest way for her to get into Linux. 

Can anyone here give me a blow-by-blow of where I can go and what I must do to get "pptpconfig" (and thus VPN) working on Kubuntu when I cannot connect to the net from that machine in any way other than VPN. 
(It's a catch-22 most times, "You need apt-get to install software to get online so that you can use apt-get")

If you could list the files (and url's) where I can go and fetch .deb files that will be needed for php-gtk and all the related pptp things, along with some kind of how-to that would be magnificent :D

I will then cut a cd and head-off to her place and install Kubu!

---

### Post by xristos on 2005-09-22
You need this [http://pptpclient.sourceforge.net](http://pptpclient.sourceforge.net)

the 5.04 has the linux mppe support so you don't need to recompile

---

### Post by Bigglez on 2005-09-22
xristos. Thanks. I have visited that site.

What I need is a link to where I can find the .deb files (for i386) and all the dependant files (like php-gtk) that I won't be able to fetch when I am offline.

Picture my situation:
1. I am at a fresh Kubu install.
2. I have no online connection from that machine.
3. I need to get VPN working in order to get online.
4. I can fetch files from another machine and burn cds.

Take it away....

:D

---

### Post by xristos on 2005-09-22
try these :

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) 

and

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Bigglez on 2005-09-22
Xristos - thank you for the links. It's a start !

I am wondering if pptp-linux is the only file I will need?
I have read some other threads that suggest other things like php-gtk and something about glade ??

The ubuntu packages site says I need:
      [dep] libc6 (>= 2.3.2.ds1-4)
      [dep] ppp
      [sug] kernel-patch-mppe
Now, how do I know (not being in front of Kubu right now) which of these already comes with a std Kubu install?

Is there anyone who knows what other deb files I would need to get this pptp thing done?

Sorry to be so dumb. I am not exactly a newbie, but I sure aint no hacker either ;)

---

### Post by xristos on 2005-09-22
If you follow the guide in pptpclient.sourceforge about debian and especially make the files needed on your own then you don't need pptpconfig or php-gtk or what else.

Follow this link [http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)

The only one you need is pptp-linux which is in the cd of Ubuntu ( I don't know about Kubuntu but you can find out )

---

### Post by Bigglez on 2005-09-22
Xristos - great link, thanks a million. 
I am sure I will get things working now.
If there is anything extra I need to do to get it up - I will come back here and make some notes, just in case others are on the same trail.

Respect to you!
Ciao.

---

### Post by Bigglez on 2005-10-03
Okay. I finally got Kubu to connect to the Internet. I am posting the steps I took here in case it help others and for myself because I can't remember all these things!

Note: I don't know if anything here is redundant or plain wrong. It works, that's the bottom line. Please correct anything. 
I know zip-all about networks.

First. I have done this from the Kubu 5.04 Intel LIVE CD.
I have not had a chance to test this on an installed system yet.

**Step 1: pptp-linux**
**Problem:**[I]"pptp-linux" is not available on the LIVE cd. (Well, near as damn as I could tell). I had to suck it across from a USB stick.)
Have a stiffy or a USB storage-device or another network connection available so that you can suck "pptp-linux_1.5.0-4_i386.deb" (or whatever version you have) across to the kubu machine.[/I]
I *think* that the installed version of Kubu/Ubu already install pptp-linux, so you should be good to go.
If you need to install it:
```
dpkg -i pptp-linux_1.5.0-4_i386.deb
```
**Step 2: Editing some text files**
Open a root terminal somehow. You might need to open a normal one and then type:```
sudo su
```
Create "/etc/ppp/options.pptp" 
(Sets options for all tunnels, they say.)
Put this stuff in it:```
lock
noauth
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
require-mppe-128
```
Create or add to "/etc/ppp/chap-secrets" 
(Holds username and password)
[i]$TUNNEL = Some name. You decide. It's used all over the place, so keep it simple. 
$USER = Your username.
$IP = The IP address of your gateway (or ISP), or whatever.
Replace them all as appropriate.[/i]
Put this info into the file:
```
$USER $TUNNEL password *
```
Where you obviously insert your info as appropriate.
Create "/etc/ppp/peers/$TUNNEL"
(Does some stuff, I dunno.)
Put this rubbish into it:
```
remotename $TUNNEL
linkname $TUNNEL
ipparam $TUNNEL
pty "pptp $IP --nolaunchpppd "
name $USER
usepeerdns
require-mppe
refuse-eap
persist
debug dump
noauth
file /etc/ppp/options.pptp
```
**Step 3: Starting the VPN connection**
Enter this command as root:
```
pon $TUNNEL
```
To diagnose problems try this:```
pon $TUNNEL debug dump logfd 2 nodetach
```
To stop the tunnel, I am informed you use:```
poff $TUNNEL
```
**Step 4: Making it "see" the Internet.**
I don't know if you will have to do this, I have to do this for my ISP situation. It makes a default route that works across the VPN tunnel. I am guessing here, but I think this moves all packets across the VPN link by telling the O/S that if it can't figure out where to send them it should just "default" to sending them to the ppp0 device. Don't quote me.
Enter this command as root:
```
ip route add default dev ppp0
```
And now you should be able to surf and so on.

Well, that's it for now. When I get this working on an installed Kubu/Ubu then I will repost with the stuff needed there. I should imagine it would include how to auto-start the link as well as create some kind of icon on the desktop to maually start it, who knows :D

**For more information go to [www.pptclient.sourceforge.net](www.pptclient.sourceforge.net)**

---

### Post by chambs10 on 2005-10-21
Thank you for the thorough documentation.  I've ran into a problem that I can't seem to work out though. I have created all the files necessary, my tunnel is called "vpn".

Here's what I have at the prompt:

>ifconfig -a (returns no ppp0 connections)
>pon vpn (seems to work)
>ifconfig -a (shows ppp0 connection)
>route add .... (this returns an error)

The error I get from this is: "SIOCADDRT: No such device"

Does anyone have any clues into solving this?

---

### Post by Bigglez on 2005-10-21
Chambs,
I ain't no expert on networks - in fact I know bugger all :D Still, in your last step did you try:
ip route add default dev ppp0
With the "ip" command in front?

---

### Post by Bigglez on 2005-10-21
Just to add that I repeated this thread with added info on:
[http://ubuntuforums.org/showthread.php?t=71860](http://ubuntuforums.org/showthread.php?t=71860)

---

### Post by chambs10 on 2005-10-22
Syntax...thanks, it worked great!

Looks like I'm up and running.

---

### Post by Bigglez on 2005-10-22
Peachy! Glad I could help - even if I know nothing at all about networks!
;)

---

