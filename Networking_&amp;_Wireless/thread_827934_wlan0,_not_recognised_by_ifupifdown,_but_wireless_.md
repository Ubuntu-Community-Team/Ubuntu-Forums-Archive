---
title: "wlan0, not recognised by ifup/ifdown, but wireless works fine."
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by The Martian on 2008-06-13
Hi Folks.

I'm pretty new to Ubuntu, installed two days ago, onto my Samsung Q35 laptop, .although some years ago I had a bit of a mess around with Red Hat, 6 or 7 I think, after a few teething troubles, (sound and wireless), everything is now working fine.
So I'm ready to install Kismet, all that goes fine, I go to edit the config, and in a Cli terminal, ifconfig tells me my wireless interface is wlan0, (as it does in everything else), I edit the file, and before I try kismet I thought I'd try ifdown/ifup from the terminal, but it will not work.
heres the input and output.

martin@linuxlaptop1:~$ sudo ifdown wlan0
[sudo] password for martin: 
ifdown: interface wlan0 not configured.

But the wireless is working splendidly, and everything reports the interface as wlan0, eth0 is my wired ethernet, as it should be, also the loopback interface is OK.

Has anyone any ideas?????
I've had a good look round the forum and cannot find an answer, if theres another thread that will answer my Q I appologise, and can ya point me to it.
TIA

The Martian

---

### Post by kevdog on 2008-06-13
ifdown is a much higher level command than ifconfig <interface> down.  The difference between the two commands is that with ifup/ifdown the process calls ifconfig, and parses the commands in the /etc/network/interfaces file, I believe passing the parameters to iwconfig, and then sets the route.  

I suspect that there are no commands within the /etc/network/interfaces file.  If ifup/ifdown are not working then try using the ifconfig statement instead.  You are not really telling us what you want to do, so that is about as much advice as I can offer right now.

---

### Post by The Martian on 2008-06-13
Hi All,
Thanks mate, smashin explanation.
I checked out the interfaces file and its contents were only:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

what else should be in there?
and should I enter the line.?

iface wlan0 inet dhcp

BTW, I ran kismet with the config file containing wlan0, and it seemed to work fine.
Whaddaya think mate?

Thanks alot my friend.
                         The Martian

---

### Post by equusaustralus on 2010-06-22
Thanks kevdog, ditto on the smashing explanation, worked for me as well! ;)

---

