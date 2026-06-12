---
title: "wireless problems"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by dazthejunglist on 2011-04-03
hi does any one know how to get a list of installed hardware on ubuntu  10.10 i need to find out what wireless card i have, i know its a belkin  54g but i need the model.
i have been having problems with the  wireless connection cutting out when the computer is idle so i was going  to try and install the windows driver only i dont know what one i need:confused:

---

### Post by bkratz on 2011-04-03
> **dazthejunglist said:**
> hi does any one know how to get a list of installed hardware on ubuntu  10.10 i need to find out what wireless card i have, i know its a belkin  54g but i need the model.
i have been having problems with the  wireless connection cutting out when the computer is idle so i was going  to try and install the windows driver only i dont know what one i need:confused:




```
lspci | grep Network
```

should do it

---

### Post by grahammechanical on 2011-04-03
You should study this

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

otherwise you may break more things than you fix.

Regards.

---

