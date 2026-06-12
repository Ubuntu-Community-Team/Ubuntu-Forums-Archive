---
title: "Why does my wifi suddenly disconnect?"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by listerdl on 2009-05-29
Does anyone have any suggestions why my Internet connect suddenly disconnects? It happens sometimes and for no apparent reason - (all the other computers in my apartment work fine). 

Odd...

(Am running the latest ubuntu)

---

### Post by porchrat on 2009-05-29
> **listerdl said:**
> Does anyone have any suggestions why my Internet connect suddenly disconnects? It happens sometimes and for no apparent reason - (all the other computers in my apartment work fine). 

Odd...

(Am running the latest ubuntu)

What wifi card/module are you running? I've heard of this happening before, especially with the Intel wireless modules. Perhaps a driver change is in order?

---

### Post by listerdl on 2009-05-29
> **porchrat said:**
> What wifi card/module are you running? I've heard of this happening before, especially with the Intel wireless modules. Perhaps a driver change is in order? Right - thanks for the reply. How can I check what type of card/module I have?

---

### Post by freeman2000 on 2009-05-31
> **listerdl said:**
>  How can I check what type of card/module I have? 

Go to Applications --> System Tools --> Device Manager to check on what hardware you have installed.  If you don't see Device manager, you may have to right-click on Applications, then click on Edit Menus, then click on Device Manager to have it show up.  Otherwise, go to Synaptic to download/install it.  Good luck.

---

### Post by superprash2003 on 2009-05-31
could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367) ?

---

### Post by listerdl on 2009-05-31
yeah thanks for the replies.

My wifi card equipment is PRO/Wireless 3945ABG [Golan] Network Connection

I googled this and guess what! It went straight to people with the same problem in the ubuntu forums....

If I just update this will it help?

Any ideas how to do that?

Thanks

---

### Post by superprash2003 on 2009-06-01
update?? arent you on 9.04?

---

### Post by porchrat on 2009-06-02
> **listerdl said:**
> yeah thanks for the replies.

My wifi card equipment is PRO/Wireless 3945ABG [Golan] Network Connection

I googled this and guess what! It went straight to people with the same problem in the ubuntu forums....

If I just update this will it help?

Any ideas how to do that?

Thanks

I haven't had much experience with newer PRO/Wireless modules, but I know the older ones had terrible support, very patchy, always disconnecting.

A friend of mine has a laptop with an Intel PRO/Wireless 2100 and it was horrificly difficult. Eventually just used ndiswrapper with the WinXP drivers and all the problems just melted away.

To gain further information on what your card is doing and how it is configured you can run these commands in the terminal:

```
lshw -C network
```
AND
```
iwconfig
```

The first one will give you the specs on your module (as well as any other network devices you may have connected) and the second one will tell you whether or not it is associated with an access point, the ESSID of the access point and some other useful stuff.

If you don't come right with the Ubuntu drivers then download the WinXP driver from the laptop manufacturers website and install it using ndiswrapper (you can get ndiswrapper and ndiswrapper-gtk by using synaptic package manager, they are very easy to use).

---

