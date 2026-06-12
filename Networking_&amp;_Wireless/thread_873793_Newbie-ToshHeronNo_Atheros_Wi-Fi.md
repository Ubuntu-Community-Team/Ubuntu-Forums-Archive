---
title: "Newbie-Tosh/Heron/No Atheros Wi-Fi"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by psst on 2008-07-29
Hi all,
i did have a search for answers to this issue but I am  a Linux newbie and so some of the answers were not clear to me.

My situation is that i have a Toshiba A210-12U lappy which has an AMD Turion 64 x2 processor in it.

It came with Vista but i have Heron as a dual boot at present.

The lappy also has an Atheros wireless card in it and according to System>Administration>Hardware Drivers i have

Atheros HAL in use

and

Support for Atheros 802.11.xx wireless lan cards 

Now then,on my desktop,if i go up top right to the network icon,thereis my wired network showing but the wireless isnt

There are tabs for editing wireless networks,connecting to networks but clicking on them does not list any available networks so i am assuming that something is amiss.

I know there are solutions to put it right so im wondering,

Can someone tell me how to identify the exact model of atheros card

and also perhaps a laymans guide to fixing the problem?

The lappy is only about a year old.

Also,am i enjoying 64bit computing or 32 bit computing with 8.04 and my turion 64 x2?  !!


Also another little issue..

I have a wired network mass storage device,a Buffalo Gigabit linkstation which is wired to my router as a NAS. I cant see it in Ubuntu. Any clues as to how to make it accessible?

Thanks

Jo

---

### Post by chili555 on 2008-07-29
> Can someone tell me how to identify the exact model of atheros cardOpen a terminal and do:```
lspci
```One of the entries will be your Atheros. You can the search the forum for your model and surely someone has solved it. Post back if you get stuck.

---

### Post by clymer on 2008-09-14
I am having the same issue: Toshiba Satellite A215 S5818. Heron installed with no issues - ran the updates but no wireless option. Any helpful feedback would be greatly appreciated. Thanks-

---

