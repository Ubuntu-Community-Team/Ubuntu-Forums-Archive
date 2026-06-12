---
title: "Network Manager Issues"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by inexperienced_linux_user on 2008-12-02
How do i make my IPv4 ip address, subnet mask, default gateway and DNS servers static in Ubuntu 8.10.

Please help wid the commands that i will need to use in the terminal as I am new to linux.

Thanks

---

### Post by ErroneousBosch on 2008-12-03
Hi! ):P

I just got static IP working (this morning) and hopefully it is not as tricky for you as it was for me. I had a virtual server as well, which complicates things

There are two places you can/may have to set the static IP. One is in Network Manager. Right click on the icon, select edit connections and edit the wired connection. Under the IPv4 tab, set it to Manual and set the address, netmask and gateway for your network. You can also set the DNS to your router. click close etc, then click on the network manager icon and select the wired interface to reconnect. Go to terminal and check ifconfig to see if it worked.

If you don't seem to have net right away, give it a minute, if still no net or if the IP is not pulling right, do the following:

The other place you may have to set it is in your /etc/network/interfaces file. You need to edit this with sudo so open terminal and type: 
```
sudo gedit /etc/network/interfaces
```
Type your password and it will open gedit. 

Your interfaces file should contain the following:
```
auto lo
iface lo inet loopback
```

You are going to **ADD** a section that reads as following:

```
auto eth0
iface eth0 inet static
        address 192.168.1.100 
        netmask 255.255.255.0
        gateway 192.168.1.1
```

Setting the addresses as appropriate. save and close, then type 
```
sudo /etc/init.d/networking restart
``` 
to restart your networking. Use ifconfig to confirm the address. 
If it does seem to be working still, go back into interfaces and change static to manual, but keep the rest the same, restart networking and check ifconfig. 

Hope this helps! :D

---

### Post by inexperienced_linux_user on 2008-12-03
> **ErroneousBosch said:**
> Hi! ):P

I just got static IP working (this morning) and hopefully it is not as tricky for you as it was for me. I had a virtual server as well, which complicates things

There are two places you can/may have to set the static IP. One is in Network Manager. Right click on the icon, select edit connections and edit the wired connection. Under the IPv4 tab, set it to Manual and set the address, netmask and gateway for your network. You can also set the DNS to your router. click close etc, then click on the network manager icon and select the wired interface to reconnect. Go to terminal and check ifconfig to see if it worked.

If you don't seem to have net right away, give it a minute, if still no net or if the IP is not pulling right, do the following:

The other place you may have to set it is in your /etc/network/interfaces file. You need to edit this with sudo so open terminal and type: 
```
sudo gedit /etc/network/interfaces
```
Type your password and it will open gedit. 

Your interfaces file should contain the following:
```
auto lo
iface lo inet loopback
```

You are going to **ADD** a section that reads as following:

```
auto eth0
iface eth0 inet static
        address 192.168.1.100 
        netmask 255.255.255.0
        gateway 192.168.1.1
```

Setting the addresses as appropriate. save and close, then type 
```
sudo /etc/init.d/networking restart
``` 
to restart your networking. Use ifconfig to confirm the address. 
If it does seem to be working still, go back into interfaces and change static to manual, but keep the rest the same, restart networking and check ifconfig. 

Hope this helps! :D



Well i'm having this problem with my wireless. I keep getting disconnected from the network even before i can open a page on the net. I was hoping that if i make my IP static, maybe then the problem would'nt recurr. It'll be really kind of you to post the procedure for making these parameters static for a wireless connection

Thanks and Regards

---

### Post by drober05 on 2008-12-09
Hello all, I too am attempting to setup my Ubuntu 8.1 server with static IP.  I started off with Fedora 10 and that went nowhere.  At least with Ubuntu following ErroneousBosch's directions I am able to establish a static IP.  I can then access other devices within my home network (my Belkin router setup utility for instance).  However, I cannot access any websites.  I pointed the DNS to my router IP address and that did not help.

Any suggestions?

---

