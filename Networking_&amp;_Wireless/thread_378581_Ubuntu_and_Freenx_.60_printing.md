---
title: "Ubuntu and Freenx .60 printing"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by asosa on 2007-03-07
So I got latest freenx 0.60 onto Ubuntu and was able to connect with Nxclinet 2.10 - awesome technology. 

My thought was to build debs for all the servers I host and use the latest freenx and really push to convert all the fedora, and pclinuxos and window based servers we have to ubuntu maybe even build a custom ubuntu with freenx already installed to help companies and ourselves build terminal servers off of cd easily. I really want to build a basis to sell ubuntu to enterprises in chicago and having worked in and help build datacenters, I want to massage ubuntu into a viable terminal server. I've gotten this to work for fedora as well as pclinuxos but I really love ubuntu and want to get it to work on it. I want to go all ubuntu and get rid of my RPM hell.

BUT --- :) ran into my first stumbling block. Let's just say I have spent the better part of the last 4 weeks on getting the code from freenx.berlios.de and nomachine.com to compile and build me nice binaries. I love to code and spend most of my time coding but getting this to compile was a pain. Anyone else who has tried , knows what I mean. Anyone else need the debs, let me know and I'll forward them to you. I found abunch of sites with older debs but I wanted the newer .6 serverside and new 2.10 nxclient for window clients.

So...
I have my server up and even tested it both with the Nxclient for linux, windows and on my little 'ole mac.
I tested both the native and of course the web embedded java client. Works great. Within the sessions, I have Wine serving my window apps as well as all my fabulous linux apps.
Great way to showcase the technology because the company you are prospecting doesn't even need to install or boot ubuntu off cd - just go to a website and login and you get a virtual desktop running and showcasing linux technology as well as linux technology that runs window applications. 

NOW on with my issue - My issue being of course on window's client side. MIND you it works if I use the nomachine Nxserver just not the opensource freenx server. It is also noteworthy that nomachine's offers a 2 user version of their nxserver for free but I need more connections than just 2 and the freenx project is based on the code so I want to get that working than buying the solution thru nomachine.

I can connect from windows - I have sound and display works great but have not been able to print remotely from my Window Desktop - SP2. 
Following things I have done:
I shared the printer out - calling it printer1 I then went into NXClient and added it to my shared printers.

When I login to server I get an xmessage that says 'Choose vendor for printer printer1' but it never allows me to add or choose printers. 

I have been troubleshooting for a couple days now and yesterday I tried sharing out a folder from my xp machine in the ncxlient called apps

Now when I login I get the same xmessage about printer and now I also get a xmessage saying" Share://master1/apps' failed to mount: Error connecting to 127.0.0.1 24559: Connection to master1 failed: SMB connection failed.

So I know the client and server are communicating about the share but there is obviously some problem with the communication.

I went online and tried to find help in google, etc and I received a lot of different confs for node.conf

Some of the options I tried are
ENABLE_FILE_SHARING = '1'
ENABLE_CUPS_SUPPORT = '1'
I even tried MOUNT_SHARE_PROTOCOL = "cifs"
But it looks like the freenx server does not support these commands as I get and error connect from the nxclient on windows

'/etc/nxserver/node.conf: line 392: ENABLE_FILE_SHARING: command not found
/etc/nxserver/node.conf: line 393: ENABLE_CUPS_SUPPORT: command not found
/etc/nxserver/node.conf: line 397: MOUNT_SHARE_PROTOCOL: command not found '

Any help would be really appreciated - I even jumped on the freenx mailinglist the last 2 days as well and some of the guys had the nerve to tell me to just use fedora cause it just works. 

Anyways if anyone has any thoughts or has seen this before or got this working on ubuntu let me know.

Thanks

Antonio Sosa
[http://www.ansotech.com](http://www.ansotech.com)

---

