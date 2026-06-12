---
title: "NetworkManager gives nm-ppp-auth-dia segfault error 4 when connecting with PPTPClient"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by sujitpal on 2007-05-26
I have installed the Network Manager with the pptp client packages. I can use the NM-appliet fine from my gnome toolbar.

However, when trying to connect, I enter my domain\user and password and hit enter, I see the following error in /var/log/messages:
May 26 16:38:25 localhost kernel: [ 1551.795197] nm-ppp-auth-dia[9283]: segfault at 0000000000000088 rip 00002b9513eb221b rsp 00007fff9c78f220 error 4

Not sure if I did something wrong, or if something is broken in the code and if there is a workaround.

I have also been looking at using pptpclient manually (using pon and poff), I can connect but dont know what routing commands to add to the ip-up and ip-down files.

OS is Ubuntu 7.04 (Fiesty Fawn) 64-bit running on a 64-bit Turion x2 machine.

Thanks in advance for any help you can provide.

---

### Post by sujitpal on 2007-05-26
Just a quick update. I still get the same error message in the /var/log/messages with NetworkManager, but I found out the route commands to add so my pon/poff approach is now working. Not as pretty as doing it through the NetworkManager, but it works.

Thanks to the comment in this thread by jklappenbach:
[http://ubuntuforums.org/showthread.php?t=28396&highlight=pptp&page=3]("http://ubuntuforums.org/showthread.php?t=28396&highlight=pptp&page=3")

I have my own little script in my /home/sujit/bin directory, which goes like this:
#!/bin/bash
case $1 in
  'on')
    echo "Starting VPN tunnel to MegaCorp..."
    sudo pon vpn_megacorp
    sleep 10
    sudo route add -net 10.1.128.0 netmask 255.255.255.0 dev ppp0
    sudo route add -net 10.1.1.0 netmask 255.255.255.0 dev ppp0
    ;;
  'off')
    echo "Stopping VPN tunnel to MegaCorp..."
    sudo poff vpn_megacorp
    ;;
esac

Substitute your company name for MegaCorp, and possibly the IP addresses. I remembered seeing the same 10.x IP addresses when I did nslookups on machines within the company network, so on a hunch I just put in the same that he had, and it works.

My vpn_megacorp file looks like this, and was built using the contents of my old file (written by pptpconfig on Fedora Core 3):

sujit@sirocco:~$ cat /etc/ppp/peers/vpn_megacorp
pty "pptp vpn.megacorp.com --nolaunchpppd "
name MEGACORP\\sujit
remotename PPTP
require-mppe
file /etc/ppp/options.pptp
ipparam vpn_megacorp
usepeerdns
noauth

My options.pptp file was also based on the contents of the options.pptp file from my old laptop running FC3/PPTPConfig.

Anyway, I hope this helps someone. Not being able to connect to my company network over VPN would have been a complete deal breaker for me. I would probably have had to downgrade to 32 bit Fiesty, or 32 bit FC4/5, or 32-bit Vista if I could not make this work.

Unfortunately, pptpconfig will not work because its missing couple of 64 bit libs from the repository. I guess one option would be to recompile and/or install the 32 bit package, but I dont know enough of Debian/Ubuntu to do that yet.

Meanwhile, if anyone knows about the NetworkManager problem (I did remember it being logged as a bug but the solution was not clear to me), I would appreciate being pointed to relevant URLs.

-sujit

---

### Post by zoward on 2007-07-23
Found this quite a bit later, had the same problem, using 64-bit Feisty. After futzing around a bit, I solved it in NetworkManager by unchecking the "Use Peer DNS" option on the PPP Options page.  Hope this helps someone!

---

### Post by ]grimm[ on 2007-07-29
Unfortunately, I tried unchecking "Use Peer DNS" but am still getting the segfault.  Did you try using an ip-up.d script to set your routing?  I tried writing one, but I can't get it to work.  I'm currently using a similar script similar to yours, but I have two of them setup because I sometimes need to connect from the road when I'm using an EVDO card and my network device for the VPN changes from ppp0 to ppp1.

---

### Post by randommoniker on 2007-09-24
I just rolled desktop to KDE, and started getting this error.

  --rm--

---

