---
title: "Apache reverse proxy not working on LAN/WAN"
date: 2019-01-14
forum: Networking &amp; Wireless
---

### Post by atif2 on 2019-01-14
Hi

Following is the network diagram



[ATTACH=CONFIG]282201[/ATTACH]


I have installed and configured Apache Reverse Proxy on Ubuntu 16.04 with following modules

sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod proxy_ajp
sudo a2enmod rewrite
sudo a2enmod deflate
sudo a2enmod headers
sudo a2enmod proxy_balancer
sudo a2enmod proxy_connect
sudo a2enmod proxy_html

[COLOR=#ff0000]I have configured **proxyfilter.conf** as follow[/COLOR]

# site2.com
<VirtualHost *:443>
#
  ServerName site2.com
  ServerAlias [www.site2.com]("http://www.site2.com")
#
  ServerAdmin [EMAIL="webmaster@site2.com"]webmaster@site2.com[/EMAIL]


  SSLEngine On
  SSLProxyEngine On
  SSLProxyVerify none 
  SSLProxyCheckPeerCN Off
  SSLProxyCheckPeerName Off
  SSLProxyCheckPeerExpire Off
  SSLCertificateFile /etc/apache2/ssl/site2-com.crt
  SSLCertificateKeyFile /etc/apache2/ssl/site2-com.key


  LogLevel debug
    ErrorLog ${APACHE_LOG_DIR}/site2com.log
  CustomLog ${APACHE_LOG_DIR}/site2com.log combined


  ProxyPreserveHost On
  ProxyRequests off
  ProxyPass / 'https://192.168.23.64/'
  ProxyPassReverse / 'https://192.168.23.64/'    
</VirtualHost>
#
# sync.site1.com
<VirtualHost *:443>
#
  ServerName sync.site1.com
#
  SSLEngine On
  SSLProxyEngine On
  SSLProxyVerify none 
  SSLProxyCheckPeerCN Off
  SSLProxyCheckPeerName Off
  SSLProxyCheckPeerExpire Off


  SSLCertificateFile /etc/apache2/ssl/sync-site1.crt
  SSLCertificateKeyFile /etc/apache2/ssl/sync-site1.key
    
  LogLevel debug
  ErrorLog ${APACHE_LOG_DIR}/sync.site1.log
  CustomLog ${APACHE_LOG_DIR}/sync.site1.log combined
    
  ProxyPreserveHost On
  ProxyRequests off
  ProxyPass / 'https://192.168.23.65/'
  ProxyPassReverse / 'https://192.168.23.65/'


#
</VirtualHost>
#

After configure the **proxyfilter.conf** I enabled the file and disabled both "sudo a2dissite **000-default.conf**" and "sudo a2dissite **default-ssl.conf**"

After enabling and disabling the files when **I open site1.com, site2.com or sync.site2.com, browser display default HTML page (/var/www/html) from PROXY server.** I made lots of changes including clear the DNS and Cache but still PROXY doesn't want to forward the packet to the right destination server.

What I am missing here?

**Thank you for your help**

---

