---
title: "OpenDNS dynamic IP update script/program?"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by adcwoef on 2008-08-07
Hello

Are there any good scripts or programs that will update your dynamic IP-address with your OpenDNS account when it changes? I think I'm looking for a script that I can set up for a cron job but other solutions are welcome as well

Thanks!

---

### Post by dmizer on 2008-08-07
```
sudo aptitude install ddclient
```
No need to set it up as a cron job.  it runs as a daemon in the background.

More information here: [http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

---

### Post by adcwoef on 2008-08-07
Works fine. Thanks!

---

### Post by edoardo on 2008-08-12
Worked fine for me too. But here is a detailed HOWTO :

You should have an account on opendns.com, and defined a network consisting of one dynamic ip.

OPENDNS.COM - automatic dynamic IP update from Ubuntu

With Synaptic install 
1) ddclient
2) libio-socket-ssl-perl   
if the latter is missing /var/log/daemon will show an error and the update won't work

enter anything in the synaptic UI configuration, you';ll edit files by hand.

then as sudo edit
-------------
# /etc/default/ddclient
...
# Set to "true" if ddclient should run in daemon mode
run_daemon="true"
...
-------------
and, as explained in [http://www.opendns.com/support/article/192](http://www.opendns.com/support/article/192)

# /etc/ddclient.conf

##
## OpenDNS.com account-configuration
##
ssl=yes
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=whatismyip.org
server=updates.opendns.com
login=<my-username>
password='<my-password>'
<my-opendns-network-name>

------------
running 
 sudo /etc/init.d/ddclient restart

and check /var/log/daemon.log
 SUCCESS:  updating <my-opendns-network-name>: good: IP address set to ...

---

### Post by jonathanmotes on 2008-08-21
I'm getting the error below (from my /var/log/daemon.log file) on startup:
```
Aug 21 19:23:13 jmotes1-laptop ddclient[5434]: WARNING:  cannot connect to myip.dnsomatic.com:80 socket: IO::Socket::INET: Bad hostname 'myip.dnsomatic.com'
```

(I'm using Dns-O-Matic rather than updating openDNS directly).

I think it is because my internet connection has not yet been made. How would I make it rerun after my connection is made - or is that not needed since ddclient might be checking again in a few seconds?

Thanks!

---

### Post by Nitewalker on 2008-10-03
Just installed as your post, works good, thanks for the info:popcorn:

---

### Post by mattman on 2008-11-18
I think the hostname for dnsomatic should be "all.dnsomatic.com" instead of "myisp.dnsomatic.com".

> **jonathanmotes said:**
> I'm getting the error below (from my /var/log/daemon.log file) on startup:
```
Aug 21 19:23:13 jmotes1-laptop ddclient[5434]: WARNING:  cannot connect to myip.dnsomatic.com:80 socket: IO::Socket::INET: Bad hostname 'myip.dnsomatic.com'
```

(I'm using Dns-O-Matic rather than updating openDNS directly).

I think it is because my internet connection has not yet been made. How would I make it rerun after my connection is made - or is that not needed since ddclient might be checking again in a few seconds?

Thanks!

---

### Post by Wendell_Brown on 2009-05-10
Here's how I did it....

[LIST=1]
[*]Set up a Dns-O-Matic account ([https://www.dnsomatic.com/](https://www.dnsomatic.com/)) - this service is provided free of charge by the OpenDNS folks.  It automatically updates the dynamic dns services you select (OpenDns, dynDNS, No-IP, ZoneEdit, etc).

[*]Edit your /etc/crontab file. ```
sudo gedit /etc/crontab
```
[*]Add the following line to the file (changing the User and Password to your DNS-O-Matic User Id and Password):```
0 5 * * * root wget https://user:password@updates.dnsomatic.com/nic/update
```  
[/LIST]

Now your dynamic Ip address is published to DNS-O-Matic every morning at 5:00 am and DNS-O-Matic publishes that address to all of the dynamic dns services you have set up on your account.

Hope this helps!

---

### Post by CAPLinux on 2009-06-29
When I Check the log file, I get this message

Jun 29 22:02:47 Trinity-Laptop ddclient[22072]: WARNING:  caught SIGTERM; exiting

What is wrong?

---

### Post by dmizer on 2009-06-29
> **CAPLinux said:**
> When I Check the log file, I get this message

Jun 29 22:02:47 Trinity-Laptop ddclient[22072]: WARNING:  caught SIGTERM; exiting

What is wrong?

Are there any other errors when running the following command:
```
sudo /etc/init.d/ddclient restart
```

If not, please post your current /etc/ddclient.conf (please remember to remove your username and password).

---

### Post by CAPLinux on 2009-07-06
> **dmizer said:**
> Are there any other errors when running the following command:
```
sudo /etc/init.d/ddclient restart
```

If not, please post your current /etc/ddclient.conf (please remember to remove your username and password).
Dmizer,

When I run the command I get the following.

/etc/default/ddclient: 27: Home: not found
 * Restarting Dynamic DNS service update utility ddclient     

Home is the name of my network on OpenDNS.  I have copied the OpenDNS settings as they were in the post, what am I doing wrong??

Thanks again.

---

### Post by dmizer on 2009-07-06
CAPLinux, please post your ddclient.conf file (remember to edit out your username and password)

---

### Post by CAPLinux on 2009-07-06
> **dmizer said:**
> CAPLinux, please post your ddclient.conf file (remember to edit out your username and password)
Dmizer,

Here is my ddclient.conf file

# Configuration for ddclient scripts 
# generated from debconf on Mon Jun 29 21:51:33 EDT 2009
#
# /etc/default/ddclient

# Set to "true" if ddclient should be run every time a new ppp connection is 
# established. This might be useful, if you are using dial-on-demand
#run_ipup="false"

# Set to "true" if ddclient should run in daemon mode
run_daemon="true"

# Set the time interval between the updates of the dynamic DNS name in seconds.
# This option only takes effect if the ddclient runs in daemon mode.
daemon_interval="300"

##
## OpenDNS.com account-configuration
##
ssl=yes
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=whatismyip.org
server=updates.opendns.com
login=username
password='PASSWORD'
Home

---

### Post by fusionfox on 2009-07-14
I'm having some trouble with this process, if anybody is able to help I'd be very appreciative.

In /var/log/daemon.log I'm getting this message:
```
Jul 14 23:01:16 ubuntu-vpn ddclient[2897]: UPDATE:   updating all.dnsomatic.com
Jul 14 23:01:16 ubuntu-vpn ddclient[2897]: FATAL:    Error loading the Perl module IO::Socket::SSL needed for 
SSL connect.
Jul 14 23:01:16 ubuntu-vpn ddclient[2897]: FATAL:     On Debian, the package libio-socket-ssl-perl must be ins
talled.
Jul 14 23:09:15 ubuntu-vpn init: tty4 main process (1872) killed by TERM signal
Jul 14 23:09:15 ubuntu-vpn init: tty5 main process (1873) killed by TERM signal
Jul 14 23:09:15 ubuntu-vpn init: tty2 main process (1878) killed by TERM signal

```

I've installed libio-socket-ssl-perl through apt-get so I'm not sure why it cant find the module. I also tried installing the Perl module directly through CPAN but I get this:
```
Writing Makefile for IO::Socket::SSL
Could not read '/home/******/.cpan/build/IO-Socket-SSL-1.26-saEB5t/META.yml'. Falling back to other methods to determine prerequisites
Can't exec "q": No such file or directory at /usr/share/perl/5.10/CPAN.pm line 7698.
  SULLR/IO-Socket-SSL-1.26.tar.gz
  q -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 SULLR/IO-Socket-SSL-1.26.tar.gz              : make NO

```

Not sure what's going wrong here at all :(

---

### Post by brianfreytag on 2009-12-09
If you're trying to use dnsomatic.com for your config stuff, follow this tutorial:

[https://www.dnsomatic.com/wiki/ddclient](https://www.dnsomatic.com/wiki/ddclient)

I got it to work perfectly with ddclient, using this config:

```

# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf
##
## dnsomatic.com account-configuration
##
ssl=yes #use ssl-support
pid=/var/run/ddclient.pid
use=web, web=myip.dnsomatic.com
server=updates.dnsomatic.com,
protocol=dyndns2,
login=myusername,
password=mypassword
all.dnsomatic.com

```

Note: I'm running it in Daemon mode, updating every 3600 seconds (approx. 1 hour).

HTH

---

