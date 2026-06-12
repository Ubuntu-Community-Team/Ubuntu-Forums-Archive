---
title: "URL for internal network"
date: 2021-05-06
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2021-05-06
I have an Ubuntu server setup and have installed LAMP and would like to install Drupal.  Everything is up and running, but when I install Drupal and the underlying application, the main URL gets stored in the application.  

For example, if I am out on the Internet, I can get to the Apache server using something like "https://mydrupal.outsidenetwork.com".  But if I install the application from the Internet, I cannot use it internal to my home network because the application has stored the URL for redirection purposes and based on the rules imposed by my ISP, it will not allow me to reflect back from my home network.

If I have installed the application from my internal home network using the internal IP, I cannot access the application from the Internet due to the same application redirection issue.

Anyway, is there someway to be on my internal home network and have the Internet defined URL go to the internal IP address so I can work on the application inside and outside?  For example, mydrupal.outsidenetwork.com will go to the correct IP address if I'm outside my home network and got to my internal IP address when I'm on my home network?

I thought about using /etc/host file, but wondered if that would work or if there's a better way.

Hope this make sense....

---

### Post by mIk3_08 on 2021-05-06
This should be the CName, A, and @ the domain name settings. pointing of the name from the static address. I'm thinking of the static IP settings pointing to the domain and your domain registration. Are you talking about pointing your domain? or did you try to run your drupal thing using you IP? this is a subdomain thing I think;

https://"mydrupal" ----> Subdomain 
and your 
outsidenetwork.com ---> main domain. Am I right? this is the one who bring the static IP address.

---

### Post by SeijiSensei on 2021-05-06
Yes, I would first try the /etc/hosts file.  (This file exists on Windows machines as well at C:\Windows\System32\Drivers\etc\hosts.)

Edit the file as root with "sudo nano /etc/hosts" and add a line that reads:

```
server.inside.ip.addr     mydrupal.outsidenetwork.com
```

You must make this change on any client machines that might connect to the server.

A more global solution would be to run a local DNS server on your network with local records for outsidenetwork.com. For instance, my domain's public-facing DNS records are hosted on servers in the cloud. However I also have an instance of BIND9 running on my local server that's also authoritative for my domain. I point local clients at that server so they get answers within the local network.

---

### Post by mIk3_08 on 2021-05-07
you can also create your own diretory to make sites-available:
```
mkdir sites-available
```
inside the directory sites-available create a file .conf:
```
sudo vim mydrupal.outsidenetwork.com.conf
```
then add the ff code:
```
server{
        listen          80; 
        server_name     mydrupal.outsidenetwork.com; 
        location /{
                root /var/www/mydrupal.outsidenetwork.com/public_html;
                index index.html;
                }
}
```
then save the file:
in your nginx.conf file add the ff code:
```
include /etc/nginx/sites-available/*.conf;
```
then save the file.
Then restart nginx:
```
sudo systemctl restart nginx.service
```

---

