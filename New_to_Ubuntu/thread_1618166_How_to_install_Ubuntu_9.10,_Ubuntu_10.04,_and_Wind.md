---
title: "How to install Ubuntu 9.10, Ubuntu 10.04, and Windows XP"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Harold879 on 2010-11-10
I'm already [ninipokertour](http://ninipokertour.all-up.com/t9-europa-casino-a-une-riche-histoire#9/)
 booting Ubuntu 10.04 and Windows XP and was interested  in installing Ubuntu 9.10 [ultraspoker83](http://ultraspoker83.superforum.fr/t31-nouvelles-en-direct-sur-le-poker#65/)
 side those two. Is this possible?  Thanks!shops, supermarkets and on the street. [guitpoker](http://guitpoker.forumsactifs.com/t11-nofoldem-holdem#11/)
 through OSMP usually follows. The player indicates the number of R-purse online casino in the payment system Webmoney, and lowers the right amount of bills in the bill acceptor automaton. Then you need to take the [50dollarsgratuits](http://50dollarsgratuits.forumpro.fr/t9-bonus-de-casino-en-ligne#9/)
 and inform the customer support online casino control information from him. The Commission does not exceed 5 percent. Translation takes no more than 24 hours. Receive gain through OSMP not. This is not all ways to replenish the game score in the Internet casino, but they 
[pokerclubtheza.1fr1](http://pokerclubtheza.1fr1.net/t7-dans-le-cadre-de-l-interdiction#7/)
 the most convenient and popular. But even if you use a payment system that does not support Internet casino, you can always exchange money at an exchange office, after opening the account, for example, in system Webmoney. This can be done free of charge. All popular [trekkerpoker.big-forum](http://trekkerpoker.big-forum.net/t9-nombreuses-salles-de-poker#9/)
 casino support this payment system. With every new game account in the casino the player can be credited bonuses, which can be as well for the money to play online casino.

---

### Post by munna.cheyur on 2010-11-10
Ya it's possible try alloting new drive for ubuntu 9.10.. but why 9.10 is there any special ?

---

### Post by Megaptera on 2010-11-10
Do 9.10 and 10.04 use the same version of Grub?

---

### Post by amjjawad on 2010-11-10
> **Megaptera said:**
> Do 9.10 and 10.04 use the same version of Grub?

Yes, both use GRUB2.

---

### Post by Megaptera on 2010-11-10
Phew, that should simplify it!!

---

### Post by amjjawad on 2010-11-10
> **Harold879 said:**
> I'm already dual booting Ubuntu 10.04 and Windows XP and was interested  in installing Ubuntu 9.10 along side those two. Is this possible?  Thanks!

Even though it's a bit weird to install an old version but I'm not going to ask you why you want that :)

I have 9 OS's installed. The boot loader of each OS is installed in it's partition. Only one of them has its boot loader installed in the MBR.
IMHO, if you're going to install 9.10, don't install its boot loader in the MBR. Install the boot loader in the same partition where you'll install 9.10 then after that, run from 10.04

```
sudo update-grub

```

I guess that's all what you need.

---

### Post by oldfred on 2010-11-10
I agree with amjjawad.

You want to keep the newest version of grub2 in charge of the boot process. While I have had no trouble with any version of grub2 they have made major improvements with each new distribution.

---

