---
title: "How to connect 2 PCs using ethernet"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-04-10
Hi all

I expect to transfer data from Ubuntu 12.04 desktop to Debian 7.3 desktop (2 PCs) using ethernet without a router.

I found following link;
How to network two Ubuntu computers using ethernet (without a router)?
[http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router)

But that is for 2 Ubuntu computers.  Is there a more recent document?

Thanks

Rgds
satimis

---

### Post by SeijiSensei on 2014-04-10
I suggest using static IP addressing on both sides.  You can either do it only the fly by running ifconfig at the prompt, or edit /etc/network/interfaces on each machine.  Give the machines different addresses in the same subnet, e.g.,
```
sudo ifconfig eth0 10.1.1.1 netmask 255.255.255.0 broadcast 10.1.1.255
```
and similarly on the other machine to define 10.1.1.2.

You don't need any additional routing unless you want one of these machines to also have Internet access.  That adds complications beyond just connecting the two machines together.

---

### Post by 23dornot23d on 2014-04-10
Sometimes you need a crossover cable .......
 
I remember a long time ago having a friend make me one up .......... but read here as it may just be for older
computers........

[http://www.wikihow.com/Connect-Two-Computers](http://www.wikihow.com/Connect-Two-Computers)

---

### Post by satimis on 2014-04-11
> **SeijiSensei said:**
> I suggest using static IP addressing on both sides.  You can either do it only the fly by running ifconfig at the prompt, or edit /etc/network/interfaces on each machine.  Give the machines different addresses in the same subnet, e.g.,
```
sudo ifconfig eth0 10.1.1.1 netmask 255.255.255.0 broadcast 10.1.1.255
```
and similarly on the other machine to define 10.1.1.2.


Thanks for your advice.

I suppose the cable for router could be used for connecting 2 PCs?

After connection established I can run rsync/cp etc to copy the file from PC1 to PC2?

> 
You don't need any additional routing unless you want one of these machines to also have Internet access.  That adds complications beyond just connecting the two machines together.
No.  Just connect 2 PCs and copy file/directory from PC1 to PC2

Thanks

Rgds
satims

---

### Post by SeijiSensei on 2014-04-11
> **satimis said:**
> I suppose the cable for router could be used for connecting 2 PCs?

It depends on the network adapters in the two machines.

In the past you typically needed to use a special "crossover" Ethernet cable to connect machines directly.  Those cables connect the transmit pins on one machine to the receive pins on the other, and vice versa.  However modern network adapters have an "auto-sensing" ability to detect which pair of connectors should be used.  I'd give your regular Ethernet cable a try and see if it works.  If not, you need to buy a [crossover cable]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100016774&IsNodeId=1&srchInDesc=crossover&page=1&bop=And&ActiveSearchResult=True&Order=PRICE&PageSize=20").

To copy the files, I'd choose rsync.  If neither machine has openssh-server installed, you might want to do that first.

---

### Post by satimis on 2014-04-11
> **SeijiSensei said:**
> It depends on the network adapters in the two machines.

In the past you typically needed to use a special "crossover" Ethernet cable to connect machines directly.  Those cables connect the transmit pins on one machine to the receive pins on the other, and vice versa.  However modern network adapters have an "auto-sensing" ability to detect which pair of connectors should be used.  I'd give your regular Ethernet cable a try and see if it works.  If not, you need to buy a [crossover cable]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100016774&IsNodeId=1&srchInDesc=crossover&page=1&bop=And&ActiveSearchResult=True&Order=PRICE&PageSize=20").

To copy the files, I'd choose rsync.  If neither machine has openssh-server installed, you might want to do that first.
Hi

Performed following steps:

PC1 Ubuntu 12.04```

sudo ifconfig eth0 10.1.1.1 netmask 255.255.255.0 broadcast 10.1.1.255

```

PC2 ```

sudo ifconfig eth0 10.1.1.2 netmask 255.255.255.0 broadcast 10.1.1.255

```

Connected 2 PCs with a router cable

PC1 can ping PC2 and vice versa

On PC1 ran ```

rsync -r -a -v -e "ssh -l satimis" Temp_Storage/* 10.1.1.2:/home/satimis/Temp_Storage/

```

Files copied.  Thanks

Rgds
satimis

---

### Post by SeijiSensei on 2014-04-11
Great!  You might want to mark this [SOLVED] using the Thread Tools drop-down at the top of this page.

---

### Post by satimis on 2014-04-12
> **SeijiSensei said:**
> Great!  You might want to mark this [SOLVED] using the Thread Tools drop-down at the top of this page.
Where is it?

I did that before but I couldn't discover it this time

Edit:
I found it

Rgds
satimis

---

