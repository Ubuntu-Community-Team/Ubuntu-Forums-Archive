---
title: "service supplied ip"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by mike628 on 2010-07-21
Hello,
 
Id like to find the ip address assigned to the box by my service provider. Like when I go to "WhatsMyIp.com" in my browser. but I log into my box with putty. I tried ifconfig, but that gives me the DHCP address from my router.
Thanks

---

### Post by corrytonapple on 2010-07-21
To access your IP adress type (or copy and paste)in Terminal (Applications/Accessories/Terminal)
```

/sbin/ifconfig

```Then, there are three sections. Go to WLAN0 and look at the second line where it says:
Inet addr:
That is your IP address.
Also included is a picture for reference.

---

### Post by Iowan on 2010-07-21
I suspect you'll need to get that information from the router.
(... but I've been wrong before...)

---

### Post by corrytonapple on 2010-07-21
> **Iowan said:**
> I suspect you'll need to get that information from the router.
(... but I've been wrong before...)
I'm learning and many times been wrong too.;)

---

### Post by Zeike on 2010-07-21
> **corrytonapple said:**
> [/CODE]Then, there are three sections. Go to WLAN0 and look at the second line where it says:

Its only on the wlan0 interface if he is using wireless.  If he is connected via regular a wired ethernet connection it'll be under eth0, or possibly eth1 or something else.

The only IP address your computer knows about is the one assigned to it by the router (usually 192.168.x.x).

You can always visit "whatismyip.com" via putty in a text based webbrowser such as lynx or links.

---

### Post by lisati on 2010-07-21
Having remembered seeing a link in the forums to a simple web page that lets you get your IP address, but not remembering the actual link, I've put something similar on my web site:
[http://lisati.homelinux.com/myip.php](http://lisati.homelinux.com/myip.php)

[php]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Who am I?</title>
</head>
<body>
<?php
$host = getenv("REMOTE_ADDR");
echo $host;
?>
<br />
</body>
</html>
[/php]

---

### Post by cariboo on 2010-07-22
I personally like [canyouseeme.org]("http://canyouseeme.org"), it's great for checking to see if you have setup port forwarding correctly

---

### Post by mike628 on 2010-07-22
If I do Whats my ip from this computer and I do it romotely from the linux box i get the same ip. Shouldnt they be different? What if each was running a webserver on the same port?

---

### Post by lisati on 2010-07-22
If you are using multiple computers to connect to the internet through the one router/modem it is normal for them to all have the same public IP address. The router takes care of which computer "sees" which interaction through a trick known as "[NAT]("http://en.wikipedia.org/wiki/Network_address_translation")" (network address translation)

If you want to have multiple web sites available, one option would be through Apache's system of "[virtual hosts]("http://httpd.apache.org/docs/2.2/vhosts/")". The basic idea is that Apache listens to port 80, and when it receives requests for a particular domain name it knows about, it can use a specific folder on your web server; each domain name it serves has its own folder, and apache uses the corresponding folder as a source of web pages to feed out in response to incoming requests when it recognizes the specific domains. (Example: my main web site is [http://lisati.homelinux.com](http://lisati.homelinux.com) and a secondary web site it [http://lisati.homelinux.org](http://lisati.homelinux.org) - both are served by the one copy of Apache, but because I have pointed apache at different folders for the domain names, it is able to dish out different content depending on the URL used.)

---

