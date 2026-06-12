---
title: "How to connect using cable modem? HELP!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by zer011 on 2009-06-18
Greetings,
 
I am a green-horn when it comes to this stuff, so please bear with me.:smile:  I am trying to connect to the internet via Charter services using an Ambit U10C018 Cable modem. Everything works fine with XP(I'm dual booting for the time being), and I've tried to unplug the modem to reset it, as I have read in other threads, but to no avail.  I think I might be missing a crucial (and probably elementary) step in setting up my internet connection. As I mentioned, green-horn. I've tried to look up the steps for connection in the help files, but the only thing that comes close(I guess) is dsl instructions, or wired(LAN).   I am desparately trying ween myself(and others) off the M$ teet.  A basic step-by-step guide would be greatly appreciated.

---

### Post by lonetreetechy on 2009-06-18
1. What version of Ubuntu?
2. Wireless or ethernet?
3. Network hardware drivers installed?

Are you reading this Web site from your Windows partition? Tip: log into Ubuntu, copy-n-paste the system info into a text file and save the file to your Windows hard drive volume. That way, it will be available when you reboot to Windows.

---

### Post by -kg- on 2009-06-18
> the only thing that comes close(I guess) is dsl instructions, _or wired(LAN)._

Pretty obvious that he's using wireless.  Do you have WEP or WPA wireless security enabled, and have you entered your key?  If this is not the problem, then we will need to know what kind of wireless card/chipset you are using.  In the terminal (under Ubuntu, of course) enter the command:

```
lspci
```

This command will list the pci devices connected to (or installed in, in the case of an internal on-board device) your computer, including the wireless device.  Then, using the method suggested by lonetreetechy, post the output of that command here.

If your wireless device is a USB device, try:

```
lsusb
```

instead.

---

### Post by zer011 on 2009-06-19
Ubuntu 9.04
Ethernet
Writing this in Xp

---

### Post by zer011 on 2009-06-19
Not sure about drivers. :(

---

### Post by Hoodline on 2009-06-19
resetting my modem seemed to be the only way i could get internet on linux

You can reset the modem before your pc boots this normally works for me or while your on the desktop you could try disconnect the cable from the modem reset the modem wait untill a few of the lights are on and connect the cable then open firefox and test

---

### Post by Mike'sHardLinux on 2009-06-19
-kg-: wireless??? obvious????? huh???

zer011: Did you have to install any software in XP for your cable connection?
Do you remember how you set up XP for Charter? Contrary to what you might see people say on the Internet, cable companies DO use PPPoE, and that may be true in your case.

In XP, go to a command prompt and post the output of:
```
ipconfig /all
```

Then, boot into Ubuntu, go to a terminal, and post the output of:
```
ifconfig
```

---

### Post by zer011 on 2009-06-19
ipconfig /all
Microsoft(R) Windows DOS
(C)Copyright Microsoft Corp 1990-2001.

C:\DOCUME~1\ZER0>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : OHOME
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel 21143-Based PCI Fast Ethernet
Adapter (Generic)
        Physical Address. . . . . . . . . : 00-08-C7-3F-A0-8A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 68.113.108.36
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 68.113.108.1
        DHCP Server . . . . . . . . . . . : 68.114.39.2
        DNS Servers . . . . . . . . . . . : 24.177.176.38
                                            24.178.80.36
                                            24.197.160.18
        Lease Obtained. . . . . . . . . . : Friday, June 19, 2009 8:49:46 PM
        Lease Expires . . . . . . . . . . : Saturday, June 20, 2009 4:49:46 AM

Ethernet adapter Local Area Connection 2:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-50-FC-6A-BC-C0

C:\DOCUME~1\ZER0>


ifconfig
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:c7:3f:a0:8a  
          inet6 addr: fe80::208:c7ff:fe3f:a08a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:11 dropped:0 overruns:0 carrier:21
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2400 

eth1      Link encap:Ethernet  HWaddr 00:50:fc:6a:bc:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by zer011 on 2009-06-19
I have not had to install anything to XP to get the connection. I run the Netwrk Setup Wizrd a time or two and im on.

---

### Post by Toshubu on 2009-06-19
You need to get into the eth0 setup (System --> Administration --> Network) gui and make sure that the ubuntu setup is dhcp. (Automatic Configuration (DHCP)). (At least I assume 9.04 is the same as 8.04, for this function.) May need to re-boot.

---

### Post by zer011 on 2009-06-20
Yes, my network settings are set to DHCP(Automatic).

---

### Post by zer011 on 2009-06-20
I am using an old PIII Compaq Presario 5695 if that helps.  Maybe new drivers would help??:confused:  Im stabbing in the dark now.  I gotta say, I love the idea/ideals of linux, esp. Ubuntu, but Im finding the practical use and execution is rather frustrating.  I'll keep pluggin' along with ya'lls help. Thanks for the help thus far:)!

---

### Post by LewRockwell on 2009-06-20
just for fun you can check these out:

[http://www.partedmagic.com/](http://www.partedmagic.com/)

[http://www.puppylinux.org/](http://www.puppylinux.org/)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Toshubu on 2009-06-20
Hi Zer011,
Please post the output of the command:
**lspci | grep Eth **    (or:  **lspci | grep eth**)

(The | symbol is the uppercase version of the "\").

Also, please post the output of:
**ping -c 3 127.0.0.1**

Thanks

---

### Post by zer011 on 2009-06-20
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

zer0@0home:~$ lspci | grep eth
zer0@0home:~$ lspci | grep Eth
00:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:12.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)


zer0@0home:~$ ping -c 3 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.125 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.094 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.094 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.094/0.104/0.125/0.016 ms
zer0@0home:~$

---

### Post by Toshubu on 2009-06-20
Can you ping the Gateway?  (I got the gateway address from your M$ "ipconfig /all" output in an earlier post of yours)..

**ping -c 3 68.113.108.1**

Please post the output of:
**cat /etc/resolv.conf**

Please post the output of:
**cat /etc/hosts**

If nothing much seems to come from all that, you might want to try:
**sudo ifconfig eth0 down **    (you may have to enter root password) then:

**sudo ifconfig eth0 up**  (just turning the eth card off and on)...

Also, it looks like you have 2 ethernet cards...just out of curiosity, have you tried the other RJ45 (ethernet) port?...

---

### Post by zer011 on 2009-06-21
I haavent tried to use the second eth card yet, but it seems like that might be worth a shot.  I wasnt sure how that would effect everything.  Im using the 2nd card to run a ntwrk to my other computer.  Ill try it soon.  As for the requested info:
root@0home:/home/zer0# ping -c 3 68.113.108.1

connect: Network is unreachable

root@0home:/home/zer0# cat /etc/resolv.conf

cat: /etc/resolv.conf: No such file or directory
root@0home:/home/zer0# cat /etc hosts

cat: /etc: Is a directory

cat: hosts: No such file or directory
root@0home:/home/zer0# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    0home

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@0home:/home/zer0# ifconfig eth0 down
root@0home:/home/zer0# ifconfig eth0 up
root@0home:/home/zer0#

---

### Post by bveritoa on 2009-06-22
I have the same problem like zer011...i look on many forums...but i still have no answer yet.Zer011 did you find how to fix it?Or is a lost fight?? As much i a see the only thing that we can do is change the internet provider(so lose the damn modem)....

---

### Post by sadaruwan12 on 2009-06-22
Hi,

I'd the same kind of a problem when I upgraded my self from Ubuntu V8.04 to 8.10 the net was nit working I think after going through all the details that you've provided you must be running on a router that have a DSL modem built in to it. I think you're on junty right normally the networking side of jaunty is very good compared to Interpid but I suggest that you down grade to Ubuntu v8.04 it's a LTS version which is very stable now and have very little bugs compared to other normal releases if you can download the 8.04 and give it a go, I think it might help you in your problem 'cos it have helped me to continue my work continuously with out any hiccups.

---

### Post by zer011 on 2009-06-22
I guess iam goin to try my old 8.04LTS install. I will also try to use eth1. If all else fails im going to get a router and see if that helps. If all that fails i guess ill go buy a new cable modem and tell Charter that they can take theirs back and shove it...:lolflag: Hopefully ill get a couple newer computers and see if that doesnt help as well.  Newer equipment is usually pretty helpfull. :) All in good time for most of this work, cause the work week is here again and i have a FULL plate at the moment. Keep all the great suggestions comming! Thanks everyone!

---

### Post by zer011 on 2009-06-22
As a side note, i am unsure why this thread is titled with Kubuntu.  I am running regular Ubuntu.

---

### Post by bveritoa on 2009-06-23
Ok so 8.04 :popcorn: better than windown anyway :D I will try it.Thank you for your help.

---

### Post by zer011 on 2009-06-23
Happy Day!!!!!! \\:D/ I am proud to say that I am writing this from Ubuntu!!!!  I installed 8.04 LTS, and got to snooping around the GUI network configs when all of a sudden I noticed Ubuntu was not recognizing my mobo ethernet. So I reconnected my line to my secondary ethernet card, rechecked the configurations, reset the modem, and ... WABAAAMM!!!!!!  I am now proudly on the Net via Ubuntu!!!!!! I still have to try this with 9.04, and I think it might work, but for right now I am absolutely thrilled!!!!! Now I just have to get another ethernet card so I can LAN. By the way I am using cards with Realtek chipsets. I wont call this one completely solved, but it s damn close. Thanks to everyone that has been so kind to take the time to help out! I couldn't have done it without y'all!:) Y'all kept me goin when I got frustrated and discouraged. Thanks.
    I'll keep posting to this thread to keep y'all up to date on my progress with Jaunty.

---

### Post by Toshubu on 2009-06-24
Good for you, Zero...
Sounds to me like you intend to try to use the 9.04 (if it works) to try route with it (2 eth cards)...I'm not sure what you want to do...But, I think I'd lean towards just getting a simple consumer brand router to set up a home LAN...especially if you want to get wireless going sometime...If it were me, I would do some research on my ISP's web pages...see if they have any FAQ's about home LANs..I'd do more research, if I were you...

---

### Post by zer011 on 2009-06-24
Good advice Toshubu. I'll look into their FAQs and see what their setup looks like. Thanks!

---

### Post by zer011 on 2009-06-29
SOLVED: sort of. Well I couldnt find any useful info on my ISPs homepage. But I have DO have stable internet access to my first computer.  Turns out it was an eth compatibility problem. I put in 2 Realtek chipset NICs and that seemed to do the trick. Now I have another problem.  I am trying to share my net connection with my second computer using a crossover cable. Both the 1st and second computer are running Ubuntu 9.04.  The Network Manager sas that they are connected, but the second is not able to access the net.  Ive tried to configure the settings manually, but without success. Any help will be greatly be appreciated!  Thanks!!
 
P.S.
 
On a lighter note, I'm proud to say that two more computers have and will be fully liberated!!!  Take THAT M$!!!!!!:lolflag:

---

### Post by LewRockwell on 2009-06-29
I didn't read up on the whole saga but congratulations and thanks for not throwing in the towel while there's still fight left in the dog

.

---

