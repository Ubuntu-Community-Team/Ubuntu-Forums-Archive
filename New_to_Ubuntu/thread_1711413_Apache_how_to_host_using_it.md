---
title: "Apache how to host using it"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Ulrichvw on 2011-03-21
Hi,

I installed apache using the terminal so now how would I go about hosting a website with it off of my pc with ubuntu os.

Thanks

---

### Post by bluefrog on 2011-03-21
reading some howto at [http://www.howtoforge.com/howtos/web-server/apache](http://www.howtoforge.com/howtos/web-server/apache) might help you

---

### Post by sriramrangan on 2011-03-21
Basically, you have to follow these steps:
1.Go to your router config page using your browser (Usually: [http://192.168.1.1](http://192.168.1.1)), and set the DMZ host as your local IP, this field should be under NAT.
2. If you have a static IP, then you can skip this step; Make an account with [http://www.dyndns.com](http://www.dyndns.com) with the host of your choice. Leave the host field empty.
3. If your router provides a dynamic dns option, you can skip this step. Basically you have to set up a cron job which updates your IP change to dyndns every 5 minutes or so. You can do that by adding the line: ```
*/2 * * * * root  curl -u username:password "http://members.dyndns.org/nic/update?hostname="hostname"&wildcard=NOCHG&mx=NOCHG&backmx=NOCH" > /dev/null 
``` . Be sure to replace username and password and "hostname" with your dyndns account details that you have created.
4. Visit [http://www.megaproxy.com/freesurf](http://www.megaproxy.com/freesurf) and enter the name of your dyndns site you have created after a few minutes. As, if you access a remote site locally, it directs you to the router config page
5. Modify the "www" CNAME record to point it to your dyndns host.
6. If you are adding a vhost then you should use the following code with the Server name, etc. :
```

<VirtualHost localip:80>
 ServerName domain.com
 DocumentRoot location of site
</VisrtualHost>

```
Be sure to replace localip, domain.com and location of site with the respective values

---

