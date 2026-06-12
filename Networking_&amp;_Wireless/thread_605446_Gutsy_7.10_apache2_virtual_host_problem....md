---
title: "Gutsy 7.10 apache2 virtual host problem..."
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by rusty0101 on 2007-11-07
Had problems updating my debian box to a new kernel, and ultimately lost it entirely. So, put Gutsy Server on it and am now having other interesting issues (like grub not loading quite correctly... Ah well..)

In any case the immediate problem I have is that virtual hosting is behaving an in inconsistent fashion.

I host a couple of small domains for personal use, and have no problem with them being hosted out of the /var/www/ directory. Let's say I have the domain names MyDomain.net MyOtherdomain.com and MyDynamicDomain.nu. It's close enough to the situation that I won't argue. Also I have a host name for the machine that I want to be able to use from within my network, but will not be generally available to the Internet.

In my /var/www directory I have folders named mydomain, myotherdomain.com and mydynamicdomain.nu along with the generically provided apache2-default.

In my /etc/apache2/sites-available folder I started with the 'default'  file, and copied it to mydomain, myotherdomain.com, mydynamicdomain.nu and localhostname.

I then edited each of the files that are not 'default' and deleted the first line.

In mydomain I added the line
  ServerName *.mydomain.net
then changed the DocumentRoot line to read
  DocumentRoot /var/www/mydomain
then changed the <directory /var/www/> line to read <directory /var/www/mydomain/>

I performed similar changes to the configuration files for myotherdomain.com and mydynamicdomain.nu configuration files The localhostname file is not yet being used, so I have not modified it.

Next up I ran sudo a2ensite mydomain, sudo a2ensite myotherdomain.com, and a2ensite mydynamicdomain.nu

For good measure I added 192.168.1.x localhostname mydomain.net myotherdomain.com mydynamicdomain.nu to the /etc/hosts file, and ran 'sudo /etc/init.d/apache2 reload' to load up the new domains into Apache2.

The only error I get is the wonderful fqdn message for ServerName. (corrected by editing 'default' and adding a line that reads ServerName localhostname' between the 'VirtualHostName *' line and '<VirtualHost *>' lines.

So, pointing a web browser at [http://www.mydomain.net](http://www.mydomain.net) gives me a directory listing of /var/www. Pointing another tab at [http://myotherdomain.com](http://myotherdomain.com) gives me a directory listing of /var/www. And pointing a third tab at [http://mydynamicdomain.nu](http://mydynamicdomain.nu)' results in a display of the index.htm[l] file in /var/www/mydynamicdomain.nu/.

In other words, I'm getting some things that are working right, and other things that definitely are not. I'm not seeing what is actually wrong or different between the configurations. I'm not getting errors abut missing files, etc. The last error.log message relates to the last restart of Apache (done after reloading gave me the same results.

I'm at a loss to understand why I am seeing this behavior. If all of the URLs ended up pointing at the /var/www directory, I would somewhat understand, or at least mark it up to something else being wrong that I would have to go and dig up. However I'm seeing one of the sites behave exactly as expected, but the others not. :confused:

Any help welcome. Thank you,

-Rusty

---

### Post by rusty0101 on 2007-11-10
Solved my issue. May help others as well.

Make sure that the ServerName for the virtual domain is what will be passed to the server on a connection attempt. I.e. 'ServerName *.mydomain.net' is not correct. 'ServerName [www.mydomain.net](www.mydomain.net)' is correct.

As far as I can tell, you have to specify each possible 'ServerName' entry in a separate virtual domain record. If you want 'mydomain.net', 'www.mydomain.net', and 'web.mydomain.net' to all point at the same virtual server instance, you have to set up three virtual domains, and give each one a separate 'VirtualName' line to handle the differences. I'm not entirely sure I like that, as it means three different places to make updates if necessary, but it does allow you to treat users of each of the addresses differently.

Thanks..

---

### Post by john./ on 2008-02-08
I spent days reading other posts trying to find the answer to this problem. Just for the record, the key thing that 'they' all missed telling me was to insert the FQDN related line at line 2 of the default site configuration file.

THANK YOU!! :guitar:

john./

PS next to the ServeName directive, you can use ServerAlias to get the same site to serve to more than one URL.

Best;

john.//

---

