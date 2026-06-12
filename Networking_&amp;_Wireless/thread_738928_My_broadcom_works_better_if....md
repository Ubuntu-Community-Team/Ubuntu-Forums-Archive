---
title: "My broadcom works better if..."
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by ughacks on 2008-03-29
Hi,

my broadcom wireless works with a restricted firmware. That was OK but sometimes I feel it cannot grasp signal evenif the signal is strong.

Now I feel in such situation it works better if I first boot with windows with dual boot (in such case it always works well), and then boot again ubuntu. Then ubuntu also get the signal VERY well.

So I should conclude there is no incompleteness in firmware but some operation my ubuntu cannot control.

---

### Post by dstew on 2008-03-29
There may be a setting that WIndows makes in your wireless card that Ubuntu does not make. Check to see the properties of the wireless settings in Windows, and compare that to what you see in Ubuntu. Or, look at the Ubuntu settings before and after the WIndows boot, to see if anything changes. To get an output of the wireless network settings in Ubuntu, use```
iwconfig
```To see all the available settings for a particular parameter use the iwlist command.

---

### Post by ughacks on 2008-03-29
When I tried iwconfig, so irrelevant (only status such as speed, frequence, not connection configuration etc) information is shown so I was somewhat disappointed. However it turned out that it is the most important information! And I found some important things, when I use iwlist scanning option.

1. I use "hidden" SSID (ESSID), and my nm-applet sometimes try to connect to a network without name (or with the name "")!! This can be seen if I place the mouse pointer to nm-applet icon, it shows "it is trying to join (null) network." In fact it should connect to the network with the "hidden" name. So I suspect it is a bug of nm-applet. It can also be seen in another following way.

2. The command
> iwlist scan 
shows sometimes null name "" and sometimes the real "hidden" name. Even, it shows the both names as different cells. (Maybe there is another hidden cell from elsewhere?)

3. I could see that actually I had another problem. Some of my neighbor used the same channel, so nm-applet was much harder to connect my network, since it continually changes tsf value. So I have changed the channel and now I stably connect to the desired network with full power! ha!

So thank you very much, dstew!

---

### Post by ughacks on 2008-03-30
Hi,

I thought the problem is solved, but it is not. The most severe problem is the network manager in ubuntu cannot find the network with the correct SSID. It always tries to find with some stupid name (in fact without a name, (null)). I reported this bug to launchpad yesterdy and today I found many similar complaint.

---

