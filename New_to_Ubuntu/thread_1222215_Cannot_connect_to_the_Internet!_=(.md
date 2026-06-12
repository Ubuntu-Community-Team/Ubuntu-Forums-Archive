---
title: "Cannot connect to the Internet! =("
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Tiwaz44 on 2009-07-24
Hello, 

I have recently installed "Ubuntu 7.1 Desktop x64" (the title of an old burned disk I had lying around) because Windows had all sorts of problems, etc. etc.

Everything seems to be running smoothly, I ran the updater and now it appears to be version Ubuntu 8.04 - the Hardy Heron - released in April 2008.

The Problem:  The internet does not work.  Upon startup it appears to connect (does the little blue comet between the green dots, and then shows two computer screens), but there is no response from Google when I open up the Firefox browser.  

I am currently posting this from my laptop which also has Ubuntu, though not a 64 bit version (the internet works fine for this computer).  I don't understand much about internet connections in the first place, so any help will be appreciated!!!

Thanks for reading,
Tiwaz

---

### Post by cgb on 2009-07-24
Could possibly be a driver problem.  Have you checked if you are actually obtaining a IP address when connecting?  You can verify this by typing "ifconfig" in terminal and you should see a inet addr which will probably be something like "192.168.1.*" if it is valid.  If you have a valid IP address another good troubleshooting step would be to see if you can ping your other computer to see if that works or if all local connections are broken as well.

---

### Post by LookTJ on 2009-07-24
How do you connect? e.g. ethernet, Wi-Fi etc.

---

### Post by Tiwaz44 on 2009-07-24
Thanks for the replies!

I will try the "ifconfig" to see if that works and get back in a few minutes.

I connect using an ethernet cable through a wired router on a local network. (desktop machine)

Will write again soon,
Tiwaz


Okay, I'm not getting anything that I can understand from the ifconfig, but I will try to describe it here so that perhaps you may understand what is going on.

The output is four headings: eth0, eth1, eth0:avahi, and lo

Under eth0:avahi there is something that looks like an IP address which reads: "inet addr:169.254.7.122 Bcast:169.254.255.255 Mask:255.255.0.0" 

Under lo there is also something that looks like an IP address which reads: "inet addr:127.0.0.1 Mask:255.0.0.0"

Does this mean anything that will be of use to me?

Thanks!!!

---

### Post by LookTJ on 2009-07-24
you could try 
```
sudo dhclient eth0
```
to attempt to get a lease from the dhcp server(router)

---

### Post by Tiwaz44 on 2009-07-24
Okay, I will try that and get back to you.

Thanks!

Okay it seems not to be working, it goes through some sending and listening and then says "No DHCPOFFERS received." and "No working leases in persistent database - sleeping."

---

### Post by cgb on 2009-07-24
It appears you are unable to obtain a IP address from DHCP.  You could try and set a static IP address and see if that makes a difference under System/Preferences/Network Connections.  Then select eth0 and edit, you will need to know a valid IP address to give this as well as your subnet mask and gateway.  If you need help with determining this let me know.  If you know the address of your Router this would be a good start and depending if there is any other computers on the network you can probably use this address, *.*.*.20 (replacing the *'s with the first three sets from your Router address.  I'm assuming you have a subnet mask of 255.255.255.0 and the gateway will be your Routers address.

---

### Post by Tiwaz44 on 2009-07-24
I think I understand where you are going with this, but how would I go about finding out the IP address for the router? 

Also, I do not have System/Preferences/Network Connections but I do have System/Administration/Network Tools which has IP information listed in it.  Will that work?

Thanks!!
Tiwaz

---

### Post by credobyte on 2009-07-24
Ubuntu 7.10 EOL : [http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)
I'm pretty sure that if you would upgrade it to 8.04 LTS or 9.04, you would have less problems ( if any ) ;)

---

### Post by LookTJ on 2009-07-24
> **Tiwaz44 said:**
> I think I understand where you are going with this, but how would I go about finding out the IP address for the router? 
On a Linux machine that works with the internet, you can look into:
```
sudo route
```

Or on Windows look at adapter details and look for gateway or something.

:)

---

### Post by LookTJ on 2009-07-24
> **credobyte said:**
> Ubuntu 7.10 EOL : [http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)
I'm pretty sure that if you would upgrade it to 8.04 LTS or 9.04, you would have less problems ( if any ) ;)
It has been pointed out in the OP that the poster upgraded to 8.04 and is now having issues.

Have a wonderful day! :)

---

### Post by cgb on 2009-07-24
Like LookTJ said sudo route should provide you the address of your router/gateway if you have a working Linux machine or in windows you can go to the command prompt and type ipconfig which should give you a gateway/subnet address for your network.

---

### Post by Tiwaz44 on 2009-07-24
Thanks LookTJ, 

I tried the "sudo route" from this computer that has internet and it came up with this:

```
tiwaz@tiwaz-laptop:~$ sudo route
[sudo] password for tiwaz: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
tiwaz@tiwaz-laptop:~$ 

```

Credobyte, 

I don't have a recent CD that I am able to install from.  I can try to download the current version 9.04 if you think that will help, but I did upgrade to 8.04 ... regardless we should be able to figure it out, right?!  Thanks for suggesting this though.  I do think it would have been smart to install the latest version from the beginning if I had the means to do so...

---

### Post by LookTJ on 2009-07-24
From the looks, your router's ip is 192.168.0.1


It would be better to reinstall with 9.04 then to go through the headaches;).  If you want to go this route, make sure to backup any important data to an external drive or flash drive if you don't have much to backup.

---

### Post by credobyte on 2009-07-24
> **LookTJ said:**
> It has been pointed out in the OP that the poster upgraded to 8.04 and is now having issues.

Have a wonderful day! :)

Sorry, didn't saw it :-s

---

### Post by Tom Chaudoir on 2009-07-24
Maybe a dumb question but: Did you try resetting the router? Unplug it for a minute.

Tom

---

### Post by cgb on 2009-07-24
Yes, your gateway address would be 192.168.0.1 and subnet mask 255.255.255.0.  If you wanted to setup a static address you can use these numbers for your gateway and subnet mask and set your static IP address to 192.168.0.20, although you should ping this address prior from the working pc, with below code, to make sure it does not get a response and verify it is not in use.  Not sure why you are not showing the network connections manager but I'm sure there is a terminal command as well for changing to a static IP but I am not familiar with this.  

Also you may want to just double check to make sure you dont have a bad cable and all this trouble is over that...  I've seen bad cables cause issues such as this.

```
ping 192.168.0.20
```

---

### Post by LookTJ on 2009-07-24
```
sudo ifconfig eth0 <ip address> netmask <netmask> up
```

```
sudo route add default gw <ip address of the gateway>
```

so in cgb's case,

```
ifconfig eth0 192.168.0.20 netmask 255.255.255.0 up
```

```
route add default gw 192.168.0.1
```

:) Hope that helps!

---

### Post by Tiwaz44 on 2009-07-24
I have tried putting those three settings into both my wired connections to no avail....  perhaps it's worth waiting on a long download for the 9.04 version?  It just seems like it should be a fairly simple thing to fix... but perhaps not!

I have also tried setting the connection to DHCP as well as Local Zeroconf network, neither of which provided an internet connection.

Also, I am downloading the newest 64 bit version of Linux (9.04 version) but it keeps failing.  My computer has an Intel core 2 duo processor, which I believe is 64 bit, and the file that I am downloading says AMD in the filename.  Is this going to be a problem?

Thanks for all the help that you guys have been giving me, I reeeeeeeeeeeeeeeally appreciate it!!!
Tiwaz


Also, I have tried what you suggested, LookTJ, with the information from cgb, but that has not worked either.  There is no output in the terminal from either one of those commands... is that okay?

---

### Post by cgb on 2009-07-24
this has definitely became harder then it should be for you.  One other thing I forgot to mention is if you are setting everything to a static IP you also need to set the DNS.  The DNS can be set to the gateway's address which is 192.168.0.1.  Without the DNS address you will not be able to resolve DNS lookup's and basically not be able to see any websites.  

Did you ever try swapping out the network cable to ensure it is working?

---

### Post by LookTJ on 2009-07-24
> **cgb said:**
> this has definitely became harder then it should be for you.  One other thing I forgot to mention is if you are setting everything to a static IP you also need to set the DNS.  The DNS can be set to the gateway's address which is 192.168.0.1.  Without the DNS address you will not be able to resolve DNS lookup's and basically not be able to see any websites.  

Did you ever try swapping out the network cable to ensure it is working?
With more details, you need to open:

```
sudo gedit /etc/resolv.conf
```

and add:
```
nameserver 192.168.0.1
```

:)

---

### Post by Tiwaz44 on 2009-07-25
Okay, so I downloaded the newest version and I get the same problem with the internet being unresponsive.  I loaded up my live CD of puppy linux and it connected to the internet immediately and everything was fine and dandy.  I will try that last suggestion of yours to see if it works.

Thanks!
Tiwaz

---

### Post by LookTJ on 2009-07-25
You could also try this [suggestion]("http://ubuntuforums.org/showpost.php?p=7276275&postcount=8") to get a dhcp connection. 

:)

---

### Post by Tiwaz44 on 2009-07-25
That didn't work, I don't seem to have a dhclient.conf located in etc... it is blank!

---

### Post by LookTJ on 2009-07-25
> **Tiwaz44 said:**
> That didn't work, I don't seem to have a dhclient.conf located in etc... it is blank!
Hmm interesting, it should be there :S

EDIT:

My friend who has Ubuntu says it doesn't exists.


But I don't know if you have /etc/dhcpcd.conf because that what I have on my system.

:)

---

