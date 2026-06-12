---
title: "ENL832-TX-EN Fast PCI Ethernet on Intrepid, Help needed desperately"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by evilkastel on 2009-01-22
Ok, I just installed intrepid in this other box i got, and works nice except *sigh* it does not recognize the ethernet card. I got the Diskette with the drivers and (surprisingly) it has a linux driver. Unfortunately the readme instructions do not work on intrepid.

[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=83_11&pid=2#DOWNLOAD](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=83_11&pid=2#DOWNLOAD) 

Thats the device and the driver, i need to make it work as fast as possible, because that pc is for a friend...

The ubuntu installed is the standard 8.10 1386. 

thanks in advance

---

### Post by cariboo on 2009-01-22
The sundance module is included with both kernel 2.6.27.7 and 2.6.27.9, so you don't need to install any extra modules.

Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and in the same terminal

```
ifconfig
```

The first command lists the details of the network card and if the driver is loaded. The second command will list the the details of the connection, including the ip address if any. Paste the output of the two commands in your next post.

you can create text files of the output by appending  > <filename> to the above commands eg:

```
sudo lshw -C network > network.txt
```

Of course use a different file name for the second command.

Jim

---

### Post by evilkastel on 2009-01-24
Jim: since the sundance modules are included in this kernel i tought i ckeck what kernel i had. I found that iwas running hardy LTS instead of intrepid. A huge lapsus there. Anyway i had a partitioning need for windows so i just reinstalled, intrepid this time and it worked out of the box. So thanks very much, you lead me to the key of my stupidness.

---

