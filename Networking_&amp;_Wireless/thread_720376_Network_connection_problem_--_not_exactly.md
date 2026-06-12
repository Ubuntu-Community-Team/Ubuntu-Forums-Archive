---
title: "Network connection problem? -- not exactly"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by mahiyar on 2008-03-10
You cannot say this is exactly a network issue it is more of a configuration issue. My current set up is -- I'am connected to the network through my LAN card on to the LAN using pppoe configuration. Now there are more than one access configurators. I use two one for my internet and the other one for the "intranet like LAN", where I can use my DC++ etc. Every time I want to go from one access configurator to other I have to run "sudo pppoeconf", my user name and password are the differentiator. In windows there are two seperate dial up shorcuts for the same. Can anyone help me stop doing this round about way of connecting. Thanks in advance.

---

### Post by SpaceTeddy on 2008-03-10
pppoeconf will always overwrite the configuration files - if you move the file to be named different, you can have as many configrations as you want.

the configurations are found in /etc/ppp/peers - there should be one there saying - "dsl-provider"

once you have two different files in the /etc/ppp/peers directroy, you can use the with the pon command, or simply thought network manager (i think)

with pon, you'd say 
```
sudo pon %filename%
```

hope it works

---

### Post by mahiyar on 2008-03-10
Thanks spaceteddy cant wait to try this out

---

### Post by mahiyar on 2008-03-11
It worked, but is a bit unpredictable. As suggested I made two connections one for local LAN and other for internet. It worked for a while. However after rebooting both "dialers" ended connecting the local LAN and not the internet concentrator. Then I had to make a new connection and that helped. Is there some DNS address somewhere to be put so both these dialers connect surely to where we want them to connect?

---

### Post by SpaceTeddy on 2008-03-11
that is beyond what i have ever done with pppd - you'd probably work your way through the configuration in those files - maybe you can specifiy it somewhere there.

but i am of no help there - sorry :(

---

