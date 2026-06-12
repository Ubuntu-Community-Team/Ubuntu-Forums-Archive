---
title: "Only 1 on-board network connection works at a time"
date: 2016-12-23
forum: Networking &amp; Wireless
---

### Post by Christopher_J._Cra on 2016-12-23
I have a server with 2 on-board network connections. I can see both connections in the network configurations in ubuntu gnome. But it only has a spot for 1 wired connection to be active at a time. I am able to switch between the 2 but would like them both to be active at the same time to lessen the load sent on 1 connection by having different ports sent to each of the connections. Any suggestions on how to get both active at one time?

---

### Post by chili555 on 2016-12-24
>  I can see both connections in the network configurations in ubuntu gnome.To do what you want to do, I think you will need to abandon Network Manager and make all your settings in /etc/network/interfaces; something like this: [http://askubuntu.com/questions/227282/how-to-connect-to-the-internet/227305#227305](http://askubuntu.com/questions/227282/how-to-connect-to-the-internet/227305#227305)

If you need specific guidance, post back and I'll be happy to help.

---

### Post by SeijiSensei on 2016-12-24
You can look into [bonding]("https://help.ubuntu.com/community/UbuntuBonding"), though to be honest, I doubt you'll see any serious gains in performance unless your machine has 100BT ports connected to a gigabit Ethernet network.  If that's the case, you'd be better off buying a [gigabit Ethernet card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033").

Having both interfaces on the same IP subnet can cause all sorts of routing problems.

---

