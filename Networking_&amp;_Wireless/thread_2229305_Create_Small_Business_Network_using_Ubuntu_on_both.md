---
title: "Create Small Business Network using Ubuntu on both Server and Clients"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by HughQugh on 2014-06-12
I have been tasked to create a small network for a clinic. There are 5 computers that will be connected to the network and a server. The requirements are pretty simple:

- An intranet based solution for management of medical records/patients/physicians (I'm considering Open-EMR: [http://www.open-emr.org/](http://www.open-emr.org/) )
- A file server with different permissions for different users (I'm thinking SAMBA)
- Possibly a local mail server (postfix?)
- Possibly a LAMP stack to setup a very simple web interface for managing emails, private messages and file transfer between users (or something more complicated like Alfresco)

I have setup several Windows networks in the past and I am familiar with the Active Directory and centralized user management. However, since in this case the cost of the OS is a problem (my clients want to be completely legal and keep the budget as low as possible) I was thinking about building the whole network using Linux Machines. 

My questions are the following:

What hardware is usually recommended to setup a network like the one that I described above? For example, will I need a switch or I can plug everything in the LAN sockets and just setup one machine to act as a (DNS, HTTP, FTP, SSH) server?

What software is essential for setups like this? I have read a lot of good thinks about Puppet (and I think the Enterprise edition is free for up to 10 nodes). 

One very important aspect of the network is to give me the ability to perform administration tasks remotely. I will be using SSH of course, but are there any Remote Desktop solutions that I can implement in an Ubuntu machine?

I know that there are a lot of stuff that need to be done and explaining everything takes time, so if you could point me to a book/tutorial that contains information on how to setup an Ubuntu-only network, I would be really grateful.

Thanks in advance

---

### Post by grahammechanical on 2014-06-12
I have no experience in the area. We, basically, have two editions of Ubuntu. A desktop edition with a graphical user interface (GUI) and the usual desktop applications, and also a server edition without a GUI but with various server type applications.

There is nothing stopping us from installing server applications onto a desktop installation of Ubuntu or from installing the Ubuntu desktop on to a server installation of Ubuntu. This community document will explain about remote desktop access using the VNC protcol.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

This also might help

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

Ubuntu 14.04 Long Term support (LTS) version will have support for five years and the desktop version has Reminna Remote Desktop Client as part of the default installed applications.

[http://remmina.sourceforge.net/](http://remmina.sourceforge.net/)

Regards

---

