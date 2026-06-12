---
title: "Newb cant get internet connection to work"
date: 2005-04-03
forum: Networking &amp; Wireless
---

### Post by pown on 2005-04-03
Im a fairly new linux user and today i decieded to try out Ubuntu becouse I dident like the other distros I tried, and i absolutely loved it! I only have one problem though, I cant get my connection to work! When I open firefox and try to visit a site it says it cant be found, I also tried loggin in to msn via Gaim and that dident work either :cry: . I have cable and connect via an ethernet modem and I also have a router as well (a netgear rp614). I have searched other threads but they dident help, I dont understand whats wrong. In Fedora and Red Hat it worked like a charm but I have also tried Debian and mandrake and a few others and in there it dident work. The funny thing is that the update manager tells me that theres new updates available but when I try to download them I get an error messege (cant remember what it said, something about a temporary error connecting to [http://***.***)](http://***.***)). But I guess that something must work becouse otherwise Ubuntu wouldent tell me that theres updates available.
I have also read that a new update causing some dns problems but i tried one of the solutions that was listed in that thread but it dident work ](*,) 

Sorry I cant provide more info :/

Edit: My network card is CNet PRO200

Any help is appriciated!
// pown

---

### Post by arctic on 2005-04-03
hi there.

what you are experiencing is a common problem. read my little howto (it works for other distros, too). it should explain what you need to do. if you still have problems, please report back.
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

good luck :)

---

### Post by pown on 2005-04-03
[QUOTE=arctic]hi there.

what you are experiencing is a common problem. read my little howto (it works for other distros, too). it should explain what you need to do. if you still have problems, please report back.
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

good luck :)[/QUOTE]

Thanks for the quick reply but...

> 1. to open a terminal, ping the apt-get mirrors you have chosen. at the same time, open a new tab and install the following packages as superuser:

1. resolvconf
2. pump
3. dnsmasq

After downloading the files, deactivate your network and write valid DNS-entries into your /etc/resolv.conf file, save and restart your network. Your problems should be fixed now.
 
I cant get it to work becouse I cant download packages, nor do I know how to log in as a super-user ](*,) 

> 2. If you don't want to download new packages, you can fix it manually if you are using an ext2 or ext3 filesystem. open your /etc/resolv.conf and set valid DNS-servers, as above. Now save the file. Lock it with "sudo chattr +i /etc/resolv.conf" from a terminal. This will permanently lock your DNS-values. (to unlock, use chattr -i) 

I cant edit resolv.conf, its protected and I dont know how to open it as root. But I looked in the file and my ISP's DNS servers where there.

> 3. You can alternatively hack your files even more. Run in a root terminal:

echo "net.ipv4.tcp_window_scaling=0">> /etc/sysctl.conf

Now type in the same root terminal the following:

sed -i -e 's/^alias *net-pf-10 *ipv6/alias net-pf-10 off/' /etc/modprobe.d/aliases
Thats the thing I tried, dident help at all.

 ](*,)  ](*,)  ](*,)

---

### Post by arctic on 2005-04-03
okay okay... here we go :D

do the following: right click on your desktop. you will see a menu entry "run terminal". click it. a terminal should pop up. now type:

sudo gedit /etc/resolv.conf

hit enter. now enter the superuser password (= by default the same, you use as first user on the newly installed system)

the editor should come up the the resolv.conf file. now change the default ip address you see there to a VALID dns entry (like e.g. 217.237.149.161, a dns-server located in germany). once you have modified your file, save it and close the editor. now, back at the terminal, type

sudo chattr +i /etc/resolv.conf

now open your browser or synaptic and test if everything works. :)
if not, report back. ;)

edit: 
>  I cant edit resolv.conf, its protected and I dont know how to open it as root. But I looked in the file and my ISP's DNS servers where there. 
one question: which dns-entries do you have in there?

---

### Post by pown on 2005-04-03
[QUOTE=arctic]okay okay... here we go :D

do the following: right click on your desktop. you will see a menu entry "run terminal". click it. a terminal should pop up. now type:

sudo gedit /etc/resolv.conf

hit enter. now enter the superuser password (= by default the same, you use as first user on the newly installed system)

the editor should come up the the resolv.conf file. now change the default ip address you see there to a VALID dns entry (like e.g. 217.237.149.161, a dns-server located in germany). once you have modified your file, save it and close the editor. now, back at the terminal, type

sudo chattr +i /etc/resolv.conf

now open your browser or synaptic and test if everything works. :)
if not, report back. ;)

edit: 

one question: which dns-entries do you have in there?[/QUOTE]
Alright I just tried that, still no luck. Edited the file and ran 
sudo chattr +i /etc/resolv.conf and then logged out and then in. I dont remember the entries exactly I just booted back to Winblows.

---

### Post by Gandalf on 2005-04-03
can you quote please your /etc/network/interfaces?

and also your modem deliver dhcp or static ips???

---

### Post by arctic on 2005-04-03
uh uh... so we will have to start from scratch. first of all: are you connected trough the router or through a modem first? i hope your config is comp to router, then to modem, then to dsl-box.
if you are using a router, it should work the way i described unless you need to activate your modem from within ubuntu. in any case: have you run the network-config tool from the system-menu?
please explain in detail everything you have done so far, which tools you had started etc. and which error messages you got somewhere.
also, here is more information if you are not afraid of reading a bit. ;)
[http://www.yoper.com/yoperwiki/index.php/2.2-pre_Networking](http://www.yoper.com/yoperwiki/index.php/2.2-pre_Networking)

---

### Post by pown on 2005-04-03
> **arctic]uh uh... so we will have to start from scratch. first of all: are you connected trough the router or through a modem first? i hope your config is comp to router, then to modem, then to dsl-box.
if you are using a router, it should work the way i described unless you need to activate your modem from within ubuntu. in any case: have you run the network-config tool from the system-menu?
please explain in detail everything you have done so far, which tools you had started etc. and which error messages you got somewhere.
also, here is more information if you are not afraid of reading a bit.  said:**
> http://www.yoper.com/yoperwiki/index.php/2.2-pre_Networking[/url]
 Alright I dont know if my modem uses DHCP or static ip, I belive its static becouse my Ip address doesnet change. I went to system>administration>network and than changes to static and put in my info and then when I tried  to visit a site Firefox dident display an error messege (blabla cant be found) but the site just timed out.

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]Alright I dont know if my modem uses DHCP or static ip, I belive its static becouse my Ip address doesnet change. I went to system>administration>network and than changes to static and put in my info and then when I tried  to visit a site Firefox dident display an error messege (blabla cant be found) but the site just timed out.[/QUOTE]
 ok quote /etc/network/interface please
sudo gedit /etc/network/interface

---

### Post by pown on 2005-04-03
I couldent save interfaces as a text file on the floppy but it was similar to ipconfig in windows.

   DNS-suffix . : chello.se
  IP-adress . . . . . . . . . . . . : 192.168.0.2
  Netmask . . . . . . . . . . . . . : 255.255.255.0
  Standard-gateway  . . . . . . . . : 192.168.0.1

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]I couldent save interfaces as a text file on the floppy but it was similar to ipconfig in windows.

   DNS-suffix . : chello.se
  IP-adress . . . . . . . . . . . . : 192.168.0.2
  Netmask . . . . . . . . . . . . . : 255.255.255.0
  Standard-gateway  . . . . . . . . : 192.168.0.1[/QUOTE]
 so it's resolving static not DHCP, make sure than you have a line that looks like
```

dns-nameservers XXX.XXX.XXX.XXX YYY.YYY.YYY.YYY

```
where XXX.XXX.XXX.XXX and YYY.YYY.YYY.YYY are often your DNS nameservers but you can also put foreign nameservers, check ipconfig /all on windows to know them

---

### Post by pown on 2005-04-03
I just checked ipconfig /all and it says DHCP is activated :???:

DHCP-server . . . . . . . . . . . : 192.168.0.1
DHCP activated . . . . . . . . . : yes
Auto configuration activated: yes

hmm  :???:

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]I just checked ipconfig /all and it says DHCP is activated :???:

DHCP-server . . . . . . . . . . . : 192.168.0.1
DHCP activated . . . . . . . . . : yes
Auto configuration activated: yes

hmm  :???:[/QUOTE]
 then change your interfaces file
```

sudo cp /etc/network/interfaces /etc/network/interfaces_backup
sudo gedit /etc/network/interfaces &

```

you will find a line like
```

iface eth0 inet static

```

change it to
```

iface eth0 inet dhcp

```

and erase everything after it

run
```

sudo ifdown -a && ifup -a
sudo ifconfig

```
and see if the eth0 is connected

---

### Post by pown on 2005-04-03
Did that and it still doesent work :x And when I tried to reboot Ubuntu froze >.<

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]Did that and it still doesent work :x And when I tried to reboot Ubuntu froze >.<[/QUOTE]
 hmmmmmm... weird
what ifconfig tells you about eth0?

---

### Post by pown on 2005-04-03
[QUOTE=Gandalf]hmmmmmm... weird
what ifconfig tells you about eth0?[/QUOTE]
From what I remember it dident say anything 8-[

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]From what I remember it dident say anything 8-[[/QUOTE]
 then there's a problem with your modem not given the DHCP ip address

---

### Post by pown on 2005-04-03
[QUOTE=Gandalf]then there's a problem with your modem not given the DHCP ip address[/QUOTE]
What can I do to fix that?

---

### Post by arctic on 2005-04-03
check the modem manual, you might find a topic on that in it. otherwise, please post the output of "ifconfig eth0", run in a terminal, in order to verify that your modem does not respond.
also: try to ping first your router (ping 192.168.0.1) from the terminal and after that, try to ping e.g. [www.google.com](www.google.com). no reaction?

---

### Post by pown on 2005-04-03
eth0      Link encap:Ethernet  HWaddr 00:08:A1:12:FE:4A
          inet6 addr: fe80::208:a1ff:fe12:fe4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1784 (1.7 KiB)  TX bytes:2772 (2.7 KiB)
          Interrupt:16 Base address:0xe000

Couldent ping anything though :/
I also found out that my router is the DHCP server if thats any good info.
Thx for your support :)

---

### Post by arctic on 2005-04-03
okay,.. you do not have any ip adress set, so we need to change that. please try to activate your network card in the system menu at you top panel again. and activate is as a lan connection. otherwise, your box cannot connect to your router and get the dns-values from him.

---

### Post by pown on 2005-04-03
Not shure where to find that. But in the network settings it was enabled but it wasent at DHCP I changed that now.

---

### Post by Gandalf on 2005-04-03
[QUOTE=pown]Not shure where to find that. But in the network settings it was enabled but it wasent at DHCP I changed that now.[/QUOTE]
 then try to go back to static, by just reloading the backup file you did
```
sudo cp /etc/network/interfaces_backup /etc/network/interfaces
```

and be sure to put dns-nameservers

after that
```
ifdown -a && ifup -a
```

try to ping
```
ping siemens-mobiles.org
```

if nothing try
```
ping 82.225.70.234
```

try also to 
```
dig siemens-mobiles.org
```
must see A records

and last but not least to verify if the DNS servers that you put in the interfaces are correct
```
dig
```
must see a lot of code, if the output is one/two lines then something is wrong, ubuntu isn't connected to any DNS cache server

---

### Post by pown on 2005-04-03
I have already tried with static, sorry to make you type all that for nothing Gandalf!

---

### Post by Gandalf on 2005-04-03
when using static and you do 
```

dig

```
what is the output?
try it now again, just make a backup if the dhcp one, load the static one and reload the network

---

### Post by arctic on 2005-04-03
ummm gandalf, if his router is configured and used for dhcp, then a static ip won't solve anything unless he changes the router from dhcp to static ip, right?:-k

now... have you been successfull at activating the eth0 device? if yes, please give again the output of "ifconfig eth0" and "ping www.google.com"

whew... this is becoming a long topic indeed :D

edit: uh... and i guess we should stick to one solution at a time. either static or dhcp... so ... first we try gandalfs approach.

---

### Post by Gandalf on 2005-04-03
[QUOTE=arctic]ummm gandalf, if his router is configured and used for dhcp, then a static ip won't solve anything unless he changes the router from dhcp to static ip, right?:-k

now... have you been successfull at activating the eth0 device? if yes, please give again the output of "ifconfig eth0" and "ping www.google.com"

whew... this is becoming a long topic indeed :D

edit: uh... and i guess we should stick to one solution at a time. either static or dhcp... so ... first we try gandalfs approach.[/QUOTE]
 in fact even if the router is DHCP as long as you don't exceed the dhcp range limit you can define it static, no problem with that, but when you define a network a static you MUST also provide your ISP dns servers to have the external DNS cache (ISP or any other DNS cache) if this values are not there, the network will fait to resolve hosts, it will ping 82.225.70.234 but will return unknow host on ping siemens-mobiles.org, see my point why i'm asking him to retry static and quote me dig output?

---

### Post by arctic on 2005-04-03
> see my point why i'm asking him to retry static and quote me dig output?
sure. :D
bfff.. i am tired. will go and get some sleep before work awaits me. good luck to both of you.

---

### Post by Gandalf on 2005-04-03
[QUOTE=arctic]sure. :D
bfff.. i am tired. will go and get some sleep before work awaits me. good luck to both of you.[/QUOTE]
 lol no problem, sweet dreams :D

---

### Post by pown on 2005-04-09
I found out that the routers DHCP adress is 192.168.10, maybe I can set this up and if so where?

---

### Post by ibs on 2005-04-12
I have a very similar problem with Hoary and i think i have tried everything mentioned on this thread and something on other threads also. I think there is something wrong with the DHCP packages in Hoary.

I am almost giving up on using Ubuntu, Warty worked like a charm but Hoary has too much network problems.

---

### Post by ibs on 2005-04-29
Please help me. I can't configure the network via DHCP or statically. I have tried everthing mentioned on this thread and other threads regarding this issue but with no luck. DHCP, and static network configuration worked well in Warty on the same computer.

---

