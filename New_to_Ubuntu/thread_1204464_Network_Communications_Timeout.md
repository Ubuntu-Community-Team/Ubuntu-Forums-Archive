---
title: "Network Communications Timeout"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by contax on 2009-07-04
I have a Media-Server 9.04 with Gnome, which was working just fine.  I could upload/download and stream to various devices and Windows/Linux and Mac computers.

Now, upon initiating a download the communications timeout.  If I begin the transfer on the Media-Server the transfer begins and a few gigabytes later communication is lost.  This is a problem on the server side in that it happens with Mac and Windows machines.

My permissions remain intact, including viewing permissions on the windows machine to reveal that everyone is allowed to read and write.

Where might I look and what might I do to investigate/remedy this communications timeout?

Thanks..

---

### Post by cariboo on 2009-07-06
What changes occured before networking stopped working. If no changes were made ie: updates, configuration file changes etc. It might be an idea to try another nic.

---

### Post by contax on 2009-07-06
I re-installed the 9.04 Server and have had varied success in copying 20-50GB ISO files.  Perhaps it is hardware.  I have been using the Gigabyte connection provided by the Intel Atom 330 motherboard, but it does have one PCI slot and I have lots of old Gigabyte cards, so if no other suggestions come my way, this sounds like a reasonable option.

---

### Post by contax on 2009-07-06
I replaced the motherboard, which contains the GB NIC.  Same results, but I noticed that the communications doesn't stop at a set time, or set GB transferred.

Could I be running out of resources which end the transmission?  I know that this is software in that changing all the hardware, except hard drive and power supply didn't fix things.  Also, I know that it is a problem with this server in that the same thing happens with all computers..at least Mac Leopard and Windows Vista via Samba.

---

### Post by contax on 2009-07-06
Assumptions can be deadly.  I assumed that I had a Samba problem and then a hardware problem.  I'm not sure of the why, but it seems that I had one mounted partition full of files that could not traverse my home network.  When I moved new files (not originating on the Ubuntu Server) to and from, they seem to work just fine.  What is strange is that I copied all of these files to another drive and they still won't transmit without timeout.  For now, I have been moving new large files over the network and will see if this ends my problem.

Thanks for input and I'll be back should this limited success unravel.

---

