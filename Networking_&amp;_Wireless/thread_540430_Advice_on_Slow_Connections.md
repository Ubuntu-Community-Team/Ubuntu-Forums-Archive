---
title: "Advice on Slow Connections"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2007-09-01
I have some advice on slow wired-type net connections. (Although, some of this may apply to wireless.)

Open a terminal window on your own workstation, expand it to full screen, and type:

```
sudo su
ethtool eth0 | more
ifconfig | more
exit
```

Notice the RX and TX, line speed, duplex, and negotiation settings or information.

Now do this on the system you are trying to connect to but find that it is slow. (If you're testing against an Internet connection, then that's something you'll have to work out with your ISP's tech support. However, at least the workstation part of this may still apply.)

Some things to note about what you see:

On the 'ethtool', watch if your NIC speed is set right. If not, you can use ethtool to try and set it to an optimal speed. For help on that, just 'man ethtool' and I think everything you want is under the '-s' switch. For instance, you'll want to ensure you're at 10, 100, or 1000 Mb connectivity depending on how fast your network is. (You may have different numbers if you're on wireless.) Full duplex is recommended instead of half duplex. And autonegotiation has its plusses and minuses. The good side is that on a congested network, it can help everyone eek out more bandwidth. The bad side is that you may want that bandwidth and it might be clipping you. You should experiment with your network connection to see if it runs faster with auto negotiation on or off, and not just on one day, but on several days of testing here or there during high traffic on your network.

*One question I still haven't answered is, "Once I have the NIC speed set to its optimal setting, how do I keep it that way on a reboot?" If you have an answer to that, please let us all know. For now, you may have to drop a Bash script entry in /etc/X11/xinit/xinitrc or something so that you optimize the NIC at the point when you load X.*

On the 'ifconfig', watch for those errors, discards (aka drops), or overruns. If you see those, I can tell you from experience that the number one cause, and the one so prone to error, is the cabling unless you're on a wireless network. So let's start from that. You have to ask, "What changed?" You have to think about the most likely cause, such as you may have moved a server, for instance, or used an Ethernet plug on the wall that you had not tested completely yet. Among the two systems -- your workstation and the remote system you were trying to connect with -- see if you're getting errors, drops, or overruns. If you are, notice if they are from the RX pair, TX pair, or both. RX = receive, while TX = transmit. These refer to the orange and orange-white, green and green-white wires in CAT 5 cabling if that's what you used. (I'm not certain about other CAT cabling.) These wires may need to be adjusted, such as some residue buildup or some other reason why you're not getting a solid connection on those pairs. Note that some hubs will actually change their lights depending on whether the NIC card is at a certain speed or duplex, or whether it has errors.

Once you believe you have the wiring ruled out, then usually it's the NIC card. If you have another known-good NIC, swap it out and see what happens. (Note some people may argue to swap the NIC first before checking the cabling because it's easiest and fastest, and that's okay. Sadly, though, I often find it's not the NIC -- it's the cabling. Your situation may vary.) There's not much more you can do with a NIC besides getting another driver. If it were me, I'd swap the NIC with another known-good NIC. Note that storms have knocked my NIC cards out at least twice in my house before I said "ENOUGH!" and got serious about checking all the grounds in phone wiring, the power wiring, putting everything on UPS with surge protection, and running my DSL wiring through a power filter on the UPS (there are two plugs for that). Hopefully I'll be able to tolerate the next storm -- one storm I had blew out everything electronic in my house and I had to file it on homeowner's insurance. Thank goodness I had that.

Oh, and if you have a NIC on your motherboard in a workstation-type PC, you may have to get a separate NIC card and go into the BIOS Setup of your PC to disable the onboard NIC.

Next, you're looking at the Ethernet jack where the cable comes out the wall and plugs into the hub. You may have to check that wall jack to see if it also has issues.

Last, you're looking at swapping ports on the hub with another known-good one, or swapping the hub out entirely with a known-good one.

---

