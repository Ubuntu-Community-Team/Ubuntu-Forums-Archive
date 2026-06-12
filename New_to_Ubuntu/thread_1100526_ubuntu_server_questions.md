---
title: "ubuntu server questions"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by mbrxjepp on 2009-03-19
Hi,

I'm looking for some help on how to install and configure ubuntu server on one of these:

[http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html#a15]("http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html#a15")

I know I can boot from a USB memory stick, but do I need to temporarily attach a keyboard and monitor? I have been told that if I install ubuntu desktop on my laptop and boot that (I'd have no problems doing this) I can configure the server through my laptop, and install additional programs such as squeezecentre. The laptop connects wirelessly to the router, and the server would be connected via ethernet cable.

Has anyone done anything like this? 

Cheers, 

Ewan

I'm

---

### Post by 505 on 2009-03-19
You don't need a keyboard attached. I think you also do not need Ubuntu on your laptop (although Ubuntu is a very good OS, so you might want to try it anyway). A lot of these servers run Linux, and you can connect to them using SSH. This is a sort of console or command prompt (do you remember MS-DOS?). You can have that in Windows too. It is a program called Putty. However, everything is command based, so you need some knowledge of Linux if you want to administrate your server this way.

---

### Post by mbrxjepp on 2009-03-19
Thanks for that. The barebones server I'm looking at has a pci controller in it, which I think I would need to enter BIOS to set up for RAID10, so perhaps a monitor and keyboard might be required anyway... 

Assuming the drives are successfully configured using the controller, if I connect it to my router via an ethernet cable and plug in a bootable USB mem stick and turn on the server (I think it is set to boot via USB initally), will I be able to just access it over the network immediately, and how would I do this? I thought that some configuration (esp. SSH) was needed, but I'd need access over the network in the first place to make these changes!

I think I might be way out of my depth here - I'd love to set up a server running Ubuntu, but I may just be the type of person windows home server was invented for :(

---

### Post by MrWES on 2009-03-19
I just set up a server a couple of weeks ago following this guide:

[http://howtoforge.com/perfect-server-ubuntu8.04-lts]("http://howtoforge.com/perfect-server-ubuntu8.04-lts")

You only need a hardwired monitor and keyboard to install the server. From that point on you can use ssh from either an Ubuntu desktop via the terminal, or puTTY (freeware) from a Windows machine.

I currently run mine headless and do everything via ssh. Give me a shout if you need help.

Bill

P.S. Oh..you can install Webmin, which is a GUI based app to maintain the server.
[http://webmin.com/]("http://webmin.com/")

---

### Post by mbrxjepp on 2009-03-20
Thanks MrWES, that's very helpful indeed. I'm trying to work out as much as I can before buying any hardware, but I think I need to get hands on with this to fully understand it. I do have a few questions in the meantime though!

1. It's going to be a home sever. It will be used as a central file store for all the other computers and for running squeezecentre to stream music round the house. It would also be good to access to server from work, or any other computer connected to the internet. I'm not planning on hosting any websites. Will I just need to select openSSH and samba during installation? Is it worth using the LAMP option?

2. After the base install, will my server connect to my network via the router without me doing anything else? I have a macbook, so can open terminal - how do I access the server using terminal? 

3. I found the following regarding Webmin:



First you need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Now download the latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb)

Now we have webmin_1.420_all.deb package install this package using the following command

sudo dpkg -i webmin_1.420_all.deb

This will complete the installation.


Regarding the apt-get command in the above, does this refer to packages that are loaded from the install cd, or do I have to get these elsewhere?


4. My server will be running 4 HDDs in RAID10. There is a 5th bay in the server case. Will ubuntu allow me to automatically backup folders (such as music, photos, work documents) to different HDDs slotted into this bay? For example, I name a HDD 'music' and configure ubuntu to recognise this drive when inserted and backup the 'music' folder to this drive. Even better, will ubuntu only update new or altered files to save time?


Sorry for dumping all this on you - I really am a beginner :(

Cheers!

Ewan

---

### Post by MrWES on 2009-03-20
> **mbrxjepp said:**
> Thanks MrWES, that's very helpful indeed. I'm trying to work out as much as I can before buying any hardware, but I think I need to get hands on with this to fully understand it. I do have a few questions in the meantime though!

1. It's going to be a home sever. It will be used as a central file store for all the other computers and for running squeezecentre to stream music round the house. It would also be good to access to server from work, or any other computer connected to the internet. I'm not planning on hosting any websites. Will I just need to select openSSH and samba during installation? Is it worth using the LAMP option?

2. After the base install, will my server connect to my network via the router without me doing anything else? I have a macbook, so can open terminal - how do I access the server using terminal? 

3. I found the following regarding Webmin:



First you need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Now download the latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb)

Now we have webmin_1.420_all.deb package install this package using the following command

sudo dpkg -i webmin_1.420_all.deb

This will complete the installation.


Regarding the apt-get command in the above, does this refer to packages that are loaded from the install cd, or do I have to get these elsewhere?


4. My server will be running 4 HDDs in RAID10. There is a 5th bay in the server case. Will ubuntu allow me to automatically backup folders (such as music, photos, work documents) to different HDDs slotted into this bay? For example, I name a HDD 'music' and configure ubuntu to recognise this drive when inserted and backup the 'music' folder to this drive. Even better, will ubuntu only update new or altered files to save time?


Sorry for dumping all this on you - I really am a beginner :(

Cheers!

Ewan

1. My server is a simple file and printer server, so I didn't install LAMP either at the initial install nor manually after the basic installation was completed. I only installed the openssh. That way I could immediately ssh into the box from my laptop. It would be best to assign your server a static IP, either from your router (which is how I did it), or through the network interface as described in the guide I posted. I ssh into my server from work, so I had to forward port 22, or whatever port you want, from the router to the server. However, that now creates some security risks, so I also installed Denyhosts to help prevent brute force attacks, etc. For music sharing, I'd look into mt-daap, which is what I run. It's a media server that shares my music over the network, which Windows machines running iTunes, and Ubuntu machines running Rhthymbox will see automatically -- runs great.

2. My server connected to the internet straight off. After the basic install, I edited the software sources list and ran sudo apt-get update && sudo apt-get upgrade. 

3. I don't have a RAID configuration, so I have no experience with that.

Bill

---

### Post by mbrxjepp on 2009-03-20
> **MrWES said:**
> That way I could immediately ssh into the box from my laptop.

There is probably an obvious answer to this, but how exactly do you do you access the server from Terminal? When I open terminal on my mac, I can navigate around the mac's system (changing directories etc) but wouldn't know how to gain access to the server's system and contents.

I think i'm happy with assigning a static ip address - there are plenty of guides on the internet as well as the one you posted. I'll have to look into forward porting though, I might be able to get some support from my ISP as they supplied the box.

I'm still a little unsure about the sudo apt-get update & sudo apt-get upgrade bit. What does this step do?

Thanks for all you help so far - i'm already much further on in my understanding that I was!

Ewan

---

### Post by MrWES on 2009-03-20
> **mbrxjepp said:**
> There is probably an obvious answer to this, but how exactly do you do you access the server from Terminal? When I open terminal on my mac, I can navigate around the mac's system (changing directories etc) but wouldn't know how to gain access to the server's system and contents.

I think i'm happy with assigning a static ip address - there are plenty of guides on the internet as well as the one you posted. I'll have to look into forward porting though, I might be able to get some support from my ISP as they supplied the box.

I'm still a little unsure about the sudo apt-get update & sudo apt-get upgrade bit. What does this step do?

Thanks for all you help so far - i'm already much further on in my understanding that I was!

Ewan

1. If you're running Mac OS X, the ssh client is built in. From your Mac terminal type ssh username@IP. If you're not on Mac OS X, there are several ssh clients [http://www.lysator.liu.se/~jonasw/freeware/niftyssh/]("http://www.lysator.liu.se/~jonasw/freeware/niftyssh/")

2. Normally to maintain and change settings to your router you point your web browser to [http://192.168.1.1](http://192.168.1.1) -- are you sure you have a router, or is it a cable modem? My system goes cable modem --> router --> server.

3. My ISP is Comcast Cable, I don't have a 'static' IP per say, but my IP has probably changed only once or twice. Anyhow, to be sure I can always connect from work, I signed up for a free Dyndns account at [http://dyndns.com]("http://dyndns.com"), and configured my router to use dyndns as a DNS server. Dyndns gives you a 'domain' ie xxxx.homedns.org and always updates that domain with your current IP address.

4. The server iso file only contains the basic packages, you must enable the multiverse repositories in the sources list and run the update command to install any updates that have been issued since the iso was released.

Keep banging those keys
Bill

---

### Post by mbrxjepp on 2009-03-20
Okay, I get it now with accessing the server via terminal. I assume the ip address is the one you set in step 7 of the guide (sorry, I know this is 'baby learning to walk' stuff!)

I definitely have a router. It's a wireless one provided by my ISP (o2, UK), and this is what I am going to connect the server to via an ethernet cable. The computers in the house connect to it wirelessly. I know how to access it via a browser, but it's not clear from the menus in there how to go about forward porting. I'll keep looking though!

Got it with the update/upgrade bit. Do I need to do this manually from time to time to stay updated?

So, if I have samba installed, I can connect to the router via Finder in os-x (found some guidance on how to do this) and browse the contents as I would with the mac's own HDD? Will I need to set a directory level as an 'entrance point' so I'm not dropping into root?

Also, how do I 'interface' with my files if I'm accessing from a computer at, say, work? Will the server show up as a drive in 'My computer' after some sort of login process?

Ewan

---

### Post by MrWES on 2009-03-22
You can use WinSCP or PuTTY to connect to your server from Windows. If plan on transfering files, I'd use WinSCP since it's over a ssh connection.

[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")

Bill

---

### Post by aago1254 on 2009-07-07
Hey dont forget you after you have all this stuff installed you need to set up samba and the premissions to access the drive thats where i got stuck 
 
im such a novice its kinda crazy gotta lot to learn myself

---

### Post by mahmoud_899 on 2009-07-22
Hello Guys,

Does any one know how to do the Reverse DNS?

---

