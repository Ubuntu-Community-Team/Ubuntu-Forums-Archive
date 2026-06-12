---
title: "Can't connect to internet after update"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by kulpojke on 2007-05-29
I downloaded new updates this afternoon and since then i have not been able to connect to the internet. Ubuntu says it is connected to the wired network, but nothing requiring a connection (i.e. browsing the web, skype, ssh connections)  actually works. Furthermore, my wireless card no longer shows up in the Network Settings window.   Before the update everything worked fine.  As far as I can tell everything is configured the way it was previously.  Eth0 is configured with "roaming mode" enabled.

Unfortunately, I did not look in detail at what was in the update so i really have no idea what is going on.
Any help would be appreciated. Thanks

---

### Post by lionel1024 on 2007-05-31
For what its worth, I too am having this issue. I was afraid to update, because this same thing has happened to me in the past with Dapper, and Edgy. Now feisty is broken. :(

---

### Post by erkka on 2007-05-31
Same with me,
I updated to Dapper and lost my internet.

I have been working with that for some two days
and still there seems not to be a solid answer.

I only managed to find a way to bring the net up manually,
so maybe you could also try this;

1. first, when you boot up, hit ESC to activate the
GRUB-menu.

At least in Dapper it boots by default with kernel
2.6.15-28-386

But I tried to boot with kernel 2.6.12-10-386


2. Then, when you have GNOME up with kernel
2.6.12-10-386, select NetWork settings
and manually activate eth0 (if that is what
you used to use to connect the Net).


That is how it works with me,
it's clumsy because I have to activate eth0
every time I start the system, and I still
have not found a way to make it
to be activated automatically...

is there somebody out there,
could you please help us with the issue?

I think this might have something to do
with the so-called hotplug subsystem,
but I'm not pretty sure.

-Erkka

---

### Post by stoian on 2007-05-31
Same issue here: let's bump these links, perhaps somebody at ubuntu will notice:

[http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem](http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem)
[http://ubuntuforums.org/showthread.php?t=459665](http://ubuntuforums.org/showthread.php?t=459665)

thanks!

---

### Post by nekator on 2007-05-31
I run Dapper Drake and after May 28 (give or take a day) Ubuntu suddenly woke up not recognizing my wired modem...same PC I am currently writing this post on...(running XP hate to say it). I have posted twice in the last two days and have not had a response to my concern...Is there anyone (NASA scientist to 13 year old will do) capable of helping me? I had a hard time convincing my family Ubuntu was the way to go, and everyone has really had it on me eversince this happened...Is ubuntu really not ready for us common human beings?

---

### Post by jfinkels on 2007-05-31
Here are some helpful things you can do:

To check if your wired or wireless ethernet cards are detected and installed by the system, type the following in the terminal
```
sudo lspci -v
```
this will list all cards connected via PCI.

To view a more complete listing of all your hardware, type the following in your terminal:
```
sudo lshw | less
```
you can scroll up and down, left and right with the arrow keys. Press 'q' to quit from the 'less' program.

To list all your network connections, type the following in the terminal:
```
ifconfig -a
```

To view info specifically for wireless cards, type the following in the terminal:
```
iwconfig
```

Now, to test if your ethernet card is functioning properly, type the following in the terminal:
```
ping -t 10 127.0.0.1
```
you should get an output that shows a very short response time (very near zero milliseconds). That means your card is functioning properly.

If your wireless card is not working, most likely, you may need drivers. As a starting point if you need wireless drivers, take a look at this website: [http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

Each person should make his or her own thread for each specific problem! Be sure to post your wireless or ethernet card information specifically, and the problem you're having.

---

### Post by llanitedave on 2007-06-01
Same problem here.  This is infuriating.  I've had to go back to my rarely-used Mac, like someone in need of "rescue".

Using Kubuntu, I have an icon from my KNetwork Manager that announces "Disconnected".

Using the "System Settings", I have eth0 and eth1 both enabled.  I went from automatic to manual and back again.  When I hit the "apply" button, I got the message "The default Gateway IP address is not valid".

Selecting the "Routes" tab, the default Gateway IP address reads 0.0.0.0

I enter the same gateway address that is displayed on the Network Preferences for my Mac.  

I get a message that says "Please wait while saving network settings".  When I exit after the message disappears, the internet is still not connected.

When I go back in the Default Gateway IP address once again displays as 0.0.0.0

The setting I enter simply does not take.

This is a horrible bug!

---

### Post by nekator on 2007-06-01
I agree, after reading related posts all night I have come to these conclusions:

1.- It is a bug present in some update installed during the last two weeks of may (mine happened on May 28th).

2.- Other people seem to be having a similar problem with different modems and setups.

3.- There seems to be a constant denominator: subnet mask is weird.

4.- For those of us who have dual boot PCs, the problem does not show up on the other OS and IP configuration and addresses are different between the OS...

5.- Many people have given hundreds of hours worth of time going over several code submissions and config files, they got no money out of it and have burnt a couple of neurons going overthem, my hat goes off to you!

6.- No one has yet managed to come up with a working solution...

So, based on these possibilities (and for those not willing to wai it out anymore):

1.- Do you think a re-install of the current Ubuntu OS will solve the poblem?
2.- Do you think an upgrade (for those of us not using the latest Ubuntu will do the trick?
3.- How do I go about knowing which Bcast address to use and how would I go about changing the defaults in my 6.06 ubunutu?

Any further suggestions? Please let me know....

---

### Post by cptcrunch on 2007-06-01
Updating to the latest kernel 2.6.20-16-generic broke my wireless. I am going back to 2.6.20-15-generic kernel

---

### Post by stoian on 2007-06-01
a bug has been confirmed here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580)

---

### Post by llanitedave on 2007-06-02
That bug seems only to refer to wireless.  Maybe it's the same bug, but it's the wired connection that I found broken.

---

### Post by stoian on 2007-06-04
> **llanitedave said:**
> That bug seems only to refer to wireless.  Maybe it's the same bug, but it's the wired connection that I found broken.

yes, it the bug in the link above relates to wireless - my wired connection works fine.

---

### Post by Gizim on 2007-06-06
I have the .15 kernel and i have this same problem on a clean install it worked FINE on the LiveCD

---

