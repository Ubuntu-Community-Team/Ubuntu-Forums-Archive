---
title: "Install ubuntu on USB encrypted"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by nishanthaMe on 2011-01-23
Hi All
I want to install Ubuntu 10.04 in my USB flash drive and boot from it because in my working place, only centos is installed in workstations.In advance, I thought of encrypting the installation of Ubuntu in the USB flash drive and In would be very thankfull if some can give me some help regarding this.
Basically what I need is, encrypted Ubuntu installation in my usb fashdrive and can boot from it.

Thanks

---

### Post by schwascore on 2011-01-26
Depends on what level of encryption you want. Here are the two options I can think of:

1) You want to completely encrypt the entire USB drive, including the OS. I would suggest investing in a hardware encrypted USB drive such as: 
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007960%2050011962&IsNodeId=1&name=IRONKEY](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007960%2050011962&IsNodeId=1&name=IRONKEY)

With a bit more work, you *could* figure out how to do a LUKS or similar install on a USB drive. Here is how I would get started (I have never done this before):
-Create a custom LiveCD ISO: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
-Create your USB image from the ISO you created.

2) If you only need to encrypt the DATA on your USB drive, you can use TrueCrypt and use the persistent memory on the USB drive to store encrypted data.
[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

---

