---
title: "Netgear WG121 - Error when entering encryption key"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by alpage2 on 2006-11-12
I am running xubuntu 6.10 on an old laptop, and have a Netgear WG121 wireless adapter, which works in Windows.

I followed the instructions in the wiki and ndiswrapper installation instructions, and ndiswrapper seems to have loaded the windows drivers. All seemed to go well, amd dmesg confirms the module is loaded.

I have successfully used iwconfig to enter the network name, but when I try to enter the encryption key, I hit problems.

sudo iwconfig eth1 key restricted {hex key} results in:
Error for wireless request  "Set Encode" (8B2A)
SET failed on device: eth1: Unknown error 524.

I would be grateful for any advice as to what is wrong.

Many thanks
Alan

---

### Post by FrodoB on 2006-11-12
Here are the setup commands, edit to suit your essid and key.

sudo iwconfig eth1 mode "Managed"

sudo iwconfig eth1 key "xxxxxxxxxxxxxxxxxxxxxxxxxx"

sudo iwconfig eth1 essid "Your_Essid"

sudo dhclient eth1

if you want to use ASCII keys then:

sudo iwconfig eth1 key "s:xxxxxxxxxxxxx"

---

### Post by alpage2 on 2006-11-12
> **FrodoB said:**
> Here are the setup commands, edit to suit your essid and key.

sudo iwconfig eth1 mode "Managed"

sudo iwconfig eth1 key "xxxxxxxxxxxxxxxxxxxxxxxxxx"

sudo iwconfig eth1 essid "Your_Essid"

sudo dhclient eth1

if you want to use ASCII keys then:

sudo iwconfig eth1 key "s:xxxxxxxxxxxxx"

The firstand third commands work OK.

The second command fails with an error message as per my first message, above.

Any ideas would be most welcome.

Exploring this a bit deeper, I have come across an inconsistency which may have a bearing on this.

In the netgear manual, the adapter is supposed to support 40 bit (10 hex digits) and 128 bit (26 hex digits) encryption, and in Win XP I am able to set 128 bit encryption, which is used by my network.

However, sudo iwlist eth1 encryption produces the following output:

  eth1 3 key sizes: 40, 104, 256 bits
  4 keys available:
  Error reading wireless keys (SIOCGIWENCODE): operation not permitted

I don't know what is going on here - any help gratefully received. It seems to think that the key should be 104 rather than 128 bits? But if I lop hex digits off the end of the key, I get the same result. Trying to set a 10 hex digit key results in the same error - I'm confused!

Thanks
Alan

---

### Post by FrodoB on 2006-11-12
104 and 128 bit are the same thing.

Nice Wikipedia article on WEP:

[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)

Now you said something about a 10 digit key and there is none. The keys are 13 characters for ASCII and 26 for Hex.

For 26 character Hex:
sudo iwconfig eth1 key "xxxxxxxxxxxxxxxxxxxxxxxxxx"

For 13 character ASCII:

sudo iwconfig eth1 key "s:xxxxxxxxxxxxx"

The "s:" tells iwconfig that this is an ASCII key.

---

### Post by FrodoB on 2006-11-12
A nice wep key generator, gives the equivalent keys in ASCII and HEX. You should probably make some 128bit keys and put then into your router and Ubuntu.

---

### Post by alpage2 on 2006-11-12
FrodoB - thanks for clarifying the key length issue - I'm less confused on that now. However, I am no further on what is causing the error message when I try to use iwconfig to set an encryption key. Any thoughts?

Thanks
Alan

---

### Post by FrodoB on 2006-11-12
Publish the output of a plain iwconfig

$ iwconfig

lets see what is happening here.

---

### Post by alpage2 on 2006-11-13
Hi FrodoB

Thanks for your continuing pateince.

I have loaded the module again (confirmed by dmesg).

Output of iwconfig is:

eth1      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=11  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I was able to set the channel with iwconfig, but it won't let me set the essid or the encryption key.

Thanks
Alan

---

### Post by FrodoB on 2006-11-13
Alan;

We are so close, but something basic is in the way and we can't see it. The Yawnster has spent many days getting his WG121 to work and has kindly made a howto explaining everything that he did.

I suspect something it wrong in your ndiswrapper setup and this howto suggests dropping back to ndiswrapper 1.16. 

The best bet is to start with a clean system and follow this howto carefully and then report back on the key issue, I will bet that this solves it.

Best Regards,

FrodoB

---

### Post by alpage2 on 2006-11-13
Thanks for your help FrodoB - I'll give that a try.

Regards
Alan

---

### Post by FrodoB on 2006-11-13
Sorry, the howto is at:

[https://help.ubuntu.com/community/WifiDocs/Device/WG121#preview](https://help.ubuntu.com/community/WifiDocs/Device/WG121#preview)

Follow carefully, it should work.

---

### Post by yawnster on 2006-11-14
Did this work? I would like to know if it is indeed a working document.. Also if you could take the time to perhaps add in WPA Support it would be great.. Or if you could outline the procedure and I will try and add it in..

Thanks.. Alex

---

### Post by alpage2 on 2006-11-14
Many thanks to both of you. It may take me some time to work through this, I have very little spare time to devote to it, but I will report my progress on this thread, in detail.

Thanks again
Alan

---

### Post by alpage2 on 2006-11-14
OK - I have started working through the instructions, and have overcome the first problem, but need some advice about the second. I'll spell them both out so you can judge what amendments may be needed for the howto.

1. Maybe ubuntu is slightly different, but in xubuntu the command:

  sudo apt-get install update

ran through the package list and deoendencies, but then terminated with:

  E: Couldn't find package update

However, I think I had already reached the fully updated state because I started with the way that I am accustomed to doing it, with two commands:

  sudo apt-get update
  sudo apt-get upgrade

A few packages were upgraded, so this way works for xubuntu.

sudo apt-get install build-essential went fine.

And now for my present confusion, concerning the required symbolic link. Looking at /usr/src, I see that by default I already have two sub-directories containing the headers:

  /usr/src/linux-headers-2.6.17-10
  /usr/src/linux-headers-2.6.17-10-generic

(so it is the 2.6.17-10 kernel that I am running)

Question 1: are the headers enough for compiling ndiswrapper, or will I also need the kernel sources (which seems to be suggested by the insructions on the ndiswrapper site).?

But, using the synaptic package manager, the only kernel sources listed (after uncommenting the universe repository) was for kernal-source-2.4.27, so does not appear to match my kernel.

Question 2: Do I need to go hunting for the 2.6.17-10 kernel sources? - and any tips on that would be most welcome.

Looking at /lib/modules, I have a single subdirectory:

  /lib/modules/2.6.17-10-generic

which includes a 'build' subdirectory, so the second half of the symbolic link will be no problem, once the question of the kernel sources is resolved.

Thanks in anticipation
Alan

---

### Post by yawnster on 2006-11-14
Hmm.. Well I believe there was a typo in the tutorial, but I believe that it was removed by FrodoB..

It should indeed be *sudo apt-get update* and not *sudo apt-get install update*..

As for the kernel link, I didnt bother to get the sources, it seems to work fine without them.. But just give it a try and if theres an error then try downloading the sources..

Good Luck.. Alex

---

### Post by alpage2 on 2006-11-15
Eureka!!  --  it lives!! :o)

I worked through the howto, and there were just a few variations in my xubuntu 6.1o, as follows:

The command:

  sudo apt-get install linux-headers-`uname -r`

checked the package lists etc and informed me that:
  linux-headers-2.6.17-10-generic is already the latest version.

I'm afraid I can't recall if they were installed by default, or if I added them at some point.

The command:

  sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

produced an error message - no such directory.

In xubuntu 6.10, the relevant directory in /usr/src appears to be linux-headers-2.6.17-10-generic (although /usr/src also contains a linux-headers-2.6.17-10 directory, it was the 'generic' version that the system quoted as the latest version). The symbolic link was established with:

  sudo ln -s /usr/src/linux-headers-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build

In xubuntu, gedit was not installed by default, so I used:

  sudo mousepad /etc/modprobe.d/blacklist

Perhaps it was the way that I interpreted it, but where the ndiswrapper instructions caution against using the drivers from the CDROM, I took it to mean download a fresh set, so I downloaded the version 2.0 drivers from the netgear website, and used the files in the ndis5 subdirectory of the expanded archive.

Ndiswrapper compiled fine, and everything went according to the howto.

A final variation is that my wireless network is encrypted, for obvious reasons, so I also used iwconfig to set the encryption, before bringing up the network:

  iwconfig wlan0 key restricted xxxxxxxxxxxxxxxxxxxxxxxxxx

I hope that feedback helps to perfect the howto. Thanks again for your help.

Regards
Alan

---

### Post by alpage2 on 2006-11-15
I just recalled one more variation for the howto:

System->Administration->System Log does not exist in xubuntu, but the successful loading of the kernel module was confirmed by the last few lines of the output from dmesg, and by:

  tail /var/log/messages

Hope that helps.

Cheers
Alan

---

