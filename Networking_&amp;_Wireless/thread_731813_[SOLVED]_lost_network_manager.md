---
title: "[SOLVED] lost network manager"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by hellomoto on 2008-03-22
I was trying to get pidgin working on my ubuntu box and someone surgested i try:

```
 sudo chmod -x /usr/sbin/NetworkManager 
```

Now of course my wireless conection fails to load due to the lack of network manager... 

I feel very stupid for putting in the above command but can someone please tell me how to remove the permissions i have set on this file so it will load!

thankyou!

---

### Post by poobalanc on 2008-03-24
hey how u solve this problem? im facing the same problem. please let me know ya..

---

### Post by Eiríkr on 2008-03-24
I'm baffled why this thread is marked as SOLVED when there's no solution evident, so I thought I'd add one.  ;)

When you ran [font=courier]chmod[/font] before, you removed (the minus sign) the e_**x**_ecute permission on the [font=courier]/usr/sbin/NetworkManager[/font] program.  To make it executable again, you need to do the reverse -- add (a plus sign) the e_**x**_ecute permission, like so:
```
sudo chmod +x /usr/sbin/NetworkManager
```

Incidentally, what thread did you see this in, and who recommended you do this?  This seems like a bad "mess up the noobie" prank, but I suppose the thread context might make it clear.

Let us know if you need help with anything else.  

Cheers,

Eiríkr

---

