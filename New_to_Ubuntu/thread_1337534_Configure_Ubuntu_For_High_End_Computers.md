---
title: "Configure Ubuntu For High End Computers?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-11-25
This is NOT an Ubuntu bashing, I am looking for a solution. Yes, I know, I write a lot, sorry. - lol

I have been a long time off and on Ubuntu user. I have always found the responsiveness of Ubuntu in comparison with XP to vary drastically depending on your hardware.

I've used Ubuntu as well as Windows on many different hardware configurations. I've always found Ubuntu to be a better choice for lower end computers, and Windows for higher end computers. On computers that could barely run XP, I found they would usually run twice as well on Ubuntu. That's where it ends though, on higher-end computers XP would run much better than Ubuntu. Everything is really just much more responsive. I am aware this is not the case for most Ubuntu users, but it is for me. Please don't start a debate, that's not what I'm looking for here.

I started using Windows 7 in the beginning of September and I found myself surprisingly impressed. My laptop had came preloaded with Vista which I decided to give a chance as I had only tried it on a friend's computer previously. After a month nothing had changed, I still hated Vista. I formated and installed Ubuntu 9.04 x64 which I enjoyed much more.

I found Ubuntu wasn't giving me the responsiveness I wanted, so I decided it was time to give Windows 7 a shot. I formated once again and installed Windows 7 Ultimate x64. After such a bad Vista experience I found myself very much surprised by Windows 7. It still had the visual appeal yet it was much more responsive. After nearly 3 months of using Windows 7, I am still very much enjoying it. Microsoft seems to have redeemed themselves.

When Ubuntu 9.10 was released, I decided to give it a shot. I set up a dual boot configuration. I hate to say it, but I found it not very responsive. I don't know if I've just been unlucky with my hardware configurations just not having proper drivers for Ubuntu? Or maybe something else along those lines?

I'm using a Dell 1545 laptop (2.2GHz Dual Core CPU/4GB RAM). If I could find a way to get Ubuntu responding as well as Windows 7, I would make the switch right away. I've always found Ubuntu to be much more productive and customizable. I love being able to have multiple taskbars (panels, I know) on a single monitor in Ubuntu, as well as multiple desktops (without third party software like Dexpot for Windows). 

The only thing I would miss from Windows is the new SuperBar which I would love to find a way to (perfectly) mimic it's functionality in Ubuntu. I like the grouped applications and window previews).

I don't mean to start up any sort of debate here. I'm looking for suggestions to make the most of my hardware with Ubuntu and increase responsiveness.

Yesterday I installed Xubuntu for the sake of it, I didn't notice any increase in responsiveness. I'll likely switch back to regular Ubuntu.

---

### Post by mikewhatever on 2009-11-25
Can you be more specific and define responsiveness.
Opinions vary, yet quite recently, I've been discussing a prospect of running Ubuntu on older hardware in another thread, and the OP claimed that XP was running faster then Ubuntu, go figure.

---

### Post by ubuntuforums on 2009-11-25
It's basically opening things. Like if I open a folder in Windows 7 it's nearly instant, in Ubuntu it takes a second longer. The same goes for everything else, running Firefox in Windows 7 it starts up in about a second and a half, in Ubuntu it takes probably 3 seconds.

Overall everything seems slower to respond.

edit: maybe I should try different distro... would that make a difference? Or would it basically all be the same?

---

### Post by mikewhatever on 2009-11-25
I'd suggest trying two things, reduce swappiness, and install preload.

sudo echo "vm.swappiness=10" >> sysctl.conf
sudo sysctl -w vm.swappiness=10

sudo apt-get install preload

---

### Post by dearingj on 2009-11-25
Do you have Compiz enabled? Some of its plugins, such as the one that does window open/close animations, can make Ubuntu seem less responsive.

---

### Post by falconindy on 2009-11-25
It's a bit advanced, but recompiling your kernel for preemption and a 1000hz clock frequency can greatly increase desktop response. The default kernel included is extremely vanilla, in an effort to ensure compatibility across a multitude of platforms. In that regard, a little tweaking (and a lot of stripping) can go a long way.

---

### Post by pi.boy.travis on 2009-11-25
> **falconindy said:**
> It's a bit advanced, but recompiling your kernel for preemption and a 1000hz clock frequency can greatly increase desktop response. The default kernel included is extremely vanilla, in an effort to ensure compatibility across a multitude of platforms. In that regard, a little tweaking (and a lot of stripping) can go a long way.

+1

If you want maximum performance, look up the exact instruction set for your CPU.  I do this on all my servers, and the performance advantage is huge.

---

### Post by x C0MMAND0 x on 2009-11-25
> **pi.boy.travis said:**
> +1

If you want maximum performance, look up the exact instruction set for your CPU.  I do this on all my servers, and the performance advantage is huge.

How would you go about doing so?

---

### Post by pi.boy.travis on 2009-11-25
> **x C0MMAND0 x said:**
> How would you go about doing so?

Here is a [basic guide]("https://help.ubuntu.com/community/Kernel/Compile"). . .  Be careful and take your time, the first time is always the hardest. . .

---

### Post by Lvcoyote on 2009-11-25
Subscribing to this thread because like the OP, I also notice a little slower performance with 9.10 vs. Win7....

---

### Post by bruno9779 on 2009-11-25
I subscribed too as I am very interested on increasing the responsiveness of my system.

I am not comparing it to Win7 though. It's installer has just done a lot of harm to my machine. 
I will try it against itself (I'll clone my system on a different partition and tweak the copy)

---

### Post by JBAlaska on 2009-11-25
Before going through the advanced course on compiling a kernel 101, I submit to the OP that unless your running a Alienware laptop, laptops are hardly "High End Computers" I would first look at your video driver and check compiz settings if it's running as the likely culprits.

I have several boxes running Ubuntu and a couple could be described as somewhat "High End", all running compiz and ALL running much faster that ANY version of windoze ever did on them.

Please post your laptop model and myself or someone here will be glad to help you make the desktop more responsive.

---

### Post by pi.boy.travis on 2009-11-25
> **JBAlaska said:**
> Before going through the advanced course on compiling a kernel 101, I submit to the OP that unless your running a Alienware laptop, laptops are hardly "High End Computers" I would first look at your video driver and check compiz settings if it's running as the likely culprits.

I have several boxes running Ubuntu and a couple could be described as somewhat "High End", all running compiz and ALL running much faster that ANY version of windoze ever did on them.

Please post your laptop model and myself or someone here will be glad to help you make the desktop more responsive.

It's in the OP's first post:

> I'm using a Dell 1545 laptop (2.2GHz Dual Core CPU/4GB RAM)

---

### Post by JBAlaska on 2009-11-25
I guess it was so long I missed that part LOL.

Graphics accelerator Intel GMA 4500MHD...Yup video driver

---

### Post by NoaHall on 2009-11-25
> **JBAlaska said:**
> I guess it was so long I missed that part LOL.

Graphics accelerator Intel GMA 4500MHD...Yup video driver

+1 . Don't blame Ubuntu, blame Intel for not releasing good drivers/cards.

And I would not call your system high end. Only when your quad core CPU is overclocked to 5.3GHz, you have 16GB or more RAM, and 3 graphics cards on the same system can you call it high-end.

---

### Post by pi.boy.travis on 2009-11-25
> **NoaHall said:**
> +1 . Don't blame Ubuntu, blame Intel for not releasing good drivers/cards.

And I would not call your system high end. Only when your quad core CPU is overclocked to 5.3GHz, you have 16GB or more RAM, and 3 graphics cards on the same system can you call it high-end.

Regardless of the system statistics, a properly customized kernel will do wonders for your performance.

---

### Post by NoaHall on 2009-11-25
> **pi.boy.travis said:**
> Regardless of the system statistics, a properly customized kernel will do wonders for your performance.

Yes, indeed.

To the OP, I will recommend you read about arch if you are familiar with the terminal. It will be a lot faster, really.

---

### Post by Garyhans on 2009-11-25
Please could someone define to me a Highend Computer. Sorry this just doesn't sound Highend to me..  could be me of course.

---

### Post by NoaHall on 2009-11-25
> **Garyhans said:**
> Please could someone define to me a Highend Computer. Sorry this just doesn't sound Highend to me..  could be me of course.

Maybe it was a high-end computer when he bought it.

---

### Post by pi.boy.travis on 2009-11-25
> **Garyhans said:**
> Please could someone define to me a Highend Computer. Sorry this just doesn't sound Highend to me..  could be me of course.


What is or is not "high-end" is totally subjective.  The best computer is the one that easily does what you need it to do, with room to upgrade and expand to meet increasing demands.  *That, * is a high-end machine!

---

### Post by sandyd on 2009-11-25
> **falconindy said:**
> It's a bit advanced, but recompiling your kernel for preemption and a 1000hz clock frequency can greatly increase desktop response. The default kernel included is extremely vanilla, in an effort to ensure compatibility across a multitude of platforms. In that regard, a little tweaking (and a lot of stripping) can go a long way.
This is a simple guide to building a custom kernel....
```

 sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile
 sudo apt-get build-dep linux
sudo apt-get install linux-source
//next two steps might not work, ignore errors
sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
apt-get source linux-ubuntu-modules-$(uname -r)
cd /usr/src
bunzip2 -d kernel*.bz2
tar xvf kernel*tar
cd kernel-source*
sudo make menuconfig
//set your stuff thats in there
sudo make //build the kernel[FONT=Verdana]
[/FONT][FONT=Verdana]sudo make modules //make sure modules are built[/FONT]
sudo make modules_install //install modules
[FONT=Verdana] sudo make install //install kernel
**sudo mkinitramfs -o ./initrd.img-2.6.xx.xx //replace with compiled kernel, HINT, look in /boot for a vmlinuz thats missing a initrd.img**
sudo update-grub
[/FONT]
```[FONT=Verdana]
done.
boot into your nice new fast kernel.
\p.s. you might wanna simply go through all of the config in the menuconfig section. gives you lots of customizations. 
HINT: in the CPU section (or processor, something like that, i dont remember) theres an option for Core2Duo.Xeon
enable it.

oh, and it definately speeds up.
im using a dell 17xx model which is the same as yours, only bigger screen.

might add this to the howtos section if i can actually prove this works.
[/FONT]

---

### Post by Cheesemill on 2009-11-25
carlee,

You've missed out downloading the kernel source, also I get a command not found for bunzip :)

---

### Post by pi.boy.travis on 2009-11-25
> **Cheesemill said:**
> carlee,

You've missed out downloading the kernel source, also I get a command not found for bunzip :)

Interesting, I thought bunzip was in the default install. . . 

```
sudo apt-get install bzip2
```

---

### Post by Cheesemill on 2009-11-25
> **pi.boy.travis said:**
> Interesting, I thought bunzip was in the default install. . . 

```
sudo apt-get install bzip2
```

It is. Still command not found for bunzip though. Do you have it as an alias maybe?

---

### Post by sandyd on 2009-11-25
> **Cheesemill said:**
> carlee,

You've missed out downloading the kernel source, also I get a command not found for bunzip :)
corected.
should have been bunzip2, but whatever..

---

### Post by handydan918 on 2009-11-25
> **mikewhatever said:**
> I'd suggest trying two things, reduce swappiness, and install preload.

sudo echo "vm.swappiness=10" >> sysctl.conf
sudo sysctl -w vm.swappiness=10

sudo apt-get install preload

Swapiness?! With all the ram the OP has!?

---

### Post by harfa on 2009-11-25
I've found windows 7 to be a can of mixed worms, much like karmic. I've had a guy bring me a cheap asus laptop with it, he had a rogue antivirus after having it less than a week, lol. but once i cleaned it up it ran quite well. On the other hand, I had another bring me an expensive dell studio XPS laptop, and it ran like an absolute dog. My guess is dell tweaked the install badly and asus left theirs basically vanilla, but I'm sure I'll find out more in the soon enough. 
All I'm saying is windows 7 seems to be about as patchy as karmic, great to some people, woeful to others...

---

### Post by Lvcoyote on 2009-11-25
The last several posts have me confused.....so which would be the best way to configure the kernel for the system I have Ubuntu on??  Its a Core2Duo E8400 on an Intel P45 Motherboard.

---

### Post by sandyd on 2009-11-25
> **Lvcoyote said:**
> The last several posts have me confused.....so which would be the best way to configure the kernel for the system I have Ubuntu on??  Its a Core2Duo E8400 on an Intel P45 Motherboard.
you will have to recompile the kernal manually. ive posted a untested script above to do that.

---

### Post by JBAlaska on 2009-11-25
carlee, does the default menuconfig account for the SLUB allocator bug and use SLAB allocator instead?

**[COLOR="Red"]Also warning to people new to compiling a kernel, any drivers not using DKMS (Dynamic Kernel Module Support) will have to be re-compiled for the new kernel![/COLOR]**

Just thought someone should point that out. :-)

---

### Post by ubuntuforums on 2009-11-25
For those who are saying my system isn't high end, you're completely missing the point of this discussion. Obviously I'm not talking about a gaming computer. I'm simply talking about a computer that should be more than capable of running any operating system at it's maximum potential. Rather than going into complete detail, I thought it would make things easier and simply say high end (I didn't expect a debate on the definition of a high end computer). After all, we're not discussing gaming, we're discussing desktop performance.

Maximizing visuals effects or disabling them altogether has absolutely no affect on performance. That was the first thing I tried. Windows 7 runs very smooth with all visual effects enabled (which is much more than Ubuntu's default visuals), and with way too many processes running (and it still runs incredibly well).

I actually have the page file disabled in Windows 7, although I didn't notice any increase in speed. Would it be a good idea to disable the swap (page) file (or whatever it's called) in Ubuntu, would that make any noticeable difference?

As for bad drivers, I understand that is pretty much out of our control... but doesn't Dell sell computers with Ubuntu preloaded? Wouldn't they have drivers?

Finally as for compiling the kernel myself, that's something I'll definitely try. I'll get to it just as soon as my downloads finish and I finish my work (currently in Windows 7).

---

### Post by JBAlaska on 2009-11-25
@ubuntuforums, While I can only speak for myself, I don't think anyone was trying to "put down" your computer. It's just that laptops in general are inherently less capable then there desktop counterparts, eg (or is it ie..I get them confused); integrated GPU's, typically 5400RPM HD's  and low wattage CPU's. The point I was trying to make is that on my FrankenAcer 6920, Linux is much more responsive than XP, Vista or W7. The fact that you tried Xubuntu and reported slow performance on it as well...leads me to believe that you have a configuration problem or are a anti-Linux troll (unlikely). And I was just offering my assistance in solving your problem.

Again no disrespect intended.

---

