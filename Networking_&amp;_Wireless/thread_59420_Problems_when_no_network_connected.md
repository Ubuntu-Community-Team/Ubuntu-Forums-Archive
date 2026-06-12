---
title: "Problems when no network connected"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by Chris Cromer on 2005-08-23
Well today the internet went out... and I was completely locked out of ubuntu, it froze on startup when trying to syncronize with the ubuntu website's clock.

So I tried unconnecting my LAN Ethernet cable, then it froze when trying to initlize the network.

These 2 issues are major because I do have internet outages every now and then, and I am on a laptop so I won't always be connected to my network anyway.

How do I make it so I can start ubuntu without it hanging because I don't have a network connection or an internet connection?

---

### Post by s_p_a_r_k_y on 2005-08-23
I have a similar proble, but you can press ctrl-c when it "hangs" on network detection. THis will cancel the dhclient program and fail the network statup script, but its better than waiting for it to timeout

---

### Post by Chris Cromer on 2005-08-24
Thanks, that's a good temporary solution. Although I will need something more permanent since this is a laptop and I will be disconnected from the network when I am not at home.

---

### Post by s_p_a_r_k_y on 2005-08-24
find this line in /etc/init.d/networking

ifup -a >/dev/null 2>&1

and change it to

ifup -a & >/dev/null 2>&1

I think this will push it to the background so that it looks for a dhcp address while the system continues to boot. Give it a try

sudo /etc/init.d/network stop

unplug network cable

sudo /etc/init.d/network start

and see if it lets you press enter while it displays output to get to a prompt...of course you can always restart to test it as well : )

---

### Post by Chris Cromer on 2005-08-24
You made a mistake in your code, you told me to execute network. But the file is called "networking". But anyway it apparently works from what I can see. Although what about when my internet is down and I am still connected to the network?

It dies when trying to syncronize my clock with the ubuntu server.

I should be able to get past it with ctr-c, but I need a more permanent workaround for that as well.

---

### Post by s_p_a_r_k_y on 2005-08-24
sorry for the typo, it indeed is networking on ubuntu...I deal with to many linux distros where some call it network, othersnetworking...Thats why I use tab completion to figure out file names. If your in bash and you type in /ect/init.d/network and hit tab it should finish the filename for you.

now to ntp issue, edit /etc/init.d/ntpdate
and change this line
/usr/sbin/ntpdate -b -s $NTPOPTIONS $NTPSERVERS 
to
/usr/sbin/ntpdate -b -s $NTPOPTIONS $NTPSERVERS &

the ampersand at the end of the line should force that command into the background as well. Using the & will help a lot for various command line things. If you want to copy a large file but not wait till its done to type more commands, cp file /to/location/ & and it goes to the background allowing you to type more commands while it copies

---

### Post by ahh_dee on 2005-08-24
[QUOTE=s_p_a_r_k_y]find this line in /etc/init.d/networking

ifup -a >/dev/null 2>&1

and change it to

ifup -a & >/dev/null 2>&1

I think this will push it to the background so that it looks for a dhcp address while the system continues to boot. Give it a try

sudo /etc/init.d/network stop

unplug network cable

sudo /etc/init.d/network start

and see if it lets you press enter while it displays output to get to a prompt...of course you can always restart to test it as well : )[/QUOTE]



I Changed the file and it works but I exec command dhclient to start up my ethernet i get this

```
sit0: unkown hardware address type 776
sit0: unkown hardware address type 776
Listening on LPF/eth1/00:0f:1f:00:0f:14
sending on  LPF/eth1/00:0f:1f:00:0f:14
sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
no DHCPOFFERS recieved
no working leases in persistent database - sleeping.
```


does anyone know how i can fix it? my internet is working fine on my other computers thxs

---

### Post by s_p_a_r_k_y on 2005-08-24
that means that eth1 isn't finding a dhcp server so its timing out. make sure that all cables are pluged in and the such, or if its wireless that you have the correct ESSID, channel and key

---

