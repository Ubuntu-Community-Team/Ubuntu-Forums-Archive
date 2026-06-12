---
title: "try to set up ssh"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by scottc992004 on 2008-03-23
i'm following a guide to set up ssh but when i type in  i get:

mdk@mdk:~$ ssh localhost
[COLOR="Red"]The authenticity of host 'localhost (127.0.0.1)' can't be established.[/COLOR]
RSA key fingerprint is c2:96:f9:d3:8c:04:29:c6:42:a7:3e:7c:49:31:4d:e1.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
mdk@localhost's password: 
Linux mdk 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sun Mar 23 15:42:19 2008 from localhost
mdk@mdk:~$ 


here is the guide i'm following

[http://php.8ez.com/drsmall/blog/?p=124]("http://php.8ez.com/drsmall/blog/?p=124")

If you can help me to see if what i'm doing is correct that would be great.

---

### Post by Eiríkr on 2008-03-23
What you've shown is a normal first-time connection over ssh.  Sure doesn't look like anything is wrong.  :)

Cheers,

Eiríkr

---

### Post by scottc992004 on 2008-03-23
I have made an address from DynDNS. I Have a linksys router model WAG54G v3. I have given the address the ip of my laptop but should i give the address the ip of the router?

I have tried to access my computer from the internet but it doesn't work.I have firestarter installed and have attached some pics of it. where am i going wrong?

I also have two screenshots of my port forward for the router. I noticed msnmsgr has a number added on its ip address but port 22 doesn't have that. can i add any number to port 22?

---

### Post by Eiríkr on 2008-03-23
Your laptop IP address is likely something similar to 192.168.0.xxx.  This is a LAN-only address, probably assigned by your router, and is useless for DynDNS.  You'll have to find out what your external IP is.  The online security website [grc.com](http://www.grc.com/default.htm) is a good place to go for this; scroll down to the "Shields Up!" link, and this should show you your external IP.  This is what you'd need to plug into DynDNS.  However, since your IP will change over time, you're better off using any dynamic DNS settings available in your router -- many consumer-grade routers now have DynDNS compatibility built in.  

The IP addresses shown in your router have the basic subnet (the part that doesn't change) displayed as 192.168.0.  The numbers in the text boxes refer to the actual hosts on your subnet.  Ostensibly your Ubuntu machine is at 65, or 192.168.0.65 in full IP address terms.  If you want to have port 22 on your router forwarded to port 22 on your computer at this IP address, you should definitely add 65 to the text box for that port.

HTH,

Eiríkr

---

### Post by casperlingus on 2008-03-23
I've had this setup at home for a while, so I should be able to solve most of your problems.   But the key is understanding general network/IP concepts.  I'll provide a quick lesson:

1)  All computers on the internal network, connected to your router, have *local* IP addresses, in the range 192.168.*.*, usually assigned by your router through DHCP.  **These addresses are irrelevant outside your house/network**.   
2)  Your router is both on the internal network (usually 192.168.*.1), and is also the gateway to the outside world (*the internet*).  It has an unique external address visible to the internet, which is used for communicating with other servers and websites.  Your ISP provides you this address, and you can see it yourself by going to [www.whatismyip.com](www.whatismyip.com)
3)  When your computer accesses a website, it sends a request to the router, which records your internal IP (192.168.*.*), sends the request to the desired website with the *external address*, the website returns the desired info to that external address, and the router forwards it back to your computer on the internal network.  
4)  The point of port forwarding is for when a computer on the outside wants to access a computer on the inside, but the internal computer didn't send out the initial request.  This is precisely what happens when you try to open an SSH session to your home computer remotely.  Since the internal addresses are irrelevant from the outside, you set up port forwarding to tell the router that all traffic to a certain port should be forwarded to you computer (I'm not sure about the difference between UDP and TCP, try both).
5)  Therefore, you set up a static IP address on your main computer (below),  then you tell the router to forward all traffic sent to port 22 from the outside world (default port, can be changed if desired) to go to your local IP address.  If you have set up your computer correctly, you should be able to access it from the internet using the external address, or ssh to it from another computer in your house using the 192.168.*.* address.
6)  "localhost" is simply your own computer.  By typing "ssh localhost" you are requesting to ssh into the computer you are currently using.  There isn't much use to doing it (since you're already logged on), but it can be used to test ssh settings.

There's a extra complexity with the fact that your ISP may change your external IP address day-to-day (not sure why).  You don't usually notice, because when you send out a request to a website, the external address is always checked before sending the request, and rarely changes by the the time the website responds.   But for SSH where there is no initial request from the inside, you need a consistent way to always the external address of your home router ([www.whatismyip.com](www.whatismyip.com)).  This is what DynDNS does...

For now, just set it up as if you had a static, non-changing external address.  It will probably work for a couple days until your ISP changes your address, but at least you'll know that everything else works, and then you can deal with the DynDNS complexity.

For all this to work, you'll want to set up your machine with a static *local* IP address so that it will *always* have the same local IP address (it ensures that port forwarding won't break, the router always knows your IP address).  I demonstrate how to do this below, with /etc/network/interfaces
 
My /etc/network/interfaces file is copied below.  Adjust it to your liking.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.120
netmask 255.255.255.0
gateway 192.168.2.1
```
After you change this file, type the following command to put the changes into effect:
```
/etc/init.d/networking restart
```
You can type ifconfig to see if it worked.

Next, go into your port forwarding dialog on the router and select to forward port 22 to port 22 of your local IP address (in my case, 192.168.2.120).  

Visit the website [www.whatismyip.com](www.whatismyip.com) and write down the address it shows, in my case, it's 71.92.175.111.  You should be able to type "ssh username@71.92.175.111" and it will ssh to itself.  Again, you're just ssh'ing to the same computer you are currently using, but it verifies whether it is all setup correctly.  If this works, you should see something like you saw in your first post.  If so, then you should be able to go to a friend's house and use the exact same command to get onto your home computer.

DynDNS is another issue altogether.  Get the stuff above working first, then deal with DynDNS. 

-Casper

---

### Post by scottc992004 on 2008-03-23
ok i setup the DDNS Settings to DynDNS.org and host name as my address and it says DDNS is updated successfully. And set up 65 for my port 22. tried it but it wants access to my router not the computer how do i get it to go to the computer. attachment of login.

---

### Post by casperlingus on 2008-03-23
You are confusing SSH with HTTP/webaccess.  When you set up your computer to accept ssh sessions, you are not setting up a website that allows access via web-browser.  You are simply providing *yourself* a way to access your own computer via command-line.  You could also provide a few close friends with login-names and ssh access to be able to log in to your computer too.  I do this, for big file transfers ("I put a file in your home directory on my computer", and they ssh in and grab it).  But this requires someone to have a username/password on your computer.

If you want to set up a webpage/webserver, look into apache (although, you will still use the port forwarding feature on your router).

If you think you are set up correctly, you should be able to SSH (using "ssh" from a command line) from a computer outside your network, in. 

Try typing "ssh hax099.homelinux.org" and see if it logs on to your own computer (you will get the authentication message asking you to accept, just type 'yes'.  this only happens once).  If this works, then try it from another computer.  

If you're not familiar with the command line, using ssh in this manner may not be all that useful.  Although, if you "sudo apt-get install gftp" you can use that program as a graphical interface from another computer to xfer files back and forth.

---

### Post by kevdog on 2008-03-23
ssh really just gives you a login shell on the server.  You can create tunnels using ssh to send data encrypted between client and server using different ports that other programs can access if you want.

What exactly do you want to set up?

---

### Post by scottc992004 on 2008-03-24
I want to be able to get access from work and other computers at home to get files like music, movies and general documents. do i need to use firestarter for ssh?

---

### Post by scottc992004 on 2008-03-24
this is what i get from terminal from my other ubuntu computer 

mdk@mdk1:~$ ssh [email]mdk@hax099.homelinux.org[/email]
ssh: connect to host hax099.homelinux.org port 22: Connection refused
mdk@mdk1:~$ 

Does this mean my settings in my router aren't correct? Do i sent the port forward to the ip of the laptop?

---

### Post by kevdog on 2008-03-24
Means one of many things (with how to test)

1. DNS lookup error <-- Might try to connect be IP address rather than by name hax099.homelinux.org
2. Your router is not port forwarding port 22 to your server running the ssh daemon <---Check router settings
3. Your firewall on your machine running the server is blocking incoming connections on port 22 <-- Verify settings of the IPtables or by using Firestarter, Guarddog GUIs (which interface with the IPTables)
4.Your ssh server is not listening <-- Verify the deamon is active and listening on port 22

---

### Post by casperlingus on 2008-03-26
Did you install openssh-server?

Typically you get that kind of response when openssh-server isn't installed on the target computer, or if you tried to connect to the wrong port (which shouldn't be a problem since you are using the default port).  I get the feeling that you would get a different message if the port-forwarding settings were incorrect, but it doesn't hurt to continue playing with that.

---

### Post by Eiríkr on 2008-03-26
@casperlingus --

It seems clear that scottc992004 has ssh installed and running, given that in the first post here in the thread he shows that he can log in just fine when connecting to localhost.  

@scottc992004 --

Could you please post the contents of your [font=courier]/etc/ssh/sshd_config[/font] file?  One possibility is that your ssh daemon might be configured to only accept connections to certain IP addresses, which should be apparent by looking through this file.

Cheers,

Eiríkr

---

### Post by scottc992004 on 2008-03-28
how do i configure ssh i installed ubuntu 8.04 and forgot the comand line. I have moduli file and a ssh_config file showing:



# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

---

### Post by Eiríkr on 2008-03-28
Maybe I'm looking in the wrong place, but a number of the options shown here don't seem to show up in any man page I can find for sshd_config... :confused:  

Are you using the default ssh package in the Ubuntu repositories?  If so, I think that's OpenSSH, and the man page for this sshd_config is [here]("http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config").  I don't see any of these options listed in this man page:
```
Host *
SendEnv LANG LC_*
HashKnownHosts yes
GSSAPIDelegateCredentials no
```

That aside, the man page also notes:
> Arguments may optionally be enclosed in double quotes (") in order to represent arguments containing spaces.

This would seem to suggest that your SendEnv line should look like this (assuming that it's a valid option for your version of ssh):
```
SendEnv "LANG LC_*"
```

Cheers,

Eiríkr

---

