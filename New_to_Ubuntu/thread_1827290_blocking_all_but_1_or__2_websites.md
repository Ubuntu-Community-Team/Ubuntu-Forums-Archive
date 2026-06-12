---
title: "blocking all but 1 or  2 websites"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by callmebadger on 2011-08-17
hi all

i am hoping to block access to all websites but say moshimonsters and weebles, with the option of adding more in the future if so needed.

i am an absolute beginner so makes sense to post it here.

I have looked through other posts but as I am so green i dont really no what to search for in the first place.

so far i have come accross terminal code, gnome nanny, Dansguardian and various combinations with squid.
can u think of anymore?? in order to make the computer safe for my kids. it will only be used for games and moshi and weebles.

what i really would like is help to narrow down my options.
 then help on how to.
thank you.:-k

---

### Post by donkyhotay on 2011-08-17
dansguardian is what I usually see suggested around here. I'm assuming this is to limit kids' access (which is why most people want filters). I have a brother who attempted to set up a network filter for his kids. He did the same thing you did, posted to a forum, got a link to a howto online somewhere and followed the steps. It took only a day or two for my nephews to figure out how to bypass it. I've seen it many times and generally don't recommend in relying upon an installed program to limit access, especially if your knowledge of computers is limited. Security is only as good as the person who set it up so if you don't know much then it won't take much to get past whatever you can do. Also even if you are a master computer networking guru, there is nothing you can install on a computer that a determined kid won't be able to bypass so long as he is physically sitting at the computer. One of the first rules of computer security is that physical access *is* root access. Real security requires proxies between the computer and the internet that are under lock and key, not on the computer you're trying to filter. Proxies like that aren't very practical for the average user as it's unlikely to have your own personal server. In addition to simply uninstalling/removing the filtering software on the computer you're trying to protect, creating a liveCD will bypass the filter temporarily and completely prevent you from even knowing something is wrong afterwards since it doesn't save any changes. Even if they're young and you figure "aww, they're not old enough to know how to do that kind of stuff", all it takes is one google search for "how can I bypass an internet filter" on a friends' or local library computer to come up with the answer. Assume you're kids are smarter then you, no offense but most kids usually are smarter then their parents when it comes to computers. My recommendation for people wanting to limit computer is access is to not mess with software filters, they'll do nothing but give you a false sense of security. The best security is to simply keep the computer in a public location (like the family room), and just keep an eye on what your kids are doing.

---

### Post by cchester on 2011-08-17
You could create a whitelist (only the sites you have approved) and include the ones you mentioned.

Dansguardian works pretty good and has a GUI.

Also you could create another account on the computer and make it the admin account and the other account restricted and lok down everything that you don't want them to be able to do.

---

### Post by callmebadger on 2011-08-17
thanks donkyhotay,
she is only 7 so think she would just take my word for it that it only does what i say. ;)

but i understand what u are saying, for the time being i am happy to try. and hope a better solution crops up when she is a little older.

most of the time she is in the living room playing these website games but i want to introduce her to the educational games and edubuntu early on.

may try dansgardian and see.

thank you
any other suggestions/recomendations

---

### Post by callmebadger on 2011-08-17
thanks cchester 
a whitelist you say, will look into this more.

would dansgardian control her account from the admin account?

thankyou

---

### Post by fdrake on 2011-08-17
sometimes your isp account may give you some filtering options did you check or call them? anyway it's still possible to get around this things easly with a proxy server. so in the end it's already lost fight.

---

### Post by callmebadger on 2011-08-17
thanks fdrake,
think i just want to control the bedroom computer with little messing about with static ip on all 3 computers and one laptop the wii the ps3 and mobile phones and so-on.

for me just changing edubuntu or loading some software on edubuntu would be a lot less hassle.

thank you

---

### Post by callmebadger on 2011-08-18
:-k

[SIZE=3][COLOR=Black]has anybody used dansgardian ? is it good and why?

has anybody used a whitelist ? what instructions did you follow and did you have any problems?

or would anybody recommend another that they have used or are using?

thank you[/COLOR][/SIZE]

---

### Post by donkyhotay on 2011-08-18
> **callmebadger said:**
> thanks donkyhotay,
she is only 7 so think she would just take my word for it that it only does what i say. ;)

but i understand what u are saying, for the time being i am happy to try. and hope a better solution crops up when she is a little older.

most of the time she is in the living room playing these website games but i want to introduce her to the educational games and edubuntu early on.

may try dansgardian and see.

thank you
any other suggestions/recomendations

When I was 7 I was modifying the source code of my games on my dads C64. Admittedly I broke them more often then not and had to revert since I was just going by trial and error but I doubt my dad could have successfully kept me out if he wanted to (wasn't relevant since C64 didn't have any real networking). I have a friend who's 4 year old could (by himself) turn on his parents computer, launch starwars battleground, and manage to hold his own pretty well against the bots. Don't underestimate kids just because they're young.

//edit: if you're insistent on learning more about dansguardian [this thread](http://ubuntuforums.org/showthread.php?t=207008) looks like it has the information you want.

---

### Post by callmebadger on 2011-08-18
t[COLOR=Black]hanks for the info will give it a try,

just taking a look at squib at the moment[/COLOR] [COLOR=Black]
i was planning on combining info from two sources does anybody know if this would work.
what i write below is not sure to work so please dont use it unless someone says it is good as i am a noob and just grasping at straws. lol

the  first is of ubuntu and was planning to use some with some of the info on linuxquestions this is how it is on there, but below is how i was planning to use this information for my kids pc.[/COLOR] [COLOR=Black]
please advice
[/COLOR] [COLOR=Black]
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)
Install Squid

Install squid and squid-common

sudo aptitude install squid squid-common

Edit the squid config file.

sudo vi /etc/squid/squid.conf

Set the allowed hosts.

acl internal_network src 192.168.0.0/24 (Where 192.168.0.0/24 is your IP range.)
http_access allow internal_network

Set the correct permissions.

sudo chown -R proxy:proxy /var/log/squid/
sudo chown proxy:proxy /etc/squid/squid.conf

You will need to restart squid for the changes to take affect.

sudo /etc/init.d/squid restart

Now open up your browser and set your proxy to point to your new squid server on port 3128

Authentication

If you wish to use authentication with your proxy you will need to install apache2 utilities

sudo aptitude install squid squid-common apache2-utils

To add your first user you will need to specify -c

sudo htpasswd -c /etc/squid.passwd first_user

Thereafter you add new users with

sudo htpasswd /etc/squid.passwd another_user

Edit the squid config file

sudo vi /etc/squid/squid.conf

Set the the authentication parameters and the acl

auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid.passwd
auth_param basic children 5
auth_param basic realm NFYE Squid proxy-caching web server
auth_param basic credentialsttl 3 hours
auth_param basic casesensitive off

acl users proxy_auth REQUIRED

acl sectionx proxy_auth REQUIRED

http_access allow users

So this is what your squid.conf should look like.

acl all src 0.0.0.0/0.0.0.0
acl internal_network src 192.168.0.0/24
acl users proxy_auth REQUIRED
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 # https, snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl sectionx proxy_auth REQUIRED
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow manager localhost
http_access allow users
http_access allow internal_network
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all

Redirect the all HTTP traffic.

If you would like to redirect the all HTTP traffic through the proxy without needing to set up a proxy manually in all your applications you will need to add some rules

iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

Where eth1,eth0 are the LAN, WAN devices and 192.168.0.1 is the IP address of your LAN device.

If you wish to monitor the performance of your proxy you can look as some log parser&#8217;s (sarg, calamaris, ect.)





[/COLOR]      [COLOR=Black]www.linuxquestions.org/questions/linux-networking-3/squid-to-block-all-sites-except-1-or-2-sites-573655/

who ever asked for content filtering??? you appear to just be advertising your own project, not answering the question at hand.

winxandlinx you can do exactly what you want very very simply with squid. there is no need whatsoever to use other tools in conjunction with it. you just want a dstdomain whitelist and permit everything in that whitelist and then follow up with a blanket deny after it.


acl whitelist dstdomain .google.com .mycompany.com
acl all src 0.0.0.0/0.0.0.0

http_access permit whitelist
http_access deny all




[/COLOR]    [SIZE=3][COLOR=Black]here is what i was planning to do.
Install Squid

Install squid and squid-common

sudo aptitude install squid squid-common

Edit the squid config file.

sudo vi /etc/squid/squid.conf[/COLOR][/SIZE]    [COLOR=Black]

[/COLOR]  [SIZE=3][COLOR=Black]acl whitelist dstdomain .moshimonsters.com .binweevils.com
acl all src 0.0.0.0/0.0.0.0

http_access permit whitelist
http_access deny all[/COLOR][/SIZE] [COLOR=Black]

will this work? [/COLOR] [COLOR=Black]
does it need more adding?

thank you[/COLOR] [COLOR=Black]

ps will this make changes to to the admin account, as i want to still be able to use it to go onto the net[/COLOR] [COLOR=Black]
pss will this stop me from downloading more games through ubuntu software centre[/COLOR]

---

### Post by callmebadger on 2011-08-18
got this at this point
acl whitelist dstdomain .moshimonsters.com .binweevils.com .linuxforums.org ubuntuforums.org .ubuntuforums.org
No command 'acl' found, did you mean:
 Command 'alc' from package 'amule-utils-gui' (universe)
 Command 'alc' from package 'amule-adunanza-utils-gui' (universe)
 Command 'cal' from package 'bsdmainutils' (main)
 Command 'ace' from package 'libace-perl' (universe)
 Command 'ack' from package 'ack' (universe)
 Command 'acm' from package 'acm' (universe)
 Command 'cl' from package 'cl-launch' (universe)
 Command 'mcl' from package 'mcl' (universe)
 Command 'ac' from package 'acct' (main)
 Command 'al' from package 'mono-devel' (main)
 Command 'gcl' from package 'gcl' (universe)
 Command 'bcl' from package 'bash-completion-lib' (universe)
 Command 'acl2' from package 'acl2' (universe)
 Command 'axl' from package 'afnix' (universe)
acl: command not found

---

### Post by bodhi.zazen on 2011-08-18
For this problem I would use iptables.

iptables -A INPUT -p tcp -s first_ip --sport 80 -j ACCEPT
iptables -A INPUT -p tcp -s second_ip --sport 80 -j ACCEPT
iptables -A INPUT -p tcp --sport 80 -j DROP

You can add ports 443 also if needed.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by callmebadger on 2011-08-18
> **bodhi.zazen said:**
> For this problem I would use iptables.

iptables -A INPUT -p tcp -s first_ip --sport 80 -j ACCEPT
iptables -A INPUT -p tcp -s second_ip --sport 80 -j ACCEPT
iptables -A INPUT -p tcp --sport 80 -j DROP

You can add ports 443 also if needed.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

thank you bodhi zazen
i dont get it :(     or do i?
do i change first_ip  to   .moshimonsters.com    in line 1
then second_ip        to   .binweevils.com
then third_ip             to   ubuntuforums.org
and so on with                .linuxforums.org  .ubuntuforums.org
then
iptables -A INPUT -p tcp --sport 80 -j DROP      # to block everything else

you also mention ports 443 is this the port used for ubuntu software centre? 

thank you for the help

---

### Post by bodhi.zazen on 2011-08-18
Well, you mentioned you wanted access to only one or two sites.

So, yet, list the sites you wish to allow, drop the rest.

If you have a long list of sites, then a proxy is better.

You have to block 443 as many sites use https (in addition to http).

You can also make a custom chain, call it whitelist, and whitelist your ip addresses.

These rules add a custom chain, whitelist, add gogole and ubuntuforums to the whitelist, and block all other sites.

```
iptables -N whitelist
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ubuntuforums.org -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s google.com -j ACCEPT
iptables -I INPUT 1 -j whitelist
iptables -I INPUT 2 -p tcp -m multiport --sports 80,443 -j DROP
```

save your changes with iptables-save

---

### Post by callmebadger on 2011-08-19
thank you
I will give this a try now.

got this error
iptables -N whitelist
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting ip_tables (/lib/modules/2.6.32-33-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

is there a way to allow all requests from ubuntu software centre?

---

### Post by bodhi.zazen on 2011-08-19
You need to run those commands as root.

apt uses port 80, so you will have to allow port 80 for the ubuntu repo you are using.

---

### Post by callmebadger on 2011-08-19
Thank you

will doing sudo be the same as doing it from root?

just dont know anything lol

ok apt ubuntu software centre uses port 80 thanks, but what line do i do to alow this to over ride DROP?

---

### Post by bodhi.zazen on 2011-08-19
Yes sudo is root

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You have to keep adding web sites to your whitelist.

iptables -A whitelist -p tcp -sport 80 -s ubuntu_repos -j ACCEPT

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you are going to use iptables, read this page

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Especially [http://bodhizazen.net/Tutorials/iptables#Saving_your_configuration](http://bodhizazen.net/Tutorials/iptables#Saving_your_configuration)

---

### Post by callmebadger on 2011-08-19
Thank you for all your help bodhi.zazen

will take a look give what you have told me so far a try.

learnt so much these last 2 weeks :biggrin:

this is what i did
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ubuntuforums.org -j ACCEPT
[sudo] password for user: 
 sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ubuntuforums.org -j ACCEPT
 sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s moshimonsters.com -j ACCEPT
 sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s binweevils.com -j ACCEPT
 sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s linuxforums.org -j ACCEPT
 sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s fronter.com -j ACCEPT
 sudo iptables -I INPUT 1 -j whitelist
 sudo iptables -I INPUT 2 -p tcp -m multiport --sports 80,443 -j DROP
 sudo iptables-save
# Generated by iptables-save v1.4.4 on Fri Aug 19 21:15:51 2011
*filter
:INPUT ACCEPT [6074:6664079]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [5717:801898]
:whitelist - [0:0]
-A INPUT -j whitelist 
-A INPUT -p tcp -m multiport --sports 80,443 -j DROP 
-A whitelist -s 91.189.94.12/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 91.189.94.12/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 98.129.229.140/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 174.132.123.98/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 158.36.191.10/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
COMMIT
# Completed on Fri Aug 19 21:15:51 2011


but this has now done the following
didnt realise how many websites were interlinked into 1 website just to load information on a webpage.

for example while trying to load binweevils.com
it connects to x1.binweevils.com        #which i think is covered with binweevils.com allow
it connects to cdn.binw.net                 # which i think i have to  add to white list also how i just add individual websites im not sure?
it connects to google-analytics.com   # why i dont know surely they aint watching what kids are doing
it connects to googleadservices.com # yet again why are they advertising on a kids game website?
guess this is how they make the money. and will just have to add these to the white list to allow it to run.


also think i must of done something wrong for moshimonster.com  used 
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s moshimonsters.com -j ACCEPT
because i got this
XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.18/chrome/toolkit.jar!/content/global/netError.xhtml
Line Number 60, Column 12:    <title>&loadError.label;</title>
-----------^

must say ubuntuforums.org worked straight away :)


and everything else is blocked good so far just need to tweak it more.
can i just do this or do i need to do all of it again with the top line added in?
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s binw.net -j ACCEPT
sudo iptables-save

---

### Post by bodhi.zazen on 2011-08-19
You seem to be learning iptables just fine =)

Yes, that is how the internet works, lots of interconnectivity and hyper links.

If you wish to allow only a few web sites, you should be fine with this approach, but, as you can see, if you start adding too many sites it is unwieldy.

So if your whitelist starts getting too long, at that point you would use a proxy server such as squid or privoxy, although you will need to do similar configuration on squid (whitelist sites).

---

### Post by callmebadger on 2011-08-19
thank you for all the help so far

would adding google.com to the white list
cover googleadservices.com
google-analytics.com
google-analytics.com
googleapis.com

guessing they are from same ip address?

off to bed thats enough for today, maybe try pinging them addresses tomorrow to see if they are from same or not.

---

### Post by bodhi.zazen on 2011-08-19
As you can see, iptables converts to ip address, so as long as the domain name (googleadservices.com) all point to the same ip you are good to go.

If you want to allow google, but not googleadservices.com, and they share the same ip, then again you need a proxy.

Personally on a home LAN I use privoxy as squid is a big gun, but you would again need to learn the syntax of privoxy or squid to configure those proxies.

---

### Post by callmebadger on 2011-08-20
help

whats happened switched off and now seem to be back at square one, everything that i managed to block yesterday is allowed again?

thought i was doing so well.

any ideas? :confused:

---

### Post by bodhi.zazen on 2011-08-20
Did you save your settings ? 

See: [http://bodhizazen.net/Tutorials/iptables#Saving_your_configuration](http://bodhizazen.net/Tutorials/iptables#Saving_your_configuration)

---

### Post by callmebadger on 2011-08-20
Thank You Bondi.zarzen

I tried this
sudo iptables -N whitelist
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ubuntuforums.org -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s linuxforums.org -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s moshimonsters.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s binweevils.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s fronter.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ad2.netshelter.net -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s kona40.kontera.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s static.crowdscience.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s lb.binweevils.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s seg.sharethis.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s yui.yahooapis.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s c.mmcdn.net -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s google.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s x1.binweevils.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s partner.googleadservices.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s cdn.binw.net -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s google-analytics.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ajax.googleapis.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s rts.sparkstudios.com -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s adv.netshelter.net -j ACCEPT
sudo iptables -A whitelist -p tcp -m multiport --sports 80,443 -s b.scorecardresearch.com -j ACCEPT
sudo iptables -I INPUT 1 -j whitelist
sudo iptables -I INPUT 2 -p tcp -m multiport --sports 80,443 -j DROP
sudo iptables-save
sudo iptables-save > /etc/iptables.rules

and then got this 
bash: /etc/iptables.rules: Permission denied

can you help please
Thank you Badger

---

### Post by bodhi.zazen on 2011-08-20
You can not redirect output with sudo like that.

sudo bash -c "iptables-save > /etc/iptables.rules"

or become root, sudo -i , and run all those commands, saves on the typing "sudo" over and over.

---

### Post by callmebadger on 2011-08-20
Thanks again
i see it created the file now in /etc/iptables.rules

so i could of just done this instead.

sudo -i
iptables -N whitelist
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ubuntuforums.org -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s linuxforums.org -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s moshimonsters.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s binweevils.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s fronter.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ad2.netshelter.net -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s kona40.kontera.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s static.crowdscience.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s lb.binweevils.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s seg.sharethis.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s yui.yahooapis.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s c.mmcdn.net -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s google.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s x1.binweevils.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s partner.googleadservices.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s cdn.binw.net -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s google-analytics.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s ajax.googleapis.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s rts.sparkstudios.com -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s adv.netshelter.net -j ACCEPT
iptables -A whitelist -p tcp -m multiport --sports 80,443 -s b.scorecardresearch.com -j ACCEPT
iptables -I INPUT 1 -j whitelist
iptables -I INPUT 2 -p tcp -m multiport --sports 80,443 -j DROP
iptables-save
iptables-save > /etc/iptables.rules


cheers
thanks again for all the help. hope this learning curve for me helps others in the future :P

---

### Post by bodhi.zazen on 2011-08-20
> **callmebadger said:**
> Thanks again
i see it created the file now in /etc/iptables.rules

so i could of just done this instead.

Yes, and in that case, the last line would be just:

```
iptables-save > /etc/iptables.rules
```

The only reason you needed sudo -c bash was because sudo does not allow your to re-direct output through redirects ( > ) or pipes ( | ) directly.

So yes, when doing a bunch of commands, I usually just sudo -i ;)

---

### Post by callmebadger on 2011-08-20
thanks 2 more questions lol

question 1
is
.google.com           different to     google.com 
relating to iptables
seems im having trouble with moshimonsters

or is it possible that it uses different port? not sure really if i am on the right track.

question 2

stuck on editing rc.local to add the line suggested iptables-restore < /etc/iptables.rules keep getting permission denied
am i right in trying to use gobby, and if so how do i sudo my account in order to edit and save it?

thanks

---

### Post by robsoles on 2011-08-20
What's gobby?

I too have a seven year old (has own PC though) and I've employed a few different strategies but I have a tendency of attacking the problem at the DNS level rather than mucking about with firewalls.

I'm going to mention this twice: checkout [www.opendns.com]("http://www.opendns.com"), they have your child-minding needs stitched up in my humble opinion - I tested them and they [s]are[/s] were beaut; I don't personally use them because I can deploy my own DNS server in a virtual machine on my network at home **BUT** that's not for everybody and if I didn't have prior experience I would have just used them guys.


Here's an answer to your DNS question, I hope you note the bias where I am trying to discourage you from maintaining some list of IP addresses that may change over time;

*.google.com is effectively different from google.com

Not only is the basic DNS setup capable of;
google.com = x.x.x.1
[www.google.com]("http://www.google.com") = x.x.x.2
search.google.com = x.x.x.3
... so on and so on, as many sub-domains as they care to have (with limits, however massive)

But the DNS system has been capable of 'round-robin' address response for years;
search.google.com = x.x.x.1, x.x.x.2, x.x.x.3, x.x.x.4, x.x.x.5 etc etc

And there are other things like address (IP) and location (physical) biases that can be applied.

If you are using your ISP's DNS then you may be subject to their white/black list or whatever other 'extra services' they may (charmingly) provide.

Speaking specifically of Google; That organisation has the capability of completely changing their IP address ranges for services fairly dynamically - they don't "all the time, just randomly" but they can, when reasons crop up they do.


Seriously, the level of control offered by [www.opendns.com]("http://www.opendns.com") is extraordinary, it doesn't take rocket science (certainly not by comparison to mucking about with iptables for the exercise) to implement and I am sure they have retained a reasonable level of 'free' service (do correct me if I am wrong.).

---

### Post by callmebadger on 2011-08-22
anyone?

stuck on editing rc.local to add the line suggested iptables-restore < /etc/iptables.rules keep getting permission denied
am i right in trying to use gobby, and if so how do i sudo my account in order to edit and save it?

---

### Post by androssofer on 2011-08-22
> **callmebadger said:**
> anyone?

stuck on editing rc.local to add the line suggested iptables-restore < /etc/iptables.rules keep getting permission denied
am i right in trying to use gobby, and if so how do i sudo my account in order to edit and save it?

a simple thing like:

```
sudo gedit rc.local
```

shud do the trick! :-).


**side note: was just wanting to learn how to do stuff like this! this thread is awesome! haha, so helpful!

---

### Post by callmebadger on 2011-08-22
> **androssofer said:**
> a simple thing like:

```
sudo gedit rc.local
```shud do the trick! :-).


**side note: was just wanting to learn how to do stuff like this! this thread is awesome! haha, so helpful!

thanks was just a case of opening original file copy everything in it then do sudo gedit rc.local
pasting into new opened file then save in same folder to replace.

cheers if there is a quicker way let me know so i can just edit original doc  

done androssofer way this time

:)

---

### Post by callmebadger on 2011-08-24
OK so I have created iptable whitelist with everything that was trying to load while opening
ubuntuforums.org  :KS
linuxforums.org   :)
binweevils.com         :P
moshimonsters.com :confused:

# Generated by iptables-save v1.4.4 on Wed Aug 24 08:58:59 2011
*filter
:INPUT ACCEPT [265:37693]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [873:121068]
:whitelist - [0:0]
-A INPUT -j whitelist 
-A INPUT -p tcp -m multiport --sports 80,443 -j DROP 
-A whitelist -s 91.189.94.12/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 174.132.123.98/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 98.129.229.140/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 158.36.191.10/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 46.137.78.255/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 74.121.176.40/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.33/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.19/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.106.153/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.185.69/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.214/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.231/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.72.218.16/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.196/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.162/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.167/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.185.83/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 77.238.187.43/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 77.238.187.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.188.128.44/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.188.128.18/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 173.203.57.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 74.125.230.124/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.184.220.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.103/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.106/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.105/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.143.95/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 64.27.17.200/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 50.19.211.87/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.40/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.49/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.103/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.106/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.105/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.94.148.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.80.124.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.80.126.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
COMMIT
# Completed on Wed Aug 24 08:58:59 2011

the problem is I cant get moshimonsters to load up, keep getting
The connection has timed out 
The server at [www.moshimonsters.com](www.moshimonsters.com) is taking too long to respond.

     *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

can anyone help with how to allow all of what is trying to load on moshimonsters, i've tried whois and added the servers to the whitelist but still no joy.

is there a way to show all that is trying to run in the browser and what websites the browser is trying access in order to load moshim. other than looking at the bottom left as it happens.

thanks

---

### Post by callmebadger on 2011-08-24
> **callmebadger said:**
> OK so I have created iptable whitelist with everything that was trying to load while opening
ubuntuforums.org  :KS
linuxforums.org   :)
binweevils.com         :P
moshimonsters.com :confused:

# Generated by iptables-save v1.4.4 on Wed Aug 24 08:58:59 2011
*filter
:INPUT ACCEPT [265:37693]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [873:121068]
:whitelist - [0:0]
-A INPUT -j whitelist 
-A INPUT -p tcp -m multiport --sports 80,443 -j DROP 
-A whitelist -s 91.189.94.12/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 174.132.123.98/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 98.129.229.140/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 158.36.191.10/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 46.137.78.255/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 74.121.176.40/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.33/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.19/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.106.153/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.185.69/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.214/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.231/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.72.218.16/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.196/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.162/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.184.167/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 184.73.185.83/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 77.238.187.43/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 77.238.187.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.188.128.44/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.188.128.18/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 173.203.57.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 74.125.230.124/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 93.184.220.39/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.103/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.106/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.105/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.143.95/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 64.27.17.200/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 50.19.211.87/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.40/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 62.24.179.49/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.103/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.106/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.146.105/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.104/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.147/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 209.85.229.99/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.94.148.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.80.124.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 208.80.126.13/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
-A whitelist -s 213.229.92.110/32 -p tcp -m multiport --sports 80,443 -j ACCEPT 
COMMIT
# Completed on Wed Aug 24 08:58:59 2011

the problem is I cant get moshimonsters to load up, keep getting
The connection has timed out 
The server at [www.moshimonsters.com]("http://www.moshimonsters.com") is taking too long to respond.

     *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

can anyone help with how to allow all of what is trying to load on moshimonsters, i've tried whois and added the servers to the whitelist but still no joy.

is there a way to show all that is trying to run in the browser and what websites the browser is trying access in order to load moshim. other than looking at the bottom left as it happens.

thanks

think i might of found something of use but still would like to here from others that have got round this sort of problem before tools.pingdom.com

---

### Post by bodhi.zazen on 2011-08-24
> **callmebadger said:**
> can anyone help with how to allow all of what is trying to load on moshimonsters, i've tried whois and added the servers to the whitelist but still no joy.

is there a way to show all that is trying to run in the browser and what websites the browser is trying access in order to load moshim. other than looking at the bottom left as it happens.

thanks

Use a packet sniffer such as tcpdump or wireshark.

---

### Post by callmebadger on 2011-08-24
> **bodhi.zazen said:**
> Use a packet sniffer such as tcpdump or wireshark. 
thanks bodhi.zazen will give them a try, actually need to learn them next term, will be good practice.

---

### Post by b2zeldafreak on 2011-08-24
> **donkyhotay said:**
> dansguardian is what I usually see suggested around here. I'm assuming this is to limit kids' access (which is why most people want filters). I have a brother who attempted to set up a network filter for his kids. He did the same thing you did, posted to a forum, got a link to a howto online somewhere and followed the steps. It took only a day or two for my nephews to figure out how to bypass it. I've seen it many times and generally don't recommend in relying upon an installed program to limit access, especially if your knowledge of computers is limited. Security is only as good as the person who set it up so if you don't know much then it won't take much to get past whatever you can do. Also even if you are a master computer networking guru, there is nothing you can install on a computer that a determined kid won't be able to bypass so long as he is physically sitting at the computer. One of the first rules of computer security is that physical access *is* root access. Real security requires proxies between the computer and the internet that are under lock and key, not on the computer you're trying to filter. Proxies like that aren't very practical for the average user as it's unlikely to have your own personal server. In addition to simply uninstalling/removing the filtering software on the computer you're trying to protect, creating a liveCD will bypass the filter temporarily and completely prevent you from even knowing something is wrong afterwards since it doesn't save any changes. Even if they're young and you figure "aww, they're not old enough to know how to do that kind of stuff", all it takes is one google search for "how can I bypass an internet filter" on a friends' or local library computer to come up with the answer. Assume you're kids are smarter then you, no offense but most kids usually are smarter then their parents when it comes to computers. My recommendation for people wanting to limit computer is access is to not mess with software filters, they'll do nothing but give you a false sense of security. The best security is to simply keep the computer in a public location (like the family room), and just keep an eye on what your kids are doing.

In addition to this, your router might have the filtering options that you're looking for. You would have to look up your specific model, but typically you type 192.168.0.1 or 192.168.1.1 (this varies based on router) into your web browser, and you can have a go there.

---

### Post by donkyhotay on 2011-08-27
> **b2zeldafreak said:**
> In addition to this, your router might have the filtering options that you're looking for. You would have to look up your specific model, but typically you type 192.168.0.1 or 192.168.1.1 (this varies based on router) into your web browser, and you can have a go there.

True, but again you have to physically lock up the router. If you don't and just put on a password it only takes one paperclip to reset the device and remove the filter.

---

