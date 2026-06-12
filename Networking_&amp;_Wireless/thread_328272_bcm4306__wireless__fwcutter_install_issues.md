---
title: "bcm4306 / wireless / fwcutter install issues"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by maclenin on 2006-12-30
I am a Linux maiden and soon-to-be mono-boot Xubuntu Edgy Eft (2.16.17.10-generic) user. However, before I take the plunge (and wipe clean all remnants of the windows world from my laptop) I'd like to jump-start my wireless card (Dell Truemobile 1350 / Broadcom 4306 on a Dell Inspiron 600m) within the LiveCD environment (i.e. Linux running from a CD, not from my hard drive).

Essentially, I am trying to extract and install my wireless driver's (bcmwl5.sys) firmware using the fwcutter tool (bcm43xx-fwcutter-006).

A. The first few steps seem productive:

```
sudo mkdir /c
sudo mount /dev/dha2 /c -t ntfs
sudo mkdir /home/utilities
sudo mkdir /home/drivers
sudo cp /c/windows/linux/bcm43xx-fwcutter-006.tar.bz2 /home/utilities
sudo cp /c/windows/system32/drivers/bcmwl5.sys /home/drivers
cd /home/utilities
sudo tar -jxvf bcm43xx-fwcutter-006.tar.bz2 -C /home/utilities

bcm43xx-fwcutter-006/
bcm43xx-fwcutter-006/bcm43xx-fwcutter.1
bcm43xx-fwcutter-006/Makefile
bcm43xx-fwcutter-006/md5.c
bcm43xx-fwcutter-006/README
bcm43xx-fwcutter-006/fwcutter_list.h
bcm43xx-fwcutter-006/fwcutter.c
bcm43xx-fwcutter-006/fwcutter.h
bcm43xx-fwcutter-006/COPYING

ubuntu@ubuntu:/home/utilities$
```

B. Then, I run into trouble. My research tells me that, in a perfect world, these next few steps (with the possible exception of the need for ./configure) should lead to (bcm4306) wireless nirvana:

1. I've run the ./configure and make commands, with the following results. The "make" errors are very selectively summarized:

```
cd /home/utilities/bcm43xx-fwcutter-006
./configure
bash: ./configure: No such file or directory
make

cc -02 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_SOURCE -DFWCUTTER_VERSION_=006   -c -o fwcutter.o fwcutter.c
In file included from fwcutter.c:24:
md5.:4:20: error: stdint.h: No such file or directory
In file included from fwcutter.c:24:
md5.h:7: error: expected specifier-qualifier-list before 'uint32_t'
md5.h:10: warning: struct has no members
In file included from fwcutter.c:25:
fwcutter.h:4:20: error: stdlib.h: No such file or directory
fwcutter.h:5:19: error: ctype.h: No such file or directory
fwcutter.h:6:20: error: string.h: No such file or directory
fwcutter.h:7:19: error: stdio.h: No such file or directory
In file included from fwcutter.c:25:
fwcutter.h:70: error: expected ':', ',', ';', '}' or '_attribute_' before 'flags'
fwcutter.h:90: error: expected ':', ',', ';', '}' or '_attribute_' before 'type'
fwcutter.h:93: warning struct has no members

fwcutter_list.h:1653: error: unknown field 'iv_pos' specified in initializer
fwcutter_list.h:1653: warning: excess elements in struct initializer
fwcutter_list.h:1653: warning: (near initialization for 'files[124]')
fwcutter_list.h:1654: error: unknown field 'iv_map' specified in initializer
fwcutter_list.h:1654: warning: excess elements in struct initializer
fwcutter_list.h:1654: warning: (near initialization for 'files[124]')

fwcutter.c: In function 'do_cmp_arg':
fwcutter.c:655: error: 'size_t' undeclared (first use in this function)
fwcutter.c:655: error: expected ';' before 'arg_len'
fwcutter.c:659: error: 'arg_len' undeclared (first use in this function)
fwcutter.c:659: warning: incompatible implicit declaration of built-in function 'strlen'

fwcutter.c:850: warning: implicit declaration of function 'extract_iv'
fwcutter.c:850: error: 'const struct file' has no member named 'flags'
fwcutter.c:851: error: 'const struct file' has no member named 'iv_pos'
fwcutter.c:852: error: 'const struct file' has no member named 'iv_map'
make: *** [fwcutter.o] Error 1
```

2. I have yet to execute these commands:

```
fwcutter /home/drivers/bcmwl5.sys
cd /home/drivers
sudo make installfw
```

C. Issues and Questions:

I could not run the ./configure command. Perhaps because the tool's Makefile already existed (or ./configure was not a part of the setup script)?

How might I resolve this wave of "make" errors. Could there be a problem with the files I'm trying to make/recompile? Is there something I need to be doing differently?

I can untar fwcutter, I just can't find / generate the fwcutter executable!

Any tiniest bits of advice would be welcomed.

---

### Post by teaker1s on 2006-12-30
fwcutter=12mbit/s is unreliable crap save your self the effort and follow [this ]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by taco_truck on 2006-12-31
I think the bcmwl5.sys driver has to be saved as bcmwl5.inf

---

### Post by maclenin on 2006-12-31
Thanks folks, for the input. I am trying to get this done without a connection to the internet - ergo no access to the latest version of ndiswrapper - the files I am working with (i.e. fwcutter and bcmwl5.sys) were copied from my windows partiton.... Also, my chipset is 4306 (not 4311) - will that make a difference vis a vis ndiswrapper use? Thanks, again.

---

### Post by teaker1s on 2007-01-01
ndiswrapper there should be an .INF that is on manufacturers install cd. you may need cabextract or unzip to extract it. 
Be aware that if bcmwl5.inf that ndiswrapper has installed comes back as invalid driver then you will need the inf driver off your install cd, this too may be bcml5.inf which has been customised for your hardware and should result in working wireless driver:KS

---

### Post by haiku99 on 2007-01-01
> **taco_truck said:**
> I think the bcmwl5.sys driver has to be saved as bcmwl5.inf


that is not correct, those are two different files and both are required....FWIW I copied both from my windows partition
and got ndiswrapper to work on Dapper and Edgy using thids howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by maclenin on 2007-01-02
Thanks for the suggestion - I have seen this howto - and may end up coming back to it - if I can't (stubbornly) get  fwcutter to work.

---

### Post by maclenin on 2007-01-15
This is where I ended up...

[http://ubuntuforums.org/showthread.php?t=332253](http://ubuntuforums.org/showthread.php?t=332253)

...and am currently in wireless connectivity trouble-shoot mode:

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

I chose bcm43xx because it seemed cleaner than ndiswrapper - but am not opposed to wrapping (or another solution) should all else fail....

---

### Post by teaker1s on 2007-01-15
it's your choice but fwcutter=12mbit/s and this is direct sight 
ndiswrapper=54mbit/s and reliability

---

### Post by spd106 on 2007-01-15
Have you tried the wl_apsta.o firmware from this thread [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)?

I found it works well with my BCM4306 based f5d7000 card. After trying to use ndiswrapper for hours and hours, going back to the bcm43xx driver meant that I could connect with WPA. As you have noticed I do get the occasional drop. But typically only once a day.

Fair enough I do take a speed hit over my laptop with an Atheros card, it's about 40% slower i.e. 10 Mbps vs 6Mbps peak, according to iperf. That's certainly better than nothing at all.

---

### Post by maclenin on 2007-01-15
Thanks for the glimmer of hope (re: wl_apsta.o).... I had about 5 minutes of blazing connectivity, then:

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

(The 5 hours mentioned in the link is now, really, only 5 minutes....)

---

### Post by teaker1s on 2007-01-15
follow the link in my signature;)  as I said before fwcutter is crap

---

### Post by spd106 on 2007-01-15
5 minutes,... bah i can beat that.

On win2k I get between 17-20 SECONDS, no thanks to Belkin. They don't provide a WPA update to their wireless utility. So I was forced to either upgrade to XP (no way) or find an alternative third party utility. Enter the free McAfee wireless security assistent. It works well with my f5d7010 cardbus card, but on the f5d7000 pci card it constantly drops, then reconnects. It's a joke!

Since I have to dual boot for University projects, it's rather difficult to get on, so I reboot to Ubuntu whenever I can. The odd dropout seems like a small price to pay.

/rant

Getting back to your problem, you've probably gone back to the other driver firmware. I would suggest that you try out ndiswrapper. You don't need to delete the bcm43xx firmware or driver, just blacklist it and install ndiswrapper alongside. As long as you make sure only one of them is loaded at once you should be ok. You might even be able to script swapping between them.

Since they use different interface names (eth1 and wlan0, last time I checked) you can have them both configured in the /etc/network/interfaces file. No need to comment out or anything.

---

### Post by maclenin on 2007-01-15
teaker: You've said it many times before.... ;)

teaker / spd: I'll post word once I've given the wrapper route a whirl....

---

### Post by maclenin on 2007-01-15
Hmmm.... I get all the way to Step 6 in the ndiswrapper installation guide ([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)) and then I can't seem to find wlan0 via iwconfig (or anywhere, for that matter - other than it's brief mention in /etc/network/interfaces).... The wireless card shows up as eth1. Do I need to "restart in order for the changes to take effect"? Still unable to connect. Any suggestions? Something doesn't seem to be "clicking". FYI (and maybe this is a big deal), I am trying to complete this setup while running Linux from the LiveCD....

---

### Post by teaker1s on 2007-01-15
If your device shows up as wlan0 then you should be able to put your data in through the System-->Administration-->Networking applet.

(If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.)

---

### Post by spd106 on 2007-01-16
Since you're running from the live-cd, the bcm43xx driver will load automatically every time you boot. So the first thing you have to do is remove the kernel module **sudo modprobe -r bcm43xx**. I suggest you check this by scanning through the output of **lsmod**. You will also find that eth1 has disappeared.

Next you will have to install the ndiswrapper-utils package, checking that you also have v1.8 installed. Then install the driver from the bcmwl5.inf and .sys files (or whatever you use). It should be enough to now load this through modprobe. If things have gone right there will be a new wireless device in iwconfig. 

I'm not 100% sure that ndiswrapper works on the live cd. I know it caused a kernel crash back on Breezy and I think also on the original Dapper release. I have not tried the 6.06.1 release or Edgy, chances are this was sorted out.

Sadly installing a newer version ndiswrapper is a lot more complex. You could try making a deb on another PC (or search the web) then transferring it over via a usb key or maybe a cd.

---

### Post by maclenin on 2007-01-16
I remember that reference from the guide - however, when I run the command...

sudo nano /etc/iftab

..."iftab" is empty - no "eth1" line - and nano lists the file as "[ New File ]" as if the file does not exist....

Furthermore, when I navigate through the Thunar file manager - there is no "iftab" file to be found at /etc/iftab....

Any additional thoughts?

---

### Post by maclenin on 2007-01-16
spd (and teaker):

Let me outline some of the more relevant steps I've taken (with reference to your post):

1. As I am (though via livecd) hardwired to the internet to complete the set up of my wireless card, I have been able to download the latest version (1.34) of ndiswrapper (from: [http://sourceforge.net/projects/ndiswrapper)](http://sourceforge.net/projects/ndiswrapper)). NOTE: The output after I run (and after having completed 2. and 3., below)...

```
ndiswrapper -v
```

...is:

```
utils Error: no version specified!
driver version: 1.22
vermagic: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
```

2. I have also loaded the ndis utils package 1.8 you mention, by chance...

Essentially, after running:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

...I received the seemingly common error...

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

...for which (via [http://www.ubuntuforums.org/showthread.php?t=325518&page=2](http://www.ubuntuforums.org/showthread.php?t=325518&page=2)) the following solution was recommended:

```
sudo aptitude install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

3. I ran modprobe, again, (after running the above commands), without errors....

4. Now I find myself in the position I have described regarding the "empty" /etc/iftab file and missing wlan0....

5. Might "sudo modprobe -r bcm43xx" be the answer?

---

### Post by spd106 on 2007-01-16
You can only have one driver module loaded at once. So you have to remove the bcm43xx driver to use ndiswrapper and vice-versa. Running **lsmod | more**, will allow you to step through the loaded modules (you could also pipe it through grep).

You will need to install the build-essential package in order to build ndiswrapper v1.33. This will be gone when you reboot, so it's not really advisable on the live-cd, unless you can use a usb key for persistent changes.

I get this output ```
$ ndiswrapper -v
utils version: 1.9
driver version:        1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

```

/etc/iftab stores persistent name for imterfaces, so it will be pointless to use on the live-cd, unless you plan to use to use it for a long time, adding removing interfaces. Plus, it maps to mac addresses so it will only work if you have multiple cards.

---

### Post by maclenin on 2007-01-16
My reason for running the livecd is just to get everything working - complete all the troubleshooting - in a test environment.... Once I've figured out how to configure, I'll start from scratch and use what I've learned within the livecd to build the permanent space.

Yes, I did install build essential - and used it to build ndiswrapper 1.34....

As you suggested, I  removed bcm43xx using sudo modprobe -r bcm43xx. Eth1 has vanished - and the wireless card is now listed (after running lshw -C network) as UNCLAIMED.... Is there anyway to (without rebooting) "re-claim" the wireless card for ndiswrapper?

I appreciate your help with this process....

---

### Post by spd106 on 2007-01-16
Yes, check that ndiswrapper is installed and configured, **ndiswrapper -l**. You should see something like
```
$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

```
Then **sudo modprobe ndiswrapper**. It probably won't give any feedback, so check it's loaded with **lsmod | grep ndis**. Also check **dmesg | tail**, wlan0 should now have appeared.

---

### Post by maclenin on 2007-01-16
Thanks for the guidance...I am writing this note via the wireless connection!

I have a couple of questions / observations:

1. I reinstalled ndiswrapper and removed bcm43xx using sudo modprobe -r bcm43xx just prior to modprobing ndiswrapper (vs. after modprobe as I'd previously done).

2. Why did I have to remove bcm43xx entirely? Why did blacklisting bcm43xx not suffice? Is this a livecd issue?

3. Also, the "driver version" of ndiswrapper 1.34 still showed as "1.22" after ndiswrapper -v. Why might I be showing the wrong driver version? There were no versions of ndiswrapper installed when I began the installation process.

Alas, all seems well - so far....

Thanks, again for the help! I am sure more questions will ensue....

---

### Post by spd106 on 2007-01-16
1. Not sure, it should work either way, as long as you only have one module loaded at a time.

2. From what I understand the blacklist is used to during the boot process to prevent kernel modules being loaded. When the system is up and running it's a different story, simply blacklisting a module doesn't cause it to be unloaded, you have to tell it specifically. I think this is probably a safer position, especially when some modules shouldn't be removed without removing other dependent modules first.

Since the disc image has the bcm43xx being loaded as default, this is what you boot the live environment and it's what you get after a default install. Only when you have an installed system will the blacklist come into play.

3. Ubuntu does have an ndiswrapper module included, this is probably what you are seeing. You need to install the driver loading tools, i.e. ndiswrapper-utils. At least I think that's right, I do know it must be very complicated or you would see lot's of pre-compiled debs floating around.

Check that you have followed all the instructions correctly. It might not work without a reboot, I honestly don't know.

---

### Post by LavaHot on 2007-01-17
man, thank god you finally got it, but I'm still a little schetchy as to what your steps were from start to finish. I have a bcm4306 puilt in card on my compaq presario r4000 laptop and I've literally worked for days to get the wireless working and I have had absolutely no success. If you could piece together your steps to help me get my machine online, I will be eternally greatful!

---

### Post by maclenin on 2007-01-17
I am putting together a brief "howto" based HEAVILY on  this solid and comprehensive [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") (as well as advice received via this thread from sdp and teaker).

Maybe it will help you wrap things up before I get my version on line....

---

### Post by maclenin on 2007-01-17
spd (et alia): This is where I've ended [_up_]("http://ubuntuforums.org/showthread.php?p=2027150#post2027150") - I think I'll take a closer look at the blacklist of bcm43xx when I finally cut the livecd umbilical.... Removing bcm43xx does seem more "drastic" but should it create any problems if I don't intend on using the bcm43xx module again (especially, if ndis is running smoothly on wlan0)? Thanks, again, for the help re: ndiswrapper install!

---

### Post by teaker1s on 2007-01-17
fwcutter while the attempts the project makes are admirable, the result is 12mb/sec allegedly and useless in reality. It's not particularly hard to reinstall fwcutter-but broadcom seems to work well with ndiswrapper at 54mbit/s so why would you ever want fwcutter back

---

### Post by LavaHot on 2007-01-17
> **maclenin said:**
> I am putting together a brief "howto" based HEAVILY on  this solid and comprehensive [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") (as well as advice received via this thread from sdp and teaker).

Maybe it will help you wrap things up before I get my version on line....

I actually could not get past step 5 in that guide, I kept having make errors. I'll try and see if your guide works for me though, thank you for making it!

---

### Post by spd106 on 2007-01-18
Although ndiswrapper currently offers better results than bcm43xx, I don't think there's any doubt that it will be replaced by bcm43xx in the long term. Particularly as it's in the kernel tree.

About the speed difference. I have seen others run bcm43xx at higher speed, you can do this yourself manually, just **sudo iwconfig rate xxM**. The problem is that it's not as stable at higher speeds and it's already unstable enough at 11Mbps. It would be interesting to do a comparison of the two drivers, I'm surprise someone like phoronix.com haven't done this yet. But I suppose there are so many variables.

Does anyone know whether the [Broadcom,03/23/2006, 4.40.19.0]("ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe") HP driver seen in [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)
is better than the [Broadcom,06/25/2004, 3.40.73.0]("http://ftp.us.dell.com/network/R81433.EXE") Dell driver I found on the ndiswrapper list?
I'm using a 4306 chip. The driver is newer, but that doesn't always mean better. I suppose I could download it and try it out.

---

### Post by teaker1s on 2007-01-18
my advice is stick with the manufacturer of your hardware's driver-from my experience the driver is sometimes tweaked by the manufacturer. This means two identical named drivers from different card manufacturers won't always both work

---

### Post by spd106 on 2007-01-18
Hmm, I switched from the supplied Belkin drivers because even though they worked ok without encryption and with WEP, WPA just didn't work. I tried the Belkin web site for an update, but it was just the same driver. 

After switching to the DELL driver, WPA worked straight away. Maybe it was because I was more experienced by then.

Since ndiswrapper is a fairly generic in it's support I doubt it really takes advantage of the special additions by the card manufacturers.

---

### Post by maclenin on 2007-01-18
Thanks, folks, for all of your guidance - ndiswrapper seems (for now, at least) the clear winner.... In the future, if I choose, for some reason, to switch drivers (in linux using ndiswrapper) would I just need to cabextract the driver executable and re-install the driver using ndiswrapper? Or, would I have to reinstall ndiswrapper from scratch - to switch drivers? Loving the logic of it all....

---

### Post by spd106 on 2007-01-18
There's no need to re-install ndiswrapper, just unload the ndiswrapper module (modprobe), remove the driver (ndiswrapper -e bcmwl5), then add the new driver, same as you did before. You can check which drivers are being used with ndiswrapper -l. All of this information should be in the man pages (man ndiswrapper). 

It gets confusing with all of the extracted driver files with similar names, so I advise you to keep them organised in separate folders. They are redundant once they've been used by ndiswrapper/bcm43xx-fwcutter so they can be deleted, but I like to keep them around just in case.

---

### Post by maclenin on 2007-01-18
Could you be a little more explicit re: "just unload the ndiswrapper module" - how would that look in the command line? sudo modprobe -r "bcmwl5.inf" , for example? (Use lsmod to find the correct name?)

---

### Post by spd106 on 2007-01-18
As an example 

**1. Remove ndiswrapper **
In may case I already have wlan0 up and running after boot. So I have to take it down first. ```
spd106@ubuntu:~$ sudo ifdown wlan0
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.x.x port 67
spd106@ubuntu:~$ sudo modprobe -r ndiswrapper
```**2. Un-install current driver** 
By looking at ndiswrapper -l, I see that I need to remove bcmwl5. I can check that it has gone by looking in the /etc/ndiswrapper directory.
```
spd106@ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
spd106@ubuntu:~$ sudo ndiswrapper -e bcmwl5
spd106@ubuntu:~$ ls -a /etc/ndiswrapper
.   ..
```**3. Install new driver**
I then change to the directory with the new driver (bcmwl5a) and install it.
```
spd106@ubuntu:~$ cd fromdell
spd106@ubuntu:~/fromdell$ ls
bcmwl5a.inf   bcmwl5.sys
spd106@ubuntu:~/fromdell$ sudo ndiswrapper -i bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
```**4. Check**
Now I just have to check that it's been installed and is valid
```
spd106@ubuntu:~/fromdell$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```**5. Re-insert ndiswrapper**
Let's get that interface back up and running, it should automatically  grab an ip address. You can check what has happened in dmesg.```
spd106@ubuntu:~/fromdell$ sudo modprobe ndiswrapper
spd106@ubuntu:~/fromdell$ dmesg 
...
[17212616.420000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17212782.428000] ndiswrapper: device wlan0 removed
[17212782.428000] ACPI: PCI interrupt for device 0000:01:0a.0 disabled
[17212782.428000] usbcore: deregistering driver ndiswrapper
[17212782.468000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17212782.512000] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
[17212782.512000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17212782.524000] ndiswrapper: using IRQ 209
[17212783.172000] wlan0: ethernet device 00:11:50:xx:xx:xx using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: '', 14E4:4320.5.conf
[17212783.176000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17212783.176000] usbcore: registered new driver ndiswrapper
[17212783.232000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17212783.452000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17213021.348000] ndiswrapper: device wlan0 removed
[17213021.352000] ACPI: PCI interrupt for device 0000:01:0a.0 disabled
[17213021.352000] usbcore: deregistering driver ndiswrapper
[17213021.408000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17213021.436000] ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) loaded
[17213021.436000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17213021.444000] ndiswrapper: using IRQ 209
[17213022.092000] wlan0: ethernet device 00:11:xx:xx:xx:xx using NDIS driver: bcmwl5a, version: 0x50000, NDIS version: 0x500, vendor: '', 14E4:4320.5.conf
[17213022.092000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17213022.092000] usbcore: registered new driver ndiswrapper
[17213022.168000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17213022.392000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17213025.984000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17213034.404000] wlan0: no IPv6 routers present
``` As you can see this process is reversible. Though it' s unlikely that you will change much when you find a driver that works.

---

### Post by maclenin on 2007-01-18
Perfect. Thanks. Getting set to divvy up the partitions and wipe windows from the laptop....

---

### Post by maclenin on 2007-01-19
Maybe it's because it's late - but I am having trouble getting my last brain cell around (this particular aspect of) the linux directory concept....

With specific reference to the following examples:

1. I made a directory called "home" in my "/home" or "~" or "~/" directory:

```
ubuntu@ubuntu:~$ mkdir home
```

2. While taking a quick peek at the Thunar File Manager ("Thunar"), I found my new "home" directory in (the way in which I navigated the GUI) /home/ubuntu/home. I then changed directories, via the terminal, in the following manner:

```
ubuntu@ubuntu:~$ cd /home/ubuntu/home
```

**3.** With the following result:

```
ubuntu@ubuntu:~/home$
```

4. After another glance at Thunar, with a similar result, I then changed directories, again, in a slightly different manner:

```
ubuntu@ubuntu:~/home$ cd /home/ubuntu
```

**5.** With this slightly different result:

```
ubuntu@ubuntu:~$
```

My post-midnight logic (coupled with what I witnessed via Thunar) tells me (perhaps naively) that the results of **3.** and **5.**, respectively, should read:

my **3.**

```
ubuntu@ubuntu:~/ubuntu/home$
```

my. **5.**

```
ubuntu@ubuntu:~/ubuntu$
```

Where does the /ubuntu "directory" appear in either of the actual output examples (**3.** and **5.**)? Is /ubuntu not a real "location"? Is this not the way to perceive it: /home/ubuntu?

---

### Post by spd106 on 2007-01-19
We're going a little off-topic here, this question belongs more in the newbie sub-forum. So please excuse me if I just confuse you even more.

The problem you have is that your username is ubuntu. This causes confusion because the normal structure is /home/username, This is classes as an absolute reverence and can be used at any time. When you change directory (cd) you can use absolute or local references. They are distinguished by the first character being a "/" or not.

If you change the names to something unique rather than two home and two ubuntu, it will become much clearer. You can also see more through combining it with an ls -a command. Your true home directory contains many hidden . files, used for settings.

---

### Post by maclenin on 2007-01-19
I had discovered the hidden files (ls -a) and will probably come to terms with the absolutes and locals as I continue dabbling.... I'll work my way back to topic very soon....

Thanks for your repeated attempts to confuse....

Addendum: I have co-posted my directory structure query [here]("http://ubuntuforums.org/showthread.php?t=341915")....

---

### Post by lukemack on 2007-01-20
maclenin - can you post details of how you got WPA working with ndiswrapper? I can connect fine without encryption but need to get WPA working. there seem to be conflicting guides and posts on this. did you edit /etc/wpa_supplicant.conf , or /etc/network/interfaces or both?

can you post your interfaces and conf files? (just hash out your keys if you like!)

thanks,

lukemack.

---

### Post by maclenin on 2007-01-20
I have not tested these settings on my own, yet - but what I can do is direct you to the "[howto]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")" that I used to get the card going - Step 6 'till the end....

Good luck and let me know if you make any progress....

---

### Post by lukemack on 2007-01-21
thanks - did you install network manager? if so, are you on i386? My add/remove applications panel says that this is not supported on i386??

---

### Post by maclenin on 2007-01-22
I have not installed network manager...I've done most of my configuring from the terminal.... Have you been able to solve your i386 issue?

---

### Post by lukemack on 2007-01-23
yes, though i uninstalled network manager again. I got it installed by enabling more repositories. The built-in network monitor (available on the top and bottom screen panels) seemed to do the same job anyway. I did all the configuration from the terminal and now have WPA working. It was much harder than it should have been but I suspect I wouldn't have had the same problems with a netgear card and will ditch the Belkin at some point. Interestingly, it gets a better signal in Linux than in XP.

My advice to anyone reading this would be to get rid of your Belkin card if you have one. I've had nothing but problems with Belkin products and drivers on Linux or XP. This probably doesn't apply to all cards with Broadcom chipsets though.

I used this guide to get things working - [http://ubuntuguide.org/](http://ubuntuguide.org/) and these are the best guides I have found.

---

### Post by dubbedout on 2007-01-25
I followed these guides and I am able to browse just fine wirelessly, until I reboot and then I loose my connection.  After rebooting if I type:
```

sudo depmod -a
sudo modprobe ndiswrapper

```
then I am again connected via wireless.

What am I doing wrong?  What do I have to do so upon reboot I dont have to type the above commands to get it back?  Thanks!  This is the most helpful forum ever!

---

### Post by maclenin on 2007-01-25
Assuming iwconfig shows your wireless card at wlan0, I would follow Step 6 'till the end (Step 8ish) of this seminal [**_guide_**]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")-to-installing-ndiswrapper, to make your wireless settings "stick"....

---

### Post by zeddock on 2007-05-02
I am coming back to the fountain!

I do not know how I did this, but my wireless card just disappeared!  HELP!

**This may be beyond the scope of this thread, but I have found many answers here..
On the command  sudo lshw -C network I get:
```
jim@lat-lap:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ec:bc:24
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=half firmware=5705-v3.11 ip=128.183.80.234 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:fafec000-fafedfff irq:11
jim@lat-lap:~$ 

```

See the part where is it UNCLAIMED?
What should I do?

TIA,
zeddock

---

### Post by maclenin on 2007-05-02
First, take a leap to this [**_thread_**]("http://ubuntuforums.org/showthread.php?t=340689") and take a run through the guide - and if you have the same problem - post-re-install, drop another line!

---

### Post by zeddock on 2007-05-02
> **maclenin said:**
> First, take a leap to this [**_thread_**]("http://ubuntuforums.org/showthread.php?t=340689") and take a run through the guide - and if you have the same problem - post-re-install, drop another line!


Ooops! That is the thread I thought I was on!
Sorry.

zeddock

---

### Post by maclenin on 2007-05-09
**zeddock:**

I trust you found your way....

---

