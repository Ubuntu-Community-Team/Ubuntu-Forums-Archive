---
title: "Internet Connection Sharing Ubuntu-&gt;XP with PCMCIA 3G modem"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Tigermoth on 2008-04-01
Hi,

I'm using a Vodafone Mobile Connect PCMCIA card to connect to the internet on Ubuntu.

I want to share this connection with another computer running XP.

I have networked the two computers succesfully with samba - I can see the shared XP folder on my ubuntu machine.

I have followed the following steps to set up internet connection sharing:

> Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

From this thread: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

I think I am probably using the wrong port name for my PCMCIA card - I have said it is ppp0 but I really have no idea what it actually is.

# iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

What should I use instead of ppp0 for a PCMCIA 3G modem?

Thanks!

Chris

---

### Post by sheffrem on 2008-04-03
Well i also use gprs (No 3g available yet). But mine is usb.
The way i found out about the port was that after booting your system remove the 3g card then plug it back.
run dmesg in the terminal to see information on device newly added so you should see info about your 3g card.
Just change the ppp0 to the port you see that has been aisgned to your 3g card. if there are many, try each on of them. 

mine is /dev/ttyACM1

Hope that help

---

### Post by sheffrem on 2008-04-04
well i have i  use GPRS( 3g is not yet available) but mine is usb.
To know thr port of my device i first booted as usual, removed the card then plugged it back.
then  run dmesg at the terminal. it will give you details about newly plugged in device. the last line should be about your card. change ppp0 whith the name the you will see after running dmesg while following the procedure to share the internet.
Note: Mine displayed upt 3 port . I had to try them all to get the right one.

ex:  /dev/ttyACM0
       /dev/ttyACM1
       /dev/ttyACM2

/dev/ttyACM1 was the right one.

Also how do you connect your 3g card to the net on ubuntu, if have successfully done that then i think you should know the port.

---

