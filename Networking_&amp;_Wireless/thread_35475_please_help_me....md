---
title: "please help me..."
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by dane_braddy666 on 2005-05-19
ok, this is my first post so, hello.
i need some help, i am new to the linux world and although at first it seemed daunting i am really liking it.

I started out about a month ago using Red hat 9 , again being new i found it very difficult and then a couple people suggested some more user friendly distro's, namely MEPIS and ubuntu.

heres my problem:

on red hat 9 the internet worked as soon as i intalled a network card in my computer (i have adsl via lan at home), u was then lured to MEPIS because of the debian package system and how easy it is to install. but alas the internet did not work on mepis. i have now installed UBUNTU, again because of its simplicity adn how easy it is to install new programs... but again the internet does not work, the card is recognised... and set as active in the network dialog... 
i dual boot with windows xp and it works fine (in fact that is how i'm sending you this message now)

Had it not worked on red hat i would simply go get a new card but since it has worked on a linux system i am very confused.  ](*,) 

again i am new so if you can help me ( a HUGE THANKS IN ADVACE) could you please instruct me as if i am the dumbest person on earth.

any help would be great so i can fully be drowning in UBUNTU greatness.

thanks
                     - DANE

---

### Post by Ali_Baba on 2005-05-19
Hi,would be good if you could tell some more details about your problem,then it would be easier to help.Also the name and type of your network card :)

---

### Post by dane_braddy666 on 2005-05-19
the problem is the internet won't work even though ubuntu says the card is active and working fine.

i tried the loopback address to double check and it works fine.... but i still cannot connect to the internet ( i connect via lan )

the card make is realtek 8139 ( i think)... i know it's a realtek....

again any help would be great. thanks.

---

### Post by ltmon on 2005-05-19
Hi fellow Melbournite.

Can you post the results of typing "ifconfig" into the terminal.

Cheers,

L.

---

### Post by dane_braddy666 on 2005-05-19
sorry about the fomatting, i had to use my usb flashdisk to transfer a text file with the results...
here they are:

[FONT=Arial]eth0      Link encap:Ethernet  HWaddr 00:E0:4C:90:17:0D
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe90:170d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1458 (1.4 KiB)  TX bytes:2061 (2.0 KiB)
          Interrupt:4 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:154430 (150.8 KiB)  TX bytes:154430 (150.8 KiB)[/FONT]

- dane

---

### Post by mohaham on 2005-05-19
Open up the terminal and issue this command

sudo ifup eth0

Hope this works..the ifconfig output looks ok to me..

---

### Post by dane_braddy666 on 2005-05-20
thanks but it didn't work,
the terminal just replied

"ifup: interface eth0 already configured"

should i reboot after doing this?

am i beyond help? i just don't understand, i booted into XP and it works fine.

am i asking too many questions? possibly.

does anyone have any ideas? your help is greatly appreciated, this forum rocks!

---

### Post by byourg on 2005-05-20
I assume your using Firefox for a web browser. Type "about:config" (without quotemarks) in the address window, scroll down to NETWORK.DNS.DISABLEIPV6 and double click this line. Change the setting to TRUE, now type a web address in and see if you can browse the web. I had the same problem and this worked for me.

---

### Post by ltmon on 2005-05-21
I don't see any ifconfig issues either.

Try 'ping www.ubuntuforums.org' in your terminal (press Ctrl-C to stop the ping).  If this gives you output like 
```

ltmon@arturo:~$ ping www.ubuntuforums.org
PING ubuntuforums.org (64.21.33.9) 56(84) bytes of data.
64 bytes from 64.21.33.9: icmp_seq=1 ttl=47 time=279 ms
64 bytes from 64.21.33.9: icmp_seq=2 ttl=47 time=281 ms
64 bytes from 64.21.33.9: icmp_seq=3 ttl=47 time=282 ms

--- ubuntuforums.org ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 4889ms
rtt min/avg/max/mdev = 279.716/281.248/282.411/1.130 ms

```
Then your problem isn't the conenction, and it's likely within the browser like the previous post said.

---

### Post by Davepet on 2005-05-29
I stumbled on this thread while looking for clues to my network card problem. I have a similar situation, but different HW.

I've got a brand new system with a gigabyte GA K8NF-9  motherboard (AMD64 3200 proc) with built in (Nforce4 chip) nic. I installed the nvidia drivers for sound & nic    , sound now works, but I get the same results as Dane on the nic:

-------------------------------------------------------------------------------
root@davepet:/home/davepet # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:8A:DB:D6
          inet6 addr: fe80::20f:eaff:fe8a:dbd6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:31572 (30.8 KiB)
          Interrupt:10 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7324634 (6.9 MiB)  TX bytes:7324634 (6.9 MiB)


root@davepet:/home/davepet # ifup eth0
ifup: interface eth0 already configured

root@davepet:/home/davepet # ping 192.168.0.1
connect: Network is unreachable

---------------------------------------------------------------------

So I can't even ping my router, which rules out a firefox problem here.

Not looking to highjack the thread, just adding my $.02

Dave

---

