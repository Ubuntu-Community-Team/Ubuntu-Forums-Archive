---
title: "Changing reverse proxy private IP on Ubuntu"
date: 2016-11-13
forum: Networking &amp; Wireless
---

### Post by OtagoHarbour on 2016-11-13
I have two instances on Amazon ec2. One was running Ubuntu 16.04 (LTS) while the other was running Amazon Linux AMI. They were on the same virtual private cloud and I had LAMP installed on both. I followed the directions here to enable app1 to point to the Amazon Linux AMI instance which had a private IP address of 10.0.1.27. Specifically, I edited /etc/apache2/sites-available/proxy-host.conf to consist of the following.


```
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/html/
  ErrorLog ${APACHE_LOG_DIR}/error.log    
  CustomLog ${APACHE_LOG_DIR}/access.log combined
  ProxyPreserveHost On
  # Servers to proxy the connection, or
  # List of application servers Usage
  ProxyPass /app1/ http://10.0.1.27:8080/
  ProxyPass / http://10.0.1.110:8080/
  # ProxyPassReverse / http://server-ip-address:8080/
  ServerName localhost
</VirtualHost>

```


Then, after I restart apache I could simply enter the following code, on a web page of the current server


```
<li><a href="/app1/Whatever.php">Whatever</a></li>

```and the web page Whatever.php, on the server with the private IP 10.0.1.27, was displayed on my browser when I clicked the Whatever button.


However, I terminated the instance, with the private IP address 10.0.1.27, and replaced it with a Ubuntu 16.04 (LTS) server with IP address 10.0.1.7. I therefore changed the /etc/apache2/sites-available/proxy-host.conf to


```
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/html/
  ErrorLog ${APACHE_LOG_DIR}/error.log    
  CustomLog ${APACHE_LOG_DIR}/access.log combined
  ProxyPreserveHost On
  # Servers to proxy the connection, or
  # List of application servers Usage
  ProxyPass /app1/ [http://10.0.1.7:8080/](http://10.0.1.7:8080/)
  ProxyPass / [http://10.0.1.110:8080/](http://10.0.1.110:8080/)
  # ProxyPassReverse / [http://server-ip-address:8080/](http://server-ip-address:8080/)
  ServerName localhost
</VirtualHost>

```
I then entered the following


```
sudo a2dissite proxy-host.conf
sudo a2ensite proxy-host.conf
sudo service apache2 reload
sudo service apache2 restart

```


However, when I click on the "Whatever" button, I get the 503 error.


```
Service Unavailable


The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.


Apache/2.4.18 (Ubuntu) Server at 52.207.143.84 Port 80
It appears that it is still trying to access the instance with the private IP address 10.0.1.27.

```
I would make app1 point to the instance, with the private IP address 10.0.1.7, instead?


I looked at the /home/ubuntu/.viminfo file and it contained the following lines.


```
# Registers:
"0      LINE    0
          ProxyPass /app/ http://10.0.1.7/
"1      LINE    0
        ProxyPass /app1/ http://10.0.1.27/
"2      LINE    0
        ProxyPass /app1/ http://10.0.1.27/
"3      LINE    0
        ProxyPass /app1/ http://10.0.1.27/
""-     CHAR    0
        2

```


I changed the 10.0.1.27 entries to 10.0.1.7 but running


```
sudo /etc/init.d/apache2 restart

```


changes them back to 10.0.1.27.  There is clearly some configuration file that sets


```
ProxyPass /app1/ http://10.0.1.27/

```


when 


```
sudo /etc/init.d/apache2 restart

```


is called but I was unable to find anything, along those lines, in /etc/apache2/apache2.conf or in  /etc/apache2/httpd.conf or by calling


```
sudo grep app1 /etc/apache2/*.*

```

---

