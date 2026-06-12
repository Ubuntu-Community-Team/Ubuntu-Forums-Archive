---
title: "Flushed network settings"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by Luddite Savant on 2014-03-06
Hi, I've had some problems with my network configuration, made some changes which didn't work and decided to reset it. Unfortunately I chose the wrong way to do this and have flushed my network settings (using command flush). I'm now unable to access wired connection or wireless at home and haven't found a way to fix this. Hence asking here. Don't know the actual command I ran as I took it from elsewhere on the net and can't locate it anymore.

I thought I'd be ok just reinstalling ubuntu 12.04 but when I load this up it makes no difference as my internet connection is still showing as disconnected.

Unfortunately I'm not able to easily copy paste terminal outputs as I'm having to type this at my work where Ihave an internet connection, but if someone can let me know what info would be useful to diagnose this & get my connection back on-line I'll get it.
Meantime I've printed out a load of documentation on Linux networking issues & commands and will try working through this, but I'm rather new to command line stuff & not great on networks/ips/etc so any advice or assistance would be greatly appreciated.

If it helps I'm on Ubuntu 12.04

---

### Post by Hadaka on 2014-03-06
hi, i'm not seeing any thing on my end 12.04 ubuntu for the
flush command, I used to use that and also chomp and splat
back in the good ole days. Let's take a look and see if stuff
is showing like it should. please post the output of.
```
lspci -nn | egrep '0200|0280'
```
im guessing you have NO internet access on this machine at this point?
just for grins.please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot and see if your ethernet comes to life...thanks.

---

### Post by Luddite Savant on 2014-03-07
I am borrowing a laptop tonight so should be able to post output for this later tonight or tommorrow.

---

### Post by Luddite Savant on 2014-03-09
I've now managed to run these, still no luck getting online.
Output from ```
lspci -nn | egrep '0200|0280'


```

is 
```
03:00.0 Ethernet controller [0222]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] 9rev 06)
```

For ```
sudo apt-get remove --purge bcmwl-kernel-source
``` it gives:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
```

I also thought it might help to run ifconfig & it gives the following:
```
lo   Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:192 errors:0 dropped:0 overruns:0 frame:0
TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14512 14.5 KB) TX bytes:14512 (14.5 KB)
``` 

You'll note there's no eth0 coming up. That may in part be due to the /etc/network/interfaces settings I set a bit earlier while trying to fix things from some other online guides. Content of interfaces is:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255
dns-nameservers 192.168.0.1
```

Hope all this is helpful, I've had to print out the outputs and manually type them in here as I wasn't able to get the laptop as I'd thought.

---

### Post by Hadaka on 2014-03-09
hi, please edit your /etc/network file to look like this..
```
auto lo
iface lo inet loopback
```
just comment out the other lines...you only
need the first 2...boot and report back.
thank.

---

### Post by Luddite Savant on 2014-03-12
I've now done that an it's made some difference. eth0 is now showing up and the little network icon has changed to two arrows in opposite directions rather than an upside down empty triangle. That said I'm still not able to connect to the internet as it keeps coming up with server not found when I try to connect to a web page.

My Ifconfig is now showing:
```

eth0   Link encap:Ethernet HWaddr 90:2b:34:a0:4a:55
inet addr:192.168.0.4 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::922b:34ff:fea0:4a55/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1157 errors:0 dropped:0 overruns:0 frame:0
TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:92418 (92.4 KB) TX bytes:101697 (101.6 KB)
Interrupt:45 Base address:0xc000

lo   Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2307 errors:0 dropped:0 overruns:0 frame:0
TX packets:2307 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:151186 (151.1 KB) TX bytes:151186 (151.1 KB)
```

Not sure what the issue is now, think it might be my settings, changing the /etc/network/interfaces has made an improvement though, now just got to set it up so it can connect to the server.

---

### Post by Luddite Savant on 2014-03-18
No idea what's going on with my computer now, the GIU network settings show it as connected, with 100Mb/s, pinging computer works ok but I'm unable to connect to any webpage or to e-mail server. Firefox says unable to connect ot server but I'm not able to diagnose what the issue is.

---

### Post by Hadaka on 2014-03-18
hi,please do..
```
sudo iwlist eth0 scan
rfkill list all
ifconfig
```
thanks.

---

### Post by Luddite Savant on 2014-03-18
I've run that now :

```
sudo iwlist eth0 scan
```
```
eth0 interface doesn't support scanning
```

```
rfkill list all
```
no output, nothing happens
ifconfig

```
Link encap:Ethernet HWaddr 90:2b:34:a0:4a:55
inet addr: 192.168.0.3 Bcast:192.169.0.255 Mask:255.255.255.0
Inet6 addr: fe80::922b:34ff:fea0:4a55/64 Scope:link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0 KB) TX bytes:8936 (8.9 KB)
Interrupt:45 Base address:0xc000

lo   Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:3192 errors:0 dropped:0 overruns:0 frame:0
TX packets:3192 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:210240 (210.2 KB) TX bytes:210240 (210.2 KB)

```

---

### Post by Hadaka on 2014-03-18
is this the command you used?
2
**Enter the DNS flush command.** In the terminal, enter[COLOR=#0000ff]...->[/COLOR] /etc/init.d/nscd <-...restart and press Enter. This will flush your DNS.
or did you type the actual word "flush" ??  if so was that done in windows???

---

### Post by Luddite Savant on 2014-03-19
It might have been that, I think there was an init in there along with / can't really remember though and I'd thought there was the actual word flush, may just've been in the instructions though. It definitely wasn't done on windows though, it was on ubuntu in the terminal.

---

### Post by Hadaka on 2014-03-19
perhaps one of these?
```
 sudo /etc/init.d/networking restart
sudo /etc/init.d/dns-clean start
```
If all you were doing was clearingyour DNS
data..it shouldnt have borked your machine.
please do..and post
```
cat /etc/network/interfaces
```
also
power down the computer,then the router/modem
power up the modem after a 5 min rest...then the computer.
any changes?

---

### Post by Luddite Savant on 2014-03-19
I've already tried powering down the computer & the router, I've even reset & rebooted the router but to no effect. 
I'll try cat when I get home.

---

### Post by Luddite Savant on 2014-03-20
```
cat /etc/network/interfaces
```
shows
```
auto lo
iface lo inet loopback
```

which is what I'd set it to to get it to start recognising eth0 again.
The power down of computer & router hasn't caused any changes, still can't access websites or other servers.

---

### Post by Luddite Savant on 2014-03-24
I've tried using a different router now and a bootable cd but I still get the unable to connect to server message.

---

### Post by chili555 on 2014-03-24
I think Hadaka and I would like to see:```
route -n
nm-tool
```We now return you to your regularly scheduled guru!

---

### Post by Luddite Savant on 2014-03-25
Ha, Don't mind which guru helps me out, I'm just glad for the help.

I've run```
route -n
nm-tool

``` and the results are

```
Route –n
Kernel IP routing table
Destination        Gateway              Genmask             Flags         Metric          Ref         Use        Iface
0.0.0.0           192.168.0.1         0.0.0.0                   UG          0              0              0              eth0
169.254.0.0         0.0.0.0                   255.255.0.0         U             1000       0              0              eth0
192.168.0.0         0.0.0.0                   255.255.255.0     U             1              0              0              eth0
 
Nm-tool
 
NetworkManager Tool
 
State: connected (global)
 
-Device:eth0 [Wired connection 1]---------------------------------------
Type:                     Wired
Driver:                  r8169
State:                    connected
Default:                               yes
HW Address:      90:2B:34:A0:4A:55
 
Capabilities:
Carrier Detect:  yes
Speed:                  100 Mb/s
 
Wired Properties
Carrier:                 on
 
IPv4 Settings:
Address:              192.168.0.3
Prefix:                  24 (255.255.255.0)
Gateway:             192.168.0.1

```

Formatting is a little out of sorts as I wasn't able to copy & paste, but that's what's coming up.

---

### Post by chili555 on 2014-03-25
@Hadaka-- No DNS?? Hmmm.

---

### Post by Hadaka on 2014-03-25
hi, chili555 is correct, your nm-tool report shoud
have shown the dns in the next field display. Looks
like the command you used...worked.Let's use network manager to fix it.
click your antenna symbol (upper right corner)
edit your wireless connection. set Ipv4 to look like the attached.
8.8.8.8,8.8.4.4 is google.  thanks chili555
see next post for attached...sorry

---

### Post by Hadaka on 2014-03-25
visual aid

[ATTACH=CONFIG]251455[/ATTACH]

---

### Post by Luddite Savant on 2014-03-25
Thanks, i'll give that a try but i'll be away from my computer for the next day so it'll need to wait till i get back.

---

### Post by Luddite Savant on 2014-03-27
I've tried 8.8.8.8,8.8.4.4 - still can't find the server but it's taking a lot longer looking before it comes up with the 'can't find server' message.
I'll try and find out what my DNS settings should be from my ISP and see if that makes any difference.

---

### Post by Luddite Savant on 2014-03-27
Whoo Hoo I'm back online.
I called to find out the DNS settings for my machine and we tries a few diferent ones, nothing worked, after a while we realised that the router password & username I was logging into the server with wasn't accurate. In trying to fix things a while ago I'd reset the router to factory settings and it'd been wiped. 
It's fixed now & DNS is up,

Thank you guys for all your help

---

### Post by Iowan on 2014-03-27
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by Hadaka on 2014-03-27
Glad you are up and running...
please mark your thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

