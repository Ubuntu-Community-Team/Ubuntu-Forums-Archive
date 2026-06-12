---
title: "Firestarter problem"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by fettuohi on 2008-05-10
I'm using firestarter to configure my firewall and I'm having problems seeing my 1 TB (formated in ntfs) network HD. My Linux box is part of a Windows network where also my network HD is and I can't see the HD when Firestarter (the firewall) is running. I've opened up for the Samba ports but still I can't see it. The minute I turn of the firewall (stop Firestarter) I can see the drive and connect to it. Is there something I'm missing to configure?

Regards

André

---

### Post by fettuohi on 2008-05-11
Anybody?

Regards

André

---

### Post by mputin on 2008-05-11
Hi

Iv got a 1TB NAS and running Firestarter also. To allow the traffic through try setting it to allow all connections from the IP address your NAS is set to.

So, click on the Policy tab, make sure "inbound traffic policy" is selected, then click on "add rule", type in the IP address of your NAS and you should be sweet.

If your gonna do it like this you should makes sure your NAS is using a static IP address otherwise it'll stop working when the address changes.

Hope that helps

---

### Post by fettuohi on 2008-05-11
> **mputin said:**
> Hi

Iv got a 1TB NAS and running Firestarter also. To allow the traffic through try setting it to allow all connections from the IP address your NAS is set to.

So, click on the Policy tab, make sure "inbound traffic policy" is selected, then click on "add rule", type in the IP address of your NAS and you should be sweet.

If your gonna do it like this you should makes sure your NAS is using a static IP address otherwise it'll stop working when the address changes.

Hope that helps

That helped A LOT. THANK YOU!!!

Regards

André

---

