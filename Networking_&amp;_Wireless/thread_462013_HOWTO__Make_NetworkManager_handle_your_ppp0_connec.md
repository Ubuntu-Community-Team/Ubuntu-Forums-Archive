---
title: "HOWTO:  Make NetworkManager handle your ppp0 connection"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by bimmerd00d on 2007-06-02
I'm using Cingular, so this is what we'll use for the time being as a naming convention but you can call it whatever you want.  If you arrived from my Dell Expresscard thread, keep on reading after step 1!

1.  Edit your /etc/network/interfaces file and add at the end
```
sudo gedit /etc/network/interfaces
```

iface ppp0 inet ppp
provider **Cingular**
In the case above, provider 3G refers to the ppp initialization script located in /etc/ppp/peers/Cingular

(I capitalized it so it looked pretty) :p

2.  You download the scripts from here 

right?[http://www.novatelwireless.com/support/files/hsdpa_scripts.zip](http://www.novatelwireless.com/support/files/hsdpa_scripts.zip)

I dont believe i had to modify anything in these files....i'll double check and report back.
```
 unzip hsdpa_scripts.zip

cd hsdpa_scripts/ppp_scripts

sudo cp hsdpa_chatoptions /etc/ppp/peers/Cingular_chat

sudo cp hsdpa_options /etc/ppp/peers/Cingular


```

This should do it!  open your monitor so you can see what it's doing

```
 tail -f /var/log/messages 
```

Click on NetworkManager, you should see "Dial Up Connections" now, and then "Connect to Cingular via modem..."

---

### Post by cwmoser on 2007-06-08
I have the Cingular 3G Wireless card but could not get it to work.

When I go to Network-Manager and select Dial up connections -> Connect to Cingular, I get in /var/log/messages the following:

pppd 2.4.4 started by root
Exit

and no connection to Internet.

Carl

---

### Post by cwmoser on 2007-06-10
I found the solution to this ---- I had a static IP address.  When I went back to a dynamic IP address, then Network-Manager would show VPN connections and I was able to vpn to work.

Carl

---

### Post by codybuntu on 2007-06-27
Everything works except network manager shows disconnected state (but I can browse internet).

---

### Post by bimmerd00d on 2007-06-28
> **codybuntu said:**
> Everything works except network manager shows disconnected state (but I can browse internet).

Yeah i never found a way to make nm-applet display the pppd connection info.  I just added the line to Conky to make it displayy what i wanted.

---

### Post by mk4umha on 2008-05-08
> **cwmoser said:**
> I found the solution to this ---- I had a static IP address.  When I went back to a dynamic IP address, then Network-Manager would show VPN connections and I was able to vpn to work.

Carl

how did you do this? I went to my network manager and the moden does not have a static IP.

---

