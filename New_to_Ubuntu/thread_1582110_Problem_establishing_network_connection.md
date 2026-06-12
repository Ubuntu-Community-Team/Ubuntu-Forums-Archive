---
title: "Problem establishing network connection"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by pkj on 2010-09-26
Hi,

Have a sudden unexplained problem wherein the computer is not able to establish internet connection...

Net connectivity is OK (as my other machine is able to connect using the same modem)...

Wires and cables checked and are OK

What i guess, that the Ubuntu is not able to get the DHCP settings....

Am on ubuntu 9.1

Need help to resolve the issue...
pkj

---

### Post by mrhhug on 2010-09-26
ok , we want to help but please post the entire output of ```
cat /etc/network/interfaces
```

---

### Post by JohnHeikkila on 2010-09-26
Run the commands in terminal, open console.

Try
'**sudo ifconfig wlan0 up down**'
then
'**sudo iwconfig wlan0**'

This only if you are using the wireless and 'wlan0' is the name of your wireless interface. You can also replace the 'wlan0' with 'eth0' if it's an ethernet connection.

If you are using the wireless with an interface called 'wlan0', then continue with
'**sudo iwconfig wlan0 essid** *(your wireless connection's ESSID here)*'
after this,
'**sudo iwconfig wlan0 key** (your protection key, if any) **mode managed**'

Check if the connection has an Access-Point with
'**sudo iwconfig wlan0**'
and if you can find an access-point (AP)(looks something like this 00:D5:00:23:00), then do
'**sudo dhclient wlan0**'

---

### Post by HermanAB on 2010-09-26
Howdy,

For a network connection to work, you need a number of things to be configured correctly:
IP Address
Netmask
Default route
Domain Name Server
Hostname

You can see the IP information using 'ifconfig'.
You can see the route with 'route'.
You can see the DNS in /etc/resolv.conf. 
You can see the hostname with 'hostname'.

So, play around with those commands and figure it out.

---

