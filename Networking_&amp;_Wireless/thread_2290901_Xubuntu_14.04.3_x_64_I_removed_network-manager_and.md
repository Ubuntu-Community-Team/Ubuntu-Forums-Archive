---
title: "Xubuntu 14.04.3 x 64: I removed network-manager and network-manager-gnome"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by r102 on 2015-08-16
Hello. I just made a mistake, and now i want to repair it. I used this command sudo apt-get remove network-manager network-manager-gnome, and obviously now i have no internet connection. What are the options that i have to access the internet again? 

I found a solution somewhere, but i don't know how to apply it. It was: 
Step #1 = Boot an ubuntu livecd in "try without installing". (Make sure you are connected to the internet.)

Step #2 = In terminal type "sudo mount --bind /dev /chrootlocation/dev". (you will need to replace "chrootlocation" with the appropriate location of your ubuntu install, typically the label of the partition it's installed on. The partition must also be mounted so that you can access it.)

Step #3 = In terminal type "sudo mount --bind /proc /chrootlocation/proc".

Step #4 = In terminal type "sudo mount --bind /sys /chrootlocation/sys".

Step #5 = In terminal type "sudo cp /etc/resolv.conf /chrootlocation/etc/resolv.conf".

Step #6 = In terminal type "sudo chroot /chrootlocation".

Step #7 = In terminal type "sudo apt-get update". (If you don't you'll likely get an unable to connect error.)

Step #8 = In terminal type "sudo apt-get install network-manager".

Step #9 = In terminal type "exit". (This exits you from the chroot)

Step #10 = In terminal type "sudo reboot".

I am stuck at step 1, because i don't know what to write instead of chrootlocation.

I tried to reinstall it with this command: sudo apt-get install --reinstall network-manager, but unfortunately the file was not in my cache anymore

I am using a PC with wired connection only

---

### Post by Bashing-om on 2015-08-16
r102; Hello;

I do not run 'network-manager' and have little experience with the app. It is but an application.
Can you live without it and manage the networking yourself as I do ?
a) There is not wireless connection involved here;
b) This is a stationary system and relocations of the computer is not an issue;

Then we can set this up direct .
post back the outputs of terminal commands:
```

cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
ifconfig

```

Else, others will have to advise on restoring network-manager. 
Elseif I can assist in executing the CHange Root routine. And (RE-)installing the network-manager package. But. I would not know how to configure it.

[INDENT][INDENT][INDENT]we can make options
[/INDENT][/INDENT][/INDENT]

---

### Post by chili555 on 2015-08-16
I'm confident we can manage networking even with wireless in */etc/network/interfaces*. I've subscribed to the thread and let's see what you have.

---

### Post by r102 on 2015-08-16
> **Bashing-om said:**
> r102; Hello;

I do not run 'network-manager' and have little experience with the app. It is but an application.
Can you live without it and manage the networking yourself as I do ?
a) There is not wireless connection involved here;
b) This is a stationary system and relocations of the computer is not an issue;

Then we can set this up direct .
post back the outputs of terminal commands:
```

cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
ifconfig

```

Else, others will have to advise on restoring network-manager. 
Elseif I can assist in executing the CHange Root routine. And (RE-)installing the network-manager package. But. I would not know how to configure it.
[INDENT][INDENT][INDENT]we can make options
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for the quick answer

[http://pastebin.com/WF6gZR4L](http://pastebin.com/WF6gZR4L) here you have the output of that commands. 

For  me is not important to have network manager, i just want to have the  internet connection back, even if this involves installing another  program to do that


> **chili555 said:**
> I'm confident we can manage networking even with wireless in */etc/network/interfaces*. I've subscribed to the thread and let's see what you have.


I do not have the possibility to connect to a wireless network, because i have only a wired connection

---

### Post by chili555 on 2015-08-16
I suggest you change your /etc/network/interfaces to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
 
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
```Get the system to re-read the file and use the changes:```
sudo ifdown eth0 && sudo ifup eth0
```Check:```
ping -c3 www.ubuntu.com
```If you get ping returns, you are all set.

---

### Post by r102 on 2015-08-16
I will try this. But please tell me how can i change /etc/network/interfaces from the content that it has now, to the one that you told me.

I am new to Linux and i don't know yet this kind of things

---

### Post by Bashing-om on 2015-08-16
r102; Well ...

Not 100% sure what you have going on here ;

@chili555 Sure am glad you popped in here :)

To the situation at hand. Let's see what we can do.
1st up is to tell the system you will manage networking. Do this by editing the file " /etc/NetworkManager/NetworkManager.conf " line " managed=false" . Replace the term false with true.

Next let us make the above a true statement and set up the file " /etc/network/interfaces" . There are a couple of ways this should be managed.
Are you set up with your ISP to accept DHCP ?
Or is this a LAN where your router will hand out DHCP ?

Let's take the easier approach for the 2nd instance where DHCP is "auto" .
Edit the file " /etc/network/interfaces " in your favorite text editor to refect:
```

# interfaces(5) file used by ifup(8) and ifdown(8)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
where we change the interface from static to auto ' removing the static addressing and add the line " iface eth0 inet dhcp " for 'auto' detecting . (Now I can accept that we may have to follow the 'static set up' ) So, bear with this attempt.

Ok, changes made. I prefer to reboot the system for the changes to propagate.
upon reboot, is networking picked up and recognized ? No warnings of "waiting an additional 60 seconds for networking " ?

What now results ?
```

ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
Where the 1st ping is to see if you can talk to your router
the 2nd ping is to see if you can reach the internet
and the 3rd to know that name servers are being resolved.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by r102 on 2015-08-16
> **chili555 said:**
> I suggest you change your /etc/network/interfaces to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
 
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
```Get the system to re-read the file and use the changes:```
sudo ifdown eth0 && sudo ifup eth0
```Check:```
ping -c3 www.ubuntu.com
```If you get ping returns, you are all set.

Thanks, it worked, now i can access the internet.


> **Bashing-om said:**
> r102; Well ...

Not 100% sure what you have going on here ;

@chili555 Sure am glad you popped in here :)

To the situation at hand. Let's see what we can do.
1st up is to tell the system you will manage networking. Do this by editing the file " /etc/NetworkManager/NetworkManager.conf " line " managed=false" . Replace the term false with true.

Next let us make the above a true statement and set up the file " /etc/network/interfaces" . There are a couple of ways this should be managed.
Are you set up with your ISP to accept DHCP ?
Or is this a LAN where your router will hand out DHCP ?

Let's take the easier approach for the 2nd instance where DHCP is "auto" .
Edit the file " /etc/network/interfaces " in your favorite text editor to refect:
```

# interfaces(5) file used by ifup(8) and ifdown(8)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
where we change the interface from static to auto ' removing the static addressing and add the line " iface eth0 inet dhcp " for 'auto' detecting . (Now I can accept that we may have to follow the 'static set up' ) So, bear with this attempt.

Ok, changes made. I prefer to reboot the system for the changes to propagate.
upon reboot, is networking picked up and recognized ? No warnings of "waiting an additional 60 seconds for networking " ?

What now results ?
```

ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
Where the 1st ping is to see if you can talk to your router
the 2nd ping is to see if you can reach the internet
and the 3rd to know that name servers are being resolved.
[INDENT][INDENT]hey, it could happen
[/INDENT]
[/INDENT]



I was trying to say that i don't know how to edit that file, because i need root access. But i tried sudo leafpad /etc/network/interfaces, i edited the file like chili555 said and it worked. Before that i knew that i could access the router, because in my browser i could access 192.168.0.1

Now, my question is how can manually set up an ip, or change network settings, if i don't have network manager? I know that i can install it via terminal, but what's the point of installing programs if i can do things without them?

---

### Post by Bashing-om on 2015-08-16
r102; Heyhey !

Great that chili555 has ya up and running ! That works too ! - The proof is in the pudding -

> 
Now, my question is how can manually set up an ip, or change network settings, if i don't have network manager? I know that i can install it via terminal, but what's the point of installing programs if i can do things without them?


"what's the point of installing programs if i can do things without them?" -> none ! If you do not have the need, why suffer the overhead ? As your networking is static, there is no need for a 'network-manager. .

As to "manually set up an ip, or change network settings " you just did it, now you know how.

[INDENT][INDENT]as in all things
[INDENT][INDENT][INDENT]a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r102 on 2015-08-16
O, right, by editing interfaces. I hope that i will not forget this in the future.

Thank you both very much for your help.

---

### Post by Bashing-om on 2015-08-16
r102; K 

" in the future" -> We are always here to help, guide and assist.

IF this matter is now concluded, to your satisfaction;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we do something different
[INDENT][INDENT][INDENT]next time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r102 on 2015-08-16
Sure thing.

Thanks again for the support

---

### Post by r102 on 2015-08-31
Hi. Sorry to bother again, but I just connected my SSD to another PC and I cannot access the internet. Here is the outcome of ifconfig: [http://pastebin.com/NRDH7FE8](http://pastebin.com/NRDH7FE8)

I have changed /etc/network/interfaces to:

 [COLOR=#000000][FONT=Ubuntu Mono]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT][/COLOR]
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

When i try the next commands, the outcome is: Network is unreachable
ping -c3[COLOR=#000000][FONT=Ubuntu Mono] 192.168.0.1
[/FONT][/COLOR]ping -c3 8.8.8.8
ping -c3 ubuntu.com

I am connected to the internet through a router.

I am aware that when i installed the linux on the other PC, the drivers were installed for it, so maybe is problem with the driver

---

### Post by chili555 on 2015-08-31
> so maybe is problem with the driverYes, indeed! If there is no 'eth0' in ifconfig, that suggests that the hardware hasn't yet found a driver. Let's see what the hardware is:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by r102 on 2015-08-31
05:09.0 Ethernet Controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)

---

### Post by chili555 on 2015-08-31
The driver for the device is r8169. Let's load it and see if the ethernet comes to life:```
sudo modprobe r8169
```Does eth0 now appear?```
ifconfig
```Will it connect?```
sudo ifdown eth0 && sudo ifup -v eth0
```If so, let's get r8169 to load automatically:```
sudo -i
echo r8169  >>  /etc/modules
exit
```If it is eth1 or some such, we'll amend a file and fix it.

If there is no eth-anything, let's look for clues in the log:```
dmesg | grep -e eth -e r8169
```

---

### Post by r102 on 2015-08-31
[FONT=arial]After [COLOR=#000000]sudo modprobe r8169, ifconfig remains the same, so it will not connect

[/COLOR][/FONT]http://pastebin.com/TdLRG3EF

---

### Post by chili555 on 2015-08-31
And how about the other command?> If there is no eth-anything, let's look for clues in the log:
```
dmesg | grep -e eth -e r8169
```

---

### Post by r102 on 2015-08-31
Sorry, I didn't see that command. I manually copied it because i don't have my flash drive here to copy it directly from the pc with installed Linux

[http://pastebin.com/N7FcwLYK](http://pastebin.com/N7FcwLYK)

---

### Post by chili555 on 2015-08-31
> systemd-udevd[340]: renamed network interface eth0 to eth1This may be a clue. Please do:```
gksudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the file to read:```
# interfaces(5) file used by ifup(8) and ifdown(8)
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
```Proofread carefully, save and close the text editor. Reboot.

Any improvement? If not, again let us see:```
dmesg | grep -e eth -e r8169
```And also:```
ls /lib/firmware/rtl_nic 
```

---

### Post by r102 on 2015-09-01
Before I make more changes, I want to say that I brought this SSD from my home pc to my office PC, to increase the speed, and I will use it every day in both places. It would be wise to back up my files that I will modify, because if I will change something and I will have internet conection at work, maybe I will not have at home, and vice-versa. If I will run some commands that you tell me, please inform me when i need to backup some files.

Until now I only backed up /etc/network/interfaces

[http://pastebin.com/p3Fsdhcb](http://pastebin.com/p3Fsdhcb)

---

### Post by chili555 on 2015-09-01
When the SSD is in computer #1, udev associates a hardware address, that is MAC address, with a driver and an interface. If it's the first device, it is eth0, the second eth1, etc. These are stored in a file, /etc/udev/rules.d/70-persistent-net.rules. Here is a redacted sample from my machine:```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:de:f1:3e:b2:a4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4239 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:94:6b:99:55:a0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:b5:c2:12:0f:20", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```As you can see, udev associated the device xx:de:f1:3e:b2:a4 as eth0.

Now, you remove the SSD and place it in computer #2. udev no longer sees the original device; in my example, xx:de:f1:3e:b2:a4. It sees the device in computer #2, perhaps xx:de:f1:3e:b2:b5 or some such. Since eth0 is already reserved, it assigns eth1, as you see in the log snippet you posted.

All I suggested you do is change /etc/network/interfaces to manage eth1 instead of eth0. We can always change it back if needed. 

It would be possible to create a script to check to see which device is present on boot and activate eth0 or eth1 as needed. That is well beyond my experience and skill level. Moreover, it already exists! I suspect it will be done automatically in Network Manager.

You could also issue a command in the terminal every time you boot. If in computer #1:```
sudo ifup eth0
```And in computer #2:```
sudo ifup eth1
```You could also drop a command into /etc/rc.local to regenerate udev rules at every boot, assuring that eth0 is always the relevant interface.

These seem like increasingly complex band-aids to avoid the perfectly workable NM.

If it were me, I'd either reinstall NM or buy a second drive.

---

### Post by r102 on 2015-09-01
Ok, sudo ifup eth1 resolved it, now i can access the internet.

It would be better to install network manager? It is uninstalled, this is why I opened this thread in the first place.

---

### Post by chili555 on 2015-09-01
Why did you remove it in the first place? It's always better to fix the underlying issue than to saw off your arm!

---

### Post by r102 on 2015-09-01
I wanted to set up manually my ip, and some other settings, and I ended up removing it. I will install it back, in case I will use this hard drive on another PC too, to avoid other problems

---

### Post by chili555 on 2015-09-01
Static IP addresses, custom DNS nameservers, etc. are very easy in NM.

---

### Post by r102 on 2015-09-02
Yes, I saw that after the mistake I have made :D. 

Thanks for your help

---

### Post by r102 on 2015-10-06
Hi. I have some problems again, I will write here, but if somebody tell me, I will open a new thread. I tried Firefix and Opera, and in both of them the pages are loaded slowly. Thunderbird works fine, the emails are downloaded and loaded normally. Here are some results for ping 192.168.0.1

64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.509 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.452 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.504 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.493 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.472 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.489 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.658 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.462 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.465 ms

And here for ping [www.google.com](www.google.com)

64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=303 ttl=54 time=32.2 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=304 ttl=54 time=33.1 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=305 ttl=54 time=31.6 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=306 ttl=54 time=30.4 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=307 ttl=54 time=30.6 ms
64 bytes from fra02s27-in-f17.1e100.net (173.194.116.113): icmp_seq=308 ttl=54 time=31.1 ms

I don't know if this is relevant, but is the first thing that bumped in my mind

---

### Post by chili555 on 2015-10-06
I think this is an entirely different problem that the title of this thread and I recommend that you start a new thread.

---

