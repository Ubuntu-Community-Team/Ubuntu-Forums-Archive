---
title: "no network connection, because of a button"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by ilizzane on 2010-07-28
Hey.
 
i have a foolish problem. 
 
i have a acer aspire 3000 which i installed Ubuntu 10.04 on. easy as pie. 
 
what my problem is: i can't connect to my wireless internet. all the settigns are right and but it still dont work.. 
 
anyway foolish as i am i forgot all about this button i need to turn on, so my wireless are enabled.. anyway, this button wont work, so my question is simple.. how can i make it(the button) work, or at least make my wireless work without this button.
is there a way to enabled my wireless

---

### Post by mikewhatever on 2010-07-28
Depends what kind of button it is. I have an HP laptop, and if the wireless was turned off with the button, there is no way to turn it on, safe with the button. On the other hand, how do you know the button is the problem? Acer often uses Atheros wireless cards that require proprietary drivers or Ndiswrapper. Have you tried the Hardware Drivers utility under Administration?

---

### Post by ilizzane on 2010-07-28
yeah, i have looked there.. and you might have a point.. i dont know for sure that is the problem. it shows absolutly nothing what so ever of drivers in there.. so maybe i "just" need to find me some drivers. i will properly need some proprietary drivers or Ndiswrapper. 
 
i stumbled apon this [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) and i guess its the way to do it or are there alternatives?

---

### Post by mikewhatever on 2010-07-28
For the Hardware Drivers utility to work, it needs internet connection. Hook up an ethernet cable and try again.

---

### Post by ilizzane on 2010-07-29
okay its now hooked to the Internet, and i tried install Ubuntu on another older laptop(HP) and after i updated and turned the network driver on that one worked, but not the acer. 

now i don't know what to do? i understand the link i gave earlier are somehow kinda outdated for my version of Ubuntu, but apparently it worked on the HP laptop. 
Anyway any suggestions after i updated and activated the wireless (it downloaded the driver and installed it, and are now active and using, but i still can't find my wireless as i could with the HP laptop)

---

### Post by mikewhatever on 2010-07-29
If, even with ethernet connected, the Hardware Drivers show nothing, post your wireless hardware specs. If you don't know the card model, open Applications->Accessories->Terminal and post the output of the following:
```
sudo lshw -C network
```

---

