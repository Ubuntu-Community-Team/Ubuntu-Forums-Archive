---
title: "SFTP transfer slow"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by tomhsiung on 2018-09-20
I have Gigabyte H370N WiFi. This mother board has two wired network interfaces and a wireless network interface. I enabled all three cards.

I set my Ubuntu as a packet fowarder, with the I219 connected to Internet via PPPoE, and I211 as the gateway of private network.

Sever days ago, I copied large files (hundreds of GBs) via rsync and the transfer speed could reach 100 MB/s. However, for some files it dropped to less than 10 MB/s.

At present I transfer five mp4 files, the transferring speed is less than 10 MB/s. WTF? And just a moment ago I transferred sever other files (iso, dmg, zip, etc.) the rate could reach 80+ MB/s. 

The network is 1000 Mbps.

Tom

---

### Post by 1clue on 2018-09-20
For the record, 1 GBPS (gigabits per second) = 125 MB/s (megabytes per second). Don't confuse the rating of the NIC, which is in megabits/gigabits per second with data transfer speeds reported by Linux or Windows. The 100 MB/s you report is probably about as good as you'll get after overheads by TCP/IP and network latency.

So, here's the deal: Your board is not networking hardware, meaning it's not designed to be a switch or a router or anything like that. Those devices have hardware specific to the task, which makes their task (whatever it is) much faster. Latency is key here, it means the time your computer spends processing each packet; the time between the receipt of a packet on one port and the sending of it on the next port. The special circuitry for switches and routers is not that expensive, they just don't put it into systems not designed to be switches or routers. Because of that you'll lose some bandwidth over wire speed that a normal switch wouldn't lose.

TCP/IP overhead is universal though, that means that extra data is transmitted which consists of TCP/IP headers. That header takes room, and IPV6 headers take more room than IPV4 headers. So that's a slice off the top no matter how good your hardware is.

The speed of the processors which actually handle networking is the next suspect. The board you are using has some nice Intel NICs which are unlikely to be a problem here. But it's not your CPU handling most of the networking, it's the ethernet NICs themselves. That's a good thing.

Networking tends to be pretty fast unless there are errors of some sort. Dropped packets, for example. Streaming protocols tend to obsess about the dropped packet, trying again and again to get that packet. If the source of the stream isn't paying much attention, or if the repeated packets are bad too, the bit rate drops significantly. Errors can be introduced by a loaded processor, bad cables, radio interference either on cables or wifi, or a number of other things.

You can see network errors by using 'ifconfig' on the command line. It lists your interfaces and statistics about each one. This is an obsolete command but I'm not sure what the new command is to replace it.

---

### Post by tomhsiung on 2018-09-21
I suspect that my 1000 Mbps network cards use auto 10/100/1000 Mbps switching. How to make sure about that?

It seems that when the total data to transfer is huge, the speed could reach 1000 Mbps.

Tom

---

### Post by 1clue on 2018-09-21
My local box with Intel nics, the nics aren't that new. But they have color codes for what speed they sync at.

If you have a single huge data stream, or some really large files, then your speed + overhead can approach wire speed. There will be a pause between files which will bring it down some.

If you have an application where two systems communicate directly only to each other, it's sometimes possible to drop the tcp/ip stack entirely and use pure ethernet for the NICs between. That can speed up a little bit at gigabit speeds, but usually I see that sort of thing at higher speeds, like with a SAN and 10gbps nics for example. The faster the NIC the more the overhead trashes performance and the more fantastic your switches and routers have to be in order to get anything like advertised speed.

---

### Post by 1clue on 2018-09-21
A common trick for people who do large transfers in their LAN is to enable jumbo frames. The bigger the frame, the smaller the header is with respect to the total amount of data sent. They'll also disable IPV6 because the -6 packets are slightly larger than -4 packets. IMO disabling ipv6 is a little bit ridiculous but jumbo frames can be helpful if their drawbacks don't bother you.

---

### Post by 1clue on 2018-09-21
What CPU are you using? And is there a switch involved somewhere that may be slowing you down? Cheap switches tend to have issues especially under load. And don't forget that the other end of the pipe is also part of the equation. What are you connecting to?

---

### Post by tomhsiung on 2018-09-22
End 1:
i5 8400
H370N WiFi
Kingston DDR4 4GB x 2
Ubuntu 18.04 Desktop

End 2:
i7 4790k
Z97X-UD3H
Kingston DDR3 1866 8GB x 2
RX 580 8GB
macOS Mojave Public Beta

Two ends are in a same subnet via TP-Link SG1005P

Tom

---

### Post by 1clue on 2018-09-22
Are you using PoE at all? If so that can cause issues. I've never used it so I can't help with that, but AFAIK there are 3 different variants of PoE, and at least one of those gets a max of 100mbps throughput. As you're telling us gigabit speeds for at least part of the transfer, I assume you're not using those.

When you type 'ifconfig' do you get any errors listed on NICs involved in the slowness?

---

### Post by tomhsiung on 2018-09-23
Yes, I my switch supports PoE.

---

### Post by 1clue on 2018-09-23
I know your switch supports it. Are you using it? Is the switch actually set up to supply it? That's 2 different questions. You don't necessarily need to tell me either answer, but you need to be sure that PoE isn't interfering with your bandwidth. There's a ton of docs online on how to do that.

---

### Post by tomhsiung on 2018-09-24
Hi, Clue

I think I don't use the PoE function, as all devices connected to the PoE switch are powered by themselves instead of the PoE switch. I think I cannot control whether on/off of the PoE function of the switch.

---

### Post by 1clue on 2018-09-24
The only other thing I can think is to look at your error rate right after one of these slow transfers. It won't show anything if you've rebooted since then, but during or after a slow transfer like that you can check for dropped packets or other errors using 'ifconfig' on the command line.

You could also check your system logs for issues related to slowness. Not sure where they would show up though, as I haven't had that type of thing for a long time now.

---

### Post by tomhsiung on 2018-09-30
Now it seems to be OK.

---

