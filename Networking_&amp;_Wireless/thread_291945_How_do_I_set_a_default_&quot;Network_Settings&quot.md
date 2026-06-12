---
title: "How do I set a default &quot;Network Settings&quot; location?"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by MadKAT on 2006-11-03
Hello:

I am running Ubuntu 6.10, and I have set up  a couple of locations in System->Administration->Network Settings.  My question is how do I set one of  these locations as the default when I boot?

The problem is everytime I boot,  the current location is always set to  a blank location. This location does not have (and does not save) the proper DNS settings. I would always have to run "Network Settings" and select the proper location to get the proper DNS settings and click Apply.  This is only during first boot, if I just log-out  and log-in again, the selected location is still in effect.

Any ideas?

Thanks!

---

### Post by MadKAT on 2006-11-04
hello? anybody there? :(

---

### Post by dsiddens on 2006-11-16
I have a similar problem:  how to create a location.  If I type in a name for a new location then "OK", it goes into an endless process.  Then I have to alt-f4 to stop it...

---

### Post by Teppicymon on 2008-03-16
Has anyone worked this out yet?

I have a weird setup where my windows PC shares it's internet connection through a 3G modem and my ubuntu server connects through that.

This works fine, but I need to manually specify the DNS servers on Ubuntu, which I did using the Network Settings control panel, but it will only save that info into a custom location, which it will never load as default! Very frustrating as I have to go in there every boot-up and select my 'Home' location.

---

### Post by Soole on 2008-06-14
> **Teppicymon said:**
> Has anyone worked this out yet?

I have a weird setup where my windows PC shares it's internet connection through a 3G modem and my ubuntu server connects through that.

This works fine, but I need to manually specify the DNS servers on Ubuntu, which I did using the Network Settings control panel, but it will only save that info into a custom location, which it will never load as default! Very frustrating as I have to go in there every boot-up and select my 'Home' location.

Ok I've finally figured out a way.
You have  to edit dhclient.conf located in /etc/dhcp3/ :
```
sudo gedit /etc/dhcp3/dhclient.conf
```
Then just  replace the line 
```
#prepend domain-name-servers 127.0.0.1;
```
by
```
prepend domain-name-servers 193.70.192.25,193.70.152.25;
```
where  193.70.192.25 and 193.70.152.25 are you first and second dns server.

(Pay attention that you have to delete the # sign at the beginning of the line in order to un comment it)

Save & quit

Reboot, this should work !

---

### Post by darkazurka on 2008-07-07
Thanks. I've changed my dns settings according to my dns providers.

---

