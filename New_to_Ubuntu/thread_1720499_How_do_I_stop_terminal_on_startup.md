---
title: "How do I stop terminal on startup?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by super mushroom on 2011-04-03
I just downloaded ubuntu 10.10 , downloaded drivers and shut it off. Now when I turn it on it boots up terminal.?  How can I get it to start up the desktop and not terminal? [-o<

---

### Post by sahabcse on 2011-04-03
Please confirm did you installed server edition or desktop? Because there is no GUI in Ubuntu server OS.

---

### Post by super mushroom on 2011-04-03
I installed desktop edition.

---

### Post by TeoBigusGeekus on 2011-04-03
What's your graphics card?
```
lshw -C display
```

---

### Post by super mushroom on 2011-04-03
Ihave a GT215 [GeForce GT 335M]
vendor: nvidia corporation 
It also has intel integrated graphics, Mobile 4 series chipset integrated graphics controller 
I have a alienware m11x r1

---

### Post by dcsoldschool53 on 2011-04-03
**I think your problem has to do with your grub entries. I think it is booting up in recovery mode**. [B]
Check the following link for more information to see if this helps:
[/B][https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by super mushroom on 2011-04-03
> **dcsoldschool53 said:**
> **I think your problem has to do with your grub entries. I think it is booting up in recovery mode**. [B]
Check the following link for more information to see if this helps:
[/B][https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

When I boot my pc it says 

Ubuntu 10.10 david-m11x tty1
david-m11x login:

So I log in and it says
Last login: sun April  3 11:43:05 edt on ttyl
Says mor that is 2 long 2 type on my iPod
Ubuntu 10.10

Welcome to ubuntu!
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
David@david-m11x:~$
So I need grub2?

---

### Post by dcsoldschool53 on 2011-04-03
**I know the screen login that you are now talking about. Normally, when someone wants to goto that screen from Desktop, they would press the key combination Ctrl + Alt + F2, and to return back to Desktop, they would press Ctrl + Alt + F7.**
[B]What drivers did you download? You may have a driver conflicting with your Ubuntu.
[/B]

---

### Post by TeoBigusGeekus on 2011-04-03
See [this]("http://ubuntuforums.org/showthread.php?t=1635305&page=2") thread.

---

### Post by super mushroom on 2011-04-03
I downloaded a wifi driver 2 get wifi working (it worked) and I downloaded a graphics driver so I can switch between nvidia and intel integrated graphics. I just  did ctrl+alt+f7 and this came up

*pluseAudio configured for per-user sessions
 saned disabled; edit /etc/defualt/
*Enableing additional executable binary formats binfmt-support
*Checking battery state...
fsck from utility-linux-ng 2.17.2
/dev/sda1: clean, 161981/9371624 files, 155642/37478040 blocks 
*Starting AppArmor profiles 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

* Setting sensors limits 

and there are also of these [ok] to the right

And when I press ctrl+alt+f2 it goes back
Please help

---

### Post by super mushroom on 2011-04-03
> **TeoBigusGeekus said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=1635305&page=2") thread.

Thanks Alot! Looks like we have the exact same problems :D I'll peruse this later 
Thanks A Bunch!

---

### Post by TeoBigusGeekus on 2011-04-03
The user in thread I gave you managed to solve his problem after enabling the nomodset option in grub.
While at command line, give
```
sudo nano /etc/default/grub
```
Find the line that begins with
```
GRUB_CMDLINE_LINUX_DEFAULT="...."
```
You will have various options inside the quotes.
Add the nomodset option
```
GRUB_CMDLINE_LINUX_DEFAULT="option1 option2 ... nomodset"
```
Ctrl+X to exit and save and then reboot.
Post back with results.

---

### Post by rosencrantz on 2011-04-03
Did you try a live Ubuntu before installing? If you got working graphics then, I suppose the drivers shipped with Ubuntu are sufficient and it's more of a configuration problem.
Cheers,
rosencrantz

---

### Post by dcsoldschool53 on 2011-04-03
> **super mushroom said:**
> I downloaded a wifi driver 2 get wifi working (it worked) and I downloaded a graphics driver so I can switch between nvidia and intel integrated graphics. I just  did ctrl+alt+f7 and this came up
  
Yep:) Try here for conflicting driver info:
:arrow: [http://ubuntuforums.org/showthread.php?t=884190](http://ubuntuforums.org/showthread.php?t=884190)

---

### Post by rosencrantz on 2011-04-03
wait a sec ... do you have an Optimus graphics setup (or any kind of Nvidia hybrid graphics)? Forget about Nvidia proprietary drivers, they don't work, as Nvidia doesn't support switchable graphics at the moment. Try uninstalling everything Nvidia-related - the Intel chip should work out of the box. You could try the nouveau drivers, though; I think they might work at least with the conventional switchable graphics setup.
Bad news is that we're still miles away from hot switching, as this requires a major Xorg overhaul. Check this blog [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) for latest news.

---

### Post by super mushroom on 2011-04-03
Ok I followed teo bigus geekys instructions and nothing changed. 
I don't have nvidia optimus. that only comes with the alienware m11x with intel core i5 or i7 .

---

### Post by TeoBigusGeekus on 2011-04-03
Did you run 
```
sudo update-grub
```
after editing the grub file?

---

### Post by super mushroom on 2011-04-03
> **TeoBigusGeekus said:**
> Did you run 
```
sudo update-grub
```after editing the grub file?
i just did it, shut off my pc then turned it back on and this screen shows up. Well the screen goes up really fast so thats not all of it.
[IMG]http://i55.tinypic.com/256tnbo.jpg[/IMG]

and then its back to 
david-M11x login:

, although now its a bit lower than before, before it was on the top left corner now its in the middle left side of the screen.

Oh and i'm shutting my PC off with the power button i don't know any other way to do it.

---

### Post by TeoBigusGeekus on 2011-04-03
Sorry to hear that your problem isn't fixed.
Anyone else?


> **super mushroom said:**
> Oh and i'm shutting my PC off with the power button i don't know any other way to do it.

```
sudo shutdown -h now
```

---

### Post by ubunt12 on 2011-04-03
hi, try this i think i had the same prob ages ago
when your system is booting up HOLD the SHIFT key to bring up the ubuntu recovery management
then their should be a few options choose the option REPAIR DPKG PACKAGES or something similar then when this is
done reboot at the root terminal (also one of the recovery options)
remember to have an ethernet cable pluged in if you have a laptop otherwise it won't be able to repair the
broken packages.

hope this helps.

---

### Post by super mushroom on 2011-04-03
i dont see "reboot at the root terminal" in the recovery menu

---

### Post by ubunt12 on 2011-04-03
after repairing the broken packages their should be another option
to drop into a root terminal then once in the terminal type:
```

reboot

```
and if you can't find the root terminal and you have repaired the broken packages you could always
hold the power button on your computer to turn it off then turn it back on but that's up to you.

---

### Post by super mushroom on 2011-04-03
ok thanks

---

### Post by ubunt12 on 2011-04-03
kk but have you repaired the packages??

---

### Post by super mushroom on 2011-04-03
well it says 0upgraded, 0 newly installed, 0 to remove and 0 not upgraded. i have my Ethernet wire plugged in .Then i powerd off and on and reboot nothing changed.

---

### Post by ubunt12 on 2011-04-03
ok, sorry i can't help you any further

---

### Post by dcsoldschool53 on 2011-04-03
**I think, you need to un-install one of the video drivers that you are using. As I said before, they are conflicting with one another.**

---

### Post by super mushroom on 2011-04-03
> **dcsoldschool53 said:**
> **I think, you need to un-install one of the video drivers that you are using. As I said before, they are conflicting with one another.**

Thanks i don't really need that driver anyways, but how do i un-install it from the terminal?

When i downloaded that driver i needed to restart for it to work. I shut my pc off and turned it on the next day and this problem happened

---

### Post by dcsoldschool53 on 2011-04-03
Try:
apt-get remove <package name> or sudo apt-get remove <package name>

I think one of them should work for you, and here is a website about the apt-get command.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by super mushroom on 2011-04-03
I Got a solution!!!!!! :D :D :D the driver for the switchable graphics in the m11x i think is what causes the problem, because before i downloaded the driver i had no problems. In the BIOS i switched the graphics from swichable to discrete. so i wont be able to switch my graphics but its fine.

---

### Post by dcsoldschool53 on 2011-04-03
**Don't for get to mark the thread as solved**

---

