---
title: "Scanner not connecting to Simple Scan - missing saned file ..."
date: 2019-08-25
forum: Networking &amp; Wireless
---

### Post by sunrise718 on 2019-08-25
I want to enter my IP # into the saned file according to the following instructions located at [http://xmodulo.com/configure-network-printer-scanner-ubuntu-desktop.html](http://xmodulo.com/configure-network-printer-scanner-ubuntu-desktop.html).  

However, my saned file is missing and needs to be installed.   According to the instructions, it should ship by default with Ubuntu but perhaps this is old and is no longer the case.  Or the directory is different.  

Can someone help me create or install the saned file that I need to follow the steps below?  

[COLOR=#1B1B1B][FONT=-apple-system-font]2) Now we need to enable saned daemon which comes pre-installed on Ubuntu desktop. To enable it, we need to edit the /etc/default/saned file, and set the RUN variable to yes:[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]$ sudo vim /etc/default/saned[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]3) Let's edit the /etc/sane.d/net.conf file, and add the IP address of the server where the scanner is installed:[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font][[IMG]https://farm6.staticflickr.com/5581/14777977880_c865b0df95_z.jpg[/IMG]]("https://www.flickr.com/photos/xmodulo/14777977880/")[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]4) Restart saned:[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]$ sudo service saned restart[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]5) Let's see if the scanner is available now:[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font][[IMG]https://farm4.staticflickr.com/3839/14964651605_241482f856_z.jpg[/IMG]]("https://www.flickr.com/photos/xmodulo/14964651605/")[/FONT][/COLOR]
[COLOR=#1B1B1B][FONT=-apple-system-font]Now we can open "Simple Scan" (or other scanning utility) and start scanning documents. We can rotate, crop, and save the resulting image:[/FONT][/COLOR]

---

### Post by him610 on 2019-08-27
sunrise718, congratulations for attempting to address your issue; however, your source document in the referenced link is outdated (Last updated on August 19, 2014).
I have never configured a scanner using that method, and I don't know if it will work now or not. I have **never ever** had to edit */etc/sane.d/net.conf* in order to configure a scanner or printer. 

You need to restore whatever files you changed back to  the original versions. You did make a copy, right?
I doubt you are missing your saned file. From a terminal, run *locate saned*

From you original post, it indicates you are trying to connect your scanner through a network connection. Is that true?
Are you using a router? What is its local IP address?  
What IP address did you assign the scanner? It is a good idea for permanently connected devices to have a static IP address so each one can be consistently addressed on the network.

My saned file:
```

 cat  /etc/default/saned
# Defaults for the saned initscript, from sane-utils

# To enable under systemd please read README.Debian
# Set to yes to start saned under SysV
RUN=no

# Set to the user saned should run as
RUN_AS_USER=saned

```
My saned.conf file:
```

cat /etc/sane.d/saned.conf

# saned.conf
# Configuration for the saned daemon

## Daemon options
# Port range for the data connection. Choose a range inside [1024 - 65535].
# Avoid specifying too large a range, for performance reasons.
#
# ONLY use this if your saned server is sitting behind a firewall. If your
# firewall is a Linux machine, we strongly recommend using the
# Netfilter nf_conntrack_sane connection tracking module instead.
#
# data_portrange = 10000 - 10100


## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
#192.168.0.1
#192.168.0.1/29
#[2001:db8:185e::42:12]
#[2001:db8:185e::42:12]/64

# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and
# /etc/services must also be properly configured to start
# the saned daemon as documented in saned(8), services(4)
# and inetd.conf(4) (or xinetd.conf(5)).

```
My net.conf file,
```

 cat /etc/sane.d/net.conf
# This is the net backend config file.

## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60

## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost

```
Do you have the Epson scanner driver installed? 
The Epson support site does not find any model CX4000. Are you certain that is the correct model number?

---

### Post by sunrise718 on 2019-08-27
Thank you for your response!  I checked and, sure enough, I do have saned.  Everything matched what you posted.  Your scripts were very helpful.

I did not change any files.  

I have a Brother MFC printer/scanner/fax machine.  The printer works great.  The scanner is another story

For some reason, when I test a scan, I get "Failed to scan. Unable to connect to scanner"

Yet, my device is registered.  

I have been trying to troubleshoot saned and have not resolved it yet.

```
SANE_DEBUG_DLL=5 scanimage -L 
```

Shows 3 scan devices when it should only show 1.  So, I need to delete the 2 incorrect devices.

And get the scanner to pick up on the correct one which is:

```
device 'brother4:net4:net1;dev0' is a Brother BRWD44B5EFE4D96 MFC-7860DW
```

Help?

---

### Post by him610 on 2019-09-02
sunrise718,
How about running  *dpkg -l brsca** from a terminal and displaying the results between the code tags.
This is what mine looks like:
```
dpkg -l brsca*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-===============================================
un  brscan                <none>          <none>          (no description available)
ii  brscan-skey           0.2.4-1         amd64           Brother Linux scanner S-KEY tool
ii  brscan4               0.4.6-1         amd64           Brother Scanner Driver

```
Yours should look similar.

---

### Post by sunrise718 on 2019-09-04
Thank you!  My result matched yours exactly.

Is this from the cups installation or something else?

---

### Post by sunrise718 on 2019-09-04
I solved the network scan connection by enabling 'network scan' in the web panel network configuration settings.  

It had been disabled at one point but needs to be on for the scanner to work.

---

### Post by him610 on 2019-09-05
Congratulations on resolving your issue.
> Is this from the cups installation or something else?
No, my several installations were completed without issue using the Brother provided *Driver Install Tool*

---

