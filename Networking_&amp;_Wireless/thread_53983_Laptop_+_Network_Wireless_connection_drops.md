---
title: "Laptop + Network: Wireless connection drops"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by born_confused on 2005-08-02
I have seen a few threads, read a bit, however most of the problems are close but have not yet proved a solution for me.

Whats going on?
Well, What happens is my connection suddenly seems to drop. At first I thought it was perhaps servers I was downloading from. Then I began to check certain sites, even with apt-get the connection drops after every 5-10 minutes or so. However I am not certain this was an issue when I first installed as I never used this to download large files. I know its not an access point issue.

The strange thing is, I dont recall having so many problems, but it seems to have coincided with upgrading, well, pretty much all that the update manager showed.

The connection when it is there is very strong, yet it will suddenly drop, causing whatever is downloading to stop. I would like to point out this is according to lspci

Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

This is on a hp nc6000 laptop. I realised today that there is a hp specific iso. However reinstalling everything is something I am not wanting to do, considering that I am not sure how well the new iso would work not to mention the backup involved is a rather large amount.

I have also seen people having problems with ath_hal and something about it being outdated. Could this be it? is there a way of keeping the linux-restricted-modules even if i did compile the madwifi src? However, as I have become very ubuntu orientated in that all works, and if it doesnt apt will ensure it does, I do not wish to mess about with removing parts so wireless works.

Thank you.

---

### Post by ProNoblem on 2005-08-03
I also saw this problem with a friend of me, his problem was that his router couldn't handle too much connections at the same time (for instance: bittorrent clients use A LOT of connections to all the peers in the tracker)
So basicly, his router just freaked out and crashed every now and then. His solution was to simply buy another router which could manage more connections at the same time.

A way to check this is to hook up your laptop to another network and check if the problem still exists. If this is the case then my post is probably useless :).. (or when you're not using a router)

---

### Post by Jova on 2005-12-25
[QUOTE=ProNoblem]I also saw this problem with a friend of me, his problem was that his router couldn't handle too much connections at the same time (for instance: bittorrent clients use A LOT of connections to all the peers in the tracker)
So basicly, his router just freaked out and crashed every now and then. His solution was to simply buy another router which could manage more connections at the same time.

A way to check this is to hook up your laptop to another network and check if the problem still exists. If this is the case then my post is probably useless :).. (or when you're not using a router)[/QUOTE]

Please ask your friend which router he bouth becaus I shud buy one. And I don't like to have saim problem.

tnx

---

### Post by hil on 2005-12-26
I have an [ASUS router]("http://tw.asus.com/products4.aspx?l1=12&l2=43&l3=0&model=62&modelmenu=1") at home. It works well with Atheros chip. I bought it in Taiwan. You can check it out. DO not place it close to any metal object when it is on.


[QUOTE=ProNoblem]I also saw this problem with a friend of me, his problem was that his router couldn't handle too much connections at the same time (for instance: bittorrent clients use A LOT of connections to all the peers in the tracker)
So basicly, his router just freaked out and crashed every now and then. His solution was to simply buy another router which could manage more connections at the same time.

A way to check this is to hook up your laptop to another network and check if the problem still exists. If this is the case then my post is probably useless :).. (or when you're not using a router)[/QUOTE]

---

