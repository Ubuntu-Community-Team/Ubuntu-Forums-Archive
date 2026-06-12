---
title: "Trouble Installing a Belkin F5D9050 USB Wireless Network Adapter"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by IQAndreas on 2008-06-21
Hello all.

I am a bit of a beginner with Linux, but I know basic things such as installing new packages and how to use a terminal etc.

I am trying to use a Belkin F5D9050 USB Wireless Network Adapter with my computer. It works fine when I install it on Windows XP, but I can't seem to get it to work on my xUbuntu.


I started on one tutorial I found on ndiswrapper (found at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) but when I get to the part when I need to run lsusb (Section 3.3.2) the adapter does not show up on the list. The only thing I get is "Bus 001 Device 001: ID 0000:0000".

The adapter is plugged in and everything, and I know that USB slot works for other accessories.


I have searched the internet and tried many different methods, but nothing seems to work. I'm not sure if I'm doing something wrong or if the adapter just does not work with Linux.

I am using xUbuntu 7.04, but I would like to be able to use the adapter in other Linux distributions as well.

If I decide within the next week that I do not want the adapter, I am still able to return it to the store for full credit, so this is an option if all else fails.

Are there any not too expensive USB adapters that work well with Linux that I can use instead?

Thanks,
Andreas

---

### Post by IQAndreas on 2008-06-21
I feel like an idiot now.

I have 2 identical computer towers right next to each other and often switch cables between the two. Although it is a bit of a hassle switching cables every time, it is a lot easier than buying another monitor. (Yes. I'm cheap like that. ;) )

Anyway, I accidentally plugged the wireless adapter into the wrong computer.

I switched it over, and now it shows up on the lsusb list as "Bus 001 Device 002: ID 050d:905c Belkin Components".

Now, however, I have another problem. I can't find the right driver in the list of drivers on the ndiswrapper list.

I have the original installation CD with the Windows driver, but how would I go about putting that on my Linux machine?

---

### Post by IQAndreas on 2008-06-23
I still can't get it figured out.

Could someone lend me a hand?

---

### Post by IQAndreas on 2008-06-24
I hate to keep bumping this thread, but this is a large forum, and my thread keeps getting pushed down. :(

Sorry to nag so much.

---

### Post by travisn000 on 2008-07-17
Take a look at the first two post at this thread for PCLinuxOS.. the process if probably similiar:

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=27892.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=27892.0)

These might also be helpful:

[http://www.pclosmag.com/html/Issues/200712/page03.html](http://www.pclosmag.com/html/Issues/200712/page03.html)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/#install_windows_driver](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/#install_windows_driver)

---

### Post by moon2js on 2008-11-19
Correct me if I'm wrong, but doesn't this adapter work [natively on Linux]("http://linux-wless.passys.nl/query_part.php?brandname=Belkin")?

However, I have the same adapter and the system doesn't automagically recognize it.

Does anyone know how to configure the system to use a new network adapter?

---

