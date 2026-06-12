---
title: "Firestarter"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-06
Hi again, (it feels like I spend half my time on here)

I am trying to download firestarter... but it gives me the following error

Failed to fetch [http://im.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-7ubuntu5_i386.deb](http://im.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-7ubuntu5_i386.deb) Could not connect to 192.168.2.3:8080 (192.168.2.3). - connect (111: Connection refused)

It was recommended that I download firestarter in order to configure ports, but how can I open up this port in order to download stuff

Thanks again in advance

Alan

---

### Post by spiky001 on 2010-04-06
hi dont bother with firestarter is not surported any more if you need a fire wall with gui get gufw it' in synaptic. is there a reason you need a firewall?

---

### Post by fly_boy on 2010-04-06
Because I am trying to download the NFS stuff by using the following command

sudo apt-get install nfs-kernel-server portmap nfs-common

It gave me the same error, so I tried to download the firewall in order to allow the stuff through...

Alan

---

### Post by spiky001 on 2010-04-06
dont think the firewall will allow you to download any easier if you can download other stuff then the prob is somewhere else

it is in synaptic manager

---

### Post by 2hot6ft2 on 2010-04-06
> **fly_boy said:**
> Hi again, (it feels like I spend half my time on here)

I am trying to download firestarter... but it gives me the following error

Failed to fetch [http://im.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-7ubuntu5_i386.deb](http://im.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-7ubuntu5_i386.deb) Could not connect to 192.168.2.3:8080 (192.168.2.3). - connect (111: Connection refused)

It was recommended that I download firestarter in order to configure ports, but how can I open up this port in order to download stuff

Thanks again in advance

Alan
Try clicking on your own link and it should download the deb file, it did when I clicked on it. It (that repo. server) may have been down for updates or something so
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```

---

