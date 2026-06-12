---
title: "Dial-up Connection Problem"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by banditxkr on 2008-04-04
hey everyone thank you in advanced for all your help.

I hope this is the right thread to post in. (Wasn't sure if maybe it should be in general help instead)

I have recently figured out how to make my dial-up connection for ubuntu 7.04 work but i have one problem.  I can't get any of my web browsers to recognize the connection (I tried firefox, opera, and konquerer).  However i was able to get frostwire and kopete to work.

Is there some setting i have to change in them?

I am connecting ppp incase it matters.

This is very frustrating seen as how it has taken me almost 7 months to get the connection to work and now i can hardly use it.:confused:

please help!!!!!!!!

---

### Post by MrFSL on 2008-04-04
Option 1)
System > Administration > Network
Modem Properties
Options
Check - Set Modem As Default Route To The Iner

Option 2)
From a terminal type:
```
route | grep -i default
```

Check the default route. If it doesn't look like what you want try something like this:
```
sudo route add default ppp0
```

***EDIT***
Just a quick edit - I prefer using KPPP for my modem connections. Less trouble I think.

---

### Post by banditxkr on 2008-04-05
thanks for replying

when i tried the first method the only way to make it the dafault was to do the whole connection from there which doesn't work

for second method the output of the route command was jibberish to my noobish self.
for the fun of it i tried the add default command and it said no such device exisisted.

---

### Post by MrFSL on 2008-04-06
Get the connection up and working as best you can and then type:
```
ifconfig
```and post the output.

Also type:
```
route
```and post the output.

---

### Post by banditxkr on 2008-04-06
i went bck through the first solution you gave me and i found my mistake (forgot to give it a domain to look in). so my problem is fixed 

thank you very much.

---

