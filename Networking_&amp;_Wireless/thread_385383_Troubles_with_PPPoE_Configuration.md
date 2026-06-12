---
title: "Troubles with PPPoE Configuration"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by lblagoev on 2007-03-15
Hello All,

I have troubles configuring my network connection under Ubuntu. When I decided to run pppoeconfig I received a message like this: "I scanned 1 interface but the access concentrator of your provider did not respond". 

I visited my provider's web site where I found information about pppoe configuration with linux. They forwarded me to roar penguin web site to download rp-pppoe package. This doesn't lead to any positive result.

I talked with other subscribers to my ISP but no one of them shared the same problem like me. The people I talked with were not from my neighborhood. All of them told me to just run pppoeconf with a root account and that's all. I think that the problem may be in my ISP. 

If someone has any idea please share.

Thanks, Lyubo

---

### Post by danielgruen on 2007-03-16
Hi,

I'm currently facing similar problems (see [http://ubuntuforums.org/showthread.php?t=385144](http://ubuntuforums.org/showthread.php?t=385144) for that matter) and I don't have found much of a solution yet. So I'm probably the wrong one to answer, none the less, here are my hints:

1) What kind of DSL modem are you using? Generally speaking, there are two types of DSL modems, simple-minded ones that are simply modems (connected to your pc via usb, pci or ethernet cable) or highly-intelligent-ones that are modems with built-in router (to be recognized by typically having several ethernet sockets and usually coming with a version of the GNU GPL license because they're actually computers running GNU/Linux). Which kind of a modem is your computer connected to and by what kind of means? If you're having a simple-minded modem connected via ethernet cable, pppoeconf is right for you -- otherwise, it's possibly not. Especially not if your modem is one of the highly-intelligent-ones.

2) Did you check your modem is actually having any connection to the dsl provider (if so, the DSL Link/Act LED should be on)?

3) It might be helpful if you post the error output of pppoe-discovery here, which will be written to debug.txt if you run "pppoe-discovery -D debug.txt" as root.

Hope this helps 

Daniel

---

### Post by lblagoev on 2007-03-17
Hello, danielgruen

In fact I don't have a DSL modem. I think it's of the second type (a linux machine which acts as a router) which is at my provider's office. I have only a UTP cable connected to my computer. 

Under windows I create a broadband connection via PPPoE, type in my username and password and that's all. I have a connection.

Thanks, Lyubo

---

### Post by danielgruen on 2007-03-17
Hi Lyubo,

you're right, that sounds much like pppoe is necessary and pppoeconf is the correct tool. Could you just post the pppoe-discovery log as described above?

Greetings

Daniel

---

