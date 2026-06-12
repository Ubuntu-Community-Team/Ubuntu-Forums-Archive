---
title: "help setting up network"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2009-04-30
New to linux and never networked any two computers before so this is probably stupid.

I just got a router (linksys WRT54GL) and I want to setup a network between an ubuntu desktop (still on 8.10) and an ubuntu LAMP server (I want to learn LAMP).

I still have an old Vista partition on the ubuntu desktop machine. Should I run the linksys CD on that and hope that the settings will carry over to the ubuntu partition?

I'm concerned with securing the router since it's wireless even though I'm not using the wireless right now.

Oh, and I'm also a little bit concerned about having the LAMP server connected to the internet. For now I just want to be able to access it from the other machine for learning purposes.

Any advice on where to start?

Thanks!
Dan

---

### Post by lisati on 2009-04-30
Running the CD from Windows (Vista or whatever) can sometimes be of some help making sure that the basic setup is correct. I've done this a handful of times myself for my home network, and then when I started Ubuntu, there has usually been less need for tinkering with the settings.

I'm not familiar with the specifics relating to Linksys gear or LAMP, so I'm happy for others to share their wisdom on those issues.

---

### Post by Iowan on 2009-04-30
Perhaps a few links would be helpful:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server#Configuring_the_Apache_Web_Server_for_Your_Domain]("http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server#Configuring_the_Apache_Web_Server_for_Your_Domain")
[https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by NewbuntuUser777 on 2009-04-30
thanks for the links they're helpful.

I guess another question I have is about the ability of one computer to access another via LAN.

So if I hook both machines up to the router, they'll both be connected to the internet.  My ubuntu desktop is secure of course.  No worries there.  But, I'm not too sure about the server.  If someone were to access the server in theory would they also be able to get to the ubuntu desktop machine.  

I know this is not a server forum per se, but the ability to access one machine from another seems like an issue you all ought to be wise about.

Any thoughts?

---

### Post by handydan918 on 2009-04-30
If you are behind a router, it's going to require you to open a port in order to allow anyone in from the outside. 

If you don't do that, 
1) No one will be able to access your LAMP server...

2) No one will be able to access you desktop machine, either...

---

### Post by HermanAB on 2009-04-30
Hmm, if both your machines can access the internet OK, then the basic network settings are fine.

The easiest way to share files between two machines is with the good old FTP.  So as a first try I suggest that you get onto the Windows PC and look for the Filezilla web site.  Download and install the Filezilla Server and Client.  Open a DOS box and run ipconfig - write down the IP address.

Once the Filezilla Server is running on Windows, go to the Linux machine and run the file browser Nautilus.  Under the File menu, look for something like 'Connect to a Server' (I don't have Nautilus running sorry!).  Make a FTP connection to the Windows IP address.

La Voila!

Herman

---

