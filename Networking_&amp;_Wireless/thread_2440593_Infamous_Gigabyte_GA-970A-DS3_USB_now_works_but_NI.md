---
title: "Infamous Gigabyte GA-970A-DS3 USB now works but NIC does not 18.04"
date: 2020-04-12
forum: Networking &amp; Wireless
---

### Post by ehkart on 2020-04-12
New to Linux, new to this forum. I realize that there are many other people in the past who have posted on this issue however the fixes offered for their systems worked and mine did not. I am fresh enough to Linux that I follow tutorials without understanding yet what commands actually do(mostly) or what they translate to in layman's terms. 

I recently changed out my mobile, cpu and GPU for a GA-970A-DS3, FX6100 and Radeon HD6870. I have Ubuntu Server 18.04 installed with the Gnome desktop. Had zero issues with the last two boards under the sea installation. I experienced the iommu problems regarding the USB ports not working and no network controller being recognized. I followed the many tutorials found via Google to fix this issue and while my USB ports have been made functional, my Ethernet port is still completely non functional. 

I'm ready to pull my hair out over this after trying so many fixes that I honestly don't really understand in the first place. Uninstalling isn't really an option as there is large amounts of data on this drive I cannot lose. 

I'd be very grateful if someone could offer a fresh solution or help to explain simply what is happening and what the components of the problem are. I'm learning but still am fumbling fairly blindly.

---

### Post by chili555 on 2020-04-12
Let's start by identifying your ethernet device. Please open a terminal and run and post:

```
lspci -nnk | grep 0200 -A3
cat /etc/netplan/*.yaml
ip addr show
```

---

### Post by CelticWarrior on 2020-04-12
Welcome.

> I have Ubuntu Server 18.04 installed with the Gnome desktop.
Was there a point to that tedious exercise? Why didn't you install the regular desktop version?

Now, regarding your hardware, it's a old friend of mine. I no longer use it because I donated it to a ONG and I still maintain it (regulat IT services) so I know for a fact that everything works fine with Ubuntu 18.04 without tweaks, unlike what happened with previous releases up to - guessing here - 16.10.

All you have to do is update UEFI to the latest released, keep IOMMU ON, Secure Boot OFF, everything else is optional. Of course, make sure that the Ethernet is enabled (I have a feeling that's the problem here). Install Ubuntu 18.04 as you normally would, no other boot parameters required whatsoever.

It this wasn't the case you would see this forum and many others as well as AskUbuntu littered with questions and complains about it and you don't, you only see very old threads from the time when your board was new.

---

### Post by ehkart on 2020-04-12
Hey there,

So you're saying just update to the latest firmware and ensure that iommu is enabled? 

The ethernet is in fact enabled; new to Linux, not computers &#55357;&#56834; I realize the board is dated and it's honestly a scrap I had laying around to create a home server for various things. Figured I'd dabble in Linux as I've been told many times it's the cat's meow for servers. 

I'll have a look at the latest firmware and see how that jives with whichever version of the board I have is. 

Simply having someone answer to this is a great start, that is for the input.

---

### Post by ehkart on 2020-04-12
> **chili555 said:**
> Let's start by identifying your ethernet device. Please open a terminal and run and post:

```
lspci -nnk | grep 0200 -A3
cat /etc/netplan/*.yaml
ip addr show
```


I'd Love to reply with the results of entering those commands but with no network controller I can't easily share my outputs. I'm going to try flashing the bios first and see what that provides as the other poster suggested. If that doesn't work, I'll post the outputs via my mobile device.

---

### Post by ehkart on 2020-04-12
> **CelticWarrior said:**
> Welcome.


Was there a point to that tedious exercise? Why didn't you install the regular desktop version?

Now, regarding your hardware, it's a old friend of mine. I no longer use it because I donated it to a ONG and I still maintain it (regulat IT services) so I know for a fact that everything works fine with Ubuntu 18.04 without tweaks, unlike what happened with previous releases up to - guessing here - 16.10.

All you have to do is update UEFI to the latest released, keep IOMMU ON, Secure Boot OFF, everything else is optional. Of course, make sure that the Ethernet is enabled (I have a feeling that's the problem here). Install Ubuntu 18.04 as you normally would, no other boot parameters required whatsoever.

It this wasn't the case you would see this forum and many others as well as AskUbuntu littered with questions and complains about it and you don't, you only see very old threads from the time when your board was new.

As a side note, should I remove the GRUB file changes I made after following the tutorials previously?

---

### Post by ehkart on 2020-04-12
Here's a screen of the commands you advised I throw out. I hope this helps as flashing the bios offered zero solutions. Thanks again for the help!

---

### Post by chili555 on 2020-04-13
Please notice that your netplan file refers to enp[COLOR="#FF0000"]2[/COLOR]s0. Notice that ip addr show says that your relevant ethernet interface is enp**3**s0.

From the terminal:

```
sudo nano /etc/netplan/50-cloud-init.yaml

```
Change the line:
```
enp2s0:
```
To read:
```
enp3s0:
```Spacing, indentation, etc. are crucal. Please proofread twice.

Save (Ctrlo+Enter) and exit (Ctrl+x) the text editor nano. Now do:

```
sudo netplan generate
sudo netplan apply
```

It might take a reboot.

Since you installed the Gnome desktop on top of the server version, Network Manager may be a conflicting factor here. We'll check further if the netplan change is ineffective.

---

### Post by CelticWarrior on 2020-04-13
> **chili555 said:**
> Since you installed the Gnome desktop on top of the server version, Network Manager may be a conflicting factor here. We'll check further if the netplan change is ineffective.

Very likely, good catch!

@ehkart - Yes, just keep the UEFI settings as commented before. The problem with the Ethernet is very likely related with the conflict mention by chili555. Again, installing the desktop version from the start should work.

Please understand that the main difference between server and desktop editions is that the former is intended for headless (no desktop environment), something defeated by installing Gnome. Everything you can do with one you can do with another.

---

### Post by ehkart on 2020-04-13
Interesting! I was getting ready to retrieve the data I wanted to keep and then do a fresh install. Now I'm wondering if that's necessary still after reading your reply about changing the netplan details. 

I think that something worth noting is the fact that I did not realize previously changing the motherboard from BIOS to UEFI would require a fresh install. I'm so used to windows where hardware swaps are adapted by the OS(mostly). I understand that Linux can handle some major hardware changes with ease as I went from an Intel board to an AMD board without issue but both boards were BIOS. I read a post somewhere else in these forums regarding someone moving from BIOS to UEFI and how the responder mentioned BIOS to BIOS is no big deal but BIOS to UEFI is. 

Curiously I do wonder then; when you install Linux, regardless of distro, does it compile it's kernel based on the hardware it is using, creating the kernel to fit the CPU etc? Does this mean that it's more or less stiff in its ability to handle changes without updating it's kernel, sometimes automatically and sometimes necessarily manually? I want to understand more of how Linux works at the basic level and having people to pose questions to is better than watching teenagers on YouTube explain this OS.

---

### Post by ehkart on 2020-04-13
> **CelticWarrior said:**
> Very likely, good catch!

@ehkart - Yes, just keep the UEFI settings as commented before. The problem with the Ethernet is very likely related with the conflict mention by chili555. Again, installing the desktop version from the start should work.


Please understand that the main difference between server and desktop editions is that the former is intended for headless (no desktop environment), something defeated by installing Gnome. Everything you can do with one you can do with another.

Thank you. I was aware that the environment can be navigated via terminal or GUI with the same power, that much I understand about Linux. I grew up in the 80s and 90s so I'm vaguely familiar with BASIC/DOS which seem similar to how terminal works. 

As I mentioned in the quick reply, I did move from a BIOS board to a UEFI board and so if a reinstall is actually necessary, I'll do it after backing up the data I want to keep. If it isn't necessary and altering the netplan file fixes this issue I'll be happy. 

Still lots to learn about the basic Linux environment but I'm enjoying finding out how certain things work in it. If I do reinstall I may do so without a GUI so that I force myself to better learn terminal. 

So far, thanks for the help on this, I appreciate it!

---

### Post by ehkart on 2020-04-13
> **chili555 said:**
> Please notice that your netplan file refers to enp[COLOR="#FF0000"]2[/COLOR]s0. Notice that ip addr show says that your relevant ethernet interface is enp**3**s0.

From the terminal:

```
sudo nano /etc/netplan/50-cloud-init.yaml

```
Change the line:
```
enp2s0:
```
To read:
```
enp3s0:
```Spacing, indentation, etc. are crucal. Please proofread twice.

Save (Ctrlo+Enter) and exit (Ctrl+x) the text editor nano. Now do:

```
sudo netplan generate
sudo netplan apply
```

It might take a reboot.

Since you installed the Gnome desktop on top of the server version, Network Manager may be a conflicting factor here. We'll check further if the netplan change is ineffective.

It worked! Thank you so much! Clearly I need to understand WHY it worked haha. Can you offer a simplified explanation as to what was happening and what we did to solve this issue? 

I vow to continue educating myself on this OS and to be a valued member of this community moving forward as a result of this. Thanks again!

---

### Post by chili555 on 2020-04-13
> when you install Linux, regardless of distro, does it compile it's kernel based on the hardware it is using, creating the kernel to fit the CPU etc? Does this mean that it's more or less stiff in its ability to handle changes without updating it's kernel, sometimes automatically and sometimes necessarily manually?

Not exactly. It scans for hardware and loads the correct drivers not just at installation but at every boot! Some hardware, notably USB devices, even load drivers on the fly. The kernel contains many hundreds of drivers and their dependencies but, unless you swap hardware frequently, like the motherboard, it uses just a few of them at a time. 

Compiling the kernel is a very specialized process that most all of us need never undertake. Those who enjoy such a process usually install Slackware and complain that Ubuntu is too child-like, the Linux for pre-schoolers!

> Can you offer a simplified explanation as to what was happening and what we did to solve this issue?

When you originally installed Ubuntu, on previous hardware, the ethernet device was installed on PCI bus 02:00.0, approximately. Hence the interface was enumerated as enp2s0. That is, approximately en (ethernet) p (pci) 2S0 (bus 02:0).

The installer looked for the designation using a method more sophisticated but similar in function to:

```
ip addr show
```

Based on the information gathered, it populated the netplan file with the correct data. Your server connected and all was happy!

What Ubuntu cannot do, so far, and may never do, since swapping motherboards is a rather rare and unique situation, is redo the file after the swap to reflect the new location of the ethernet device, if, in fact, it has changed. In your case, the new location is PCI bus 03:00:0, enumerated enp3s0.

I suspect that there is also a bit of assumption going on here; that is, if you are running a server, you probably should know all this. Of course, this is of no help to those who build their very first server!

I also suspect that, if you had installed the desktop version, Network Manager would have made this seamless.

Please use thread tools at the top to mark Solved.

---

### Post by ehkart on 2020-04-14
> **chili555 said:**
> Not exactly. It scans for hardware and loads the correct drivers not just at installation but at every boot! Some hardware, notably USB devices, even load drivers on the fly. The kernel contains many hundreds of drivers and their dependencies but, unless you swap hardware frequently, like the motherboard, it uses just a few of them at a time. Compiling the kernel is a very specialized process that most all of us need never undertake. Those who enjoy such a process usually install Slackware and complain that Ubuntu is too child-like, the Linux for pre-schoolers!When you originally installed Ubuntu, on previous hardware, the ethernet device was installed on PCI bus 02:00.0, approximately. Hence the interface was enumerated as enp2s0. That is, approximately en (ethernet) p (pci) 2S0 (bus 02:0).The installer looked for the designation using a method more sophisticated but similar in function to:```
ip addr show
```Based on the information gathered, it populated the netplan file with the correct data. Your server connected and all was happy!What Ubuntu cannot do, so far, and may never do, since swapping motherboards is a rather rare and unique situation, is redo the file after the swap to reflect the new location of the ethernet device, if, in fact, it has changed. In your case, the new location is PCI bus 03:00:0, enumerated enp3s0.I suspect that there is also a bit of assumption going on here; that is, if you are running a server, you probably should know all this. Of course, this is of no help to those who build their very first server!I also suspect that, if you had installed the desktop version, Network Manager would have made this seamless.Please use thread tools at the top to mark Solved.That helps my understanding a lot. Thank you so much for explaining that to me. So in reality I suppose it's not so different from the way windows works with drivers on the fly then. This is in fact my first server, I installed it to run a Minecraft server for our household so the learning curve for me is pretty large at this point. I'm enjoying using terminal and when I installed the desktop, I did so to ensure I had something familiar to play with should the need arise. However so far I've actually found that I use terminal more than the mouse, especially since discovering I can open tabs in terminal! I have had some difficulties learning to control Screen and as a result thought that I was limited to starting the Mc server and then walking away. That discovery alone is golden to me! There is still a ton of information I want to learn about Linux in general and so I plan to browse these forums extensively. Thanks again for the help and I'll pop the closed button now. I welcome any PMs you want to share regarding any notes you think I'll want/need.

---

