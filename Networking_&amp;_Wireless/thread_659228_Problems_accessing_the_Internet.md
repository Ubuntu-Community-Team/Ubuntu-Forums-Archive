---
title: "Problems accessing the Internet"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by LabRatAndy on 2008-01-05
I have recently installed Gusty but am having difficulty getting access to the INTERNET firefox and even the update manager do not seam to be able to access the web. However using network tools I am able to successfully ping bbc.co.uk and google.co.uk.
I have enabled wired networks and set it to use DHCP to be configured but it seams that the programs do not realise that the Internet is there and I am stumped now. it used to work under the feisty version

many thanks in advance
Andy

---

### Post by Dark Hornet on 2008-01-05
do me a favor...trace to google, or any website, and get the IP address.  Try putting the IP address in your URL bar in Firefox..this will determine if you have a DNS issue.

---

### Post by LabRatAndy on 2008-01-05
Thanks for your reply Dark Hornet,

Have done what you asked, using network tools I did a traceroute to [www.google.co.uk](www.google.co.uk), but that didn't give me their IP so used the lookup feature and got the IP 64.233.183.147. Typing that in to firefox did give me the google website, also tried typing in [www.google.co.uk](www.google.co.uk) and that didn't work.:(
 So sounds like it's a DNS problem then, could you give me some advice on how to get the DNS to be set correctly, shouldn't the DHCP in my router set this for me?:confused:

Thanks again
Andy

---

### Post by sdide on 2008-01-05
yes, it probably should.

you can see what it uses as resolver in /etc/resolv.conf.
in that file should be a list of nameservers.

if there are no nameserver entries, you can try a openDNS server.
add the line:
nameserver  208.67.222.222

if there are no entries, try showing us the output of 
$ cat /etc/dhcp3/dhclient.conf | grep -v ^# 

So we can see if the DHCP client actually requests nameservers.

---

### Post by Dark Hornet on 2008-01-05
sdide is correct...usually your ISP will provide the DNS, but in-case they don't, or if there is an issue you can use different DNS servers such as [https://www.dyndns.com/](https://www.dyndns.com/), etc.

***EDIT***  You might want to try resetting your router...I had this issue a while back, and for some reason my router did not pick up the DNS servers that my ISP provided...but once I reset it, it picked them up just fine....Just a thought.

---

### Post by LabRatAndy on 2008-01-05
Thanks Sdide,

/etc/resolv.conf only contains 1 line that is nameserver 192.168.1.1 thats my routers IP.

and heres the results of 
cat /etc/dhcp3/dhclient.conf | grep -v ^#

send host-name "<hostname>";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
timeout 30;

Does that look right?

Will try reseting the router as Dark Hornet suggested  if that doesn't work I will use the name server that sdide suggested or just had an other thought I could look at the DNS my router uses and add them to the /etc/resolv.conf would that work?

Thanks 
Andy

---

### Post by sdide on 2008-01-05
your dhclient.conf looks just fine.
And you DO get a nameserver. Your router wants to act as a forwarder, however it seems soemthing is not working though. 
You might want to take a look at the router DNS/DHCP setup, or you could type in the DNS servers manually,and make sure dhclient does update your /etc/resolv.conf.

---

### Post by LabRatAndy on 2008-01-06
Thanks Sdide,
I think that manually setting the DNS may be easier to do, as I'm not really sure what the settings in the router do and I don't what it to stop working for windows. I take it all I do is add the DNS servers IPs to the /etc/resolv.conf but how do I stop dhclient over writing  the /etc/resolv.conf.
I also notice that if I use the network tools' ping it seams to work when I try to ping google.co.uk. Don't know if that will help someone work out whats wrong.

---

### Post by sdide on 2008-01-07
To make dhclient not replace your /etc/resolv.conf
you could have it not request the nameservers.

so instead of the request statement you posted above, you could in 
/etc/dhcp3/dhclient.conf change the request to:

request subnet-mask, broadcast-address, time-offset, routers,
domain-name, host-name;

---

### Post by LabRatAndy on 2008-01-07
Thanks Sdide,
Looks like its working now :-D

---

