---
title: "help!!??"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by skata94 on 2009-11-17
I have a sony vaio vgnsz230p laptop and when i  first installled i had no problems at all now I cant stay connected to the internet or burn a cd.  I wouild like to know how to run clam av jus cause i am parranoid and second my cd burning willl almost complete then I get a error code I dont have it handy but it has all the symptons of a good old virus or spyware can someone help or atleast point me in the right direction?

---

### Post by ukripper on 2009-11-17
Are you using Windows?

---

### Post by skata94 on 2009-11-17
when i also try to open administrative tools it says
cant grab the mouse 
A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.
try again

---

### Post by skata94 on 2009-11-17
yes widows is installed also on my computer xp pro to be exact

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> when i also try to open administrative tools it says
cant grab the mouse 
A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.
try again

If it is on Windows then you are in the wrong place. This is ubuntu support section only .

---

### Post by skata94 on 2009-11-17
no i hate windows but it has some software that i want like my finger print scanner ect and  some of my printers will only work with windows but i want my linux to work right im tired of windows

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> no i hate windows but it has some software that i want like my finger print scanner ect and  some of my printers will only work with windows but i want my linux to work right im tired of windows

Ok let get this straight as i am getting confused. To be exact are you having problem on Windows or Ubuntu?

Ubuntu doesn't have Adminstrative tools but Windows has, so your post is not very clear.

---

### Post by skata94 on 2009-11-17
oh im sorry i meant package manager.

---

### Post by ukripper on 2009-11-17
clam av won't help if your session/computer is hacked or someone is running malicious arbitrary code. Have you got ssh server running? Did you install anything outside of ubuntu repositories?

Can you post output of the following command:
```
cat /var/log/auth.log | grep sshd 
```

---

### Post by skata94 on 2009-11-17
NO i havent done anything outside of the ubuntu forum and when i put that command in it didnt do anything but it went through

---

### Post by skata94 on 2009-11-17
NO i havent done anything outside of the ubuntu forum and when i put that command in it didnt do anything but it went through amd i dont know what ssh is

---

### Post by dillandriskell on 2009-11-17
What I would do in addition to Ukripper's advice is order a free Ubuntu CD since burning is difficult with your machine.  This way if you can't get your computer fixed in that time you'll at least have an Ubuntu disk and you can just straight out use that.

Otherwise I would recommend installing ZoneAlarm if your virus issue is with Windows, there's a free version of it here; [http://download.cnet.com/ZoneAlarm/3000-10435_4-10039884.html?part=dl-69168&subj=dl&tag=button](http://download.cnet.com/ZoneAlarm/3000-10435_4-10039884.html?part=dl-69168&subj=dl&tag=button).  This is a pretty good program for blocking virus', spyware, the works.  If not just enough for you to burn Ubuntu to a disk.  Also if the disk is too much of an issue you can also consider putting Ubuntu on a flash drive instead and installing it that way.  

Best of luck

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> NO i havent done anything outside of the ubuntu forum and when i put that command in it didnt do anything but it went through amd i dont know what ssh is

When did you install ubuntu? Did you burn the cd and then installed it?

---

### Post by skata94 on 2009-11-17
no i dont have ssh running what does it do

---

### Post by skata94 on 2009-11-17
I installed it to a cd and then installed it i have been running it for 3 months love it just cant get all the little kinks worked out.

---

### Post by 3rdalbum on 2009-11-17
> **skata94 said:**
> no i dont have ssh running what does it do

Allows you, or anyone who can guess your username and password, to log into your computer. If you haven't explicitly installed it, then it's not running.

You definitely don't have a virus. There are no viruses that run natively on Ubuntu, and no Windows viruses can run unless you have explicitly installed them with Wine (and even then, they would only work when Wine is running).

Are you on a slow computer? When I was on a very slow machine, I saw the message about "couldn't lock the keyboard". A slower machine might have trouble sending data quickly enough to the DVD recorder.

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> I installed it to a cd and then installed it i have been running it for 3 months love it just cant get all the little kinks worked out.

can you post output of the following commands:
```
netstat -nat
```

---

### Post by skata94 on 2009-11-17
yes i posted that and got this reply
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:8080                             0.0.0.0:*                     LISTEN     
tcp        0      0 127.0.0.1:7634                        0.0.0.0:*                      LISTEN     
tcp        0      0 127.0.0.1:631                         0.0.0.0:*                       LISTEN     
tcp        0      0 192.168.2.4:60017                 209.85.225.138:80       ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN

---

### Post by skata94 on 2009-11-17
it finally let me into my package manager and my computer isnt really slow its a duo core running at like 1.8 gig and i got 2 gig of ram should be plenty to run it easily

---

### Post by ukripper on 2009-11-17
**tcp        0      0 192.168.2.4:60017                 209.85.225.138:80       ESTABLISHED**

Now that is interesting. Can you post output of the follwing command:
```
sudo nmap localhost
```

if you dont have nmap just install it using this:
```
sudo apt-get install nmap
```

i want to see what is using your port 60017 and why foreign address - 209.85.225.138:80  is connected to it?


EDIT:
nevermind it is false alarm. It is google ip.

i

---

### Post by skata94 on 2009-11-17
i had to install it but this is wat i got back from the command

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-17 06:14 CST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> i had to install it but this is wat i got back from the command

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-17 06:14 CST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds

your 631 port is for printing. that is fine

other one is proxy as it states. Are you running privoxy?

i think your network is fine. You must be having different problem.

Can you post output of the following:
```
tail -n 100 /var/log/messages
```

---

### Post by skata94 on 2009-11-17
no

---

### Post by skata94 on 2009-11-17
yes it let me post that command it gave me this

Nov 16 00:12:06 skata94-laptop -- MARK --
Nov 16 00:32:06 skata94-laptop -- MARK --
Nov 16 00:52:06 skata94-laptop -- MARK --
Nov 16 01:12:06 skata94-laptop -- MARK --
Nov 16 01:32:06 skata94-laptop -- MARK --
Nov 16 01:52:06 skata94-laptop -- MARK --
Nov 16 02:12:06 skata94-laptop -- MARK --
Nov 16 02:32:06 skata94-laptop -- MARK --
Nov 16 02:52:06 skata94-laptop -- MARK --
Nov 16 03:12:06 skata94-laptop -- MARK --
Nov 16 03:32:06 skata94-laptop -- MARK --
Nov 16 03:52:06 skata94-laptop -- MARK --
Nov 16 04:12:06 skata94-laptop -- MARK --
Nov 16 04:32:06 skata94-laptop -- MARK --
Nov 16 04:52:06 skata94-laptop -- MARK --
Nov 16 05:12:06 skata94-laptop -- MARK --
Nov 16 05:32:06 skata94-laptop -- MARK --
Nov 16 05:52:06 skata94-laptop -- MARK --
Nov 16 06:12:06 skata94-laptop -- MARK --
Nov 16 06:32:06 skata94-laptop -- MARK --
Nov 16 06:52:06 skata94-laptop -- MARK --
Nov 16 07:12:06 skata94-laptop -- MARK --
Nov 16 07:32:06 skata94-laptop -- MARK --
Nov 16 07:52:06 skata94-laptop -- MARK --
Nov 16 08:00:32 skata94-laptop syslogd 1.5.0#5ubuntu3: restart.
Nov 16 08:12:06 skata94-laptop -- MARK --
Nov 16 08:32:06 skata94-laptop -- MARK --
Nov 16 08:52:06 skata94-laptop -- MARK --
Nov 16 09:12:06 skata94-laptop -- MARK --
Nov 16 09:32:06 skata94-laptop -- MARK --
Nov 16 09:52:06 skata94-laptop -- MARK --
Nov 16 10:12:06 skata94-laptop -- MARK --
Nov 16 10:32:06 skata94-laptop -- MARK --
Nov 16 10:52:06 skata94-laptop -- MARK --
Nov 16 11:12:06 skata94-laptop -- MARK --
Nov 16 11:32:06 skata94-laptop -- MARK --
Nov 16 11:52:06 skata94-laptop -- MARK --
Nov 16 12:12:06 skata94-laptop -- MARK --
Nov 16 12:32:06 skata94-laptop -- MARK --
Nov 16 12:52:06 skata94-laptop -- MARK --
Nov 16 13:12:06 skata94-laptop -- MARK --
Nov 16 13:32:06 skata94-laptop -- MARK --
Nov 16 13:52:06 skata94-laptop -- MARK --
Nov 16 14:12:06 skata94-laptop -- MARK --
Nov 16 14:32:06 skata94-laptop -- MARK --
Nov 16 14:52:06 skata94-laptop -- MARK --
Nov 16 15:12:06 skata94-laptop -- MARK --
Nov 16 15:32:06 skata94-laptop -- MARK --
Nov 16 15:52:06 skata94-laptop -- MARK --
Nov 16 16:12:06 skata94-laptop -- MARK --
Nov 16 16:32:06 skata94-laptop -- MARK --
Nov 16 16:52:06 skata94-laptop -- MARK --
Nov 16 17:12:06 skata94-laptop -- MARK --
Nov 16 17:32:06 skata94-laptop -- MARK --
Nov 16 17:52:06 skata94-laptop -- MARK --
Nov 16 18:12:06 skata94-laptop -- MARK --
Nov 16 18:32:06 skata94-laptop -- MARK --
Nov 16 18:52:06 skata94-laptop -- MARK --
Nov 16 19:12:06 skata94-laptop -- MARK --
Nov 16 19:32:06 skata94-laptop -- MARK --
Nov 16 19:52:06 skata94-laptop -- MARK --
Nov 16 20:12:06 skata94-laptop -- MARK --
Nov 16 20:32:06 skata94-laptop -- MARK --
Nov 16 20:52:06 skata94-laptop -- MARK --
Nov 16 21:12:06 skata94-laptop -- MARK --
Nov 16 21:32:06 skata94-laptop -- MARK --
Nov 16 21:52:06 skata94-laptop -- MARK --
Nov 16 22:12:06 skata94-laptop -- MARK --
Nov 16 22:32:06 skata94-laptop -- MARK --
Nov 16 22:52:06 skata94-laptop -- MARK --
Nov 16 23:12:06 skata94-laptop -- MARK --
Nov 16 23:32:06 skata94-laptop -- MARK --
Nov 16 23:52:06 skata94-laptop -- MARK --
Nov 17 00:12:06 skata94-laptop -- MARK --
Nov 17 00:32:06 skata94-laptop -- MARK --
Nov 17 00:52:06 skata94-laptop -- MARK --
Nov 17 01:12:06 skata94-laptop -- MARK --
Nov 17 01:32:06 skata94-laptop -- MARK --
Nov 17 01:52:06 skata94-laptop -- MARK --
Nov 17 02:12:06 skata94-laptop -- MARK --
Nov 17 02:32:06 skata94-laptop -- MARK --
Nov 17 02:52:06 skata94-laptop -- MARK --
Nov 17 03:12:06 skata94-laptop -- MARK --
Nov 17 03:32:06 skata94-laptop -- MARK --
Nov 17 03:52:06 skata94-laptop -- MARK --
Nov 17 04:12:06 skata94-laptop -- MARK --
Nov 17 04:32:06 skata94-laptop -- MARK --
Nov 17 04:46:15 skata94-laptop kernel: [339266.891536] gksu[18663]: segfault at 1 ip b7a9129c sp bf8036a0 error 4 in libgdk-x11-2.0.so.0.1600.1[b7a37000+89000]
Nov 17 04:46:53 skata94-laptop kernel: [339305.201700] gksu[18677]: segfault at 35783020 ip b7c3d29c sp bfab0ee0 error 4 in libgdk-x11-2.0.so.0.1600.1[b7be3000+89000]
Nov 17 04:47:21 skata94-laptop kernel: [339332.381534] gksu[18682]: segfault at 526b7441 ip b7c4c29c sp bfcc00f0 error 4 in libgdk-x11-2.0.so.0.1600.1[b7bf2000+89000]
Nov 17 05:12:06 skata94-laptop -- MARK --
Nov 17 05:15:00 skata94-laptop sudo: pam_sm_authenticate: Called 
Nov 17 05:15:00 skata94-laptop sudo: pam_sm_authenticate: username = [skata94] 
Nov 17 05:15:00 skata94-laptop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Nov 17 05:32:06 skata94-laptop -- MARK --
Nov 17 05:52:06 skata94-laptop -- MARK --
Nov 17 06:12:06 skata94-laptop -- MARK --
Nov 17 06:13:28 skata94-laptop sudo: pam_sm_authenticate: Called 
Nov 17 06:13:28 skata94-laptop sudo: pam_sm_authenticate: username = [skata94] 
Nov 17 06:13:28 skata94-laptop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc)

---

### Post by ukripper on 2009-11-17
can you open up your firefox-->Tools-->Preferences-->Advanced-->network-->Settings  and tell me if it is using any proxy there?

---

### Post by skata94 on 2009-11-17
If everything is up to par the only other problems im having is my screen is blinking like it is going out and my wifi wont stay connected it says i am but it wont load the page i redownloaded the driver from intel but i dont know how to install it will u help?  You have most deffinetly the most help i have ever gotten thank you

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> If everything is up to par the only other problems im having is my screen is blinking like it is going out and my wifi wont stay connected it says i am but it wont load the page i redownloaded the driver from intel but i dont know how to install it will u help?  You have most deffinetly the most help i have ever gotten thank you

for your intel card can you run below command:
```
lspci
```

---

### Post by skata94 on 2009-11-17
It says using system proxy settings

---

### Post by skata94 on 2009-11-17
yes but it gave me this answer and its the right card


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 15)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> It says using system proxy settings

thats fine can you post lspci output

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> 
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


I have the same wifi card and it works just fine with karmic

Do you  get disconnected in windows as well then it is not issue with the card. It may be router or your wifi range of router.

---

### Post by skata94 on 2009-11-17
i dont see the ispci output option

---

### Post by skata94 on 2009-11-17
im leaning toward my router its a belkin a higher end one at that

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> i dont see the ispci output option

just ignore that sorry i didn't see you post before.

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> im leaning toward my router its a belkin a higher end one at that

When you boot into windows XP, do you get the same connection dropping problem?

---

### Post by skata94 on 2009-11-17
no not one problem in windows (except its slow as dirt and worthless)

---

### Post by skata94 on 2009-11-17
i did the ping test and it pinged like 85 times then stopped and tried everything else and my wireless is set up as a static

---

### Post by ukripper on 2009-11-17
> **skata94 said:**
> no not one problem in windows (except its slow as dirt and worthless)

ok can you post output of the following command:
```
lshw -C network
```

---

### Post by skata94 on 2009-11-17
this is the answer i got 
but i gotta go to work i will be back on at 6:00 US central time 

 WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:40:a7:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 15
       serial: 00:13:a9:2b:cb:ca
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:0e:16:94:ab:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by ukripper on 2009-11-17
personally, i don't see any problem with your card. may be problem could be your network manager or your router's signal.
can you post output of below command:


```
ping -C 60 192.168.2.1 
```

this will test if your packets are being dropped or not. assuming your router gateway is 192.168.2.1

---

### Post by skata94 on 2009-11-17
i ran that command and this is what i got


skata94@skata94-laptop ~ $ WARNING: you should run this program as super-user.
bash: WARNING:: command not found
skata94@skata94-laptop ~ $   *-network               
bash: *-network: command not found
skata94@skata94-laptop ~ $        description: Wireless interface
bash: description:: command not found
skata94@skata94-laptop ~ $        product: PRO/Wireless 3945ABG [Golan] Network Connection
bash: product:: command not found
skata94@skata94-laptop ~ $        vendor: Intel Corporation
bash: vendor:: command not found
skata94@skata94-laptop ~ $        physical id: 0
bash: physical: command not found
skata94@skata94-laptop ~ $        bus info: pci@0000:06:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
bash: bus: command not found
skata94@skata94-laptop ~ $        logical name: wmaster0
bash: logical: command not found
skata94@skata94-laptop ~ $        version: 02
bash: version:: command not found
skata94@skata94-laptop ~ $        serial: 00:13:02:40:a7:38
bash: serial:: command not found
skata94@skata94-laptop ~ $        width: 32 bits
bash: width:: command not found
skata94@skata94-laptop ~ $        clock: 33MHz
bash: clock:: command not found
skata94@skata94-laptop ~ $        capabilities: bus_master cap_list logical ethernet physical wireless
bash: capabilities:: command not found
skata94@skata94-laptop ~ $        configuration: broadcast=yes driver=iwl3945 ip=192.168.2.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
bash: configuration:: command not found
skata94@skata94-laptop ~ $   *-network
bash: *-network: command not found
skata94@skata94-laptop ~ $        description: Ethernet interface
bash: description:: command not found
skata94@skata94-laptop ~ $        product: 88E8036 PCI-E Fast Ethernet Controller
bash: product:: command not found
skata94@skata94-laptop ~ $        vendor: Marvell Technology Group Ltd.
bash: vendor:: command not found
skata94@skata94-laptop ~ $        physical id: 0
bash: physical: command not found
skata94@skata94-laptop ~ $        bus info: pci@0000:07:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
bash: bus: command not found
skata94@skata94-laptop ~ $        logical name: eth0
bash: logical: command not found
skata94@skata94-laptop ~ $        version: 15
bash: version:: command not found
skata94@skata94-laptop ~ $        serial: 00:13:a9:2b:cb:ca
bash: serial:: command not found
skata94@skata94-laptop ~ $        width: 64 bits
bash: width:: command not found
skata94@skata94-laptop ~ $        clock: 33MHz
bash: clock:: command not found
skata94@skata94-laptop ~ $        capabilities: bus_master cap_list ethernet physical
bash: capabilities:: command not found
skata94@skata94-laptop ~ $        configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
bash: configuration:: command not found
skata94@skata94-laptop ~ $   *-network DISABLED
bash: *-network: command not found
skata94@skata94-laptop ~ $        description: Ethernet interface
bash: description:: command not found
skata94@skata94-laptop ~ $        physical id: 2
bash: physical: command not found
skata94@skata94-laptop ~ $        logical name: pan0
bash: logical: command not found
skata94@skata94-laptop ~ $        serial: 9e:0e:16:94:ab:72
bash: serial:: command not found
skata94@skata94-laptop ~ $        capabilities: ethernet physical
bash: capabilities:: command not found
skata94@skata94-laptop ~ $        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bash: configuration:: command not found

---

### Post by ukripper on 2009-11-18
ok let us do things differently now as this one is not going anywhere.

We will change keep alive probes which checks normally every 2 hours to keep your connection alive. We can reduce the time so it keeps probing your conection let say after every 10 mins. 

So for that can you check first your probe value by running below commands:
```
cat /proc/sys/net/ipv4/tcp_keepalive_probes
```

```
 cat /proc/sys/net/ipv4/tcp_keepalive_time

```

```
cat /proc/sys/net/ipv4/tcp_keepalive_intvl

```

and post output here

I think if set the values for your connection to be alive more frequently your issue could be reolved as a workaorund.



Edit: 

Just remembered there could be another possible problem if your router doesn't support IPv6 you may need to disable it within ubuntu and switch to ipv4.

so to check if you are running ipv6 can you run this command:
```
lsmod | grep inet6
```
if there is some output then it means ipv6 is enabled.

---

### Post by skata94 on 2009-11-18
this is what i got from the commands you gave me at first and i guess i am not running ipv6 cause nothing came up.


skata94@skata94-laptop ~ $ cat /proc/sys/net/ipv4/tcp_keepalive_probes
9
skata94@skata94-laptop ~ $  cat /proc/sys/net/ipv4/tcp_keepalive_time
7200
skata94@skata94-laptop ~ $ cat /proc/sys/net/ipv4/tcp_keepalive_intvl
75

---

### Post by ukripper on 2009-11-18
> **skata94 said:**
> this is what i got from the commands you gave me at first and i guess i am not running ipv6 cause nothing came up.


skata94@skata94-laptop ~ $ cat /proc/sys/net/ipv4/tcp_keepalive_probes
9
skata94@skata94-laptop ~ $  cat /proc/sys/net/ipv4/tcp_keepalive_time
7200
skata94@skata94-laptop ~ $ cat /proc/sys/net/ipv4/tcp_keepalive_intvl
75


Let first make sure ipv6 is not working at all. Follow the steps as below:

Here we edit /etc/default/grub file, run below command:

 ```
   sudo gedit  /etc/default/grub
```

Change within that file

from:
    > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:
   >  GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Save and exit the file

Update the grub from the command line

```
    sudo update-grub
```

After that reboot. Now if your wireless connection stays and don't disconnect randomly think this had fix it for you. Otherwise we will go the probing route.

---

### Post by skata94 on 2009-11-18
when i opened that file there was nothing in it and i went ahead and put that new line in it then i put the command in and this is wat i got

skata94-laptop ~ $  sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Distro title is set to Linux Mint 7 Gloria
/etc/default/grub: line 1: quiet: command not found

---

### Post by ukripper on 2009-11-18
> **skata94 said:**
> when i opened that file there was nothing in it and i went ahead and put that new line in it then i put the command in and this is wat i got

skata94-laptop ~ $  sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Distro title is set to Linux Mint 7 Gloria
/etc/default/grub: line 1: quiet: command not found

this is not possible that there wasn't grub file. Are you using ubuntu 9.04 or 9.10?

Can you post output of this file:
```
sudo gedit /etc/default/grub
```

---

### Post by ukripper on 2009-11-18
ok i believe you are running either ubuntu 9.04 or lower:
In that case, can you follwo these steps:
```
sudo gedit /boot/grub/menu.lst
```

post output here enclosing in **CODE** from message tool otherwise it gets messy to read and i won't be able to edit anything.

---

### Post by skata94 on 2009-11-18
I am running Linux Mint 7 I dont know what version of ubuntu it is based off of but this is what I got


CODE

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by skata94 on 2009-11-18
sorry it wouldnt let me put it in a code box so i put it in a attachment hopefully that will help

---

### Post by ukripper on 2009-11-19
ok now just put **ipv6.disable=1** after "splash" like below, after where it says ## ## End Default Options ##:

open your menu.lst with this comamnd:
```
sudo gedit /boot/grub/menu.lst
```

> title Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro quiet splash **ipv6.disable=1**
initrd /boot/initrd.img-2.6.28-11-generic
quiet


then save and exit you grub menu.lst.

After that run this command:
```
sudo update-grub
```

After that reboot and now see if your connection still drops or not.

---

### Post by skata94 on 2009-11-30
everything seems to be working just fine every once in awhile it wont stay connected

---

