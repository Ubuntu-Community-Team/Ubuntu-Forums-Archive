---
title: "Access point not-associated: what to do?"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by MMMMManuel on 2007-02-20
Hi!

I'm trying to install a wg111v2 adapter and I have installed drivers. The "hw is present", but typing iwconfig I read: wlan0 [...] Access Point: Not-Associated [...].

How can I "associate" my netgear dg834g?

---

### Post by gradedcheese on 2007-02-21
well, if you're using the shell:

```

sudo iwconfig wlan0 essid put_the_ssid_here

```

(assuming wlan0 is the name of your device).  If you use WEP keys or other encryption, then you'll need to do a little more work.  You can edit (with sudo) /etc/network/interfaces and make it contain something like:

```

auto wlan0
iface wlan0 inet dhcp
wireless-essid put_ssid_here
wireless-key put_wep_key_here

```

and then "sudo /etc/init.d/networking restart"

---

### Post by MMMMManuel on 2007-02-21
Thanks for the reply, but It doesn't run...

I tried dhcp and the output is "No DHCPOFFERS received. No working leases in persistent database - sleeping"-

With static IP address (which are correct because with Windows XP there are the same addresses and the connection runs) ubuntu can reconfigure network interfaces (the output is "yes") and the content of interfaces file is

```

autowlan0
iface inet static
wireless-essid MyFirstWireless
address [...]
netmask [...]
gateway [...]

```

I'm not using WEP.
The light of the adaptor is turned off, yet.
d'oh!


P.S.
The settings of the router are:
Region: Europe
Channel: 11
Modality: g & b

P.P.S.
A note: in the configuration of the router the name is called "ssid", and not "essid".

---

### Post by MMMMManuel on 2007-02-21
I tried both with and without wep, but nothing: access point not associated... and from the configuration of router I can't find the adapter (but "hw is present" in ndiswrapper)

---

### Post by chili555 on 2007-02-21
Please double check. I think you meant auto wlan0 and not autowlan0. Please check your /etc/network/interfaces file to be sure. Amend as needed.

> A note: in the configuration of the router the name is called "ssid", and not "essid". That's fine, but it needs to be wireless-essid here. Don't worry, once you get the settings correct, it will hook up fine, or else I couldn't send this post!

I would also check in the configuration of your router to be sure the DHCP server is set on (just to be sure we can hook up with DHCP *or* a static IP if we want to) and MAC filtering is off. Also double check that the IP address you are asking for is in the range of the router. That is, if the router's IP address is 192.168.0.1, your static address is 192.168.0.x, and not, for example 192.168.100.x.

Restart networking: sudo /etc/init.d/networking restart and let us know.

---

### Post by MMMMManuel on 2007-02-22
> **chili555 said:**
> Please double check. I think you meant auto wlan0 and not autowlan0. Please check your /etc/network/interfaces file to be sure. Amend as needed.

yes, I typed autowlan0, but I wrote auto wlan0 in the file :P


> **chili555 said:**
> I would also check in the configuration of your router to be sure the DHCP server is set on (just to be sure we can hook up with DHCP *or* a static IP if we want to) and MAC filtering is off. 

Access control is not active. 
Static IP is better, even because with winxp the adaptor runs.
MAC filtering is off (even if I know my Mac address and it's correct.

> **chili555 said:**
> Also double check that the IP address you are asking for is in the range of the router. That is, if the router's IP address is 192.168.0.1, your static address is 192.168.0.x, and not, for example 192.168.100.x.

Eh, correct IP address, too.

> **chili555 said:**
> Restart networking: sudo /etc/init.d/networking restart and let us know.

LOL, when I type this command, the answer is:```

Error for wireless request "Set Encode" (8B2A) :
invalid argument "my_net_pssw".
```
when I plug the adaptor, it appears "wireless-key :s"; if I don't delete "s:" the answer to te command is:```

Error for wireless request "Set Encode" (8B2A) :
invalid argument :s .
```


I'm using Wep (128bit), autentication: auto. 
The  mode is b&g, region is Europe and the trasmission of the name (ssid) is on.

P.S.

When I plug in the adaptor, in "networking" appears "wireless connection", so the hw is recognized.

---

### Post by MMMMManuel on 2007-02-22
If I insert s: I must write the key in asci, otherwise exadecimal... i tried both, but nothing runs...

---

### Post by MMMMManuel on 2007-02-22
I tried with wpa encoding, too, but i've the same results: "access point: not-associated"...

---

### Post by chili555 on 2007-02-22
MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMManuel!

Let's slow down and solve one problem at a time. Yesterday you said you were not using WEP. Today you are using 128-bit WEP. But then you tried WPA. I suggest we try to get WEP with a static IP address going and concentrate on it till we crack it. Then we can get crazy!

This: > If I insert s: I must write the key in asci and this: > nvalid argument :s tell us we are going down the wrong road.

Please sudo gedit your /etc/network/interfaces to look like this: ```
auto wlan0
iface **wlan0** inet static
wireless-essid MyFirstWireless
address [...]
netmask [...]
gateway [...]
wireless-key hexidecimal_key_here
```

Do not preface the key with 0x or S: or anything. Do not use the passphrase that generated the key, use the key. Save the file and exit.

Please then restart networking and let us know.

---

### Post by MMMMManuel on 2007-02-23
Ok, i tried a lot of solutions but... d'oh

Now, my interfaces file is as written. I restart and "reconfiguration is [OK]". The light is off and internet too ._. all  the 26 symbols of the public key are correct. The name is correct...

Ah every time I typed "iwconfig" the channel changes :S

---

### Post by chili555 on 2007-02-23
Hmmm. My iwconfig doesn't show channel. 

Where does this: > reconfiguration is [OK] show up, or are you saying no errors spit out of the terminal?

Can you do sudo ifup wlan0 and tell me if it just dies or if there is some other suspicious output.

We're getting close!

---

### Post by ffxr on 2007-02-23
i have the same issue..

what does Access Point : not associated (from iwconfig) & no IPv6 routers present (syslog) actually mean? what generally causes this error?

can i be certain that my wireless drivers are working properly if i can register an IP address on wlan0? ((it has the correct MAC of my USB wireless NIC)

---

### Post by MMMMManuel on 2007-02-24
Don't leave me alone, eh :P

---

### Post by MMMMManuel on 2007-02-24
> **chili555 said:**
> Hmmm. My iwconfig doesn't show channel. 

Where does this:  show up, or are you saying no errors spit out of the terminal?

Can you do sudo ifup wlan0 and tell me if it just dies or if there is some other suspicious output.

We're getting close!


When I restart network, at the and of reconfiguration I can read on the terminal "[OK]".

The output of ifup wlan0 is "interface wlan0 already configured".

---

### Post by chili555 on 2007-02-24
This: > interface wlan0 already configured suggests wlan0 is now associated. Let's look at sudo ifconfig wlan0. Does it show something like this: ```
 inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
```

We are oh, so close.

---

### Post by MMMMManuel on 2007-02-25
allora, l'output è questo:

link encap:Ethernet Hwaddr [...]
inet addre: my_ip Bcast: 192.168.0.255 {I don't know this address} Mask: 255.255.255.0
UP BROADCAST MULTICAST [...



...]

Where's the address of my gateway? Bcast is not...
LOL

---

### Post by chili555 on 2007-02-25
Wow! You have an IP address, you are associated. Great! You can find your gateway address by doing route -n.

Problem solved???

---

### Post by MMMMManuel on 2007-02-25
> **chili555 said:**
> Wow! You have an IP address, you are associated. Great! You can find your gateway address by doing route -n.

Problem solved???

LOL, I wrote in Italian :P 
Pardon

Well, I don't think the problem is solved... I've a static IP address (no dhcp) and I know my gateway address. 
The problem is that I have not set up the output values of ifconfig in wlan0 configuration! I My values in interfaces file are the correct ones... the only correct addresses of the output given by ifconfig are inet addr and Mask...

---

### Post by MMMMManuel on 2007-02-26
:confused: LOL, don't leave me alone ç_ç

---

### Post by chili555 on 2007-02-26
Are you using WEP now or not? Turn off WEP in your router and then amend your /etc/network/interfaces file to comment out your WEP information, like this:
```
auto eth1
iface eth1 inet dhcp
wireless-essid GBR1
#wireless-key 096c7xxxxxxxxxxxxxxxxxxxxxxafe 

```

Then restart networking and ping -c3 [www.google.com](www.google.com) and let us know.

If it works, we will troubleshoot WEP.

---

### Post by MMMMManuel on 2007-02-27
Well, not eth1, but wlan0.

I turned off wep and commented out the line in interfaces file and when I tried /etc/init.d/networking restart the output was:

*Reconfiguring networkk interfaces...
SIOCDELRT: No such process
[OK]


if I write ping -c3 [www.google.it](www.google.it) the output is:
ping: unkonwn host [www.google.it](www.google.it)

I'm trying without dhcp, but the settings are the same of eth0 my running wired connection.

---

### Post by chili555 on 2007-02-27
I'm getting to the end of my rope! This just can't *NOT* work! Just for my curiosity, can you please post your whole, entire /etc/network/interfaces file? I would like to see the structure of your WEP key in this file, so please leave the first four characters as they are, obscure the rest down to the last four characters that I would also like to see. Kind of like this:```
wireless-key 096cxxxxxxxxxxxxxxxxxxxxxxx4afe
```

---

### Post by MMMMManuel on 2007-02-27
Yes.
The Addresses are correct, the name is correct. The file is(omitting eth0 settings):
```

auto wlan0
iface wlan0 inet static
wireless-essid MyFirstWireless
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key A9E3xxxxxxxxxxxxxxxxxxxxxxxxxxx

```

With this setting, after restarting (ok) i can't ping 192.168.0.1 (my gateway!!!!). The light of the adapter is turned off, but hw is present in ndiswrapper's opinion (and in mine, too, beacause after some minutes the adapter is hot).

The output of "ifconfig wlan0" is:
```

Link encap:Ethernet Hwaddr: [...]
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
[...]

```
Now, what's Bcast? I don't know that address.


The output of iwconfig wlan0 is:
```

802.11b/g ESSID:"MyFirstWireless"
Mode:Managed Channel=4 Access Point: Not-Associated
Bit Rate=11Mb/s Sensitivity=4/6
Retry:on Fragment thr:off
[...]

```

Now why the channel is 4, if I setted up channel 11 in router settings? And why the channel changes every time I type iwconfig wlan0?

---

### Post by chili555 on 2007-02-27
> Now, what's Bcast? I don't know that address.
 That simply means, roughly, this is the neighborhood I will broadcast my presence to. 

> And why the channel changes every time I type iwconfig wlan0? Because the card is looking on all channels for a network to connect with. Channel 4 is just where it was in its search at the instant you asked for iwconfig.

Please do one change to /etc/network/interfaces, comment out wireless-essid MyFirstWireless. I assume, hope, WEP is still commented out and WEP is turned off in the router.

Restart networking and note any ugly messages.

Also, let me see the output of sudo iwlist wlan0 scan.

<fingers crossed>

---

### Post by MMMMManuel on 2007-02-27
Thanks :)


The output is "No scan results". I can think that the problem is here...

---

### Post by chili555 on 2007-02-27
You are right! If there is no router within scan distance, you can't really connect. I suggest rebooting the router (unplug, "uno, duo....dieci" plug in) and trying to scan again. If you get a scan result, then do sudo ifdown wlan0 followed by sudo ifup wlan0, followed by ping -c3 [www.google.it](www.google.it).

Wow, it is very late in Italy!

---

### Post by jasonbrisbane on 2007-02-27
Hello mmmmManuel,

Thought I'd jump in here....

I had the same issues.

Firstly, make sure the router is Open, no WEP/WPA or anything.

then at a terminal window, type:

> sudo wiconfig esssid MyFirstWireless ap 00:11:99:**:** commit

The details after 'ap' are the details of the router. This should be listed in the configuration somewhere (it was in my Dlink 504t)...
After I did this and then did a 'iwconfig' the eth1 (in my case) was associated and up with an DHCP assigned IP listed in ifconfig. (NB: NDISWRAPPER uses wlan0 but the IP is associated with eth1. Strange, I know, but my DHCP works perfectly and I downloaded countless updates and games using Synaptic, so it worked for me!

Oh, make sure you do NOT have the /etc/wpa_supplicant.conf file present (rename is to .bak or something so it isnt picked up - You dont want other programs interfering with the Basic setup while your trying to troubleshoot!

PS: If the light goes on and off, it is because the driver cant talk to the hardware. You might want to do a 

> lspci

and see the NETWORK section for your wireless device. Does it say 'NETWORK X: DISABLED'? (X is a number depending on how many devices you have). If so they the driver isnt working proberly.
Remove the ndiswrapper drivers (inf and sys files - I use the Gui for this - Wireless Windows Drivers) and reinstall it again from the original CD. Remember that you need the Correct INF file and .SYS file (I had two INF files on the cd directory and used the wrong one! When I used the correct file it worked perfectly and the light stayed lit!)

Remember: The light must stay lit BEFORE you can even think about getting an IP address! When the light is lit you will still have the Access Point not associated, but you can then play with the settings  (as above) to get it associated.

Make sure the driver is ok first!

:lolflag: 

Let me know how you go...

Regards,

Jason Brisbane
Ubuntu Newbie

---

### Post by MMMMManuel on 2007-03-01
> **jasonbrisbane said:**
> 
The details after 'ap' are the details of the router. This should be listed in the configuration somewhere (it was in my Dlink 504t)...

The answer is:
```
Error : unrecognised wireless request "MyFirstWireless"
```

> Oh, make sure you do NOT have the /etc/wpa_supplicant.conf file present (rename is to .bak or something so it isnt picked up - You dont want other programs interfering with the Basic setup while your trying to troubleshoot!
I renamed the file, but now I've a directory named wpa_supplicant; I have to reneme it?

PS: If the light goes on and off, it is because the driver cant talk to the hardware. You might want to do a 


> 
and see the NETWORK section for your wireless device. Does it say 'NETWORK X: DISABLED'? (X is a number depending on how many devices you have). If so they the driver isnt working proberly.


LOL, driver isn't working, so. Light is turned off!!
I have to reinstall; can you suggest me which file I've to install? Or what I have to modify?

Thanks a lot :)

---

### Post by MMMMManuel on 2007-03-01
> **chili555 said:**
> You are right! If there is no router within scan distance, you can't really connect. I suggest rebooting the router (unplug, "uno, duo....dieci" plug in) and trying to scan again. If you get a scan result, then do sudo ifdown wlan0 followed by sudo ifup wlan0, followed by ping -c3 [www.google.it](www.google.it).

Wow, it is very late in Italy!

The distance is 1 human step :lolflag:

---

### Post by MMMMManuel on 2007-03-01
Moreover, if I try to ping the ip address of laptop connect through the adaptor, 100% of packets is received! No one is loss!

---

### Post by MMMMManuel on 2007-03-02
Please, don't leave me alone :P

---

### Post by MMMMManuel on 2007-03-04
D'oh, you left me alone ç_ç

---

### Post by chili555 on 2007-03-04
Not sure how we can help you associate to an access point that you cannot see in scanning.

---

### Post by MMMMManuel on 2007-03-04
The problem is that ubuntu can't see it, Xp can (in the same position)...

---

### Post by chili555 on 2007-03-04
I saw this and I yelled, MMMMMMMMMMMManuel!!!!

[http://ubuntuforums.org/archive/index.php/t-206492.html](http://ubuntuforums.org/archive/index.php/t-206492.html)

> iwpriv wlan0 network_type g
iwconfig wlan0 essid "any"
ifconfig wlan0 up
iwlist wlan0 scan


Of course, sustitute your interface for wlan0 and network_type b if you have an 802.11b card.

Let us know, we're hoping for you.

---

### Post by MMMMManuel on 2007-03-05
Uff.... no scan results... the light is yet off...

I inserted those lines: no error.

---

### Post by MMMMManuel on 2007-03-07
Can you tell me which are the files that I must install in ndiswrapper?
I'm thinking that are those ones...

---

### Post by MMMMManuel on 2007-03-12
Problem Not Solved

Bad End

---

### Post by chili555 on 2007-03-12
Is your card installed with ndiswrapper? If so, please tell us what ndiswrapper -l says. Also, could we see dmesg | grep 8187. Thanks.

I love a challenge!

---

### Post by MMMMManuel on 2007-03-14
Excuse me for the absence!

 This is my outputut 

```

ndiswrapper -l

net111v2 driver installed

dmesg | grep 8187 

wlan0: vendor: 'Realtek RTL Wireless LAN USB NIC                                            '

```

---

