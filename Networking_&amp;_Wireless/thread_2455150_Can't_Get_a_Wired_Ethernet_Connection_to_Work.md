---
title: "Can't Get a Wired Ethernet Connection to Work"
date: 2020-12-13
forum: Networking &amp; Wireless
---

### Post by jawson1 on 2020-12-13
Hello, I'm very new to Linux. I am having problems getting my wired ethernet connection to work with a computer I got (model HP EliteDesk 800 G1 SFF). It had windows pre-installed on it, and everything works fine on windows. When I hook an ethernet cable straight from the computer to the router I get internet. But when I boot Ubuntu 20.04.1 from a flash drive, the ethernet connection doesn't work. It just says "Connecting" for a while, then says "Connection Failed" and then tries to connect again, fails, and repeats. I have tried reading many different forum posts and suggestions, but can't get anything to work or don't understand what's being said.

If it's any help I tried running different versions of Linux Mint from a flash drive too, and ran into the same problem.

Also, the computer does not have wireless internet connection, so I can't even install any driver updates from the computer because there's no internet! So I'm pretty much at a loss for what to do next, and I really don't want to keep using Windows.

---

### Post by TheFu on 2020-12-13
To be able to help, we need to know 
[LIST=1]
[*]which release you are running,
[*]the exact model of network card and 
[*]the exact driver.  
[/LIST]

From that, we can work backwards.

The release is provided by **lsb_release -a** command. It would be helpful to know which DE, if any, you are using.
There are a few different ways to get the NIC and driver information. The easiest is 
**sudo lshw -C network**
but there's a chicken-egg problem, so the system probably doesn't have lshw installed.
**inxi -Fz** is the next easiest, but it is also the chicken-egg problem. That means we need a built-in way. There are a few, I prefer this command:  
```
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
```
but if you can't copy/paste it, someone new to Linux would probably get the details and spacing wrong. So let's see what
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
```
gets.

Lacking all those working, you'll need to figure out from the motherboard/vendor which exact network card is being used.  Some bleeding edge computers are shipping with network adapters that aren't supported under mainstream Linux versions directly.  That means downloading all sorts of stuff so you can compile and link the needed drivers yourself.  But if the hardware isn't bleeding edge, it is probably just a small config issue of some sort.

BTW, if you have Windows working on the machine, you probably could run Linux/Ubuntu inside a virtual machine and skip all the unsupported hardware issues completely.  For someone new, this is a much safer way to run Linux while you learn some basics. Inside the virtual machine, extremely standard fake-hardware is emulated for the guest OS. The actual hardware doesn't matter thanks to that virtualization layer.

---

### Post by jawson1 on 2020-12-13
Thanks for responding!

1. Release: Ubuntu 20.04.1 LTS (it's the newest version on the Ubuntu website, I just downloaded it yesterday)
2. Network card model: Intel I217-LM
3. Driver: e1000e (I think)


I ran the first line of code and it says:

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
DeviceName: Onboard LAN
Subsystem: Hewlett-Packard Company Ethernet Connection I217-LM
Flags: bus master, fast devsel, latency 0, IRQ 26
Memory at f7c00000 (32-bit, non-prefetchable) [size=128K]
Memory at f7c3d000 (32-bit, non-prefetchable) [size=4K]
I/O ports at f080 [size=32]
Capabilities: <access denied>
Kernel driver in use: e1000e
Kernel modules: e1000e

Yes I typed all that out lol. I typed the second line of code as well and it output the exact same thing.

I would rather not just run Linux in a virtual machine. I'm tired of Windows altogether and all the bloatware/spyware from the factory I can't uninstall. I am just running Ubuntu from a bootable flash drive until I can get it to work correctly, then I'll install it on the hard drive. I know it has a learning curve but I'm down, I just never want to use Windows again.

I tried running the sudo lshw -C network command and that worked. I could type it all out if needed but it's pretty long.

I don't think the computer is bleeding edge. It's several years old, I just bought it refurbished on eBay for a good deal.

---

### Post by CelticWarrior on 2020-12-13
Your card is not new (not even close) and very well supported.
Have you tried rebooting the router?

---

### Post by jawson1 on 2020-12-13
Yes I tried turning the router off and on. I also tried using different CAT5/CAT6 cables I had laying around and that didn't help either.

---

### Post by DuckHook on 2020-12-13
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by starrt on 2020-12-13
HI,
I had the same problem and came across an old thread which helped me.
Go into "Settings-->Advanced Network Configuration".
In the tab for IP4v make sure to select "require IP4v addressing' with the Method as "Automatic".
Go to the IP6v, select the Method as "Disabled" and uncheck "Require IP6v addressing".
See if that works for you.

---

### Post by TheFu on 2020-12-13
No need to type sff, jstredrect te output from cods to files that can be accessed fro Windows or to a flash drive (aka sneaker-net) that can be connected to some other computer, then copy/paste here.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) - basic Linux skills include redirection.

I would not ask someone to type more than 1 line of stuff. If you think that is necessary, there is a better way.

for example,
```
lshw -C network | tee /tmp/stuff
```
Then look to verify that the file contains what you need.

Every process as 3 "files" automatically.  
[LIST=1]
[*]stdin
[*]stdout
[*]stderr
[/LIST]
redrection to/from those is very useful.  stdout from 1 process can be passed as stdin to another or simply redirected to a file as shown above. stderr can be redirected to the same "file" or to a different file. Or sent to nowhere or sent to another process.  We have control over those things.

Probably more an you want or need to know. Simple redrection is useful. Pipelining is useful. the other stuff I have to look up when needed. ;)

---

### Post by jawson1 on 2020-12-13
I did what starrt suggested and nothing changed. I was able to find those settings by doing nm-connection-editor to see some more advanced settings, but nothing there helped.

TheFu, I typed in that line of code and this is what it output. I transferred it from a flash drive, thanks for the tip!:

WARNING: you should run this program as super-user.
  *-network                
       description: Ethernet interface
       product: Ethernet Connection I217-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: f0:92:1c:ef:13:e2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:26 memory:f7c00000-f7c1ffff memory:f7c3d000-f7c3dfff ioport:f080(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



I think I am not a super-user because I am running it off a flash drive. But I don't want to install Ubuntu on the hard drive until I know I can get my internet to work. I hope there is enough information in this output to help. And thank you, I'll read some stuff on using the command line.

---

### Post by TheFu on 2020-12-13
No - you aren't super-user because you 
a) don't need to be
b) didn't use sudo (which is fine); sudo abuse is a bad problem when people are new and haven't yet learned file permissions.

So ... that tells me that it isn't a physical problem and the driver seems fine too.

**_The problem is a configuration issue._**

Follow the steps here, [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking), in the order specified and post the results here.  You can use that redirection tip above to either create different files OR you can append to 1 file with **tee -a**. The -a means to append, not overwrite.
Those steps are testing computer to router, then computer to internet, then computer DNS lookups + internet.  Most people jump to the end and say networking is broke, when it is very likely that just DNS is broke, not networking.

As for easy ways to fix this stuff, someone else will need to help with that, since I don't use GUIs to setup or configure networking. I use text files, but they will need to know what is broke, so that link with steps and the resulting output will clearly show what isn't working.


And please, please, please, when posting commands and output, please use code-tags.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how for this forum. Some of the output just isn't readable without that specific format.

---

### Post by jawson1 on 2020-12-14
I ran some of those and this is what I got:


```
ip addr
```
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f0:92:1c:ef:13:e2 brd ff:ff:ff:ff:ff:ff
    inet6 2603:8001:ba41:1d5:f292:1cff:feef:13e2/64 scope global dynamic mngtmpaddr
       valid_lft 529932sec preferred_lft 529932sec 
```
 
 
```
route -n
```
 
```
Command 'route' not found, but can be installed with:
 
sudo apt install net-tools
```


I am not sure what to make of the first one. There was no IP address in there other than localhost, so I don't see how I can proceed with the next steps.

---

