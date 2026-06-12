---
title: "After all these years, Ubuntu still finds a way to stink."
date: 2023-05-11
forum: Networking &amp; Wireless
---

### Post by Tominator on 2023-05-11
I remember asking online for free Ubuntu, many years ago. I filled out a form. I was surprised when I got an install CD in the mail. I was in South Carolina and I think that CD came from Sweden. I didn't know anything about computers except how to replace some parts on them. I bought a few computers on EBAY and loaded my copy of Windows on them. Sold them locally and made a little money. It didn't take long before MS called me a pirate, and put an end to my little enterprise by locking out that copy of Windows. That's why I did a little online research and read about Ubuntu. I started using Ubuntu and sold about 10 used computers that were loaded only with Ubuntu. I quit selling computers but I kept right on using Ubuntu, exclusively.  As far as I was concerned the biggest problem with Ubuntu was getting it to work with various devices. That was a lack of drivers problem. To say i didn't know anything about commands is the absolute truth. I don't know much more now about them. 
    Back in the day if I had a problem I would read some forum entries, do some Googling, copy and paste some commands into terminal, and then go buy a device from a list of what worked with Ubuntu. After all these years I have still never learned the commands. But I have gotten better at assessing which online solutions might be worth me trying. YouTube has been a big help. Monkey see, monkey do. That's me. To the point that I made in the title above. Why in the hell has there not been an update in the past year or two, that fixes Ubuntu not being able to use Wifi? Threw a desktop away in disgust, and bought another last week. It came loaded with Windows 10 and Wifi. It works great. Today I got around to downloading 22.04.2 onto the machine. With the help of Youtube I managed to partition the disk, and install Ubuntu into that partition. It worked great, Wifi and everything else. Then I made the mistake of updating the Ubuntu. Keep in mind that I had already made this same mistake on two other machines. As soon as the update was completed, and the machine restarted, no Wifi. The machine and the Ubuntu ,see the Wifi, it just cannot connect. Widows wifi still works fine. I think I've seen at least 50 solutions online. Tried a bunch on that old machine I threw away. This is why I say my beloved Ubuntu, that I have been so faithful to, has found another way to stink. Apparently this way cannot be fixed with an update.

I did quick replies and they did not post to the thread. The essence of my replies is that the wifi worked on these machines until they were updated or upgraded. The new unit: HP Elite 7900 Desktop PC Package, Intel Core 2 Duo Processor, 8GB RAM, 500GB Hard Drive, DVD-RW, Wi-Fi, Windows 10

---

### Post by QIII on 2023-05-11
How about less of a rant and more of a request for assistance and some information about your system?

You haven't posted since 2009, so it is clear that you have not been asking for help here.

---

### Post by Morbius1 on 2023-05-12
And please see this: [https://www.usu.edu/markdamen/writingguide/15paragr.htm](https://www.usu.edu/markdamen/writingguide/15paragr.htm)

---

### Post by VMC on 2023-05-12
> **Morbius1 said:**
> And please see this: [https://www.usu.edu/markdamen/writingguide/15paragr.htm](https://www.usu.edu/markdamen/writingguide/15paragr.htm)

Indeed! Difficult to read or understand. His title says it all in less verbiage.

---

### Post by TheFu on 2023-05-12
People are here to help.  We generally like Ubuntu, but we realize that for new users, it is easy to blame the wrong people for problems.  There are plenty of problems caused by every different group involved, but always remember that Linux distros aren't created by 1 company.  There are 100K different teams involved and most don't work for Canonical.

As for wifi ... you've been around long enough to realize that there are 1000 different wifi hardware makers in the world, each with different ideas about what wifi should and shouldn't accomplish.  Almost all of them don't test on Linux.  Of course, to be viable, they have to test and provide drivers with MS-Windows, so they do.  This applies to most hardware ... they target only MS-Windows and the fact that Linux happens to work, at all, is because either that specific company decided Linux support was important or because some volunteer coders, with the necessary skills, decided they wanted to make a specific driver, for a specific version, of a specific wifi chip.

Really new or niche hardware doesn't get moved to the top of the list for gaining volunteer help, unless the actual person doing the work has that exact hardware.  We see this a bunch with really cheap laptops.  A few friends picked up some "Chinese Specials" $60-$99 laptops from Walmart last year.  Most things worked, but not wifi.  Seems the laptop maker had used the cheapest wifi supplier in China ... which provided the lowest price chips possible that nobody had ever hear about before.  3 of these people got similar laptops - no working wifi.  2 returned the laptops, but one was stubborn and started watching for wifi driver support in the Linux forums to happen.  It took about 6 months and those drivers aren't included in the kernel, so they don't "just work", but he has to pull them as source code from github, compile them, and build a module for the wifi to work.  He likes to tinker, so he doesn't seem to mind.

If you are having issues with Ubuntu, there are lots of other OSes and distros to try.  Feel free.  Find the distro that works best for your needs. Sometimes the best distro for me is Ubuntu, but not always.  I bet all the other long time users here are the same.  Use what works best, when it works for the purpose.

As for the networking of the installer and post-install differences, I've been puzzled by that issue too.  I avoid it by not using wifi and sticking with well-supported wired ethernet cards.  I suspect most people don't want to or cannot do that.  The only idea  I have is that the installation team is different from the ongoing support team, so there are different drivers included for each, but I really don't know.

Anyway, if you'd like help, you'll need to post some facts about the system and the specific hardware that isn't working.  For networking, any of these commands are helpful.  We don't need more than 1.  
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
inxi -N
sudo lshw -sanitize -C network
```
There is a bit of a chicken/egg problem.  The easiest to use commands aren't installed by default in Ubuntu, so you'll likely have to use one of the first 2 commands in the list above.  Once you get networking working again, I'd strongly recommend installing **lshw** and **inxi** to make solving other issues easier.

If you just want to complain, that's fine too.  We all enjoy a good rant. ;)

---

### Post by VMC on 2023-05-12
> A few friends picked up some "**Chinese Specials" $60-$99 laptops from  Walmart **last year.  Most things worked, but not wifi.  Seems the laptop  maker had used the cheapest wifi supplier in China ... which provided  the lowest price chips possible that nobody had ever hear about before.   3 of these people got similar laptops - no working wifi.  2 returned  the laptops, but one was stubborn and started watching for wifi driver  support in the Linux forums to happen.  It took about 6 months and those  drivers aren't included in the kernel, so they don't "just work", but  he has to pull them as source code from github, compile them, and build a  module for the wifi to work.  He likes to tinker, so he doesn't seem to  mind.If those Chinese Specials was Gateway, which I bought for $149, my **wifi** works perfectly. In fact everything works great!

---

### Post by monkeybrain20122 on 2023-05-13
In fact the cheap Chinese wifi chips usually work out of the box since they are adhere to the most basic and therefore standard specifications, same goes with dongos. Usually it is the more fancy stuffs that could cause problems since they may require manufacturer provided drivers.

---

### Post by zebra2 on 2023-05-13
> **monkeybrain20122 said:**
> In fact the cheap Chinese wifi chips usually work out of the box 

Yep! Ubuntu still has the same price as when I started (free),  If you're doing free to start with then cheap is second best. I remember using Ndiswrapper to make wifi drivers. Required a bit of time and testing but it was still free.  So I agree that Ubuntu hasn't improved since then.  My wife seems pretty happy using her Lenovo 15in Laptop with Lunar loaded so if she is happy I'm not going to complain about how much it stinks. 

Incidentally, I also have one of those Gateway Windows systems that sold for $129.  It on the floor leaning against the wall by my desk waiting for tax season.  It wasn't free but it was indeed cheap and easier than a dual boot.  It will also run all of the same open source software that I have on my Mantic system. The Windows system also stinks but It is is cheap enough and works pretty good with Libre Office,  Claws email, Brave browser etc. 

Life is good. Enjoy it!

---

### Post by poorguy on 2023-05-13
Never understood and never will understand how you can complain about something that's free.

No one forced anyone to use Ubuntu that's a user choice.

Unhappy with Ubuntu use something else.

I agree ***zebra2*** Life is good. I Enjoy it.

---

### Post by SeijiSensei on 2023-05-13
I have one of these connected to my TV.

[https://www.newegg.com/p/2SW-007T-00001](https://www.newegg.com/p/2SW-007T-00001)

It has all Intel hardware except for a Realtek wifi adapter. I had no problems installing Kubuntu on my Dell laptop with all Intel parts, but on this device it didn't see the adapter. I fixed the problem by connecting the device to my router with an Ethernet cable and checking the "install third-party software" box during installation. Now it runs like a charm. Plays my collection of Steam games without breaking a sweat, too. Nice little box for cheap money.

---

### Post by Tominator on 2023-05-14
Obviously, you know what you are doing, with Linux. I belong to that very much larger group that does not, with this stuff. What I learned here a long time ago is that there are not a lot of hard and fast, correct opinions here. I can remember seeing many questions asked, that were not responded to, at least in a timely way.  Have things changed? Is there now a part of the forum where problems are indexed and final correct solutions are attached to the problems? Google is probably even worse but it does have one advantage. You can find the various things that other people say worked for them, on their machines, and normally they include lines that can be copied and pasted. It's a mess and there seems to be nowhere a person can go and just look up the answer to their questions. I did not come here here for a solution, I came here to rant. Rant about this huge problem that has to be turning  off a lot of people, to Ubuntu. To elaborate, I believe it was 20.04 that did not have this wifi problem with many machines. Half of the consensus online seems to be changing to an earlier kernal is the solution. I havn't tried that yet. In answer to your question my new machine: HP Elite 7900 Desktop PC Package, Intel Core 2 Duo Processor, 8GB RAM, 500GB Hard Drive, DVD-RW, Wi-Fi, Windows 10, 19in LCD Monitor (Renewed)  $111 delivered and looks like new. P.S. I normally don't need or use wifi. So the problem was easy for me to ignore.

---

### Post by Tominator on 2023-05-14
The machine I threw out was an older Optiplex. I did read something somewhere about the newest kernal not supporting some Broadcom?

---

### Post by Tominator on 2023-05-14
I seem to remember something back in the day about Ubuntu's desire to be a free solution for the good of mankind. I liked that

---

### Post by Tominator on 2023-05-14
The odds are strong that I know some things that you are not very good at.

---

### Post by Tominator on 2023-05-14
I understand what Ubuntu is. I appreciate that people are working for free at a thing they enjoy doing. To clarify my original post. I am talking about machines that had working wifi, no problems. The updates or upgrades caused the wifi to quit working.

---

### Post by QIII on 2023-05-14
Would you like to ask for help?  Would that not be a better use of your time?

---

### Post by zebra2 on 2023-05-14
@tominator
It seems to me that every user has the responsibility to file their own bug reports.  A working wifi chip that fails with a system update is a bug.  Usually this type of wifi bug is corrected with a subsequent kernel update (or two) which would include an update of the driver pool.  Still it would not hurt your own cause to file a bug report so that the kernel team is aware of the problem.

---

### Post by donald187 on 2023-05-14
> **Tominator said:**
> Obviously, you know what you are doing, with Linux. I belong to that very much larger group that does not, with this stuff. What I learned here a long time ago is that there are not a lot of hard and fast, correct opinions here. I can remember seeing many questions asked, that were not responded to, at least in a timely way.  Have things changed? Is there now a part of the forum where problems are indexed and final correct solutions are attached to the problems? Google is probably even worse but it does have one advantage. You can find the various things that other people say worked for them, on their machines, and normally they include lines that can be copied and pasted. It's a mess and there seems to be nowhere a person can go and just look up the answer to their questions. I did not come here here for a solution, I came here to rant. Rant about this huge problem that has to be turning  off a lot of people, to Ubuntu. To elaborate, I believe it was 20.04 that did not have this wifi problem with many machines. Half of the consensus online seems to be changing to an earlier kernal is the solution. I havn't tried that yet. In answer to your question my new machine: HP Elite 7900 Desktop PC Package, Intel Core 2 Duo Processor, 8GB RAM, 500GB Hard Drive, DVD-RW, Wi-Fi, Windows 10, 19in LCD Monitor (Renewed)  $111 delivered and looks like new. P.S. I normally don't need or use wifi. So the problem was easy for me to ignore.

The question and answer site is askubuntu.com.  It was very valuable to me starting out.

---

### Post by Tominator on 2023-05-14
y

---

### Post by Tominator on 2023-05-15
The new system is a HP Compaq Elite 8300 SFF. Processor is an i3-2120 @ 3.30 GHZ 3300MHZ

---

### Post by QIII on 2023-05-15
If you are requesting help, please start a new thread in a support area rather than Chat.

Networking & Wireless would be a fine place.

---

### Post by Tominator on 2023-05-15
My apologies for the long interval before this reply.  The new system is a HP Compaq Elite 8300 SFF. Processor is an i3-2120 @ 3.30 GHZ 3300MHZ 
 Just to clarify what my point is, an update or an upgrade is causing some machines to lose Wifi. I believe 20.04 was the last time I had WIFI. I have never owned a laptop so it's not a big deal for me. I recently had fiber optic hooked up and using WIFI for a desktop in another room is quite a bit cheaper than adding another wired location. That's when the problematic WIFI became a real issue for me.

---

### Post by Tominator on 2023-05-15
Yes thank you. At his point I would like some help. Here is the output to your commands.

```
utertom@putertom-HP:~$ lspci -vk |egrep --after-context=8 'Ethernet|Network'
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
	DeviceName:  Onboard LAN
	Subsystem: Hewlett-Packard Company 82579LM Gigabit Network Connection (Lewisville)
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Memory at f7c00000 (32-bit, non-prefetchable) [size=128K]
	Memory at f7c39000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

 inxi -N
Network:
  Device-1: Intel 82579LM Gigabit Network
    driver: e1000e
  Device-2: Realtek 802.11ac NIC type: USB
    driver: N/A

putertom@putertom-HP:~$ 
sudo lshw -sanitize -C network
  *-network                 
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.19.0-41-generic duplex=full firmware=0.13-4 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:25 memory:f7c00000-f7c1ffff memory:f7c39000-f7c39fff ioport:f080(size=32)
putertom@putertom-HP:~$
``` 

I'm actually using the computer in question right now. I moved it and plugged in the ethernet.
If it's useful, I can also supply this info from another computer.
Thank you

---

### Post by Tominator on 2023-05-16
I see a problem that Ubuntu has, that people who frequent this forum are apparently incapable of seeing. I see it because I'm on the outside looking in. This is the last place that non coder sort of people feel like getting help from. It's intimidating, and they don't speak the language. How can it not be common knowledge here that Ubuntu has a long time problem? How can it not be addressed, that updating or upgrading one's computer, can cause the user to lose WIFI? Is it not still the goal of Ubuntu to be a free resource for all of humanity? Or has Ubuntu devolved into a hobby, and a tool, solely for industry insiders alone? I didn't expect help when I came here. I don't need it either. I still have an ISO of 20.04. WIFI works on that iteration. Plan B is Windows, which I also have. The WIFI on that works too.

---

### Post by aljames2 on 2023-05-16
Have you tried restarting the network manager service after the upgrade:
```
[COLOR=#101010][FONT=-apple-system]sudo systemctl restart NetworkManager.service[/FONT][/COLOR]
```

---

### Post by chili555 on 2023-05-17
> As soon as the update was completed, and the machine restarted, no Wifi. The machine and the Ubuntu ,see the Wifi, it just cannot connect. That's not no wifi, it is wifi but no connection.

You have made a common logical error; that is, if Ubuntu doesn't work perfectly for your exact combination of hardware, router, etc., then it stinks. 

It works perfectly well for 99.5% of us and it doesn't stink.

We still haven't enough information to propose a solution. Please run and post:

```
lsusb
sudo dmesg | grep -i rtl
nmcli device wifi list

```Please only show the line of the nmcli command that shows the network to which you are attempting to connect and redact the MAC address like this:

```
*       XX:XX:XX GBR5      Infra  149   540 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2 WPA3 

```

---

### Post by Frogs Hair on 2023-05-17
> **Tominator said:**
> I see a problem that Ubuntu has, that people who frequent this forum are apparently incapable of seeing. I see it because I'm on the outside looking in. This is the last place that non coder sort of people feel like getting help from. It's intimidating, and they don't speak the language. How can it not be common knowledge here that Ubuntu has a long time problem? How can it not be addressed, that updating or upgrading one's computer, can cause the user to lose WIFI? Is it not still the goal of Ubuntu to be a free resource for all of humanity? Or has Ubuntu devolved into a hobby, and a tool, solely for industry insiders alone? I didn't expect help when I came here. I don't need it either. I still have an ISO of 20.04. WIFI works on that iteration. Plan B is Windows, which I also have. The WIFI on that works too.

 > I didn't expect help when I came here. I don't need it either. 

This thread is a than a waste of community time and energy, sorry to a those who took the time to reply. **Thread Closed **

---

