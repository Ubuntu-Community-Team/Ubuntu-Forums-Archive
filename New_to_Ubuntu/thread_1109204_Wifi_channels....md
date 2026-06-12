---
title: "Wifi channels..."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by mistaPJ on 2009-03-28
I am looking for a way to detect which channel my neighbours' wifi connections use (I live in a block of flats so I'm surrounded by loads of networks), the connection has been bad recently and I suspect there is interference. I have downloaded wifi radar which has detected other networks but it doesn't tell me what channel they broadcast on. It would be great if someone could tell me a way to do this, thanks.

---

### Post by binbash on 2009-03-28
iwlist scan

command shows that.

Sample : 

Address: 00:12:BF:2C:58:7C
                    ESSID:"asdasd"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)

---

### Post by mistaPJ on 2009-03-29
That tells me the channel of the network I am connected to but I can't connect to my neighbours networks because they are secured. So I still can't find their channel.

I've had a play around with sharkwire, but again this only captures packets from networks I am connected to.

It seem strange to me that there is no program out there which detects the channels with least traffic to suggest which one to choose. It would make sense if some software like that were built into either wifi routers or if it was standard issue with wifi software in operating systems.

I might have a play with aircrack later and see if that's any use.

---

### Post by binbash on 2009-03-29
Dude it does not matter if it is encrypted or not, or you are connected or NOT.iwlist shows the channel number and you can use that channel for aircrack.

---

### Post by scorp123 on 2009-03-29
> **mistaPJ said:**
> I am looking for a way to detect which channel my neighbours' wifi connections use  Looks like you need **kismet** ... but it may require some knowledge to configure it properly. And yes, it's a terminal program.

```
sudo apt-get install kismet
```

When you try to run it now you will be greeted by an error:
```
 FATAL: Please configure at least one packet source.
Kismet will not function if no packet sources are defined in kismet.conf 
or on the command line.  Please read the README for more information 
about configuring Kismet.
Kismet exiting. 
```

So you have to do as the error message says, check out the "README". The command ... ```
sudo dpkg -L kismet
``` reveals that there is a compressed "README" file here:
```
/usr/share/doc/kismet/README.gz
```

Don't bother to unpack it, you can read it on the fly with this command:
```
zcat /usr/share/doc/kismet/README.gz | more
```

Now skip forward to the section **"12. Capture Sources"** inside the file. You have to find a capture source that can work with your WLAN chipset. As you can see there are various possibilities depending on the type of chipset inside your PC or laptop.

In my case it's easy: I have a **Intel 3945abg** chipset. So according to the "README" it's either **ipw3945** or **iwl3945** ... But which one? Let's check the drivers that got loaded:
```
lsmod | grep 3945
```

To this my system responds with:
```
iwl3945                99316  0 
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211
rfkill                 17048  4 iwl3945,hp_wmi
```

... So it's the **iwl3945** one in my case.

So now armed with this info let's edit this file:
```
/etc/kismet/kismet.conf
```

Use your favourite editor, e.g.
```
gksudo gedit /etc/kismet/kismet.conf
kdesu kate /etc/kismet/kismet.conf
sudo nano /etc/kismet/kismet.conf
sudo vim /etc/kismet/kismet.conf 
``` One of them should work.

Now find the line which says:
```
source=none,none,addme
```

You have to replace that BS "none,none,addme" with a valid capture source, e.g. with the findings from browsing through the README. And a little further up in the config file one can read this text:
```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
```

"Sources are defined as: source=sourcetype,interface,name[,initialchannel] ... "

OK, so in my case I replace "source=none,none,addme" with this line:
```
source=iwl3945,wlan0,wlan0
```

I save + exit the file, I try to run **kismet** again .... and it works. I can see all neighbour WiFi networks and on what channels they are on. Bingo.

This is what it looks like:

[IMG]http://wirelessdefence.org/Contents/Images/kismet1.png[/IMG]

You can see the list of channels in the middle.

---

### Post by mistaPJ on 2009-03-29
Cheers for getting back to me, here's my script from terminal showing the results of that command.

```
patrick@patrick-laptop:~$ sudo iwlist scan
[sudo] password for patrick: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:F7:41:D4
                    ESSID:"Forrest Palace"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-29 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 92ms ago

patrick@patrick-laptop:~$ 

```

However, if I click on the wireless connection I can currently see 10 networks. So should I not get that 10 times for all the networks I can see? I was chatting with the guy who installed ubuntu for me on pidgin, he works for sun, he told me the same as you but for some reason this doesn't seem to be happening on my computer. He even posted the results of his scan with both wireless networks he can detect. Any ideas what could be wrong with mine?

---

### Post by mistaPJ on 2009-03-29
Thanks scorp, I'll give that a try, I am a total beginner who has been coming on in leaps and bounds over the past couple of days, so it's going to be a bit of a challenge, but it does look like exactly what I want so I'll "give it a bash".

---

### Post by scorp123 on 2009-03-29
> **mistaPJ said:**
>  he works for sun  And I work for a Sun partner :D

---

### Post by mistaPJ on 2009-03-30
It took me a bit of time because I didn't know what to use for interface and name, but I got there in the end. When I did it all seemed a bit obvious and I felt a bit silly, haha.

For any fellow noobs who like copy pasting commands like me i discovered a good one for finding your wireless chipset...

lspci | grep -i wireless

Which should return something like

```

03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

```

and the command where I can find the interface and name for the kismet setup is

iwlist scan

Which returned

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```

on my system just now. I suspect there were no scan results because kismet is running. however this shows that interfaces lo and eth0 dont support scanning but eth1 does, so this is what I used for interface and name.

Another command you can use once you know your interface is 

iwlist eth1 scan

Furthermore it seems that for most of you this should provide a basic list of networks and relevant information. However on my system it once returned information on 7 of the 18 visible networks and the rest of the time only returned results about my own network. I have no idea why. Anyway, if you can understand how to install kismet it does the job very well, cheers scorp!

---

### Post by QuickBrownFox on 2010-04-21
Hi,

I saw this old thread while searching for the solution to this problem.

Binbash (first reply) is right. All you need is the command "iwlist scan". But there is a little more useful information: If you are connected to a network it will only provide information about that network. If you disconnect and run it, it will provide info about all networks in range (including their channel).

---

