---
title: "Wired network ?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Romin-1 on 2007-11-11
I , just recently , installed Feisty on a stand-alone desktop and hooked it up to my Vista machine via ethernet through a K switch. I want to network these two machines but can find no 'Setup Home/Office Network' prog in Feisty. I did have the Vista PC talking to my old XP/Dapper PC with no trouble.

In Administration there is only Network and Network Tools. Samba is installed. Both PCs have the same workgroup name but, as I said, I can find no prog to introduce them to each other.

Any help, or perhaps a link to a tute will be most appreciated.

Jon

---

### Post by elspiko on 2007-11-12
If your meaning to setup a P2P network, e.g. just being able to share files between them, no internet then you'll have to give both machines static IP addresses.

E.G.

Ubuntu Machine:

IP Address: 192.168.2.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1

Vista:

IP Address: 192.168.2.4
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1

make sure the machines can see each other 

```
ping IPADDRESS.OF.OTHER.MACHINE
```

If they're talking ok, you should be able to transfer files using a FTP program.

Apologese if you already know this

---

### Post by xpod on 2007-11-12
I think you need a crossover cable to network two machines like so.

I`m not 100% sure just what a K switch is but i use a little switching hub myself although i must use a crossover cable to the switch.....from the switch to other pc`s i can use plain ethernet but i must use the crossover between pc1 and the 8  port switching hub.

Unless i`m mis-understanding.....again:)

---

### Post by Romin-1 on 2007-11-13
This is for xpod:

> A KVM switch (with KVM being an abbreviation for Keyboard, Video, Mouse) is a hardware device that allows a user to control multiple computers from a single keyboard, video monitor and mouse.

Now for the nitty-gritty. I have both PCs plugged into my DSL modem/router with internet connection. The KVM Switch is also plugged into the router. The old machine ,which died, was hooked up the same way and I was able to network, share files etc., between the two. This new machine with only Ubuntu in it refuses to see the Vista. All permissions have been given,  including the same workgroup name,Samba is installed, but I can find nothing in Fiesty that will let me setup a home network. !whew!

 A very frustipated Penguin,

Jon

---

