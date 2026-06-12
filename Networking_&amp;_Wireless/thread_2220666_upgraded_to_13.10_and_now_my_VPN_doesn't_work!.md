---
title: "upgraded to 13.10 and now my VPN doesn't work!"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by peredur2 on 2014-04-28
I recently upgraded to Ubuntu 13.10 and I've had nothing but problems with my PIA VPN ever since. I've spent a huge amount of time going over this with PIA's tech support but they've not been able to help me discover the source of the problem. Our account still works on all our other devices so that's not the issue. Only on my laptop. I can't get OpenVPN to work and can't even get PPTP to work.

First they advised me to try this:
> [FONT=Verdana, Arial, Helvetica][SIZE=2]1. sudo apt-get install openvpn
2. cd /etc/openvpn
3. wget [https://www.privateinternetaccess.com/openvpn/openvpn.zip](https://www.privateinternetaccess.com/openvpn/openvpn.zip)
4. sudo unzip openvpn.zip (sudo apt-get install unzip <-- may be required first)
5. ls -l    (see a list of the server config files)
6. sudo openvpn config-filename-goes-here.ovpn[/SIZE][/FONT]

My response:
> I have downloaded openvpn.zip however I can't seem to do anything    with it. I get the following messages:
    
    openvpn.zip: Permission denied
    Cannot write to ‘openvpn.zip’ (Success).
    peredur@Peredur:/etc/openvpn$ sudo unzip openvpn.zip
    unzip:  cannot find or open openvpn.zip, openvpn.zip.zip or    openvpn.zip.ZIP.
    peredur@Peredur:/etc/openvpn$ sudo apt-get install unzip
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    unzip is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
    peredur@Peredur:/etc/openvpn$ sudo unzip openvpn.zip
    unzip:  cannot find or open openvpn.zip, openvpn.zip.zip or    openvpn.zip.ZIP.
    
    I had previously downloaded the zip file but couldn't do anything    with it. I was still eventually able to get PIA working. I tried to    continue with step 5 and got this:
    
    peredur@Peredur:/etc/openvpn$ ls -l
    total 4
    -rwxr-xr-x 1 root root 1357 Jul 11  2013 update-resolv-conf

Then they had me attempt to set up the connection from scratch. That didn't work. They had me try various IP addresses for different servers. No luck. We added DNS addresses. Nothing. We tried adjusting the router settings. If anything, that just made it harder for the other devices to connect so we scrapped that. 

I'm really convinced that the issue lies within Ubuntu, that something is not set up right. The good folks at PIA are just not able to help me with that sort of thing so I'm turning to the Ubuntu gurus. Can anyone help me figure this out? 

Thanks! 8-)

---

### Post by sammiev on 2014-04-28
Save the zip file and right click on it and select "extract here". Those are the files you need for your VPN to work.

---

### Post by peredur2 on 2014-04-29
Sorry, I forgot to mention that I do have those files saved. I set up the VPN as per instructions but cannot connect. That's my problem.

In addition, when I had Ubuntu 12.04 and had my OpenVPN setup, I would see a list of servers (US, Canada, UK, Netherlands, etc). So far, I have been unable to duplicate that setup. Now, I seem to only be able to setup the VPN to connect to a single server (they had me trying US California). Maybe this has something to do with it?

---

### Post by lisati on 2014-05-05
OP has apparently upgraded to 14.04 and started a [new thread]("http://ubuntuforums.org/showthread.php?t=2222063") relating to this problem.

---

