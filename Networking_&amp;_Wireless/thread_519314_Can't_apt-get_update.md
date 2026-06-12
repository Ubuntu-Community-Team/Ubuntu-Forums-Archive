---
title: "Can't apt-get update"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by ncwalker on 2007-08-06
Hi everyone, 

I am using a terminal window and logging in as root and attempting

apt-get update

and I am getting

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
      Could not resolve 'security.ubuntu.com'

and a series of other similar errors.  Can anyone help me 'resolve' this :)

On a potentially related note I can't get Apache to load (either from Webmin or manually)

I also have noticed that the li command no longer works when I am in terminal window.  

It says: 

The program 'li' is currently not installed. You can install it by typing sudo apt-get install limo
Make sure you have the 'universe' component enabled
bash: li: command not found

When I enter sudo apt-get install limo I get a warning that the package cannot be authenticated.  When I tell it to install without verification it says it cannot resolve 'ca.archive.ubuntu.com'

Please help!  I have been stuck here all day!

---

### Post by benanzo on 2007-08-07
Are you able to surf the internet normally?  Something tells me you're not getting good DNS servers from your ISP, or NetworkManager is not updating your /etc/resolv.conf file.

Just for kicks, open a terminal and do:
```
sudo dhclient eth0 # change eth0 to your network interface
```
Then try to connect again.

If that doesn't work try adding your own DNS servers.

Open a terminal and do:
```
sudo gedit /etc/resolv.conf
```
Add these two lines just below the **search some.domain.name** line.  If you don't have that then just add these lines to the top:
```

nameserver 208.67.220.220
nameserver 208.67.222.222

```
These are the DNS servers provided by the free DNS service OpenDNS.  I find them to be highly reliable.

Now, to make sure there aren't any leftover addresses cached open a terminal and do:
```
sudo /etc/init.d/dns-clean start
```
That will clear your DNS cache.  Now try to connect.  Be aware that if you restart your internet connection your DNS servers will go back to whatever your router/ISP provides.  [Here's]("http://www.opendns.com/start/ubuntu.php") the OpenDNS instructions for setting these DNS servers permanently.

Good Luck!

---

### Post by ncwalker on 2007-08-07
Thank-you Thank-you Thank-you!

When you say "restart my internet connection do you mean turn off the server or reset the router?

Second question.  My router address is 192.168.0.1  

Could I just change my /etc/network/resolv.conf file to contain nameserver 192.168.0.1?  Would that work?

---

### Post by benanzo on 2007-08-07
You shouldn't have to restart your modem/router unless you're having trouble getting a connection *from* your ISP.

You can restart the network connection on your server by doing:
```
sudo /etc/init.d/networking restart
```

**192.168.0.1** is your router's address, AKA the gateway.  Normally when you connect to your ISP your modem retrieves a set of DNS server addresses which then get passed to your router, which then get passed to your server and appear in the **/etc/resolv.conf** file so that Firefox, apt-get etc know where to look when trying to find websites.  Sometimes those addresses get hung-up in the process and don't get updated properly.  It probably won't help to put the **192.168.0.1** address in your **/etc/resolv.conf** file.

---

