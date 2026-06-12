---
title: "Internet Connection"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by pinbill on 2010-08-11
Hello All-

I just re installed Ubuntu 9.04 on my Dell Vostro 1000, I am using an older Lynux router that I know works great, I can't remember what I have to do to get connected to the internet after freshly installing ubuntu. Do I have to download or activate any drivers? Right now the icon at the top of the toolbar by the time has a red X it, and I can't locate any local modums. Can anyone help?

THanks.

Bill

---

### Post by Peter09 on 2010-08-11
you need to connect using a hard wired link and do a full update to ensure all drivers are available,

---

### Post by pinbill on 2010-08-11
Thanks, I am installing all updates now. Do I need to do anything special to watch streaming videos?

---

### Post by jmfal on 2010-08-11
ubuntu restricted extra`s in synaptic

add medibuntu repository>google medibuntu instructions are there
 go to software sources and check box for medibuntu so you can get updates.

when you install restricted xtras check description it may tell you  to install something else . do it.

---

### Post by theboxseat on 2010-08-11
> **pinbill said:**
> Hello All-

...Right now the icon at the top of the toolbar by the time has a red X it, and I can't locate any local modums...

Excuse the pun, but the other 'red flag' here is that you are using an older router.

There is a very good chance that this is not running at 100mb full duplex autonegotiation.

In the parlance; your router is known as the 'link partner' to your NIC (Network Interface Card)

Both need to have the same settings.

To Check run:
#sudo ethtool eth0

Especially if your router is old you won't get much useful info returned by the 'link partner', but you will see the settings for your NIC.

The trick is 'dumb down' your NIC to match that of your link partner:

The following is not persistant..ie.will not survive a re-boot..but can easily be made permanent..for now lets try it to see if it resolves your connectivity issue:

In terminal:

# sudo ethtool -s eth0 speed 10 duplex full autoneg off

Then right click the 'connection icon' (in top right corner of screen)
Uncheck 'Enable Networking'
Recheck 'Enable Networking'

You should then get a good network connection..try speedtest.net to check it out

If unsucessful; try the above, but change the duplex setting to half

Good luck

---

### Post by pinbill on 2010-08-11
OK-

Had time to update and install medibuntu repository. Still not showing any wireless connections and not able to watch streaming movies or listen to mp3 files. I also put the router commands into the terminal but didn't quite understand that part. Thanks for your responses and additional suggestions are welcomed,

Bill

---

### Post by sandyd on 2010-08-11
> **pinbill said:**
> OK-

Had time to update and install medibuntu repository. Still not showing any wireless connections and not able to watch streaming movies or listen to mp3 files. I also put the router commands into the terminal but didn't quite understand that part. Thanks for your responses and additional suggestions are welcomed,

Bill
System -> Administration -> Hardware Drivers
anything there?

---

### Post by pinbill on 2010-08-11
There are Broadcom B43 and Broadcom STA drivers. But I am not authorized to activate them.

---

### Post by Peter09 on 2010-08-12
If yiu are the only user on the system then the chances are that you are an Admin user. When it asks for you password enter the same one as you logged in with, this should allow you to activate a driver. Select one of them and see how it goes, you may have to return and try the other oneif te first does not work.

---

### Post by pinbill on 2010-08-12
Thanks everyone for your help, problems solved!!!!!

---

