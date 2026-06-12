---
title: "Create a File Server ?"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by ROUBOS on 2007-09-03
Hello people.
I need some help from you people on how to create a File Server.

I have 6 Dell Machines running WinXP Pro. And I have my cool UBUNTU 7.04 Box.:)

Now what I want to do is turn my Ubuntu box into a File Server. I would also like to make my Ubuntu Box to control the internet for all those 6 WinXP machines.

To network them I have an ADSL Router and a 16port DELL Switch. 

How do I go about setting it up? How do I get the Ubuntu Box to assign IPs to the WinXP systems instead of the ADSL Router? Or do I leave it as is. 

My ADSL Router assigns IPs like : 192.168.2.2

It would be good if my UBUNTU box could assign the IPs and control the machines that get internet or not. 

The most importend thing I want to achieve is a File Server for all those machines to save data on my Ubuntu box so I can backup etc.

Any help would be greatly appreciated.

(I just ordered a book "UBUNTU 7.04 Unleashed" and will look into that aswell)

---

### Post by ROUBOS on 2007-09-04
no one?:confused:

---

### Post by Sendervictorius on 2007-09-04
That's a lot to ask in one post. A good start would be to read about it in the commmunity documentation: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

The brief answer to how to do these things is:

0. Setting up the ubuntu box as a file server is easy once you have the network configured. You set up your ubuntu box as a samba server to allow the windows pcs to access files on the server. (see documentation)

Networking: You should do some research and googling to understand what is going on. My comments are just a pointer to the things you need to investigate. 

Physically, just plug the ADSL, dells and ubuntu box directly into the switch.

1. You set up an local network between all your Dell machines and your ubuntu box. You can either set up a DHCP server on your ubuntu box to assign IP addresses to the windows clients, or set each up with static IP addresses. 

2. You will need to use a separate IP address range between your ubuntu box and your ADSL gateway. If your ADSL Router assigns IPs like : 192.168.2.2 I would suggest having a local Network using IPs in the range: 192.168.0.*

3. If you only have one physical network connection to your ubuntu box, you will have to create a virtual NIC so that your internal network can use a different IP range to the one connecting to your ADSL router . Use the ifconfig command. something like: "ifconfig eth0:1 <ip> <subnet> <gateway>". 

4. You might also like to give each client a name - and set up entries in /etc/hosts so you can access the Dell boxes without having to remember IP addresses.  Similarly in each Dell you can set up Hosts file entries (C:/windows/system32/hosts, I think - long time no windows!)

5. You will need to set up your ubuntu box to do Network Address Translation (NAT) to allow your windows pcs to connect out to the internet via the ADSL network. I find an easy way to do this is to install firestarter on your ubuntu box and follow the wizard when you run it for the first time.

6. You may have to change the routing rules in your ubuntu box. This is done with the "route" command line entry. Type "man route" for help. The routing rules you establish will depend on what you want to do. If you understand IP addresses, subnets and gateways, it should be fairlly self explanatory.

You could leave your ADSL router as it is, and pick up the assigned address, or just set up your ubuntu box with its own static IP address. It doesn't matter, as long as your internal network is on a different subnet to your ADSL, so that "route" and NAT will work.

---

### Post by ROUBOS on 2007-09-04
Thanks for the information. Will look into into it.

Thanks :)

---

