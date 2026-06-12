---
title: "Networking Project with Old P4 Machines"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by pasqualino31 on 2008-02-13
I have had the good fortune to have a couple of P4 machines dropped in my lap.

I'd like to take 1 and make a server out of it, but I've never done anything like this before.  I am a hardware engineer, so I'm good with the technical ins and outs; however, I am new to Linux.

I'm open for suggestions and I'm not afraid to break anything!

I have my regular gamer PC which i'm trying to make into a VM.  This machine has a HD with UBUNTU 7.10 installed on the Master and Win2k SP4 on the Slave.  I have had no luck running VMware on UBUNTU and making Win2k VM's. )

Anyway, I want to install 7.10 server on one of the P4 machines and run my gamer PC as a dual boot and use the second P4 machine as a general 32-bit Linux machine to screw around with.

I have a Rosewill Model RNX-G400 wireless router and want to use the server as a firewall.

any suiggestions?

---

### Post by Iowan on 2008-02-13
Download/burn a server-version.  My "new" server is running 6.06 LTS as a LAMP server.  My other server is still running Breezy (5.10?).  The older one does my DHCP, and runs SAMBA.  Unfortunately, the server version won't come with a desktop, but you can add one.  Howtoforge.com (link in my signature) has several server how-to's based on Ubuntu.

---

### Post by carverj on 2008-02-13
If it were me, given that you are new to the world of linux, I would start by focusing on the 32 bit regular installation. This is how you could build experience with windows/linux interoperability, networking, commands, application installation and so on. This forum will be your best friend unless you have a handy linux guru next door like I did : )
Saying that though, ubuntu makes it really easy to install and play with server technology. Personally I have a tri-boot workstation (Vista, Ubuntu - use it 90% of the time and Solaris 10 - trying to learn it...so different to linux so far!!) and a FreeNAS file server. I have setup Ubuntu with XAMPP so that it has web server development capabilites. 
Have fun!!

---

### Post by pasqualino31 on 2008-02-14
> **carverj said:**
> If it were me, given that you are new to the world of linux, I would start by focusing on the 32 bit regular installation. This is how you could build experience with windows/linux interoperability, networking, commands, application installation and so on. This forum will be your best friend unless you have a handy linux guru next door like I did : )
Have fun!!

Since it's a P4 machine there is little other choice than the 32 bit.  I downl;oaded the 32 bit ver 7.10 server version and will install it tonight.

> **carverj said:**
> Saying that though, ubuntu makes it really easy to install and play with server technology. Personally I have a tri-boot workstation (Vista, Ubuntu - use it 90% of the time and Solaris 10 - trying to learn it...so different to linux so far!!) and a FreeNAS file server. I have setup Ubuntu with XAMPP so that it has web server development capabilites. 
Have fun!!

Not familiar with XAMPP, I'll look it up before installing. [edit] XAMP ~LAMP  got it! :)

Thanks!

---

### Post by pasqualino31 on 2008-02-14
> **Iowan said:**
> Download/burn a server-version.  My "new" server is running 6.06 LTS as a LAMP server.  My other server is still running Breezy (5.10?).  The older one does my DHCP, and runs SAMBA.  Unfortunately, the server version won't come with a desktop, but you can add one.  Howtoforge.com (link in my signature) has several server how-to's based on Ubuntu.

I'm not sure what you mean by a "LAMP" server?  [edit] got it now LAMP = Linux, Apache, MySQL, PHP

I intend to install Ubuntu 32-bit 7.10 server tonight after sanding my hardwood floors (a different project! :)

I'm checking the howtoforge link now...

Thanks!

---

### Post by pasqualino31 on 2008-02-14
So I have successfully installed 7.10 server and have this cheezy little 40GB, P4 system set up as a LAMP server.

Now I want to set up my wireless network.  I have a Rosewill 54M wireless AP Router(RNX-G400)

I'm currently hard wired to the OOL modem.  I'm wondering what I need to do to make sure the server knows how to deal with DHCP with a router inserted between the server and the modem now.

Should I reinstall with the wireless router installed?  I think this is probably the way to go.

I need help!:(:confused:

---

### Post by pasqualino31 on 2008-02-14
I think I need to re-evaluate.

I think I'll leave the physical connection as is and configure a second NIC and connect this to the wireless router's WAN.

This seems to be the way to go.

After making the physical connections, what do I do?

---

### Post by carverj on 2008-02-14
Ah, so let's see you have set up wired network....
On to step 5 maybz: -
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by pasqualino31 on 2008-02-15
Ubuntu ships with a number of graphical utilities to configure your network devices.  

I'd like to install one of these graphical utilities.  I know that it seems a sacrilege to not work from the command line, but it's hard to get the ball rolling that way.  A graphical utility helps in getting things moving.

Any rec's?

---

### Post by Iowan on 2008-02-15
Do whatever works for you...
[This]("http://ubuntuforums.org/showthread.php?t=518554") is one option.  There are other desktops, too - including the "standard" Gnome.

---

### Post by pasqualino31 on 2008-02-15
I did the standard one found [here ]("http://www.howtoforge.com/lamp_installation_ubuntu6.06") but I failed to install webmin following their directions to the letter.  (Well I adapted to webmin 1.400)

I'm gonna try using the synaptic pkg mgr.

Linux is still really confusing.  I typoe the following after extracting the tar:

cd Desktop


cd webmin-1.400

./setup.sh /usr/local/webmin

I got an error saying the installer has to be run from root?

---

### Post by carverj on 2008-02-15
sudo su -
changes to root user
be careful with how used though

---

### Post by pasqualino31 on 2008-02-16
Well I have to thank you guys for your patience and appologize for being a stooge. 

So far I¨ve been directed to where I need to go and then I ask a question before finishing the research only to find my answer further on in the reading.  So I&#314;l be a little more dilligent in my reasearch before asking further questions.

Here&#347; what I have done so far:

  Working fom the howtoforge site I follwed the instructions for installing the desktop and then followed the howto for installing webmin. This did not work out and I had to modify it a little.  This cmd worked:

 apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

So now its time to figure some more stuff out..

When this is over I&#314;l write a howto!

---

### Post by sammydee on 2008-02-16
Don't worry about asking questions pasqualino, when you're new to linux there are so many things that are assumed knowledge that you just don't know - I remember what it was like when I was trying to get my head round it.

I always prefer to use aptitude instead of apt-get - it seems to cope with dependancy problems better and allows you to remove unused dependancies with an application ;-).

Everybody on these forums is happy to answer your questions, we WANT people to learn how to use Ubuntu :-D.

---

### Post by pasqualino31 on 2008-02-18
I tried a bunch of ways to do this, including the repositories method.  This was particuularly interesting because I had just learned (the hard way!) about how to access repo&#347; by editing the sources.list file.  I had struggled all night setting up my multi boot gamer machine to run Gutsy AMD64.  In order to get the flashplaer you have to do quite a rain dance.  

Anyway, after trying many methods I was able to DL webmin1.400 and installed it like this:


 sudo ./setup.sh /usr/local/webmin

That&#347; all!!!

Now it&#347; time to figure out Webmin.

Once again gang, anything come to mind?

I have one NIC going to my OOL modem and the second NIC going to WAN port of a  router (which will be wireless, but is presently wired.)  There are machines plugged
int the other lan ports of the router.

Nobody can see anybody host client or otherwise.

---

### Post by carverj on 2008-02-21
So you're saying that you have problems with your current network setup?
Have you tried using just one nic and router at a time and then seeing what you 
can ping to isolate the problem? Such as my setup which is a modem, connected to a router, which connects all the workstations. I can ping the IP address of the router first, and then the modem to see where the failure is if there is one!

---

