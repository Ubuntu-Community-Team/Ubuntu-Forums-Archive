---
title: "No Internet through wired connection on 6.10"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by cmj_21 on 2006-12-26
No one here seems to be experiencing this exact problem.

I just installed Ubuntu 6.10 on a Dell Inspiron 6000 notebook and everything was working fine, I could use Firefox to browse the internet, add programs, etc. My problems started after I put my laptop into hibernate last night and when I went to use it this morning, no internet sites will load.

I am using ADSL through a Linksys BEFSR41 router. I can ping my router as well as log into it through firefox and I am getting real ip address though DHCP. I cannot ping any internet sites though. There are two other computers using WinXP and Win2000 that work fine as well as the Ubuntu laptop that is dual booting with XP and connects to the internet without changing any settings. There is also a wireless network within range that I can do the same thing with as my wired connection, ping router, but no connection to outside sites.

Everything I've read has not helped at all for getting my internet connection to work. I have disabled ipv6 and this did not work. I have also tried to reinstall Ubuntu, but this does not change anything and I am still stuck being able to see my router and not connect to the internet. Any suggestions would be great.

---

### Post by dbbolton on 2006-12-26
reboot ?

set up a profile under 'system>admin>networking', making sure all settings for eth0 and eth1 are correct, special attention to static ip/dhcp.

---

### Post by cmj_21 on 2006-12-26
> **dbbolton said:**
> reboot ?

set up a profile under 'system>admin>networking', making sure all settings for eth0 and eth1 are correct, special attention to static ip/dhcp.

Rebooting, reinstalling, etc has not made anything work for me today.

Not sure what you mean by set up a profile. I have both my wireless (Intel Pro 2200bg) and wired (Broadcom). I have DHCP set on my router (works for my windows boot and the two other windows machines on connected to this router) and my eth0 is set for DHCP as well.

The link show a compilation of a few screenshots that may be helpful :confused: The only thing that I saw that may mean anything is that my DNS servers list 192.168.1.1, but my router is set to 123.168.1.1
[screen shots]("http://home.comcast.net/~drake_ot/screenshots.jpg")

Thanks

---

### Post by dbbolton on 2006-12-26
screen shots are always helpful! but i went to your link and:

Page URL Not Found!!

The requested page does not exist on this server.  The URL you typed or followed is either outdated or inaccurate.

---

### Post by cmj_21 on 2006-12-26
Ah, sorry, misspelled my image file when I posted. It was late and forgot to check ](*,)

---

### Post by SugarDaddy on 2006-12-26
cmj_21,

There is a known problem of the wpa_supplicant not working properly when the system goes into standby or hibernate after which you can have multiple versions of wpa_supplicant running and conflicting (although it is not clear in your post if you are running this). If so, you need to configure the STOP_SERVICES to ensure it functions correctly.

Check out this link and see if it helps:

[http://www.linux.com/article.pl?sid=06/09/05/2055232](http://www.linux.com/article.pl?sid=06/09/05/2055232)

---

### Post by cmj_21 on 2006-12-26
> **SugarDaddy said:**
> cmj_21,

There is a known problem of the wpa_supplicant not working properly when the system goes into standby or hibernate after which you can have multiple versions of wpa_supplicant running and conflicting (although it is not clear in your post if you are running this). If so, you need to configure the STOP_SERVICES to ensure it functions correctly.

Check out this link and see if it helps:

[http://www.linux.com/article.pl?sid=06/09/05/2055232](http://www.linux.com/article.pl?sid=06/09/05/2055232)

Thanks for the link, if I have problems with my regularly used network and wireless, I'll be sure to check it out. Right now my problem is based on the wired connection not working for internet.

---

### Post by cmj_21 on 2006-12-26
Also, for anyone else who may be able to help, here is my netstat -rn results. eth0 is my wired connection and eth1 is what my wireless is picking up, but it is not being used.

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
123.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         123.168.1.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

The IP address assigned by my router is 123.168.1.4 and my IP address assigned to the router by the ISP is 192.168.1.180. My external/broadcast IP will be in the range of 64.118.x.x. Don't know if any on that information will help.

---

