---
title: "Feisty Wireless problem"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by bobswat on 2007-04-04
Hello all,

I have a Linksys WUSB54G v2 card which I got to work fine on Dapper (I never had edgy, so I never tried it, but I assume it works fine).  I decided to put feisty on a second partition, but for some reason I can't get it to work.  This is what I did:

```

sudo ndiswrapper -i /linksys/drivers/wusb54gv2.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```

then I did ndiswrapper -l and got:

**wusb54gv2 drivers present hardware present**

but then I go into Networking and theres nothing there...
I don't understand what I'm doing wrong

(oh, and for those of you who insist on using Network Manager, wireless doesn't show up in there either)

Can anybody help me?

---

### Post by bobswat on 2007-04-06
Please All, Answer My Post

---

### Post by bobswat on 2007-04-06
ohhhh, look at me, my name is <insert random ubuntu user's name> and I cant even answer a post, I'm cool....

---

### Post by albs on 2007-04-07
I've used Ndiswrapper before.  Basically, when you use Ndiswrapper, you don't access your wireless network via the Networking screen or Network Manager.

I also didn't use the 2nd and 3rd lines that you used.

I think all I did was reboot my computer and was able to get wireless!  Installing wireless manager, so that you can get a visual indication of your network status, helps too.

---

### Post by Valehru on 2007-04-08
can you give us the full output of ndiswrapper -l

also
lspci

Also the output of 
uname -r

and

ndiswrapper -v

Have you disabled the bcm43xx module?

Thanks.

---

### Post by sirbats on 2007-04-09
> **bobswat said:**
> Hello all,

I have a Linksys WUSB54G v2 card which I got to work fine on Dapper (I never had edgy, so I never tried it, but I assume it works fine).  I decided to put feisty on a second partition, but for some reason I can't get it to work.  This is what I did:


Can anybody help me?

dear all,

I'm also newbie; but ndiswrapper is "old issue" ; dont use ndiswrapper. I have the same hardware, (Linksys WUSB54G ver. 4) work flawlessly in edgy box without any single tweak. I did same at feisty.

feisty by default include rt2500, rt2561, rt25xx driver (see the syanptic) use this driver will be much better.

my rt61 (2561) card work well after uninstall "gone network manager" :=)

happy ubuntu-ing

---

### Post by Fascination on 2007-04-09
> **bobswat said:**
> ohhhh, look at me, my name is <insert random ubuntu user's name> and I cant even answer a post, I'm cool....

Of course the irony here is he has now neglected to answer his own thread. ;)

---

### Post by ubuntukid on 2007-04-12
I have the WUSB54GC and couldn't connect. The problem was that the ndiswrapper driver was conflicting with the rt73 driver which is already installed with ubuntu.

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt73" to that list, reboot the machine and see if that works. Also, don't forget to run modprobe ndiswrapper once you've rebooted.

---

### Post by bobswat on 2007-04-17
> 
Quote:
Originally Posted by bobswat View Post
ohhhh, look at me, my name is <insert random ubuntu user's name> and I cant even answer a post, I'm cool....
Of course the irony here is he has now neglected to answer his own thread. 

hahaha I'm sorry, I was on Spring Break from college with no internet at home:-(  
But anyway....thank you alll for your suggestions, I shall try and get back to you

---

### Post by bobswat on 2007-04-26
> **Valehru said:**
> can you give us the full output of ndiswrapper -l

also
lspci

Also the output of 
uname -r

and

ndiswrapper -v

Have you disabled the bcm43xx module?

Thanks.

bobswat@bobswat-desktop:~$ ndiswrapper -l
Installed drivers:
wusb54gv2               driver installed, hardware present 

bobswat@bobswat-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

bobswat@bobswat-desktop:~$ uname -r
2.6.20-9-generic

bobswat@bobswat-desktop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.30
vermagic:       2.6.20-9-generic SMP mod_unload 586 
bobswat@bobswat-desktop:~$ 


There are the outputs of the things you asked for

Also, I tried blacklisting the rt73, but it didn't help

anybody else have any ideas?

---

### Post by blackbeastofaarrgh on 2007-06-08
I'm having the exact same problem.
If anyone has a solution, **please** post it. I'm desperate.

---

### Post by Shillic on 2007-06-17
I'm having this problem as well.  Will try installing wireless network manager to see if that helps.  Any other ideas?

---

### Post by kevdog on 2007-06-17
You are using a USB wireless device (correct??) so please list:
lsusb  (rather than lspci)

Also I think the answer might be staring you right in the face (I wish all posters would look at the output they are posting):

> bobswat@bobswat-desktop:~$ ndiswrapper -v
utils Error: no version specified!
driver version: 1.30
vermagic: 2.6.20-9-generic SMP mod_unload 586
bobswat@bobswat-desktop:~$ 


Do you see the problem??? No utils version specified.  The problem is with ndiswrapper.  How did you install ndiswrapper.   I would recommend at this point, modprob -r ndiswrapper, uninstalling ndiswrapper if it was installed from repository (synaptic), grabbing the ndiswrapper sources (tar.gz) on sourceforge website [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/), and then compiling and installing from source.

---

