---
title: "How to add Windows XP laptop to Linux Network"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by Stervyatnik on 2006-12-19
Hello, all!

I have successfully networked three Ubuntu boxes together using a DLink 8-port switch. I have one box configured as an Ubuntu LAMP server, just a standard "do the defaults" kind of install. I also have two Edubuntu workstations, which I've networked in. The server has IP address 192.168.0.1. The first Edubuntu has an IP address of 192.168.0.2, and the second has an IP address of 192.168.0.3. So far, so good, and I can ping from any box to any other box.

My goal is to eventually network all seven of my family's computers together, using the Ubuntu LAML Server as the server of choice. I am incrementally experimenting with bringing more and computers in, but have hit a roadblock. ](*,)

I tried to add my Win XP laptop. I unchecked all the networking protocols EXCEPT IP Address, and I assigned it an IP address of 192.168.0.4. I also - as on all the computers - assigned subnet mask of 255.255.255.0, and default gateway as 192.168.0.1.

Now, the Win XP laptop says it's connected, but I can't ping from it, nor can I ping it from any of the Linux boxes.

All the online help I've seen so far tries to "think for me" by saying I'm bringing a linux workstation into a Windows network, (when it's actually just the opposite), and they all assume I want to use the Internet. I do, but not until MUCH later.

Do I need to use Samba to bring the Win XP laptop into the Linux network? Or am I missing something basic? I'm a definite newbie to networking, but I can stumble my way through configs and such in the Linux world. Any help would be appreciated!

Thanks in advance!

---

### Post by bernied on 2006-12-19
Does the 'ipconfig' command in a DOS shell tell you anything useful?

When you say ping, are you pinging by name or IP adress?

What does 'ping localhost' or 'ping 192.168.0.4' give you?
Or 'ping 192.168.0.255' (not sure about this one, should be broadcast, all machines on subnet should respond.)

---

### Post by bernied on 2006-12-19
And have you tried a different cable and port in the switch? Or a linux live-cd? Just to rule out the hardware.

---

### Post by Stervyatnik on 2006-12-19
> **bernied said:**
> Does the 'ipconfig' command in a DOS shell tell you anything useful?

When you say ping, are you pinging by name or IP adress?

What does 'ping localhost' or 'ping 192.168.0.4' give you?
Or 'ping 192.168.0.255' (not sure about this one, should be broadcast, all machines on subnet should respond.)

From the server, I type:

   ping -c 5 192.168.0.4

I get five packets transmitted, none received.

From the C:\ prompt, I try to ping with:

   ping 192.168.0.1

And I get an error message, "'ping' is not recognized as an internal or external command, operable program or batch file."

I've pinged from other Win machines before, I wonder why it's not recognizing the command now? Did I mention I'm hating Windows more and more with each passing day? :-D 

I will try a live CD, but in the past, it's really hung up in my laptop, so I'm not confident.

---

### Post by bernied on 2006-12-20
And what about ipconfig on the windows machine?

```
C:\>ipconfig

Windows IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : bogus.name.uk
        IP Address. . . . . . . . . . . . : 192.168.1.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
```Have you tried this machine on other networks? I agree with your I hate Windows rant, the problem is probably somewhere in the networking setup on the laptop. 

Have you tried turning off the firewall? - that may be stopping the pinging into the machine.
Also, is there a light on in the laptop's network socket? Does it change if you pull out the lead? In fact, does anything change about the windows machine if you pull out the lead - does it still tell you that you're connected?

If you can download 100M fairly quickly, I recommend slax as a live cd. It doesn't boot to a gui by default, so you're less likely to have trouble.

---

### Post by Erlander on 2006-12-20
I'm having similar problems with one of my Windoze machines and have put it down to Win XP Home.  The other machine that is OK is on XP Pro.

This explains the problem:

[http://support.microsoft.com/kb/300489/](http://support.microsoft.com/kb/300489/)

Rob

---

### Post by bernied on 2006-12-20
I'm running XP Home on a LAN, and able to access samba shares, web server, ssh server.

Some more stuff to try: 
- start up a samba server (simple configuration file at bottom of this post), see if you can find the share (you might have to specify the location specifically, don't expect to find it in Network Neighbourhood)
- try to reach the web server by IP address in a browser - [http://192.168.0.1/](http://192.168.0.1/) - httpd would have to be running on the server of course

A simple samba configuration (this will give you a single share, called Share, with guest access and no password needed):
```
$ cat /etc/samba/smb.conf
[global]
workgroup = TESTGROUP
netbios name = server
server string = Samba server
hosts allow = 192.168.0. 
log file = /var/log/samba/log.%m
max log size = 50
log level = 4

guest account = guest
security = share

preserve case = yes
short preserve case = yes
default case = lower
[Share]
   comment = File Store
   path = /mnt/store
   read only = no
   public = yes
   only guest = yes
   create mask = 0664
   directory mask = 0775

```
To connect, use windows explorer, choose the Map Network Drive option in the Tools menu - use \\192.168.0.1\Share as the address.

---

