---
title: "Linksys WRT 54GS"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by bemahesh on 2007-09-25
Hi, I have recently bought Linksys 54GS router.  I have two computers at home one runnning windows vista Business and other one has ubuntu(both are desktops).

I have verizon wireless and have westell modem (westell 6100).  I have wired network from windows vista and router and it is working fine.

Now, I want to add ubuntu desktop to the network(i.e router).  I have also connected ubuntu desktop to the router(WRT 54gs).  However, I seem to not see any internet connection on the ubuntu desktop.

I spoke with linksys people and they suggested to change the port number etc. but don't know anything about that.

In addition, when i was starting internet connection in vista desktop, it did not work so linksys rep asked me to change the local ip address from 192.168.1.1 to 192.168.2.1 due to conflict with modem.  Doing this enabled the internet connection on the vista computer.

However, i can not start connection on ubuntu one.  They don't support ubuntu but suggested to change the port etc.

Can anyone help me.

---

### Post by reckless2k2 on 2007-09-25
it has nothing to do with a port number. does this word sound completely foreign to you:

DHCP

The weird thing is that IF they told you to map a hard IP to the vista box I'd think that your router is not "giving" out local addresses as it should. still sound foreign?

if so, we will need a crash networking course.

---

### Post by bemahesh on 2007-09-25
I am a newbie with networking.  I don't know anything with networking.

All i wanted to do is to get the internet working on ubuntu box.  Can anyone shed some light?

thanks
Mahesh

---

### Post by reckless2k2 on 2007-09-25
ok....post the current ip address of the vista box.

start > run > cmd

then type ipconfig / all

give use the details


ALSO,

go into network config in the adminstration panel and tell us if ubuntu sees your network card. should say eth0 or eth1

???

---

### Post by bemahesh on 2007-09-25
Ipv4 address 192.168.2.100
subnet mask 255.255.255.0

default gateway/dhcp server 192.168.2.1

dns servers
192.168.1.1

Under window IP configuration 
IP routing enabled is set to NO

Under Ethernet adapter local area connection
DHCP enabled  is set to : Yes
NetBios over tcpip : Enabled


One more thing to add here is that, I am able to use internet if I directly connect my westell 6100 modem to the ubuntu box and internet works perfectly fine without the router.  It is router that is not allowing I guess or changing/conflicting configuration settings.


in ubuntu network i see eth1 eth0



thank you very much for your co-operation.  I appreciate your help

---

### Post by bemahesh on 2007-09-25
Please help me with this.  I have posted the information that you have asked me to.  Do you need anyhing more?  Or that be enough to find out the issue?

thanks

---

### Post by patrickfromspain on 2007-09-25
ok, let's do this:

Aplications -> Accesories -> Terminal

sudo apt-get remove network-manager network-manager-gnome

then reboot your computer. Then:

Sistem -> Administration -> Networking 

There, enable your network card and set it to DHCP. DNS: put this in: 208.67.222.222 and 208.67.220.220

---

### Post by reckless2k2 on 2007-09-25
ok so it sounds like you have more than one network card in ubuntu. 

eth0 - is one card?

eth1 - is another card?

make sure each are active (enabled) and set to receive an automatic address from the router. Set each to active and in properties make sure it says auto or DHCP. 

if you are using ubuntu 7.04 this is plug and play. 

so right now you have a cable running from a network card on you ubuntu machine to the router AND a cable running from the windows machine to your router?

---

### Post by reckless2k2 on 2007-09-25
thanks for the hot tag.

---

### Post by bemahesh on 2007-09-25
rebooting machine
However, when i ran the command, here is the reposen i got




reading package lists ...done
building dependency tree 
reading state information done

E: could not find package network-manager-genome

---

### Post by bemahesh on 2007-09-25
both of them has dhcp address
and is set to asutomatic configuration dhcp

Also, i have wire running from router to the ubuntu desktop

---

### Post by bemahesh on 2007-09-25
How can i 
"There, enable your network card and set it to DHCP. DNS: put this in: 208.67.222.222 and 208.67.220.220"

put dns to the addresses you specified?  i don't see the entry for dns.  there is ip address, subnet mask and gateway adderss

---

### Post by reckless2k2 on 2007-09-25
so your still unable to get to the internet? even after reboot? did you put in the DNS address and enable the devices? 
 

what version of ubuntu are you running?

dns is in advanced tab or farther down the tab line i'm pretty sure.

---

### Post by bemahesh on 2007-09-25
where do i put dns address?  where do i get it from?

---

### Post by bemahesh on 2007-09-25
no, i can not still get it work.  I see the dns tab.  HOwever, when i try to add dns servers, it doesn't let me.

i am adding 192.168.2.1  is this correct?  i deleted the default one which is 192.168.1.1

is this write or something else is needed

---

### Post by bemahesh on 2007-09-25
I am still unable to solve this issue.  Please help me resolve this.  

how do i find the version number of the ubuntu installed?

---

