---
title: "Network interface stays up after cable removed"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by sester2 on 2016-05-20
Dear all,

I'm currently working with a headless Ubuntu 16.04 system with four network interfaces. Configuration is available [here]("http://paste.ubuntu.com/16517791/"). When I currently start the system while not all three wired interfaces have a cable plugged in, I get the "A start job is running for raise network interfaces" after booting which I mitigated by setting the systemd-timeout to 30 sec. Apart from that, the network seems fine, i.e. the interfaces are available without addresses and are marked as NO-CARRIER.

Now, as I plug in a cable, the interface correctly pulls an IP with DHCP and works as expected (eth0 in the example config). But as I remove the cable, the interface is marked as NO-CARRIER again but does not release the IP address (and also keeps all routes), thereby possibly breaking network access.

Why does the interface not come down?

I also wonder why it even waits for connections on the disconnected interfaces when starting, but I guess that's a different topic.

Thanks
Sebastian

---

### Post by sester2 on 2016-05-31
Bump. O:)

---

### Post by The Cog on 2016-05-31
It's not normal to have multiple interfaces on the same subnet. Does it do the same thing if you only use one NIC?

How do you see the NO-CARRIER state? Is it the **ip link** command or something else?

I'm just fishing - I have no good ideas.

---

### Post by sester2 on 2016-06-02
You mean the eth-interfaces? Actually they only have the same subnet because I plugged the cable into eth0 (then it got an IP from the DHCP) and then unplugged the same cable and connected it to eth1. And since eth0 didn't go down ...

If I only connect one interface and have not previously connected another interface, all is fine.

NO-CARRIER: I actually used "ip addr", but the output is pretty much the same, yes.

Thanks
Sebastian

---

### Post by QLee on 2016-06-02
> **sester2 said:**
> You mean the eth-interfaces? Actually they only have the same subnet because I plugged the cable into eth0 (then it got an IP from the DHCP) and then unplugged the same cable and connected it to eth1. And since eth0 didn't go down ...

sester, I think perhaps you don't fully understand how routers (and DHCP service) work. It sounds like you are expecting the router to reassign the IP Address it had give to Lan0 to Lan1 after you have removed the cable from Lan0 and plugged into Lan1. But routers remember the MAC address of the network interface and tries to save that previously assigned IP Address in case Lan0 wants to connect again. Thus when you plug the same cable into Lan1 it gets a different address. But maybe I misunderstood what you mean.

What could "no carrier" mean except disconnected? (carrier is the frequency that the data travels by way of, as an overly simplified explanation) It's not "up".

It might be a good idea to explain exactly what goal you are trying reach? In other words why the three separate NICs and why you move the network cable around like what you describe. What is the purpose of the network card "going down" (as you describe it) when the cable is not plugged in? 

There is no real reason that I need to understand what you want to do but others may also have trouble figuring out what your ultimate goal is and thus have trouble recommending a solution.

---

### Post by The Cog on 2016-06-02
I know it is difficult to tell just looking at written postings, but I get the impression that sester2 does understand that stuff. The question is why does the interface retain its allocated IP address and its routes after the cable is removed. I've never seen or heard of that before. The reappearance of NO-CARRIER in ip list shows that the lower driver has detected the loss of connectivity. It's just not making its way through the IP stack.

The only thing I can think of is that perhaps there is a problem with the wireless adapter trying to bind to an access-point and perhaps this is preventing the rest of the networking stack from finishing its initialisation, and therefore unable to respond to a later link-down event.

All I can suggest is commenting out all the entry for wlan0 and trying again to see if that allows the wired interfaces to react to link-down properly. 
If they still don't go down properly when the cable is removed, then I have no idea what the problem might be.
If they do then go down properly when the cable is removed, I still have no idea what to do next but at least you have a better idea where the problem lies - with wlan0.

---

### Post by QLee on 2016-06-02
@The Cog, OK I understand.

Maybe it is something to do with /etc/network/if-down.d, I think the avahi deamon is supposed to run a script when a connection is lost. But I don't know how that could have been messed up without intervention by the system admin. 

I hope I can learn something here too.

---

### Post by QLee on 2016-06-02
> [/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x157b (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="enp*s0", NAME="eth0"
# PCI device 0x8086:0x157b (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="enp*s0", NAME="eth1"
# PCI device 0x8086:0x157b (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="enp*s0", NAME="eth2"

I just had a look at the "configuration" that  sester2 posted, interesting renaming of the three identical Network cards.

---

### Post by sester2 on 2016-06-03
The renaming was done by the installation sequence of Ubuntu 14.04 if I remember correctly.

And yes, as The Cog said, the problem is that the system keeps the addresses and routes; I do understand that and why I get another IP :).

I didn't put any scripts in ifdown.d (well, at least not manually) as far as I can remember. There are three scripts ("resolvconf", "upstart", "wpasupplicant"), but my desktop system also has those, so I suppose they are nothing special? :confused:

I'll check the idea with wlan0 and check avahi - thanks! and report back on the results.

---

### Post by QLee on 2016-06-03
> **sester2 said:**
> And yes, as The Cog said, the problem is that the system keeps the addresses and routes; I do understand that and why I get another IP :).

Yes, I misunderstood until I reread what you wrote.

My point about the udev rules was:
With the new method that the system uses to enumerate attached devices, the KERNAL=<hardware location> in the rules, I suspect that future best practice will be to use those hardware location values to set the rules for manual naming of network interfaces. Presumably, the udev rules you have use the MAC to determine the manual  naming (for example eth0). In the case where a NIC fails and needs to be replaced, you would have to rewrite the rule because the replacement NIC would have a different MAC but, if your rules use the actual hardware location (for example enp3s0) then replacing the NIC would not require rewriting the rule because you'd be using the same MB slot and the system would see it as the same "Predictable Network Interface Name".

That is just a minor point because NICs don't fail often but I think that's some of what the developers had in mind when they made the choice to go with the new naming scheme. Consistancy in naming. They haven't forced us to use the new naming convention but it may have more useful aspects that I haven't thought of yet, I'm still trying to get familiar with it

I hope you do figure out what is happening with your system, it's an interesting situation to me and I would also like to know what caused it.
Good Luck!

---

### Post by The Cog on 2016-06-04
Ooh! Udev is new territory to me. I will follow with interest but Probably can't add a lot. 

As I'm sure QLee already knows, Ubuntu 16.04 uses hardware based names like enp3s0 instead of eth0. That's probably not relevant though.

---

### Post by QLee on 2016-06-04
> **The Cog said:**
> As I'm sure QLee already knows, Ubuntu 16.04 uses hardware based names like enp3s0 instead of eth0. That's probably not relevant though.

Well. it is relevant in the sense of the suggestion that I gave for consideration, sester2 can decide if that "future proofing for NIC failure" that I suggested is appropriate or not.  Actually, it is OT in this thread and I just offered it because a light came on in my head when I saw sester2's use case. I do not expect it is involved in the symptoms.

---

### Post by QLee on 2016-06-04
I was reading through other threads and I started thinking about The Cog's idea re the Wireless LAN. In the dmesg output there are these three lines>  9.127076] ath10k_pci 0000:04:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[    9.274032] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/cal-pci-0000:04:00.0.bin failed with error -2
[    9.321319] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/QCA988X/hw2.0/board-2.bin failed with error -2 

So maybe The Cog was onto something, even though it does seem to appear that wlan0 is connecting we never looked into it deeply so perhaps it is somehow holding up the IP and route from releasing. I do note that the information we have doesn't show the system enumerated wlp?S? and then switching to wlan0 but that may not matter. Grasping at straws.....and I don't have an ath10 so just speculating.

This doesn't appear to be your production system so:
Do you want to try making sure the complete correct driver is working? In addition, try and get rid of those error messages in dmesg? 

In the following current thread, jeremy31 suggests using the ath10 driver from 16.10 for an ath10 that didn't come up at all. It is not exactly the same device id as yours. [http://ubuntuforums.org/showthread.php?t=2326733](http://ubuntuforums.org/showthread.php?t=2326733) and Jeremy31 is usually correct on wireless issues. 

If you choose to try it, code listed is:
    ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
    sudo dpkg -i linux-firmware_1.158_all.deb

    Reboot and it should function 
```

---

### Post by QLee on 2016-06-04
I had another thought (my thinking is getting slower as I get older), I am also getting lazy by letting Network Manager handle things. When I used to configure manually, I often used "allow-hotplug" instead of "auto" in the stanza for NICs in the interfaces file. (This might affect those slow boot issues too, since it shouldn't try to "auto" those NICs with no cable plugged in.)

Should be an easy test to see if that makes any difference, just change the interfaces file and reboot.

I have to go now but, once again, good luck. I hope all these bumps (or maybe it's noise) attract someone with more things to try if you haven't figured it out.

---

