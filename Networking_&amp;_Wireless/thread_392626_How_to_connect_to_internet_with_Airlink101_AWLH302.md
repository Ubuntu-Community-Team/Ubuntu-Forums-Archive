---
title: "How to connect to internet with Airlink101 AWLH3026T Wireless PCI adapter"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by dawv on 2007-03-24
I have read some previous posts.. but none are helping me... What I need is a step by step guide on getting me Airlink101 AWLH3026T Wireless Adapter to work on the Ubuntu side of my XP/Linux PC. (if its even possible)  There is **no** way for me to connect to the internet through Linux as of yet, so i may need to transfer some files to separate partitions.  I can connect to the internet when running XP... but on linux, it dosen't even detect it.. i even search through the HARDWARE thingy... Please be aware, that im a total n00b at this and this is the first (and will hopefully be the only) Linux distro i have used...

So.. i need a step by step (in plain English) guide on how to get this to work...

I hope this isn't asking too much..

THANKS!

---

### Post by dawv on 2007-03-26
come on people... i really need some help here... what [SIZE=6]program[/SIZE] do i need, what [SIZE=6]driver[/SIZE], what [SIZE=4]commands[/SIZE], please help.. i don't wanna be stuck with [SIZE=4]windows[/SIZE] ([SIZE=1]oh god i said it!![/SIZE]).. **[SIZE=7]forever![/SIZE]**

---

### Post by dawv on 2007-03-26
bump...bunmpity bumpity bump.....

---

### Post by jambes on 2007-04-01
I have the exact same card and the same problem. I can see the wireless network, but I can't connect. It has something to do with the chipset, I think. lspci says it is a ralink chipset but I can't find anything on the net to confirm if that's actually what it is. There's others on the forum who have gotten it to work, but their solutions seem a bit vague, and didn't work for me.

---

### Post by rs3 on 2007-05-07
i had success tonight with this card in feisty amd64.  i think mine was another $10 or less fry's electronics special, and i had little hope of it working, but...

to make it work, i had to configure my connection via command line.

i first specified my access point's essid:

```
sudo iwconfig ra0 essid *name_of_access_point*
```

then, i specified my access point's mac address.  this number can generally be found on the wireless ap's underside on a sticker.

```
sudo iwconfig ra0 ap *00:12:34:56:ff:ff*
```

(the above mac address is an example of how the number should appear on the ap.)

then i invoked dhcp.

```
sudo dhclient ra0
```

now, i understand that the model number of your card may not indicate the chipset provided (and airlink, like most vendors, obfuscates your card's chipset with a plate, preventing you from seeing the details for whatever stupid reason) but in my case, and in the cases of many others apparently, this card uses a ralink chipset.  i understand that airlink uses others as they become available (cheap) so your mileage may vary.

also, i don't generally have any luck using network-manager or the networking tools provided in gnome.  for best results, stick to the cli and iwconfig, as running iwconfig tells you a lot more about your wireless configuration than anything provided in the gui.

good luck!

---

