---
title: "apache issues"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by dougie_boy on 2009-10-27
i am having a problem creating a web accessable server.

i am running ubuntu server with gnome desktop on a acer revo r3600 & my router is a netgear.

the hardware is fine and has stopped playing up and now i am down to the nitty gritty of the CLI.

i am trying to create and host a number of lite site and a wordpress blog, i have a LAMP config but cannot work out how to reach the apache server from anywhere apart from the local machine.

the server is 192.xxx.xxx.5
the gateway is 192.xxx.xxx.1

i have listed port forwarding on the router, for anything on port 80 to go to the server.

i can only get from 192.xxx.xxx.2 to the apache server if i go to 192.xxx.xxx.5 and i can ping it. if i type in local host it fails, as does 127.0.0.1.

i can also ping out from the server to any location on the net and to other machines on my network.

any clues as to where i should start?

---

### Post by martrn on 2009-10-27
visit 

[http://ip-address.domaintools.com/]("http://ip-address.domaintools.com/")

and post **[to someone who can test your webserver]**  the first two lines of what you find out on that page.....

IP Address:  	
Hostname:

TO EDIT:
Let us know if it works.

---

### Post by dougie_boy on 2009-10-27
i have visited the site, but i have no idea what to do with this information. i recognise my ip, but the hostname is alien to me.

how can i use this data?

Only just getting to grips with IP and learning as i go.

---

### Post by martrn on 2009-10-27
> **dougie_boy said:**
> i have visited the site, but i have no idea what to do with this information. i recognise my ip, but the hostname is alien to me. how can i use this data? Only just getting to grips with IP and learning as i go.

your hostname should be your public hostname, and if you visit it it should show your webserver for example if your host name was user987548745.switch768.antwerp.telifonica.com  then I should be able to connect to your server by specifitying :

http://  user987548745.switch768.antwerp.telifonica.com  [without the spaces].

Basically its your www address. You need to note what is on that page because you have proxy/proxytypes/connection types/remote ports on that page that should give clues if someone else cant connect.

Irrespective as to weather your hostname is alien to you or not its still your hostname.

You should also be able to connect by using your isp number if its not shared by http:// xxx.xxx.xxx.xxx and replaceing the x's by the numbers found at [http://ip-address.domaintools.com/]("http://ip-address.domaintools.com/").

---

### Post by dougie_boy on 2009-10-27
okay,

i have tested my public hostname address via my iphone over 3g and safari cannot navigate to the page. i cannot naviagte there via my home network either.

it is not showing a proxy type, nor a black list status. when i try to connect to my ip address it forwards me to my router login page.

am i right in thinking my router is part of the problem, and that it is not forwarding the request on port80?

---

### Post by halitech on 2009-10-27
if you are getting the router logo in page, something is not set up correctly. Normally routers use port 8080 for their config set up so you may want to run on a different port or disable remote admin on the router.

---

### Post by martrn on 2009-10-27
> **dougie_boy said:**
> Am i right in thinking my router is part of the problem, and that it is not forwarding the request on port80?

Maybe.

You have to switch off any firewall in your router that is likely prevent and packackets being sent in two directions.  You have to turn off any super-unintelegent firewall that you do not know what they do.  You have to turn off the ability to be able to administer the router from the internet, and you should only be able to administer or log on to the router using the local area network eg 192.xxx.xx.xxx

You need to make sure ports such as port 80 are forwarded to the computer that has apache installed on it, you need to ensure apache is correctly configured and reachable via your local network, you need to ensure that the router is forward packets properly and you need to ensure you can resolve domain names.  You also need a fixed ip address on your local machine as you may not be able to use a dynamic local address assigned by the router.  You may also need to tell the router how to switch the packets or forward them / can't remember which.  Usually it works fine.

Sometimes setting up a DMZ (de-militirised zone) is easier, than doing all of this.

---

### Post by OffAxis on 2009-10-27
> if i type in local host it fails, as does 127.0.0.1
from where?

those addresses will only work while you're sitting at the 192.xxx.xxx.5 machine, and to be perfectly clear, those should be

[http://localhost/](http://localhost/)

and

[http://192.xxx.xxx.5/](http://192.xxx.xxx.5/)

and

[http://127.0.0.1](http://127.0.0.1)

Basically, there are 3 different levels of testing. 
1. Accessing your server from itself (all three of the above should work)
2. Accessing your server from another machine on the LAN (via the 192.xxx.xxx.5 address)
3. Accessing your server from the Internet
This is where your router and port forwarding comes into play. There's two ways to access your server from the internet; direct at its IP address (http://<your WAN IP) or via name resolution (where you need to have your website name and your WAN IP set up on a DNS server. Usually this is done wherever you registered the website's name at).
If the direct IP address works, then it's your name resolution that's messed up.

---

### Post by dougie_boy on 2009-10-27
okay, checked the netgear router, as Halitech suggested, it keeps 8080 open for remote logins.

if i disable my firewall will it not leave me open to attacks? or is this naive to think so? 

i have turned off the remote logins on my router except those which come from my main pc. 192.168.0.2

>>You also need a fixed ip address on your local machine as you may not be able to use a dynamic local address assigned by the router.

Can i not use dynDNS? the netget comes with a DynDNS option built in, it is set up to track my DNS changes. will this not solve my DNS issues?

>>> you need to ensure apache is correctly configured and reachable via your local network

do you mean, via the localhost address or any way possible. i can contact it via the manchines local ID only. is this enough?

>>>you need to ensure that the router is forward packets properly and you need to ensure you can resolve domain names

is there a guide you can point me to or explain how i can test for this in linux.

Thanks for the help so far.

---

### Post by dougie_boy on 2009-10-27
> **OffAxis said:**
> from where?
Basically, there are 3 different levels of testing. 
1. Accessing your server from itself (all three of the above should work)
2. Accessing your server from another machine on the LAN (via the 192.xxx.xxx.5 address)
3. Accessing your server from the Internet
This is where your router and port forwarding comes into play. There's two ways to access your server from the internet; direct at its IP address (http://<your WAN IP) or via name resolution (where you need to have your website name and your WAN IP set up on a DNS server. Usually this is done wherever you registered the website's name at).
If the direct IP address works, then it's your name resolution that's messed up.

Thanks Offaxis,

i can complete steps 1-2 but 3 is giving me issues. is there a way to test if my request are getting passed to the apache server?

if i try to connect to my ip via proxy i get a time out response. how can i check to see if my apache server is configured to listen to the correct port and for the correct info?

---

### Post by dougie_boy on 2009-10-27
i checked shieldsup! and apparently all my ports are stealth protected. i am assuming that my ISP is blocking port 80.

how can i resolve this and point all traffic to a different port?

---

### Post by DanYoSon on 2009-10-27
so you could try to make the web server listen on another port and then forward that to the server (192.xxx.xxx.5) 

then when you try to access it over the internet you need to specify the port http:// your.ip.address: port (no spaces)

---

### Post by dougie_boy on 2009-10-27
tried using my ip-addy: port8000 but i think i have edited my apache config incorrectly.

when the server reboots i get the following messages:

restarting web server
apache2: could not be reliably determine the server's fully qualified domian name, using 127.0.1.1 for server name
[warn] NameVirtualHost *:80 has no virtualHosts
... waiting apache2: could not be reliably determine the server's fully qualified domian name, using 127.0.1.1 for server name
[warn] NameVirtualHost *:80 has no virtualHosts

is it reading correctly or do i have an error in my code as well?

---

### Post by martrn on 2009-10-27
> **dougie_boy said:**
> [warn] NameVirtualHost *:80 has no virtualHosts
... waiting apache2: could not be reliably determine the server's fully qualified domian name,[/warn] .. no virtualHosts

You must be able to reliable resolve domain names.  
[http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server]("http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server")
Also apache must be set up properly for you to reliable to resolve your domain name ... eg apache must know how to serve file for your hostname ......

[example]  http:// user987548745.switch768.antwerp.telifonica.com [without the spaces].

antwerp.telifonica.com  would go in ServerName and/or would go in place of ServerAlias see the url above.

You also need to edit your /etc/hosts and configure bind so that it resolves domain names as a computer, not relying on browsers.  For example in a terminal you should be able to type **whois google.com** and it should give you the full output from the whois server and then you will know that you can resolve domain names, as well as resolving your own domain name.

Errors and obmissions possiable, this is all from the top of my head.

---

### Post by OffAxis on 2009-10-27
> could not be reliably determine the server's fully qualified domian name, using 127.0.1.1 for server name
not such a big deal. If you're running a catch all (the *) on a basic server it's fine (and you're not running your own DNS).
 
> NameVirtualHost *:80 has no virtualHosts
That's gonna be a problem...

Your apache website configuration files are botched.

They used to be in /etc/apache2/httpd.conf but nowadays the idea is to give each website their own configuration file. These are supposed to be kept in **/etc/apache2/sites-available**
and enabled with
```
sudo a2ensite <filename>
```
and disabled with
```
sudo a2dissite <filename>
```

That way you can turn an individual website on or off without taking all your sites offline. And then a server 'restart'.
```
sudo /etc/init.d/apache2 reload
```

Anyway, there's two bad things about doing it this way:
1. Virtual Hosts aren't as obvious as they used to be
2. The order of precedence is no longer obvious, either

You can look in the **/etc/apache2/sites-enabled** folder to see what sites are currently running.

Can you post your configuration files that are currently running?

Here's about the minimum you can get away with:
```
<VirtualHost *:80>
        DocumentRoot /var/www/mysite
        ServerName mysite.com
</VirtualHost>

```

---

### Post by dougie_boy on 2009-10-28
> <VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/douglas/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/douglas/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from none
        Allow from all
    </Directory>

</VirtualHost>

am i correct in guessing that i am simply missing the server name?
to change the post to i just adjust the line
<virtualhost *:80> to a different port?

---

### Post by OffAxis on 2009-10-28
> am i correct in guessing that i am simply missing the server name?
yes and a little bit of no.

Yes, you are missing a **ServerName **directive. Gotta have that.
You can throw in a **ServerAlias **directive, too, if you like, to catch sub domains.

The best place for all your directive needs is still the apache docs;
[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

The 'no' from above is in reference to your <Directory> call outs. You've got some overlap (DocumentRoot being defined as an absolute path and /), a lot of Directory specifications that are unnecessary at this point (just comment them out with a # for testing), and some divergent syntax (some Directory names are in quotes, some end with a '/', and some end with a folder name). 
I *think *apache directives can figure it out, but I'm not entirely certain (there are a multitude of options). It's best to adopt a standard style (the one in the doc files is a good example).

---

### Post by dougie_boy on 2009-11-01
thanks for the advice. sorted it all out now and the http sever is behaving. currently in the process of creating something to go on to the site.

thanks again to OffAxis, martrn and DanYoSon

really starting to enjoy my ubuntu experience

---

