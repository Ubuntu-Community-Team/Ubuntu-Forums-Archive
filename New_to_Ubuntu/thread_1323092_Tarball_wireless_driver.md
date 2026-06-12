---
title: "Tarball wireless driver"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Uzair9E on 2009-11-11
Ok, i have been reading different users posting problems about wireless in ubuntu. I ran into the same problem. I have a dell 1397 wlan which has the broadcom chip. Now when i loaded ubuntu from the live cd, the driver manager thingy said restricted driver and asked me to allow, i did but then cancelled it and installed ubuntu. Now in the installed version, the restricted drivers wont appear, even by opening the driver manager thing manually. Its just not there, so i thought reinstalling will fix it. I reinstalled, didnt touch the manager in the cd version, but even now the restricted drivers wont show up, so wireless wont work.

I found my drivers at this dell post, but its in this tarball format or something and i have no idea how to install it. can someone point me to an exact how to guide since, the read me doesnt make any sense to me, neither does most of the stuff already posted. or tell any other way to get my wireless going.

[http://en.community.dell.com/blogs/direct2dell/archive/2008/10/03/linux-driver-available-for-dell-wireless-cards.aspx](http://en.community.dell.com/blogs/direct2dell/archive/2008/10/03/linux-driver-available-for-dell-wireless-cards.aspx)

---

### Post by mrboojive on 2009-11-11
Try installing the package bcmwl-kernel-source and then check to see if the drivers show up in the restricted drivers manager.

---

### Post by Uzair9E on 2009-11-11
i didn't find this package, but bcmwl-modaliases was already installed. if the drivers were correctly installed, the network should automatically detect available networks right? but mines doesnt even show the 'wireless enabled' thing. i have 9.10 tho.

---

### Post by mrboojive on 2009-11-11
bcmwl-modaliases and bcmwl-kernel-source are two different packages for Broadcom drivers. They don't both support all Broadcom cards. If there's nothing in the Hardware Drivers manager, then your wireless drivers are not installed.

Do you have a wired internet connection to your Ubuntu machine? If so, go to Synaptic and make sure your repositories are updated by clicking Reload. Then install the bcmwl-kernel-source package. If you don't have a wired connection, you will need to install the bcmwl-kernel-source package from the LiveCD by enabling the LiveCD repository in System > Administration > Software Sources.

---

### Post by Uzair9E on 2009-11-12
Aha! it worked, i got both the wired connection and also enabled cd installation and updated the packages and the drivers showed up, wireless is now working smoothly. bluetooth is still not working tho but its ok, i can use windows if i want to use bluetooth.
Bundle of thanks.

---

