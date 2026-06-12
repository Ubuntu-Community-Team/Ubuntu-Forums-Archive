---
title: "Issues with using DNSMasq to fake a production server"
date: 2017-08-09
forum: Networking &amp; Wireless
---

### Post by excl2 on 2017-08-09
Hello.  I am currently using Ubuntu 16.04.3.  I have set up an apache2 server on my machine to act as a local version of a production server for testing and I'm trying to use dnsmasq to point to the local IP when using the production URL.

I have edited the /etc/hosts file so that the production url is listed and points to the local ip address.  When I open a browser on the machine with apache and type in the URL, then it goes to the local IP as expected.  When I take a mobile device and connect to the local network, and attempt to go to the URL, I get a RT-N66U error page, saying the cable for the Ethernet is not plugged in.  If I type in the local IP address for the server, I'll get the server page as expected, but the URL doesn't work.

What am I missing?  Thanks!

---

### Post by excl2 on 2017-08-11
bump

---

### Post by SeijiSensei on 2017-08-11
You'd need to have the equivalent of an /etc/hosts file on the mobile device, too, would you not? 

Otherwise you need a private DNS server.  You could run BIND9 on your server, but that seems like overkill to me.  Whether the URLs have the server's fully-qualified domain name or its IP address, the application should run the same way.

---

### Post by excl2 on 2017-08-14
> **SeijiSensei said:**
> You'd need to have the equivalent of an /etc/hosts file on the mobile device, too, would you not? 

Otherwise you need a private DNS server.  You could run BIND9 on your server, but that seems like overkill to me.  Whether the URLs have the server's fully-qualified domain name or its IP address, the application should run the same way.

 I am manually setting the DNS server to point to my local machine.  I've had this set up in the past with Ubuntu 10, but it doesn't seem to be working now.  Before, I would have to configure the dnsmasq.conf file so that mybigdumbserver.com pointed to 192.168.1.2. (the local machine IP).  I would change the mobile device DNS server to manually point to 192.168.1.2 and with dnsmasq running, the device would connect to the local machine dns (I assume using dnsmasq).  I would get redirected back to the same machine ip for "mybigdumbserver.com", and go into the apache2 directory to display the website I was looking for.

Now, with the mobile device's dns settings pointing to the local machine, I'm getting a "mybigdumbserver.com"'s server DNS address could not be found.

---

### Post by Andreyshel on 2017-08-15
First try to query your dns server with nslookup.
use  nslookup *[mybigdumbserver.com]("http://www.mybigdumbserver.com") mylanip *from your computer
Post your reply here.
Thank.you

---

### Post by excl2 on 2017-08-15
I'm getting:

Server: 127.0.1.1
Address: 127.0.1.1#53

So, something seems off.

I have the DNS manually set in the network settings to point to the IP address of the machine too.

---

### Post by Andreyshel on 2017-08-15
So you do not get any ip returned?
Correct answer should look like

NoServer:        127.0.1.1
Address:    127.0.1.1#53


non-authoritative answer:
Name:mybigdumbserver.com
Address: my_lan_ip

Do you have  directive like this
address=/mybigdumbserver.com/my_lan_ip
in your dnsmasq.conf?

---

### Post by excl2 on 2017-08-15
Oh Sorry, I missed that part:

Name: mybigdumbserver.com
Address: 10.0.0.1 (not my IP)


I do have that line in dnsmasq.conf as well, but I read somewhere that you need to edit /etc/hosts instead starting in Ubuntu 12 (I believe it was).  In addition to the address line, I have "interface=enp1s0" to enable the network connection I'm using.

---

### Post by excl2 on 2017-08-15
Oh, I also wanted to add that I checked the /etc/resolv.conf file, and it points to 127.0.1.1, rather than to my local machine.  I tried to force my local IP address in there, and I get a "server cannot be reached" error.  If I restart NetworkManager, then the ip address is set back to the 127 one, which I guess is somewhat expected.

---

### Post by SeijiSensei on 2017-08-15
The file /etc/resolv.conf is rewritten when the network comes up by the resolvconf package.  If you want to specify a DNS server, edit the file /etc/resolvconf/resolv.conf.d/head and add the line
```

nameserver 10.10.10.10

```
with the appropriate IP address.  It will be placed ahead of 127.0.1.1 when you next reboot.

---

### Post by excl2 on 2017-08-15
Okay, I edited the file, despite a commented warning to "not handwrite changes as they will be over-written".  Restarted NetworkManager, and /etc/resolv.conf at least points to the local IP address now.  However, nslookup still does not give me the correct address for the lookup.

Do I need to install an actual dns server?  I was under the impression that dnsmasq would do this for me.  At least it worked in Ubuntu 10.  I edited dnsmasq.conf to point to the local machine address and changed the DNS address on my mobile device.  When I loaded the page from the device, dnsmasq would point back to the same machine and I would load the webpage locally.

---

### Post by Andreyshel on 2017-08-15
> [COLOR=#000000]Do I need to install an actual dns server? I was under the impression that dnsmasq would do this for me.[/COLOR]
Yes are right. Dnsmasq can do that for you. It is a dns server. You just need to configure it properly. 

```
[COLOR=#333333][FONT=sans-serif]grep ^[^#] /etc/dnsmasq.conf [/FONT][/COLOR]
```[COLOR=#333333][FONT=sans-serif]
shows us your config without comments. 
You can fake url if you want.

[/FONT][/COLOR]

---

### Post by excl2 on 2017-08-15
```

address=/mybigdumbserver.com/<local ip>
address=/myotherbigdumbserver.com/<local ip>
interface=eth0
interface=enp1s0
except-interface=eth1
except-interface=ens1

```

Just to note, I'm running a double network connection.  One is on a local router and is the one I'm using for this.  The other (ens1) is usually off, but I connect to it if I need to download updates and such.  When I was on Ubuntu 10, it named the connections eth0 and eth1.  When I moved to Ubuntu 16, it has now named them enp1s0 and ens1.

---

### Post by Andreyshel on 2017-08-15
Thank you for your patience.

Do you have interfaces eth0,eth1 now?
Because if they are outdated maybe it is good to tidy up them.
Also, if I understand documentation for dnsmasq correctly you do not need to combine interface and except-interface in one config file. So technically you need only
```

address=/mybigdumbserver.com/<lan ip>
address=/myotherbigdumbserver.com/<lan ip>
interface=[COLOR=#000000][FONT=&amp]enp1s0
[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
in the file

[/FONT][/COLOR]

---

### Post by excl2 on 2017-08-15
okay, I did what you suggested, and restarted NetworkManager, but still no luck.

---

### Post by Andreyshel on 2017-08-15
Okay.
What returns systemctl status dnsmasq?
We are checking if dnsmasq is running. 
Otherwise everything looks good so far.

---

### Post by excl2 on 2017-08-15
dsnmasq.service
 Loaded: not-found (Reason: No such file or directory)
 Active: inactive (dead)

However, if I do a ps -A | grep dns, there is an instance for dnsmasq

---

### Post by Andreyshel on 2017-08-15
[COLOR=#000000]You just misspelled it.[/COLOR]

---

### Post by excl2 on 2017-08-15
Sorry, that was just bad typing.  I didn't copy paste that.

[COLOR=#000000]dnsmasq.service[/COLOR]
[COLOR=#000000]Loaded: not-found (Reason: No such file or directory)[/COLOR]
[COLOR=#000000]Active: inactive (dead)[/COLOR]

---

### Post by Andreyshel on 2017-08-15
Okay. Here can be a problem.
Does you dnsmasq version up to date?
Perhaps it was not upgraded together with the system.
Try to upgrade it by using sudo apt-get install dnsmasq.

---

### Post by excl2 on 2017-08-15
I installed ubuntu 16 next to my original ubuntu 10 a few weeks ago.  I've since done an apt-get update and upgrade, so I would think it's up to date.

---

### Post by Andreyshel on 2017-08-15
Strange....
Do you have it as script in /etc/init.d folder?

---

### Post by excl2 on 2017-08-15
no, it's not there.  If I do a which, it's in /user/sbin/

However, I think I read somewhere that dnsmasq is run through NetworkManager now, so I don't know if it is called through that script or not.

---

### Post by Andreyshel on 2017-08-15
Dnsmasq can be configured as a backend for Networkmanager but it is not necessary.
Here is output of systemctl  status dnsmasq from my Pc(Ubuntu 16).
&#9679;```
 dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
   Loaded: loaded (/lib/systemd/system/dnsmasq.service; enabled; vendor preset: 
  Drop-In: /run/systemd/generator/dnsmasq.service.d
           &#9492;&#9472;50-dnsmasq-$named.conf, 50-insserv.conf-$named.conf
   Active: active (running) since &#1074;&#1090; 2017-08-15 18:48:58 CEST; 15min ago
  Process: 20890 ExecStartPost=/etc/init.d/dnsmasq systemd-start-resolvconf (cod
  Process: 20846 ExecStart=/etc/init.d/dnsmasq systemd-exec (code=exited, status
  Process: 20829 ExecStartPre=/usr/sbin/dnsmasq --test (code=exited, status=0/SU
 Main PID: 20889 (dnsmasq)
    Tasks: 1
   Memory: 656.0K
      CPU: 29ms
   CGroup: /system.slice/dnsmasq.service
           &#9492;&#9472;20889 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq 
```

Maybe you can try reinstall dnsmasq and try to start it separately.

---

### Post by excl2 on 2017-08-15
Whew.  Your suggestion worked!

This is what I ended up doing:

> 
[B]Stop NetworkManager running it's own Dnsmasq
[/B][FONT=arial]
[COLOR=#24292E]$ sudo cp /etc/NetworkManager/NetworkManager.conf /etc/NetworkManager/NetworkManager.conf.pkg
$ sudo cat /etc/NetworkManager/NetworkManager.conf \
    [COLOR=#D73A49]|[/COLOR] sed -e [COLOR=#032F62]'s/dns=dnsmasq/#dns=dnsmasq/'[/COLOR] \
    [COLOR=#D73A49]>[/COLOR] /etc/NetworkManager/NetworkManager.conf

(Or just run a sudo nano for NetworkManager and comment out the dns part)
$ sudo restart network-manager
[/COLOR]("sudo service NetworkManger restart" worked for me here.)[/FONT]
[B][URL="https://gist.github.com/magnetikonline/6236150#install-dnsmasq-and-config"]
[/URL]Install Dnsmasq and config[/B]
[FONT=arial]
[COLOR=#24292E]$ sudo apt-get install dnsmasq
$ sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf.pkg
$ sudo wget \
    [https://gist.github.com/magnetikonline/6236150/raw/dnsmasq.conf](https://gist.github.com/magnetikonline/6236150/raw/dnsmasq.conf) \
    -O /etc/dnsmasq.conf

(Or configure the dnsmasq.conf file through your editor with the address= and interface= lines configured)
$ sudo /etc/init.d/dnsmasq restart
[/COLOR]
[/FONT][COLOR=#24292E][FONT=-apple-system]**[FONT=arial]Your host machine will now be running it's own configured instance of Dnsmasq, not one managed via NetworkManager.[/FONT]**
[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]

[/FONT][/COLOR]The short of it is that I needed to stop dnsmasq running out of NetworkManager and get it as it's own instance.  Once that was going everything worked again as it had in Ubuntu 10.  Thanks so much for your help and patience![COLOR=#24292E][FONT=-apple-system]

[/FONT][/COLOR]

---

