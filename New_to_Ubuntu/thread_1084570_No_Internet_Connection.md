---
title: "No Internet Connection"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-02
Hi

Have installed Ubuntu 8.10 as the single operating system on an IBM R40e laptop. All seems well except that there is no internet connection. I have a wired 4 port router which is up and running with 3 desktops. I have tried to follow various recommendations in Help files but with no success so far. I'd really appreciate some assistance in getting the connection working.

Thanks and best regards,

George

---

### Post by carml on 2009-03-02
Try to go to System->Administration->Network,unlock the appet and set your "Cabled Connection" to DHCP. 
If you need more help just ask.:)

---

### Post by obaid on 2009-03-02
hi gdn1974.

i understand that you have a cable from router plugged into your laptop, and still you have no access to internet.

in most cases, when router has DHCP service, it automatically leases IP, Subnetmask, Default gateway, and DNS addresses for clients, in this case, you dont need to configure your ethernet interface.

however. if your router has DHCP service disabled, then you can assign a static IP address to your ethernet interface. This can be done using ifconfig command in terminal (console).

assuming you already know IP address configuration for your local network, you can use ifconfig as following:

sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0
sudo route add default gw 192.168.1.1
sudo nano /etc/resolv.conf

sudo is used to execute command with root perivileges.
in first line, assuming eth0 is your ethernet interface. 192.168.1.10 is the desired IP address for eth0, and 255.255.255.0 is the netmask for local network.
second line, we add default route to our gateway that is 192.168.1.1

last line we define the dns server in /etc/resolv.conf and we add this:
nameserver 4.2.2.2

where 4.2.2.2 is your ISP dns server, you can define multiple name servers in resolv.conf each in new line.

i hope this works.

---

### Post by gdn1947 on 2009-03-02
Hi obaid, thanks for your reply. I entered the first line instruction you proposed and the computer reports "No buffer space available" and "Cannot assign requested address". 

My son tells me that DHCP is enabled in our router

Any follow up thoughts?

Thanks

---

### Post by gdn1947 on 2009-03-02
> **carml said:**
> Try to go to System->Administration->Network,unlock the appet and set your "Cabled Connection" to DHCP. 
If you need more help just ask.:)
I think you are talking 8.04. In 8.10 you have System, Administration, Network Tools. I dont see anything which refers to "unlock the appet and set your "Cabled Connection" to DHCP."

Thanks

---

### Post by carml on 2009-03-02
Sorry,I use 8.04; with unlock the applet I meant clickon the button "unlock",if there's one,so you can edit the settings on your network card.

---

