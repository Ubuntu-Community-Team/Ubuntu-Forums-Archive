---
title: "avahi daemon problem"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by shaker108 on 2008-08-19
Hi,

I recently switched from Fedora to Ubuntu (yesterday :p) and I have a SMB share that I connect to using a Mac running OS X 10.5. On fedora I used avahi and this service file in /etc/avahi/services to automatically get the shared server in Finder.

> <?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>
    <name replace-wildcards="yes">%h filer</name>
    <service>
        <type>_smb._tcp</type>
        <port>139</port>
    </service>
</service-group>

But there seems to be a problem with Ubuntu. It wont show up in the Finder when I boot the Ubuntu pc but it pops up as soon as I restart the avahi daemon. There are no errors in the daemon log and it says that the service has been loaded so I dont know what the problem might be :confused:

---

### Post by nbcmayhem on 2009-03-06
is it this bug - [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/116984](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/116984) ?

---

