---
title: "avahi services in leopard finder"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by mcewen98 on 2007-11-12
I just installed leopard on my macbook and am trying to figure out some services published using avahi on my Ubuntu machine are not appearing in the finder.  What is more troublesome is the finder used to show an item for screen sharing but that has since disappeared.

I've tried adding the xml files for afp, rfb, and smb.   In the Leopard finder sidebar the hostname of the Ubuntu machine appears under the shared section.  When I click it, it connects and only shows the samba share.  If I run the avahi-discover utility all the services appear.  

If I remove the afpd.service, smb.service and rfb.service files from /etc/avahi/services and restart both machines, only the samba share still appears in the finder.  In /etc/nsswitch.conf I have: hosts: files dns mdns4

All other configuration files are how they were by default.

From what I understand services can publish themselves directly without needing to use the static definitions in /etc/avahi/services/*.service?  I assume this must be what's happening with samba.

Any thoughts of where to look or what could be going on?  I can connect to all services directly by using vnc://192.168.1.2, smb://192.168.1.2, and afp://192.168.1.2

Thanks!

---

### Post by mcewen98 on 2007-11-13
It turns out I have everything set up correctly.  I upgraded the firmware on my router, restarted it, and suddenly everything is working as it should.

---

### Post by puccaso on 2007-11-17
can you send us your smb and vnc xml files?
id like to try this too

---

### Post by mcewen98 on 2007-11-17
Bonjour service types in OS X:
[http://developer.apple.com/qa/qa2001/qa1312.html](http://developer.apple.com/qa/qa2001/qa1312.html)

Avahi services doc:
[http://avahi.org/download/avahi.service.5.xml](http://avahi.org/download/avahi.service.5.xml)

vnc is advertised using the remote frame buffer service, rfb.  All files are in /etc/avahi/services.
rfb.service:
```

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name>Server Desktop</name>
  <service>
    <type>_rfb._tcp</type>
    <port>5900</port>
  </service>
</service-group>

```
samba.service:
```

<?xml version="1.0" standalone='no'?>
<service-group>
  <name>Server SMB</name>
  <service>
    <type>_smb._tcp</type>
    <port>139</port>
  </service>
</service-group>

```

Most of the time the static services show up correctly in Leopard.  I think the Finder is still buggy though.  Once in a while an addition samba service that Leopard automatically discovers shows up, and so does the remote desktop service, in addition to my statically specified afp, rfb and samba services.

---

### Post by HS-L on 2007-11-24
Hmm,.. would be great to do the same with my server that's outside my LAN (like back to my mac)
does anyone know how wide area bonjour works on ubuntu? I've got pdns as dns server running on my 6.06LTS server.

---

### Post by puccaso on 2007-11-24
i added these things to my ubuntu installation
and now
when i goto applications > internet > i can see avahi vnc broswer and avahi ssh server browser..

why arent all these avahi services installed already on ubuntu?/////

---

