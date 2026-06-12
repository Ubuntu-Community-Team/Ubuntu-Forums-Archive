---
title: "GUI Internet Connect Help Please"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by dave14922004 on 2009-12-14
Hi, newbie here.  Recently installed Ubuntu 9.10 as a dual-boot option on my XP Pro sytem, and haven't been able to get a GUI Internet connection set up.  Fortunately, I found an old file:  Ubuntu Documentation > Community Documentation > ADSLPPPoE, which says that I should no longer need to use this doc, but should work through the Network Manager instead.  I tried using System > Preferences > Network Connections, but must have screwed something up, since I couldn't make it work.  So, I followed the instructions in the above file, and used "sudo pppoeconf" in a terminal to set up a connection, which worked fine, and I am using that connection at the moment.  I can connect with "sudo pon dsl-provider", and disconnect with "sudo poff dsl-provider", so I'm not stranded, but things could be better.  I selected auto-connect when I ran the configuration script, but the system does not connect when I boot.  How do I fix?

Also, I would like to set up a GUI icon or menu choice that would let me connect/disconnect with the mouse.  Can you  point me to any docs or threads that will help me solve these problems?

Also, when I ran the script, it asked me if I wanted to connect immediately, and when I chose Yes, it replied that it had triggered the connection.  Is there some quick way to trigger this connection, or must I "sudo pon dsl-provider"?

Also, is it OK to have both methods set up at the same time?  Will they work together?

By the way, I'm using a D-Link DSL-2320B modem through an Intel 1Gb LAN chip.

Thanks for any help.

---

### Post by gs777 on 2009-12-14
did you notice network managet applet . right click on it.choose option to edit. go to the wired network tab and edit the account credentials. post the findings here

---

### Post by dave14922004 on 2009-12-14
> **gs777 said:**
> did you notice network managet applet . right click on it.choose option to edit. go to the wired network tab and edit the account credentials. post the findings here

Hi, gs777-  I right-clicked on what I believe to be the Network Management Applet, selected Edit Connections", which opened a "Network Connections" pane, then selected "Wired".  Under Name, it lists one connection:  "ifupdown (eth0)", and under Last Used, it says "never".  I am connected at the moment, and am using this connection to reply to you.  Thanks for replying.

---

