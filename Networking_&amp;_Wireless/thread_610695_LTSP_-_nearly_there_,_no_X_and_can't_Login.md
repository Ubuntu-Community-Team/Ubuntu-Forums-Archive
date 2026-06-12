---
title: "LTSP - nearly there , no X and can't Login"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by JoeGregory on 2007-11-12
Hi there,

Spent the weekend setting up my Ubuntu 7.10 Thin client network and nearly made it before running out of time.

The client gets the kernel, but does not get to the graphic (X) login stage. It shows a text based scree with the following;

Ubuntu 7.10 ltsp TTY1 

Login:

When I try to log in with normal user it simply returns with:

Incorrect Login

I have ran "..ssh-keys" numerous times but to no avail.

Does anyone out there have an idea where the problem could be.

Also, concur with the idea from others to have an LTSP specific forum (separate from ebuntu)

Thanks

---

### Post by Lem on 2007-11-12
Booting to tty1 suggests either a bad client build or a problem with the graphics chip on your client.
A rummage around the log files might prove useful.

If you suspect your client graphics; then you can add options to /opt/ltsp/i386/etc/lts.conf
The full list of options can be found in /opt/ltsp/i386/usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz

but you can add the following and adjust to suit;

```
## X11 driver, e.g. auto, vesa, i810
#XSERVER                 = auto
#X_COLOR_DEPTH           = ""
X_COLOR_DEPTH            = 16
#X_VIDEO_RAM             = ""
#XF86CONFIG_FILE         = ""
```

If you feel the client build is bad, then you'll need to clear out your old build and try again;

```
sudo rm -rf /opt/ltsp/i386  
sudo ltsp-build-client
```

---

### Post by JoeGregory on 2007-11-12
Thanks for the direction. 

I had been wondering about 

a) How to rebuild the client when it already exists (got error when I tried)

and 


b) Whether to add an Lts.conf file.



I do believe that one of these is where the problem is but will have to wait until the weekend to test :(


Also, does DHCP, LTSP etc. start up automatically after boot?

Appreciate the help, will post on success (or with more questions)

---

### Post by Lem on 2007-11-12
> **JoeGregory said:**
> 
Also, does DHCP, LTSP etc. start up automatically after boot?


Should do. Let me know how you get on!

---

### Post by maybeway36 on 2007-11-12
What is the IP of the ubutnu server? It worked for me once I reinstalled the server with 192.168.0.1 as local IP.U

---

### Post by Lem on 2007-11-12
If the server IP is wrong, usually it doesn't grab the kernel. As you say using 192.168.0.1is the default setup and saves you having to edit anything to get it to run.

---

### Post by farifk on 2007-11-13
my my, i have the same problem. mine was getting <initramfs> prompt, but no login and no X. though before it, it does show ubuntu logo for a while and then after that just a blinking dash and the <initramfs>. I can do some stuffs in the initramfs, but not usefull (or maybe i just don't know how to use it properly).

---

### Post by Lem on 2007-11-13
farifk - Have you tried rebuilding your client? (see above about deleting you old build)

NB. If you are using a 64bit server and running a 32bit client, you need to run ltsp-build-client as;

```
ltsp-build-client --arch i386
```

However, you problem may well be something in the hardware of your client that it doesn't like. (probably graphics driver detection) This can usually be fixed in the lts.conf, so could you post your client spec?

---

### Post by JoeGregory on 2007-11-13
> **Lem said:**
> farifk - Have you tried rebuilding your client? (see above about deleting you old build)

NB. If you are using a 64bit server and running a 32bit client, you need to run ltsp-build-client as;

```
ltsp-build-client --arch i386
```

However, you problem may well be something in the hardware of your client that it doesn't like. (probably graphics driver detection) This can usually be fixed in the lts.conf, so could you post your client spec?

Didn't know that! That maybe another of the problems. so a summary of work for the weekend;

1. Create lts.conf and add X related properties
2. Rebuild client (after removing current) but with ---arch i386

Roll on the weekend:)

Thanks

---

### Post by farifk on 2007-11-13
GOT It, I post it on my own question. btw, how do you mark these posts as answered?

---

### Post by bazz on 2007-11-17
> **JoeGregory said:**
> Hi there,

Spent the weekend setting up my Ubuntu 7.10 Thin client network and nearly made it before running out of time.

The client gets the kernel, but does not get to the graphic (X) login stage. It shows a text based scree with the following;

Ubuntu 7.10 ltsp TTY1 

Login:

When I try to log in with normal user it simply returns with:

Incorrect Login

I have ran "..ssh-keys" numerous times but to no avail.

Does anyone out there have an idea where the problem could be.

Also, concur with the idea from others to have an LTSP specific forum (separate from ebuntu)

Thanks

If you have a custom lts.conf file just do a Ctrl+Alt+F7. tty7 is the default screen for the GUI.If your a t a terminal try to log on. By default I dont think you can logon tty1 unless you set root.

---

### Post by JoeGregory on 2007-11-18
Hi all,

Unfortunately going backwards this weekend. 

I rebuilt the client using --arch i386 and tested the boot process.

DHCP seems to work but the client hangs at " ... loading /opt/ltsp/nbi.img"  or something similar!

This is the section from /etc/ltsp/dhcpd.conf which  I think is generating this path;

option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";

I did a search and can find neither  "/ltsp/i386/pxelinux.0" nor "/ltsp/i386/nbi.img"

I am thinking of trying to add the physical workstation to DHCPD.conf but am not sure which path to use?

Anyone awake out there. :confused:

---

### Post by farifk on 2007-11-18
don't do any changes on dhcp.conf in /etc/ltsp folder. If you do change your ip address of your server, then change the subnet, netmask, range, option domain name, option domain name server, option broadcast address, option routers, option subnet mask. other that that just let it be, though you can't find /ltsp/i386/pxelinux.0 it will run just fine.
what i would recommend is adding the -v in the inetd.conf that is found in the /etc folder, it will be something like this:

tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in/tftpd -s -v /var/lib/tftpboot

save it, reboot your computer.
then try to boot your client through pxe, and look at the syslog log file, use the system log program, you'll find it on System > Administration > System Log, look at the syslog. It is better you open up the syslog before you boot your client through pxe. This way you'll find the things that your client did.

next, install firestarter, do it from the Application > Add/Remove. this is a firewall program that lets you manage the ubuntu firewall. When you have boot your client, but there is still nothing there, then try to reboot your client and look at the firestarter "blocked connection" tab. See if there is anything blocked by the firewall. Add those ports to the inbound policy by right click on the blocked port one by one. Just put everyone, when it is asked.

this is what i did to get it running. I'm not sure if it will work on yours. I'm sorry if I can't do much help.

---

### Post by JoeGregory on 2007-11-25
> **farifk said:**
> don't do any changes on dhcp.conf in /etc/ltsp folder. If you do change your ip address of your server, then change the subnet, netmask, range, option domain name, option domain name server, option broadcast address, option routers, option subnet mask. other that that just let it be, though you can't find /ltsp/i386/pxelinux.0 it will run just fine.
what i would recommend is adding the -v in the inetd.conf that is found in the /etc folder, it will be something like this:

tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in/tftpd -s -v /var/lib/tftpboot

save it, reboot your computer.
then try to boot your client through pxe, and look at the syslog log file, use the system log program, you'll find it on System > Administration > System Log, look at the syslog. It is better you open up the syslog before you boot your client through pxe. This way you'll find the things that your client did.

next, install firestarter, do it from the Application > Add/Remove. this is a firewall program that lets you manage the ubuntu firewall. When you have boot your client, but there is still nothing there, then try to reboot your client and look at the firestarter "blocked connection" tab. See if there is anything blocked by the firewall. Add those ports to the inbound policy by right click on the blocked port one by one. Just put everyone, when it is asked.

this is what i did to get it running. I'm not sure if it will work on yours. I'm sorry if I can't do much help.


I added the -v flag to inetd but the syslog showed nothing untoward. 
DHCP request and ACK all seem fine. MAC address is recognised and client says "Loading ......
But thats it.

Reaaly don't know where to go from here.

Just another note, I recently rebuilt the client using --arch i386. Before that the client loaded th file pxelinux.0, now its only trying to load "nbi.img". No idea why (or what nbi.img is?)
THe file is included in the TFTP.boot folder

JG

---

### Post by farifk on 2007-11-25
then, have you turn off your fire wall?
mine has also boot from the nbi.img, don't worry it's fine.
turn off the fire wall, reboot your client again, see what is up at the syslog
btw, did you change the default setting, delete the "silent" flag? so instead of ubuntu logo, you will get some text list of things that was done / process.

---

### Post by JoeGregory on 2007-11-26
> **farifk said:**
> then, have you turn off your fire wall?
mine has also boot from the nbi.img, don't worry it's fine.
turn off the fire wall, reboot your client again, see what is up at the syslog
btw, did you change the default setting, delete the "silent" flag? so instead of ubuntu logo, you will get some text list of things that was done / process.

It seems strange to me at the moment. 

I turned of the firewall, both using firestarter and iptables and other command line features. Rebooted client and still the same.

I don't know which flag you are referring to, or which logo, do you mean when I boot the server?

I used a program called wireshark to observe the packets transferred between client and server. I can see the two way communication between them for DHCP up to the DHCPACK.

Then the client sends an ARP packet. Wireshark gives the text info "WHOIS AT [Server IP Address]" but there is no response from the server.

I thought it might be a problem with the switch, so connected client and server directly with a crossover cable - same thing

Soemthing is blocking the response from the server. 

I have checked that tftp is running,that images are in the tftpboot directory etc. - everything seems to be ok.

Can it have something to do with 

a) A clash because of the two NICs on server (IP Networks are not the same) 

or

b) IPv4 versus IPv6 addressing???

or

c) bad karma

This whole project is so that I can provide my kids with a nice, safe toy for Christmas to play TuxPaint on. Don't know if I 'll be ready by then 8-[

---

### Post by farifk on 2007-11-26
the "default" file is in the /var/lib/tftpboot/i386/pxelinux.cfg
sorry, it is not "silent" flag. please delete "quiet" and "splash" flag, save it and reboot your server. after that turn off your firewall then reboot your client.
i turned off my firewall just using the firestarter, i didn't use any other program.
have you put the lts.conf file in the /var/lib/tftpboot/i386?

---

### Post by Dragonbite on 2007-12-06
Oh, this information is very helpfull! thanks!

You should be eable to Edit the first post and add "[SOLVED]" in the title, or there may be a link under Thread Tools link.

---

### Post by farifk on 2007-12-06
he he thanks.

---

### Post by JoeGregory on 2007-12-10
> **farifk said:**
> the "default" file is in the /var/lib/tftpboot/i386/pxelinux.cfg
sorry, it is not "silent" flag. please delete "quiet" and "splash" flag, save it and reboot your server. after that turn off your firewall then reboot your client.
i turned off my firewall just using the firestarter, i didn't use any other program.
have you put the lts.conf file in the /var/lib/tftpboot/i386?

Hi,

removed flags as stated above, but didn't see anything new :(

I am using "wireshark" to monitor the network traffic between the server and client and after the DHCP process, the client sends an ARP request which goes unanswered by the server. It keeps sending this at regular intervals.

Wireshark gives the following text;

Who is at [IP address of ltsp server (from dhcpd.conf)] ?  Tell [ IP address ending with .250] 

Surely this is a clue as to where the problem lies????

Otherwise, are there any bug issue with AMD64 server and i386 clients?

Any help welcome, one ,more weekend of hacking to go!

Thanks

Joe

---

### Post by JoeGregory on 2007-12-10
btw,

Could there be an issue with the "Server name" section of dhcpd.conf?

Thanks

Joe

---

### Post by hans1000 on 2007-12-20
Hello Joe,

thanks for the hint.

I had the same problem with different Ubuntu-versions.
The change in the server-name to the IP-address was the correct way..

best wishes

hans

---

### Post by JoeGregory on 2007-12-20
Hi Hans,

Glad to be of some help, but it was actually just a shot in the dark!

What exactly did you do to fix your specific problem?

Joe

---

### Post by JoeGregory on 2008-01-02
Thanks to all who have tried to help. On one of the ubuntu forums a
reference to NAT & forwarding

[http://ubuntuforums.org/showthread.php?t=599166]("http://ubuntuforums.org/showthread.php?t=599166")


I created the /etc/network/options file as stated and bingo!

I don't pretend to understand why this worked but it did, so I can
accept that for now.

On another thread I will try to summarise my experiences and point out my latest issues.

Thanks again and happy new year to all

---

