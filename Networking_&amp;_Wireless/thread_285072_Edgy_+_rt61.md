---
title: "Edgy + rt61"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by niko7865 on 2006-10-26
WMP54G card works fine on a fresh install of dapper but after the upgrade to edgy I no longer have an ra0 but now have wlan0 & wmaster0. ](*,)  Neither responds to scanning for essids. Any ideas on what I could do to get it working?

---

### Post by Cuppa-Chino on 2006-10-26
same problem here! 

it worked fine under dapper and now Edgy decides to do some installing but it just goes nowhere when scanning!

any idea how to make this work with WPA-PSK??? 

btw I have tried compiling and blasting the driver from RaLink on top which worked fine in Dapper but no chance here!

thanks ](*,)

---

### Post by lastrite on 2006-10-26
I have the exact same problem both wlan0 & wmaster0 are displayed instead of ra0 :( 

Please post a fix if found ](*,)

---

### Post by niko7865 on 2006-10-26
Well I did some tweaking and it sees all my wireless acess points now, but after doing:
```
sudo dhclient wlan0
```
It says "wmaster0: unkown device" and can't connect to any of the essid's I assign it with iwconfig. (just goes through DHCPDISCOVER or what ever until it says it coudn't get an address) If I find a solution I'll be sure to post it here for you guys :)

---

### Post by aloysius on 2006-10-26
same problem here. was working beautifully under 6.06...

---

### Post by sblanzio on 2006-10-27
Hey Guys!

I was upgrading, but just before clicking "Continue", I had a little doubt about the RT61 card... I came here to check and I found out it is going to have troubles!!

Please find some fix or I won't be able to upgrade safely.

I trust in you.

tnx

---

### Post by neveceral on 2006-10-27
same problem too :-/

---

### Post by m_bridge on 2006-10-27
same for me, wlan0 and wmaster0
just tried from the live, not installed yet

---

### Post by joefie on 2006-10-27
seems to be a kernel issue. I downgraded my kernel to a drapper version. I bugged some devs about this issue, before edgy was going to be release(6 days i believe), but they didn't care much. The 2.6.17 kernel crashes also on all via chipsets....however there is a workarround. But still. New kernel has to be uploaded asap!!!!!

---

### Post by Tux Aubrey on 2006-10-27
I'm also affected by this and have filed a bug report:

[HTML]https://launchpad.net/distros/ubuntu/+bug/68593[/HTML]

Please add anything else of importance.

---

### Post by Kray on 2006-10-27
Search Launchpad for 'rt61' - there are already ~10 related bugreports filled. Probably many are just duplications, but anyway:
- support for rt61 based wireless card was seriously broken for Dapper (really seriously - using GUI tool for card configuration lead to unbootable os)
- rt61 based cards aren't working in new shiny Edgy

Sadly it looks, that devs have different priorities :/

---

### Post by sblanzio on 2006-10-27
Ok, but in dapper at least it was possible to make it work. I remember I just executed one script I found in these forums and it began working...

Now it seems that RT61 is not supported at all.. and this is not just a "low priority" but is the absolute opposite of "better hardware detection" they are claiming.

I'm glad 6.06 is a LTS (long time support), but I hope this doesn't mean that 6.06 will be my last working ubuntu distro. :-| 

wi-fi is simply necessary to me.

---

### Post by unprinted on 2006-10-27
Ah, well at least I know there's no point in trying to follow the Dapper recipe.

(CWC-903 card, detected as RT2600 chipset and since posting about my problem, I see Edgy is trying to use the RT61 drivers.)

Update: Knoppix 5.0.1, which I think uses the same kernel release, doesn't detect the card at all.

---

### Post by karstendausb on 2006-10-27
I have posted a workaround - using the rt61-drivers from ratech -, which works perfectly for my rt61-card in edgy.

See
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11)
for a description of what to do to get that card working.

---

### Post by D-Evil on 2006-10-27
Please, somebody paste output of ```
sudo dmesg
``` and ```
lsmod
``` commands here (I don't need whole output, just rt61 related things). Also try ```
sudo iwlist wlan0 scan
``` and paste output here. I'm afraid nobody can help you without these informations.

---

### Post by Cuppa-Chino on 2006-10-27
> **karstendausb said:**
> I have posted a workaround - using the rt61-drivers from ratech -, which works perfectly for my rt61-card in edgy.

See
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11)
for a description of what to do to get that card working.

Thanks sounds good can I ask for a hand anyhow? you posted:
```
1) i got the drivers from http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz

```check!

```
2) followed the readme to compile the kernel-module.
the rt61-module compiles fine, as usual linux-headers were required.
copied the firmware and the modified configuration file (set up ssid,wpa etc.) to /etc/Wireless/RT61STA/
Afterwards copied rt61.ko somewhere below /lib/modules/<kernel-version/
and run depmod

```where do you copy the rt61.ko to???

```
3) blacklisted the - broken? - ubuntu kernel module in /etc/modprobe.d/blacklist:
blacklist rt61pci
```check!

```
4) added the ratech-module in /etc/modules
and put an alias in /etc/modprobe.d/aliases:
alias ra0 rt61

```how do I add the ratech-module ? I am sorry if this is really simple but I just do not know / cannot remember

```
5) added the following lines to /etc/network/interfaces:

iface ra0 inet static
address 192.168.7.228
netmask 255.255.255.0
gateway 192.168.7.1
auto ra0

```check!


Thanks in advance

---

### Post by Cuppa-Chino on 2006-10-27
> **D-Evil said:**
> Please, somebody paste output of ```
sudo dmesg
``` and ```
lsmod
``` commands here (I don't need whole output, just rt61 related things). Also try ```
sudo iwlist wlan0 scan
``` and paste output here. I'm afraid nobody can help you without these informations.

my results:

sudo dmesg
```
sudo dmesg
```

lsmod
```
Module                  Size  Used by
rt61pci                37632  0 
```

sudo iwlist wlan0 scan
**once found a neighbours net which is odd as the card was deactivated, when I activated card, did not find anything, never found my net - which definitely on (using it right now)**

---

### Post by D-Evil on 2006-10-27
That's very strange. Probably this driver from new branch (that's why you see wlan0 instead of ra0, this is new driver) is not ready to be used. I'm afraid that only the old driver (the workaround posted above) is usable at this time. Hope that someone will confirm or solve this.

---

### Post by rft183 on 2006-10-27
Hey karstendausb,

Thanks for the workaround.  It worked perfectly.  I was afraid it wouldn't because I tried to compile the drivers on a previous Edgy beta and they wouldn't compile.  It works fine now!

Russel.

---

### Post by sblanzio on 2006-10-27
how did you compile the driver? Did you follow the readme file included with drivers? did you edit some config file too?

could you please explain step by step what you did? so we could file a HowTo for other people too.

thank you very much!

---

### Post by Cuppa-Chino on 2006-10-27
Sorry for asking again...

but I do not understand all of the workaround...

```
Afterwards copied rt61.ko somewhere below /lib/modules/<kernel-version/ and run depmod
```

where do you copy the rt61.ko to???


```
4) added the ratech-module in /etc/modules and put an alias in /etc/modprobe.d/aliases: alias ra0 rt61
```

how do I add the ratech-module ? I am sorry if this is really simple but I just do not know / cannot remember

could somebody please explain how this works??

---

### Post by HJKiener on 2006-10-28
Boy, what a mess. I expected some minor probs with Edgy but this?

Yould someone please help me with compiling? ("First timer" talking here.) I just tried using the RaLink Readme. Untared archive to my Desktop (is this wrong?) and did like I was told and got error message:

1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

Check.

2> $cp Makefile.6  ./Makefile       # [kernel 2.6]
Check.

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version
Both tried to leave this out (as for old kernel) and also ran it.

4> $make all            # compile driver source code
Trouble here. Error msg reads:
root@nola:/home/hajo/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module# make all
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/hajo/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Betrete Verzeichnis '/lib/modules/2.6.17-10-386/build'
make[1]: *** Keine Regel, um »modules« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/lib/modules/2.6.17-10-386/build'
make: *** [all] Fehler 2

Ah, this is German. It says:
root@nola:/home/hajo/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module# make all
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/hajo/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory '/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to create »modules« Quit.
make[1]: Leaving directory '/lib/modules/2.6.17-10-386/build'
make: *** [all] Error 2

Anybody?

Have to say that I *upgraded* from Dapper - so the old RT61 stuff is still in place:
root@nola:/etc/Wireless/RT61STA# ls
rt2561.bin  rt2561s.bin  rt2661.bin  rt61sta.dat

Hope4help,
Hans

---

### Post by unprinted on 2006-10-28
> **D-Evil said:**
> Please, somebody paste output of ```
sudo dmesg
``` and ```
lsmod
``` commands here (I don't need whole output, just rt61 related things). Also try ```
sudo iwlist wlan0 scan
``` and paste output here. 

Here's what I have

**sudo dmseg:**

(lots deleted)
[17179592.592000] input: PC Speaker as /class/input/input1
[17179592.744000] pccard: CardBus card inserted into slot 0
[17179594.052000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179594.200000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
(lots deleted)
[17179597.284000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [C0C8] -> GSI 10 (level, low) -> IRQ 10
[17179597.324000] eth0: Tigon3 [partno(BCM5705mA1) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:08:02:e3:25:f5
[17179597.324000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
[17179597.324000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[17179597.324000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179597.324000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179597.340000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179597.340000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [C0C6] -> GSI 11 (level, low) -> IRQ 11
[17179597.340000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179597.460000] wmaster0: Selected rate control algorithm 'simple'
[17179597.680000] PM: Writing back config space on device 0000:00:13.0 at offset b (was 165d14e4, writing 5a0e11)
[17179597.680000] PM: Writing back config space on device 0000:00:13.0 at offset 3 (was 0, writing 4010)
[17179597.680000] PM: Writing back config space on device 0000:00:13.0 at offset 2 (was 2000000, writing 2000003)
[17179597.680000] PM: Writing back config space on device 0000:00:13.0 at offset 1 (was 2b00000, writing 2b00006)
(lots deleted)
[17179619.640000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179619.640000] IPv6 over IPv4 tunneling driver
[17179660.804000] wlan0: no IPv6 routers present


**lsmod:**

Module                  Size  Used by
(lots deleted) 
tsdev                   9152  0 
rt61pci                37632  0 
80211                 175880  2 rate_control,rt61pci
(lots deleted)


**sudo iwlist wlan0 scan:**

wlan0     Scan completed :
          Cell 01 - Address: 00:10:A7:2C:AF:0E
                    ESSID: ""
                    Mode: Master
                    Frequency: 2.412 GHz
                    Encryption key: on
                    Extra: tsf=0000000d9f8a9d7d

(My wireless network is set up to hide the ESSID.)

---

### Post by Starlight on 2006-10-28
Hi! I have a question... is the workaround driver the same as the one which was used in Dapper?

---

### Post by Cuppa-Chino on 2006-10-28
yes it is - but some of us (like me) stil have a few questions regarding the workaround.... please see [http://ubuntuforums.org/showpost.php?p=1674249&postcount=21](http://ubuntuforums.org/showpost.php?p=1674249&postcount=21) above


NB I did manage to get my Ralink working in Dapper no problem - the issue I have is that the workaround is not 100% clear in a couple of places, I had to wipe my hd though and that is why I up(?)graded to Edgy....

---

### Post by sblanzio on 2006-10-28
So, i did it, and I will explain here what to. I hope this will be a little more clear than previous posts.
At least, this worked for me.

First of all you must be sure you have the headers for your kernel, if you don't, you have to obtain them and install them.
If you've just upgraded to Edgy you'll likely find them here:
[http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10)
(BE SURE TO INSTALL THE RIGHT HEADERS FOR YOUR KERNEL!)
I think you can find them even on the egdy install cd but i'm not sure.

Once you've obtained them move to the same folder where you placed them and write:

sudo dpkg -i linux-headers-2.x.xx.x.deb

If everything went the right way, continue below. 
(you can find part of these steps on the driver readme file and other posts)

1- download [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)

2- move to the same folder where you downloaded this file (even home  or desktop is ok - you will need to use "sudo" otherwise) and write:
```
tar -xvzf RT61_Linux_STA_Drv_1.0.4.0.tar.gz
```3-
```
cd RT61_Linux_STA_Drv_1.0.4.0.tar.gz/Modules
```4- 
```
sudo cp Makefile.6  ./Makefile
```5-
```
sudo make all
```now it should work for a couple of minutes, and then you should come back to console

6-
```

sudo cp rt2561.bin /etc/Wireless/RT61STA/
sudo cp rt2561s.bin /etc/Wireless/RT61STA/ 
sudo cp rt2661.bin /etc/Wireless/RT61STA/

```7-
```

sudo dos2unix rt61sta.dat -f
sudo cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat

```8-
```

sudo /sbin/insmod rt61.ko
sudo /sbin/ifconfig ra0 inet YOUR_IP up

```
9- edit as superuser (root) this file
/etc/modprobe.d/blacklist
and add
```
blacklist rt61pci
```


9B- (EDIT)
edit as superuser the file
/etc/modules
and add
```

rt61

```

9C- (EDIT)
edit as superuser the file
/etc/modprobe.d/aliases
and add
```

alias ra0 rt61

```
I must admit that i'm not sure of this step. This is what I understood in another post where they was saying:
> 
added the ratech-module in /etc/modules
and put an alias in /etc/modprobe.d/aliases:
alias ra0 rt61



10- edit as superuser this file
/etc/network/interfaces
and add
```

iface ra0 inet static
address YOUR_IP
netmask YOUR_NETMASK
gateway YOUR_GATEWAY
auto ra0

```

11-
now edit as superuser the file
/etc/Wireless/RT61STA/rt61sta.dat
filling your data where needed as described in the driver readme file.

reboot

I must admit i didn't understand all the steps, but this worked for me and I hope this will work for you.

I hope i remembered everything. let me know your doubts and if it worked.

bye
sblanzio

---

### Post by Cuppa-Chino on 2006-10-28
thanks that helped! the blacklisting explanation was useful....

I am typing this from EDGY btw and not from a Windo$ reboot! 

one last question how do I ensure that it get loaded everytime?

I had to manually restart the driver:
```
johnny@Superbrummer:~$ sudo /sbin/ifconfig ra0 inet 192.168.0.102 up
Password:
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
j@r:~$ sudo /sbin/insmod rt61.ko
insmod: can't read 'rt61.ko': No such file or directory
j@r:~$ cd Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/
j@er:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$ sudo /sbin/insmod rt61.ko
j@r:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$ sudo /sbin/ifconfig ra0 inet 192.168.0.102 up

```

so how do I auto start the driver???

thanks again

---

### Post by sblanzio on 2006-10-28
uhm i forgot one step in the previous post, but I'm not sure if it actually worked. I already had this card autoloading in dapper and I'm afraid it is still loading because of that...

however, I forgot these two steps:

edit as superuser the file
/etc/modules
and add
```

rt61

```

edit as superuser the file
/etc/modprobe.d/aliases
and add
```

alias ra0 rt61

```

I must admit that i'm not sure of this step. This is what I understood in another post where they was saying:
> 
added the ratech-module in /etc/modules
and put an alias in /etc/modprobe.d/aliases:
alias ra0 rt61


hope all this helps!

---

### Post by karstendausb on 2006-10-28
I am glad to here that the workaround works for you too!

Of course, before you enable autoloading you should load the kernel module with "insmod" as mentioned in the driver-howto,
to make sure it works - and more important that the driver doesn't crash your system ;-)

According to the launchpad bug reports the old ratech-drivers have caused a lot of serious trouble with different ratech-cards in dapper. That's why edgy  uses the new branch from serialmonkey now (which sorrowly doesn't work for rt61-cards any more).

Karsten

---

### Post by Starlight on 2006-10-28
I can't compile the workaround driver... I posted a thread about it here: [http://www.ubuntuforums.org/showthread.php?t=287330](http://www.ubuntuforums.org/showthread.php?t=287330)

---

### Post by lastrite on 2006-10-28
Anyone manage to get it working? I haven't really got the time to be messing around with it at the moment :( 

If someone does manage to get it working, clear n00b proof instructions would be great please.

---

### Post by unprinted on 2006-10-29
> **lastrite said:**
> Anyone manage to get it working? I haven't really got the time to be messing around with it at the moment :( 

If someone does manage to get it working, clear n00b proof instructions would be great please.

Following the expanded instructions above worked for me :) :) :)

The one bit that didn't was getting a message that I don't have dos2unix installed (presumably strips CR/carriage return characters) but this doesn't seem to matter.

This is being sent over the wireless link...

---

### Post by niko7865 on 2006-10-29
Hey thanks for the guide, I'm glad my thread helped to produce something helpful. However trying to 'insmod' my driver didn't work, says it's the wrong format. Any ideas?

---

### Post by Starlight on 2006-10-29
I have the same problem...

is it possible to get the wireless card working using ndiswrapper and the Windows driver? I've never used ndiswrapper before, so I don't know...

---

### Post by tdehoog on 2006-10-29
I figured out that DHCP doesn't work when you compiled the driver. However, this was also an issue in Dapper. But: the solution was posted here:

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

So what i did to get my Linksys WMP54G working under Edgy was following the breezy part of the guide in the thread above.

I hope this is helpful for you guys.

---

### Post by Cuppa-Chino on 2006-10-29
> **sblanzio said:**
> uhm i forgot one step in the previous post, but I'm not sure if it actually worked. I already had this card autoloading in dapper and I'm afraid it is still loading because of that...

however, I forgot these two steps:

edit as superuser the file
/etc/modules
and add
```

rt61

```

edit as superuser the file
/etc/modprobe.d/aliases
and add
```

alias ra0 rt61

```

I must admit that i'm not sure of this step. This is what I understood in another post where they was saying:



tried all that but still not autoloading (works when I manually start it:
```
cd Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/
sudo /sbin/insmod rt61.ko
sudo /sbin/insmod rt61.ko

```

sure somebody is clever enough to see what is wrong :D , thanks

---

### Post by Mad Marty on 2006-10-29
> **Cuppa-Chino said:**
> tried all that but still not autoloading (works when I manually start it:
```
cd Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/
sudo /sbin/insmod rt61.ko
sudo /sbin/insmod rt61.ko

```

sure somebody is clever enough to see what is wrong :D , thanks

You missed out this bit:
> 
Afterwards copied rt61.ko somewhere below /lib/modules/<kernel-version/
and run depmod

So try something like this:
```

sudo cp rt61.ko /lib/modules/2.6.17-10-386/kernel/drivers/net/wireless/rt2x00
sudo depmod

```
You should then be able to do:
```

modprobe rt61

```
without errors.

HTH

---

### Post by unprinted on 2006-10-29
> **sblanzio said:**
> So, i did it, and I will explain here what to. I hope this will be a little more clear than previous posts.
At least, this worked for me.


OK, to demonstrate it's possible :) I'm doing this on a fresh .386 Edgy install.

0. Headers already installed.

2. The created directory doesn't have .tar.gz on the end, and it's Module, not Modules so that line should be 

```
cd RT61_Linux_STA_Drv_1.0.4.0/Module
```

5. Various warnings are shown, including symbol DBG not being defined (presumably it would be if you wanted to debug the driver), a comparison which is always false, and three variables which may being read before anything's been written to them. A bit naughty, but I'm not about to start debugging device drivers.

6. Failed, saying there wasn't such a directory as /etc/Wireless/RT61STA/

So make it:

```
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA
```

.. and then do the copying.

7. As I said earlier, I don't have dos2unix. Does it matter? Let's see...

8. I want a DHCP connection (the wireless router supplies the wireless card with an IP address) so I change the second line to just

```
sudo /sbin/ifconfig ra0 inet up
```

Ah, 'No such device'.

OK, we'll do this later.

10. DHCP connection, so this becomes adding

```
iface ra0 inet dhcp
wireless-essid {my ESSID}
wireless-key {my WEP password, in hex}
auto ra0
```

11. I needed to change the SSID (to my SSID), AuthMode & EncrypType (to my wireless encryption method and authorisation mode), and Key1Str (to my password). 

Is it a good idea to need to change the same info in two places, should I change my password? Dunno.

Ah yes, the .dat file has been copied as a read-only file. So...

```
sudo chmod +w /etc/Wireless/RT61STA/rt61sta.dat
```

Then edit it.

Reboot so the various config files are read, and the driver loaded. (This may not actually be necessary, but I'm used to Windows having to reboot every time you look at it oddly.)

Check with System / Adminstration / Device Manager - yep, my wireless card is now shown as one device, not two.

But... no ra0 device to be found.

OK, what did I do earlier, I didn't do this time?

Ah, from someone else's post:

```
cd RT61_Linux_STA_Drv_1.0.4.0/Module
sudo cp rt61.ko /lib/modules/2.6.17-10-generic/
sudo depmod
```

*Now* we can do the 

```
sudo /sbin/ifconfig ra0 inet up
```

.. and - ah ha! - it works!

Thanks to the people who provided so much of the solution.

Next question :) Do I have to do most of this every time the kernel is updated?

---

### Post by Cuppa-Chino on 2006-10-31
Hi, does anybody else have the impression that wireless connection / http pings are very slow? I am not sure, and my statement is really subjective but I will do some measurements to check it out.

It could also be that Firefox is running very slowly - as once connection is established FTP & HTTP downloads do reach reasonable speeds.

Will also look to find threads on Firefox slowness, but thought I would also ask for your opions.

---

### Post by m_bridge on 2006-10-31
Thank you that's working sweet!

a word on autoloading the module:
i think the appropriate place to put the kernel module is /lib/modules/2.6.17-10-generic/kernel/net/802/
```
sudo cp (...)/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.ko /lib/modules/2.6.17-10-generic/kernel/net/802/
sudo depmod
```

> **Cuppa-Chino said:**
> Hi, does anybody else have the impression that wireless connection / http pings are very slow?
i have that impression too, downloading isn't slow but takes a while to resolve page names. 
May be that is just some dns caching feature that changed between dapper/edgy or Firefox 1.5/2.0

---

### Post by Cuppa-Chino on 2006-10-31
no found it.

due to reinstall some settings were wrong!

solution is found here: [http://www.ubuntuforums.org/showthread.php?t=283472&highlight=slow+firefox]("http://www.ubuntuforums.org/showthread.php?t=283472&highlight=slow+firefox")

---

### Post by vreemde eend on 2006-11-01
Doesn't work for me, ubuntu chrashes on:

```

sudo /sbin/insmod rt61.ko

```

I tried this several times. I also tried to install with ndiswrapper and varrious Windows drivers. Didn't succeed. So after 10 hours of frustration, I still don't have my network running. 

Could somebody please help me?

---

### Post by vreemde eend on 2006-11-01
Now I tried this:
```
sudo modprobe rt61
```
System crashed and refuses to boot. System is completly useless.

---

### Post by layl on 2006-11-01
Followed this guide to the word and it would not work for me.
See [this thread]("http://ubuntuforums.org/showthread.php?t=290418") for details.  The card has status LED on, network monitor shows that it is in receiving mode, counter for received bytes/packets is increasing ... but it wouldn't find my network :-(.  Any ideas ?

---

### Post by vreemde eend on 2006-11-01
I found this ([http://svn.openfoundry.org/usert2500/rt2x00-cvs/README](http://svn.openfoundry.org/usert2500/rt2x00-cvs/README))

> 
==============================================================================
 7: Interfaces
=======================================

===================
 7.1: Wireless interfaces
=========

 After loading the modules two interfaces will now be visible in ifconfig and
 iwconfig, namely wmaster0 and wlan0. The first device is the so called master
 device which is can be used by some userspace tools, but normally can be
 ignored by the user. The second interface wlan0 is the client interface which
 the user can configure.
 With rt2x00 it is possible to run multiple client interfaces with
 only a single device. 1 client interface can run in adhoc, managed or master
 mode while a second interface can run in monitor mode at the same time.
 More client interfaces can be added by issuing the following command
 (with root privileges):

 	# $ echo -n <name> > /sys/class/ieee80211/<dev>/add_iface

 where the variable <name> is the name of the client interface that should be
 added (i.e. wlan1), and <dev> is the physical device where the new client
 interface should be attached to (i.e. phy0).

Don't realy understand what it means, but maybe it helps to analize the problem.

---

### Post by AndyCooll on 2006-11-05
Ok guys, thanks for all your help in putting together this HOWTO, it's proved really useful.

I've got three Belkin G Wireless Network cards. Two of them load by default, no configuring required. This one (version 6000uk), however uses the RT61 chipset.

Following these instructions I've now got the card working, including with WPA. Perfect ...almost.

Unfortunately it doesn't load on boot, so each time I have to do:
```
sudo ifconfig ra0 192.168.2.17 up
sudo /etc/init.d/networking restart
```

How do I get the card to autostart on boot?

---

### Post by neveceral on 2006-11-06
i had the same problem, but now the card is autostarting- try this [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980) HOWTO from judgekaster points g) - h)
(g) write a short script containing (f) to run at startup.

---

### Post by AndyCooll on 2006-11-06
> **neveceral said:**
> i had the same problem, but now the card is autostarting- try this [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980) HOWTO from judgekaster points g) - h)
(g) write a short script containing (f) to run at startup.

Thanks for your reply. Yeah I read that thread, and I've tried that script idea. However no joy. 

Is this how **you** get it to autostart? Just wondering, because if that's the case then it might be worth revisiting. When it didn't work I assumed it was because that work around was actually written for Breezy and edited for Dapper.

---

### Post by neveceral on 2006-11-06
I have edgy eft and i am not 100% sure, if this is,  how i get my wifi card Linksys WMP54G to autostart, but i did everything from page 4, post 38, this thread and wifi was working but it did not autostart, so i tryed to use howto from Judgekaster for breezy and after that it is autostarting with wpa like a charm. So i think, that it helped. :-)

---

### Post by dakakri on 2006-11-06
hm.. folowed the instructions on page 4, and finally got the card working, however, after rebooting the pc, it no longer works...

now the network link light only blinks in short bursts..

dmesg says something like:
> 
rt61: module license 'unspecified' taints kernel.

ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

RT61: RfIcType= 3


Anybody got some sugestions to what went wrong?

---

### Post by Necreia on 2006-11-07
I really hope a solution is found to this.  I've been beating my head over trying to get it to work with my install of Edgy.  Since it was my first time using Linux, I thought it was just me messing things up.

After reformatting and installing the previous version of Ubuntu, I see ra0.

According to the link here: [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=15782#15782](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=15782#15782)

It seems that the wmaster and wlan is from the rt2x00 driver, not the 2500 driver.  Hope that aids in the search for a solution!

---

### Post by Raubsau on 2006-11-09
Thank you sblanzio and unprinted!

In combination, your howtos were successful!

Maybe you can put that together somehow? Or maybe you can send me your "source code" of your posts via PM? Then I'll try to combine them.

Thx anyway,
Raubsau

---

### Post by AndyCooll on 2006-11-10
> **neveceral said:**
> I have edgy eft and i am not 100% sure, if this is,  how i get my wifi card Linksys WMP54G to autostart, but i did everything from page 4, post 38, this thread and wifi was working but it did not autostart, so i tryed to use howto from Judgekaster for breezy and after that it is autostarting with wpa like a charm. So i think, that it helped. :-)

Just want to say thanks for encouraging me to revisit Judgekasters thread. I essentially went through all the steps in that HOWTO and this time it worked like a charm for me too.

I'm not entirely sure what the correct combination is. However my theory is that it is likely to be the steps outlined in Judgekasters HOWTO ([RaLink RT61 Wireless Solved]("http://ubuntuforums.org/showthread.php?t=132980")) plus the editing of the blacklist, modules and aliases files mentioned in post 38 of this thread.

:cool:

---

### Post by Geoff2077 on 2006-11-12
Here is something else that I found that was hindering success. Possibly because I had used the RT61 drivers with Dapper, the folder 
RT61_Linux_STA_Drv1.04.0.tar.gz/Module
already had a lot of previous files. These had the extension "0" rather that "Ko" suggesting they related to earlier 2.4 headers.

I dutifully copied the Makefile.6 file to Makefile, but when I ran the make
sudo make all
I got all that crap about missing instructions. I even tried the 
make -C /usr/src/linux-headers-2.6.17-10 SUBDIRS=$PWD modules

which sort of ran. But when I looked back in the folder
RT61_Linux_STA_Drv1.04.0.tar.gz/Module
there was no sign of the RT61.ko file. Only a RT61.o file.

Short story, if the Module folder already exists, delete all the files in it before running 
tar -xvzf RT61_Linux_STA_Drv1.0.4.0.tar.gz
Then copy Makefile.6 to Makefile
and then run
make all
and low and behold it completes and after I find the RT61.ko file present.

cheer
Geoff

---

### Post by ww2 on 2006-11-15
Anyone willing to write a comprehensive howto to put together everything that was found here? I ordered an Edimax EW-7128G card and it is probably coming with the rt61 chipset --only found out that they changed from rt2500 after making the purchase-- so it would be great to have something "nice and clean" to start using Edgy for the first time. I'm sure a lot of other people would appreciate the effort too.

Thanks.

---

### Post by neveceral on 2006-11-15
look here [http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61]("http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61")

It is complete HOWTO: RT61 on Egdy Eft with WPA

---

### Post by ww2 on 2006-11-15
Thanks for pointing that out and sorry for not searching properly.

---

### Post by unprinted on 2007-02-09
Back in October, I asked...

> **unprinted said:**
> Next question :) Do I have to do most of this every time the kernel is updated?

... and the answer, sadly, is yes, I do.

The RT61 driver in the kernel is still borken, annoyingly, over three months later.

The main changes this time are that you've already created the various directories and the working driver is now version 1.1.0.0

---

