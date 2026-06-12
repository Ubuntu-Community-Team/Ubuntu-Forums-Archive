---
title: "PPPOE Shortcut"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Mutahir on 2007-04-10
Hello All,

I have just installed Ubuntu 7.0.4 beta, I have successfully configured my PPPOE connection with the following command :

sudo pppoeconf

Now, I can't seem to find a way to create a shortcut for myself and my friend to use it to dial instead of running the whole thing again and again. i tried the command pon-dslprovider which returned an error i guess ...

is there a way or an app to configure pppoe and create its shortcut.?

Regards

Mutahir

---

### Post by zvacet on 2007-04-10
system>administration>network settings>highlight your modem>properties>select your type of connection>chek uper left box>close.Go t ozhe DNS tab>replace address you find there with your nameserver>close
```
pppoeconf
```

After this you don´t need any shortcut,just click on your browser icon and you are hooked

---

