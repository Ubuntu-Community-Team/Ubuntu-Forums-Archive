---
title: "Remote printing from ubuntu to ubuntu or windows"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-08-30
[FONT="Book Antiqua"][/FONT] I am using Ubuntu jaunty Jackalope in my Dell optiplex 500 MHz 512 MB RAM 86 GB HDD quite some time. Now I am contemplating a telemedicine project for which it would be necessary to print a file created in my computer's word processor program through a printer attached to a remote computer which is connected to my computer by internet.

The remote computer can have either ubuntu or windows as os.

Please show me the way to do this.

Thanks.

---

### Post by halitech on 2009-08-30
WAN (Wide Area Network) printing is not a simple thing to set up. Do you have access to the printer(s) in question physically along with the router/firewall? What kind of printer(s) will you be printing to? It might be easier to produce a pdf and send it to the other computer and have someone at the remote location print it there.

---

### Post by DFlame on 2009-08-30
In other words, it's going to look a bit like this:

```
Printer <- Remote Machine <- Firewall <- AP <- [Internet] <- AP <- Local Machine
```

Where AP is a router or modem.

[center]**Method**[/center]
If we say that the remote machine is using Ubuntu (as it will probably be easier), you will have to [set up a printer](https://help.ubuntu.com/community/Printers) and [share it on the network](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu).

Next, I would [install Firestarter](https://help.ubuntu.com/community/Firestarter) (a firewall GUI) and set up a rule to only allow incoming connections on port 631 (Internet Printing Protocol) from your client computers IP address. If the AP is a router, you'd also have to configure that to forward port 631 connections to the machine.

With security in place, I'd take a note of the IP of the computer with the printer with [whatismyipaddress](www.whatismyipaddress.com) and head over to the other computer (the local computer in the diagram). In a browser like Firefox, I'd enter this into the address bar:

```
http://remote.machine.IP.address:631
Example: http://137.241.9.87:631
```

If everything above is set up properly, I will see the CUPS page and browse to find my printer. Following that, I'd add the printer by System -> Administration -> Printing, clicking "New", expanding "Network Printers" then selecting "Internet Printing Protocol (ipp)". In the box asking for an IP address, I'd enter the IP address of the remote machine and click "Find Queue". After that, I would select my printer and add it by following the prompts.


That is by no means the definitive way of doing it. It all depends on your hardware, whether you have dynamic IP addresses (which will affect firewall rules, whether you need a DynDNS domain etc), time and patience. If it has to be super secure, I would also throw in an SSH tunnel for good measure.

---

### Post by t_k_majumdar on 2009-08-31
Thanks to both halitech and DFlame for replies. From DFlame's answer, I got the glimpse of the hard work ahead for implementing this work successfully with the best possible security measure. I hope to do it gradually with help of ubuntu masters.

However, halitech has given a very practical solution. It is not ideal as documents of telemedicine like prescription must not be viewed by other person. It would be best if doctor can write the prescription himself and then print it before a remote patient for his collection.

---

### Post by t_k_majumdar on 2009-09-01
Before starting the project, I want to know whether it would be technically easier to take control of the remote computer, create and print the document through it instead of creating, sending and printing the document over Internet. 

To answer halitech, I intend to set up telemedicine facility at my own cost. Both the remote computer and printer will be owned and installed by me. So, I can choose any suitable computer or printer.

---

### Post by halitech on 2009-09-02
I'll admit I'm not familiar with telemedicine so not sure what its capable of doing. Generally speaking, using something like VNC to take control of a printer is easy but unless you enter the info on the remote system, its not easy to get printing to work.

As far as a printer, look into HP as they are about the most widely supported among linux.

---

### Post by DFlame on 2009-09-02
> **t_k_majumdar said:**
> Before starting the project, I want to know whether it would be technically easier to take control of the remote computer, create and print the document through it instead of creating, sending and printing the document over Internet.

Yes. It would be far easier to set up. Whichever way you choose to go, I'm sure I can provide help as I run a similar setup at the moment. Here's a shortened form of the steps you will need to take:

1. Pick a printer
2. [Check its compatibility with Linux](http://www.openprinting.org/printer_list.cgi)
3. Install & test the printer on the server via System -> Administration -> Printing
4. Install OpenSSH Server on server (Terminal -> sudo apt-get install openssh-server)
5. Install and configure [FreeNX](https://help.ubuntu.com/community/FreeNX) on the server
6. Perform any port forwarding required on the server ends router

7. As of FreeNX link above, install an NX Client on your local machine
8. Connect to your server using your server IP, user and password/key
9. Success

FreeNX allows you to take control of your server computer via SSH. It offers a viewing window much like VNC, where you can see and control the system as if you were sitting infront of it. In this window, you'd be able to create a document and print it.

When exiting from the viewer, you also have the opportunity to keep your session running on the server side, so you can pick up where you left off the next time you connect. I hope all that makes some kind of sense, just ask if you need further explanation of a specific point! :)

---

### Post by t_k_majumdar on 2009-09-02
Again I like to thank both halitech and DFlame for quick and informative replies. I shall now try to do it stepwise as explained beautifully by DFlame. Please keep an eye over the post as surely I shall need help on specific points.

---

### Post by Whiffle on 2009-09-02
You should be able to setup a ssh tunnel to print over the internet, or setup a VPN.  I think this would be much more productive than trying to use a VNC type solution.

For example:
[http://pigtail.net/LRP/printsrv/tunnel-how.html](http://pigtail.net/LRP/printsrv/tunnel-how.html)

---

### Post by t_k_majumdar on 2009-10-06
Sorry friends. Due to hard disk crash, I was unable to do any work. Now I have installed Ubuntu 9.04 in two test remote test computers, installed HP inkjet printers in them and configured the printer without any difficulty with ubuntu. Broadband internet connection was also set up in each remote computer. 

I shall report further development from time to time.

Thanks.

---

