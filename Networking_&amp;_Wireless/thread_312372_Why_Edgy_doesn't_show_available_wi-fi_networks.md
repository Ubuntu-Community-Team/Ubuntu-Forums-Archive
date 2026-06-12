---
title: "Why Edgy doesn't show available wi-fi networks?"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by tomash_cz on 2006-12-04
Hello, I have little problem, after I have upgraded to Ubuntu Edgy 6.10, the settings in networking no longer detects available wi-fi networks. I have to write the name of the network manually (basically ask some W$ user to tell me  the name of wi-fi network he's currently using)

However it seems as a minor problem, for me who is changing wireless networks very often during a day, kind of uncomfortable. Is it a bug? Regard and real thanks for any ideas or comments.

---

### Post by tomash_cz on 2006-12-04
Well, got a little searching and find this thread

[http://www.ubuntuforums.org/showthread.php?t=296047&highlight=edgy+wireless+network+show](http://www.ubuntuforums.org/showthread.php?t=296047&highlight=edgy+wireless+network+show)

temporalily you can use "wifi radar", but I still would like to know, why network manager doesn't detects wifi's like dapper did..tks

---

### Post by dbott67 on 2006-12-04
You can always use the command line:
```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

-Dave

---

### Post by tomash_cz on 2006-12-04
Hi Dave, 
Thanks for suggestion! unfortunately when I enter "iwlist scanning" to the command line, I got only following answer:

tomash@tomash-baobei:~$ iwlist scanning
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1 replied no results... does it mean i am even in bigger trouble then i thought? 

tks tomash

---

### Post by dbott67 on 2006-12-04
Hi Tomash,

```
eth1 No scan results
``` 
is the wireless interface, but it is not picking up any results (I'm assuming that there is at least 1 AP within range).

Make sure the eth1 interface is 'active':
```
sudo ifdown eth1 && sudo ifup eth1
```

And then try again & let me know what the results are.

-Dave

---

### Post by dbott67 on 2006-12-04
EDIT: D'OH!... you mentioned this in your 2nd post!

There's also a package in the repositories called 'wifi-radar':
```
sudo apt-get install wifi-radar
```
That can help manage wireless networks.

Attached are some screenshots.

-Dave

---

### Post by tomash_cz on 2006-12-05
Hi Dave,
Thanks for replies! As a newbie I prefer the graphical interface instead of the mysterious command line:), therefore I've installed the wifi-radar and wifi scanning works properly. I have found some other threads talking about the network manager bug in edgy, maybe they'll fix it later. However, right now the wifi-radar works good for me.

Thanx for help & cheers

Ps.: Just qurious, I see you wrote some articels about creating pdf in ubuntu. As I am working with some chinese pdf documents (simplified chinese characters), have you somewhere seen anything about how to make evince to read simplified chinese characters? It always shows only messy characters. Strange that the traditional chractares works properly. Thanks
Tomash

---

### Post by dbott67 on 2006-12-06
Hi Tomash,

The only thing that comes to mind is "Language Support" (System > Administration > Language Support).  Make sure that you select any languages that you want to use.  

If that doesn't work, try installing Acrobat Reader & see if that works.

-Dave

---

### Post by celem on 2006-12-06
The author's original question "...would like to know, why network manager doesn't detects wifi's like dapper did...? wasn't actually answered. I experience the same problem. Is there a bug in edgy and is it going to be fixed??

---

