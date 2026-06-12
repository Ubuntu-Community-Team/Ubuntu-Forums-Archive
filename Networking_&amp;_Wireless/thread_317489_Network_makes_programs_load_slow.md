---
title: "Network makes programs load slow"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by LucidTaZ on 2006-12-12
Heya,

Whenever I try to run certain programs (Gnome terminal, Gweled, gnome-system-monitor (pressing Ctrl-alt-del), AmaroK, Firefox, and many more), they take like 15 seconds to startup. Other programs like OpenTTD (a game) run immediately.

BUT!

When I pull the network cable out of my pc, the problem is gone. I disabled wireless (via ndiswrapper, just installed it all) to check this. So I only have one cabled connection left (and a loopback device)

When I put the cable back in the slow loading returns.

Can anyone help me out on this? I'm running Ubuntu 6.10 Edgy on an Acer Aspire 3613WLMi laptop.

---

### Post by adaptr on 2006-12-12
It is possible that your DNS times out, or there may be another network-related issue.
If you post the output of
```
cat /etc/resolv.conf
route -n
ifconfig -a
```
we may be able to help you further.

---

### Post by LucidTaZ on 2006-12-12
Thank you for your reply. Here are the results:
I might add that my internet works correctly. Manually set IP of 10.0.0.5, subnetmask: 255.0.0.0, gateway: 10.0.0.2

cat /etc/resolv.conf
```
nameserver 10.0.0.2
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:E9:1F:D8  
          inet addr:10.0.0.5  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:e4ff:fee9:1fd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:575376 (561.8 KiB)  TX bytes:202409 (197.6 KiB)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by adaptr on 2006-12-12
> **LucidTaZ said:**
> Thank you for your reply. Here are the results:
I might add that my internet works correctly.
Erm.. how do you *know* this ?

>  Manually set IP of 10.0.0.5, subnetmask: 255.0.0.0, gateway: 10.0.0.2
Awk! 
You don't really want to use a 24-bit network with a potential 16 million hosts on a home LAN.
Use, say, 10.1.1.x and a netmask of 255.255.255.0 instead.

> eth0      Link encap:Ethernet  HWaddr 00:0A:E4:E9:1F:D8  
          inet addr:10.0.0.5  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:e4ff:fee9:1fd8/64 Scope:Link
I see that you have an IPv6 address assigned.
Do you need one ?
If not, I'd remove it, since your router probably won't understand any of it.

But none of the above seems particularly problematic, or a certain reason why some programs start slowly.
I assume you have checked the programs affected and they are always the same ones, i.e. the problem is reproducible ?

---

### Post by LucidTaZ on 2006-12-12
By saying that my internet works correctly, I actually meant that I can browse without problems. Sorry on that one.

Ok I will change my IP settings. How do I remove the IPv6 part?

The problem is perfectly reproducable. It happens with those programs stated above, and probably many more that I haven't tried.

---

### Post by LucidTaZ on 2006-12-13
I have tried to run some programs on my system. The programs are chosen randomly.

**Programs that show up after about 15 seconds:**
[LIST]
[*]Gedit
[*]gnome-system-monitor
[*]KSokoban
[*]Gweled
[*]gnome-terminal
[*]Firefox
[*]AmaroK
[*]network-admin
[*]Alacarte menu layout editor
[*]Gnome minesweeper
[*]Gnome calculator
[/LIST]

**Programs that show up immediately:**
[LIST]
[*]Update Manager
[*]OpenTTD (A game called Transport Tycoon)
[*]gftp
[*]The GIMP
[*]Eclipse
[*]Synaptic Package Manager
[*]Gnome Partition Editor (GParted)
[/LIST]

**Programs that show errors:**
[LIST]
[*]VMWare: My Windows XP virtual machine won't start when I try to turn it on.
[/LIST]

I hope someone can perhaps detect similarities in these programs that causes them to behave this way. Any help is appreciated. :)

---

### Post by LucidTaZ on 2006-12-14
Does anyone have an idea? I'm really desperate cause it works very frustrating. :(

Any help is appreciated. :)

---

### Post by adaptr on 2006-12-14
Here's something I have noticed the last few days:
With VMWare installed, the VMNET virtual interfaces completely fsck up my DHCP settings, and perhaps more network issues were caused by it, but I didn't hang around to find out...

I threw it off yesterday because I was getting fed up with it, and all of my networking problems just went away...

---

### Post by LucidTaZ on 2006-12-14
I had VMWare installed too. I uninstalled it but the problem remained unchanged.

Thanks for your post. :)

---

### Post by LucidTaZ on 2006-12-20
Please... Anyone? :-k

---

### Post by LucidTaZ on 2007-01-08
Can anyone help me with this please?

Thanks in advance.

[add] I have attached a screenshot from the system-monitor. The bottom graph shows network activity while starting programs. The first two groups of spikes are from starting gnome-terminals. The last group of spikes is from pressing alt-printscreen which starts the screenshot program.

---

### Post by LucidTaZ on 2007-01-10
I have come to a discovery. When I am at the network of a friend of mine, everything works fine. The network is wired, as it is at my house. Both systems work with a router and DHCP. But now I'm stuck... What could be the problem?

---

### Post by bobbob1016 on 2007-01-11
I don't know if this will help, or why it works, but it does help on a lot of the computers I try it on.
Open a terminal:
Applications -> Accessories -> Terminal
(Not sure where the Terminal or Konsole is on Kubuntu)
Then type EXACTLY (without the quotes):
"sudo cp /etc/hosts /etc/hosts-backup"    --------This step makes a backup of the file
"sudo gedit /etc/hosts"                          --------This step opens the file for editing
I think the command on Kubuntu would be something like:
"sudo kate /etc/hosts"

Then move the part after 127.0.1.1, which is your computer's name, to the end of the line above it which should be 127.0.0.1 and put a "#" without quotes infront of the 127.0.1.1 line.  It might help, and it might not.  Save the file, overwrite the file if it says it will overwrite a file.

Reboot your computer.

If it breaks something, which I have yet to see, simply get to a terminal, and type EXACTLY (without quotes):
"sudo cp /etc/hosts-backup /etc/hosts"
If it says that it would overwrite an existing file, tell it to overwrite it.  Reboot your computer.

---

### Post by LucidTaZ on 2007-01-11
Thaks for your reply.

I have no entry 127.0.1.1 in the file. This is what it looks like.

> 127.0.0.1 localhost.localdomain localhost linuxtaz.domain.com
10.0.0.8 linuxtaz.domain.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

The 10.0.0.8 is from a previous "Fixed ip" setting. I am using DHCP and connect through 10.0.0.5
My ip at the friend's network was 10.0.0.7 (DHCP assigned) and it worked perfectly too.

I think I might have typed linuxtaz.domain.com in a network wizard a long time ago. I can't really remember it but I think it's not correct.

I tried editing the file and replaced the first two lines with this:
> 127.0.0.1 localhost.localdomain localhost

But the problem remained.

---

### Post by LucidTaZ on 2007-01-17
Does anyone have an idea? I searched everywhere but can't find it. I think reinstalling would work but then I have to reinstall my programs too, right?

---

### Post by LucidTaZ on 2007-01-18
Ok I fixed it now. This is what my new hosts file looks like.
linuxtaz is the name of this computer

> 127.0.0.1 localhost
127.0.1.1 linuxtaz

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by chayen on 2007-04-28
I was having this same problem, but in gentoo.  I added my computers hostname to /etc/resolv.conf after localhost and it went away.  Seems like a problem with the way networkmanager sets up your networking.

---

### Post by carguelles on 2007-12-16
I have the same problem. When the network cable is unplug - no internet - then the computer goes really slow and the programs take 15sec to load. But once i plug the cable and the internet starts working everything works just fine. I am using Gutsy Gibbon.

---

### Post by dsolanolx on 2008-02-29
Use "nm-applet" to create one more configuration connection, delete the gateway IP from it, so when you want work disconnected from the net, you activate that connection in your panel.

I'm use VirtualBox for run Windows XP, and had the same problem, and that work for my.

Sorry for my english

---

### Post by Akingboy on 2008-06-30
I wanna thank the topic maker and others replying here because I got my big problem off now.

Since it might be hard for someone to do this I explain better.
Your problem should be the same with LucidTaz. Programs start slow but not all.

This is how I got it at last working on my 8.04 or whatever is the latest 30.6.2008 and I take no responsibility if something goes wrong by following my advice but this is I got it working. I tell how I did step by step. Things might be little different on your machine so bevare. Common sense is preferable to be used:

**1.0**
Leftclick your network picture in the upper-rightcorner and press manual settings. Press open locks (or unlock or whatever it is in english) and type your password. This just unlocks some features so that we can modify them.
**1.1**
I have my wired connection on roaming mode which seems to work for me fine. I think it can be something else too if you just know how to configure it! I don't even know what is point-to-point so lets leave it be if you have it there.
**1.2**
Go to general information tab and first line you see is your computer name or whatever. This is good to remember (mine was aki-u). Second line you have something only if you have added afaik and I don't even know what it does. But I've noticed that better not change it or these problems occur. So leave it blank.
**1.3**
Now this is tricky. Go tab DNS. And here I saw a flaw on my machine! It had my DNS address 192.168.0.100 which was WRONG for ME (my correct one was 192.168.254.254 but you gotta check whats your own). I checked from other machine in my network (with os: windows xp) which is correct dns with commandline (like terminal). (To check it press Start -> Run -> type "cmd" without quotes -> type "ipconfig /all" in to the commandline box without quotes again and there you can see it!)
Copy that DNS to your ubuntu machines DNS part. Remove the wrong if there is wrong and add your own or modify it or something to have the correct line.
I don't know what you guys should have in the next box "searched areanames" or something like that :P but I have "domain.invalid" and I think you can check this the same way you checked your DNS.
**1.4**
Now to the Domainnames! (or what is the last tabs name in english? Anyway.) Here you see list of stuff. What you should have is 2 first lines like I had:
> 127.0.0.1 localhost
127.0.1.1 aki-u
blaablaa some stuff about something I know nothing of but don't worry they aren't crucial. Leave them there we are only intrested about the first lines
Atleast you should have something similar. Ofc you will have your own computer name but idea is that.
This is how you need to change it:
-Remove the 127.0.1.1.
-change the first line 127.0.0.1 localhost TO 127.0.0.1 localhost [yourComputerName]
As an EXAMPLE what I have:
> 127.0.0.1 localhost aki-u
Once those are changed you better check if they really did change. Im not sure if the 2.0 part is necessary but better check these for sure.

**2.0**
In terminal type:
sudo gedit /etc/hosts

it might take 3-10 seconds for it to open. Also your password might be asked.

Once the file is open check that the information there is correct compared to changes we did in part 1.4
The main cause of my problems was that there was the line:
127.0.1.1 aki-u.DATIS
and that .DATIS was leftover because I changed that "areaname" whatever I told earlier not to change or add text there. I had added that .DATIS to see our xp computer in the network area but it wasn't actually necessary so I removed it but it wasn't removed in the hosts file! So if remove it too if you got it there. (You can ignore this but I think the removal of 127.0.1.1 isn't necessary but I got it working by removing it and adding the aki-u without the .DATIS after the 127.0.0.1 localhost)
I provided picture how I had it if you wanna be sure.
[http://www.mediafire.com/?4gzgsw1w0nu](http://www.mediafire.com/?4gzgsw1w0nu)

**2.1**
now type in terminal:
sudo gedit /etc/resolv.conf

again might take a while and asks maybe your password too.
Once the file is open you should see 2 lines of text.
I have this:

search domain.invalid
nameserver 192.168.254.254

so you should check are the lines same as the changes we made in part 1.3
I took a picture of it again:
[http://www.mediafire.com/?9jximxgmltj](http://www.mediafire.com/?9jximxgmltj)

If everything matches you should be good to go. But this is how it worked for me so I can't tell for sure it works for too. Just wanna add this message here so that others can see how I solved this problem.
If something doesn't match after those changes make them match.

I did so that I changed it from the network settings and then checked did it change in the text files. And after everything was equal my computer started working normally.
Problem was that the text files and the settings didn't match together.

---

### Post by LucidTaZ on 2008-06-30
> **Akingboy said:**
> I wanna thank the topic maker and others replying here because I got my big problem off now.

Since it might be hard for someone to do this I explain better.
Your problem should be the same with LucidTaz. Programs start slow but not all.

This is how I got it at last working on my 8.04 or whatever is the latest 30.6.2008 and I take no responsibility if something goes wrong by following my advice but this is I got it working. I tell how I did step by step. Things might be little different on your machine so bevare. Common sense is preferable to be used:

**1.0**
Leftclick your network picture in the upper-rightcorner and press manual settings. Press open locks (or unlock or whatever it is in english) and type your password. This just unlocks some features so that we can modify them.
**1.1**
I have my wired connection on roaming mode which seems to work for me fine. I think it can be something else too if you just know how to configure it! I don't even know what is point-to-point so lets leave it be if you have it there.
**1.2**
Go to general information tab and first line you see is your computer name or whatever. This is good to remember (mine was aki-u). Second line you have something only if you have added afaik and I don't even know what it does. But I've noticed that better not change it or these problems occur. So leave it blank.
**1.3**
Now this is tricky. Go tab DNS. And here I saw a flaw on my machine! It had my DNS address 192.168.0.100 which was WRONG for ME (my correct one was 192.168.254.254 but you gotta check whats your own). I checked from other machine in my network (with os: windows xp) which is correct dns with commandline (like terminal). (To check it press Start -> Run -> type "cmd" without quotes -> type "ipconfig /all" in to the commandline box without quotes again and there you can see it!)
Copy that DNS to your ubuntu machines DNS part. Remove the wrong if there is wrong and add your own or modify it or something to have the correct line.
I don't know what you guys should have in the next box "searched areanames" or something like that :P but I have "domain.invalid" and I think you can check this the same way you checked your DNS.
**1.4**
Now to the Domainnames! (or what is the last tabs name in english? Anyway.) Here you see list of stuff. What you should have is 2 first lines like I had:

Atleast you should have something similar. Ofc you will have your own computer name but idea is that.
This is how you need to change it:
-Remove the 127.0.1.1.
-change the first line 127.0.0.1 localhost TO 127.0.0.1 localhost [yourComputerName]
As an EXAMPLE what I have:

Once those are changed you better check if they really did change. Im not sure if the 2.0 part is necessary but better check these for sure.

**2.0**
In terminal type:
sudo gedit /etc/hosts

it might take 3-10 seconds for it to open. Also your password might be asked.

Once the file is open check that the information there is correct compared to changes we did in part 1.4
The main cause of my problems was that there was the line:
127.0.1.1 aki-u.DATIS
and that .DATIS was leftover because I changed that "areaname" whatever I told earlier not to change or add text there. I had added that .DATIS to see our xp computer in the network area but it wasn't actually necessary so I removed it but it wasn't removed in the hosts file! So if remove it too if you got it there. (You can ignore this but I think the removal of 127.0.1.1 isn't necessary but I got it working by removing it and adding the aki-u without the .DATIS after the 127.0.0.1 localhost)
I provided picture how I had it if you wanna be sure.
[http://www.mediafire.com/?4gzgsw1w0nu](http://www.mediafire.com/?4gzgsw1w0nu)

**2.1**
now type in terminal:
sudo gedit /etc/resolv.conf

again might take a while and asks maybe your password too.
Once the file is open you should see 2 lines of text.
I have this:

search domain.invalid
nameserver 192.168.254.254

so you should check are the lines same as the changes we made in part 1.3
I took a picture of it again:
[http://www.mediafire.com/?9jximxgmltj](http://www.mediafire.com/?9jximxgmltj)

If everything matches you should be good to go. But this is how it worked for me so I can't tell for sure it works for too. Just wanna add this message here so that others can see how I solved this problem.
If something doesn't match after those changes make them match.

I did so that I changed it from the network settings and then checked did it change in the text files. And after everything was equal my computer started working normally.
Problem was that the text files and the settings didn't match together.

Nice guide. :) Maybe this could be an answer in an FAQ section or something.

---

