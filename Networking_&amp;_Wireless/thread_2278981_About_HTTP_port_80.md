---
title: "About HTTP port 80"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by satimis on 2015-05-20
Hi all,

Host - Ubuntu 14.04
VMs - Ubuntu 14.04 LAMP and WordPress

There are several websites, each running on VMs.  I have only one Static IP.  If on router forwarding port 80 to 192.168.0.xx1 then websites on other VMs couldn't be accessed on Internet.  I have tried port 8080 or 82 but it didn't work.

Please advise is there any solution?  Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-05-20
Dump the VM's and just run one server with virtual hosts as Apache is designed to do.

---

### Post by satimis on 2015-05-20
> **SeijiSensei said:**
> Dump the VM's and just run one server with virtual hosts as Apache is designed to do.

Hi,

Thanks for your advice

I have more than 40 websites running on 5 groups;
Music
Home
Information
Travel
Finance

For such a reason I don't expect running all of them on ONE VM, if possible.  Now I use name-based virtual hosts on each VM.

Regards
satimis

---

### Post by SeijiSensei on 2015-05-20
Commercial website providers host hundreds of websites on a single machine.  Forty is really not that many.  Web services are generally not that demanding an application.

If you are committed to your current model, then create a single publicly-visible site that uses mod_proxy to route each request back to its corresponding virtual host.

---

### Post by satimis on 2015-05-20
> **SeijiSensei said:**
> Commercial website providers host hundreds of websites on a single machine.  Forty is really not that many.  Web services are generally not that demanding an application.

If you are committed to your current model, then create a single publicly-visible site that uses mod_proxy to route each request back to its corresponding virtual host.
Hi,

If no solution found I'll run all websites on a SSD without virtualizaion.  They are the cloned copies of the Live running on Godaddy server.  I think a 500G SSD will provide sufficient space.  The installation is quite straight forwards.  I just download the blogs and databases from the Live sites.  The download time will be more than the installation time.  My router is connected to 100M/100M up/down optic broadband.

Regards
satimis

---

