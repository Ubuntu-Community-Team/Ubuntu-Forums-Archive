---
title: "HELP setting up a LAN"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by openheart on 2008-02-22
Hi  all I was hoping for some really basic guidance about setting up my LAN here. I can follow the how to pretty easily but am unsure as to the values needed to enter into the various fields due to my basic lack of understanding on how networks function.

I have two older machines here. The both have Ethernet cards. On machine is running Ubunto gutsy gibbon and the other Edubuntu gutsy gibbon. I have the cat 5 cabling from both machines running to a D-Link fast ethernet swithch. 

First question: Do I need a router or will this function in some way with my setup. I know in the past I was able to connect two windows (yuck) based machines and was able to get it working with this hardware (ie: Internet connection sharing).

Second question.is there a quick way to get both machines talking to each other?

Third: what are the alternatives to setting up static ip adresses for both machines?

In short... help!

---

### Post by Iowan on 2008-02-22
1) Switch should be adequate.
2) Depends on what you mean by "talking to each other"... File sharing?  NFS, Samba, SSH. 
3) DHCP (Dynamic Host Configuration Protocol).  One of the machines will need to be set up as DHCP server.  For two machines, static is probably easier.

This is kinda blunt... sorry.  I need to get off computer and get errands run.  I'll try to check back later and (lacking other, better advice) fill in some of the gaps I've left.

---

### Post by openheart on 2008-02-22
No problem thanks for taking pity on me!

I was hoping for basic file sharing and a shared internet connection between the two.

Ok I thought static Ip would be easier as well.

Does setting up two machines require other information like DNS?

Ok thanks..
:)

---

### Post by carlxs99 on 2008-02-22
Dear openheart,

One big question, if I may?

What is the nature / interface of the internet connection you are trying to share?

Broadband through a USB or Cable modem? Or just broadband through a router?
If USB / Cable Modem, has the modem also got an ethernet port on the back as well as a USB interface.

Approach:
1) The first thing to do is get the computers talking (verified with ping commands).
2) Next you can install the two file sharing services Samba (also windows compatible) and the NFS service for linux file sharing.
3) Finally, you will create a routing table in order to forward the internet packets via the other computer's network connection.

Method:
1)
Connect the PCs to the switch using your two LAN cables.
PC1 (for arguements sake this can be the one with the internet connection to be shared) and PC2 (the one which will be making use of of PC1's internet connection),

PC1
-----
Goto: System --> Administration --> Network.
Left click on the 'wired' (local area network) connection and then click properties.
Untick 'enable roaming mode'.
Under configuration settings, select 'Static IP address' for the Configuration type.
IP address: 192.168.0.1
Having entered this, clicking on the subnet mask will be automatically generated as: 255.255.255.0
Leave Gateway blank for now (for a very small setup is fairly reasonable to assume that consider gateway, DNS etc.. to be internet only settings so you can leave them until part three.
Click 'Ok' to confirm the entries.

PC2
-----
Goto: System --> Administration --> Network.
Left click on the 'wired' (local area network) connection and then click properties.
Untick 'enable roaming mode'.
Under configuration settings, select 'Static IP address' for the Configuration type.
IP address: 192.168.0.2
note: the reason that all of the digits are the same apart from the last segment is to ensure that the clients (the computers) can talk to each other directly without the need for any clever or advanced network setup (one could, just as well, have 192.168.1.5 and 192.168.1.34. The key is that the last segment (in the last example that was the five and the thirty four) is a value from 1 to 254.
Having entered this, clicking on the subnet mask will be automatically generated as: 255.255.255.0
The gateway will be the IP address of PC1 (192.168.0.1)
Click 'Ok' to confirm the entries.

On PC1 Goto: Applications --> Accessories --> Terminal (open a new terminal)
Type :
ping 192.168.0.2
If packets are returned then you have got a connection between the two computers.
Press ctrl + c to cancel pinging (as otherwise it will keep looping)

Do the same from PC2 but instead type:
ping 192.168.0.1
...

2) Goto: System --> Administration --> Shared Folders
If you have not already installed the file sharing service you will now be prompter to do so. Choose to install samba and NFS (assuming that you also have a valid internet connection hooked up to the computer at this point in time!!!)
When the installation is complete, you will be able to choose shared folders etc..
The new shared folders window should be open, click on the 'Shared Folders' tab and then click 'add'.

Set: Share Through to NFS. Click on Add under 'Allowed hosts' and change the setting for 'Allowed hosts' 'Specify Hostname' to 'Specify IP address' and then use the IP address of the other PC.

3) It is getting late now (~3am). I will give you some more help later perhaps.
Bye for now! 

Good Luck.

---

### Post by openheart on 2008-02-23
Thanks so much! I am now able to ping the two computers from either computer!. Ok I tried installing shared folder services on one computer and it went great. I cant seem to install the service on the second computer becasue I think it is looking for internet access. So I will try connecting it up to my aircard.. Oh you asked about my internet connection.. It is a sierra Wireless modem running in a USB port using KPPP . Once again thanks so much I will report back with progress

---

### Post by openheart on 2008-02-23
latest update here... I WAS able to install shared folder services on the pc connected to the internet via KPPP. (The one running edubuntu) I even followed the directions supplied and gave it the other pc's IP adress using NFS. On the other computer I was not able to do this as that machine is not connected to the internet. The next question is..

1. Do I have to install shared folders services on the second computer? 

if I do then I will have to configure it to use KPPP and set it up to use the sierra wireless modem that I am using (a royal pain in the but!)

Please let me know what your recommendations are.. also many thanks for all the help so far! Many thanks..

---

### Post by Iowan on 2008-02-23
I suspect you'll need the services on the 2nd machine, too.  I think there's a how-to around here somewhere for internet-sharing - the 2nd machine could access internet through 1st machine for upgrades, packages, etc.

---

### Post by openheart on 2008-02-23
I am guessing the same as well.. that ICS might take care of the upgrade to the second machine.. I hope so becasue I am having NO LUCK by giving the OS all of the dependencies it is asking for manually ARGGHH! That would make it easier to get KPPP on the 2nd machine which is what I have been using in conjunction with my sierra wireless card. My head hurts!

---

### Post by openheart on 2008-02-23
I am a little ahead now.. I am currently browsing the internet via my second machine.. I found I could ping both machines from either end but could acess internet untill I tried typing an IP adress from the second machin and whamo it worked so that told me the second computer was not configured with a DNS so I found the adress of a static DNS server ns1.quasar??? andgave that to the dialoug box for the ethernetport I was plugged in to so now I can browse the internet from here but the saga continues.. I can not upgrade the machine from this connection.. I guess thatis the next problem to work on. I know I have active http service (through port 80?) maybe the upgrade services require ports that are being blocked on my other machine by firestarter? any suggestions.. I really need to install the shared windows service so that I can browse the other machine and vice versa,,

---

### Post by carlxs99 on 2008-02-27
Hey, sounds like you are really winning. Glad to hear it. Try going to terminal and typing:

export


you should see the 'current environment variables'. you may have some joy by changing the http_proxy variable.

you can type:

http_proxy="xxx.xxx.x.xxx" etc... (just like you did for the http proxy setting for your web browser).

This is know as 'exporting the global proxy'. Try pinging this proxy address afterwards and see what happens. This, I think, should point to the IP address of the gateway (the one which is running the internet connection sharing service, i.e. the one attached directly to the USB modem)

I am guessing that you put in manual settings for the browser, say firefox (which I am guessing you configured by edit-->preferences-->advanced-->network and then entered in the connection details etc..)? Or did you do it by manually adding the gateway, DNS servers to the network adapter settings? Or both?

The operating system itself also needs these settings so that apt (the package manager that is trying to install those network sharing services, samba and NFS) is also able to connect. Just a quick thought. If have been to vague please ask me to explain again. 

Glad that the initial post helped you get the ball rolling. (Since you are able to browse there will definitely be a way of getting apt to work. I am fairly sure this is the correct line of attack!)

Tell me how you get on.

Regards,

carlxs99

---

### Post by openheart on 2008-02-29
did not want to leave this thread hanging but did want to say thank you to all the great people out there willing to help. I have since been able to update the second machine via the internet connected machine so all is well there.. unfortunately never did have any great luck with getting the shared folders services working and while I was able to browse the internet and update the second machine I could not seem to view files from the other machine.. oh well.. I may have to leave this one as I have discovered a disconcerting thing... I have a 100 GB drive on this machine and Ubuntu is reporting only 89 GB of the drive! what happened.. oh well on to another forum,,

---

