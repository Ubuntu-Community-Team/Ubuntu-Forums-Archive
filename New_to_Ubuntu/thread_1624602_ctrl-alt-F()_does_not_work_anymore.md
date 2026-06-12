---
title: "ctrl-alt-F(*) does not work anymore"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-11-17
I have found another thread about this but it is in the archives and the link to the solution is broken.

I dont know when that happened, but, I cannot go to a tty window anymore... 

What can I try ?

---

### Post by Gone fishing on 2010-11-18
I had this problem but it resolved itself after updates however here's a link

[http://ubuntuforums.org/showthread.php?t=1503732&page=2](http://ubuntuforums.org/showthread.php?t=1503732&page=2)

---

### Post by robsoles on 2010-11-18
Hey Mobidoy, more info such as which version of Ubuntu and what window manager, updates etc have been applied would be very helpful.

```
sudo service tty1 restart
```if [CTRL]+[ALT]+[F1] doesn't get you a tty after that (or perhaps even if it does) please post response from:

```
ps aux | grep tty
```
As an alternative, if you've another PC/Laptop on the same LAN as the machine in question and you are desperate for a terminal that won't crash if gdm (or kde or whatever) is stopped or restarted then you can SSH in and get things done - say so if you want to pursue (or checkout) this method and don't know how.

---

### Post by robsoles on 2010-11-18
Also, please tell us what video card you are using and if you have installed proprietary drivers or if you are using the Canonical drivers.

---

### Post by Mobidoy on 2010-11-18
After reading thru your post, I have found out that only F1 and F2 wont work, F3 to F7 are ok. My card is an Nvidia GTX260M on proprietary drivers running on 10.10

I have start playing with it and well, I have learned alot.

First, now my Grub menu is in my native resolution 1440 X 900 X 24, also, TTY 3 to 6 are in that resolution too and now, when I switch back to F7, it does not freeze there. Before, I had to switch back to a TTY and do a gdm start.

Only thing is I cant seem to find how I could set my graphical terminal window to be in the same resolution.

So 2 questions:

1- What can I do to fix TTY 1 and 2

2- How can I change my Grapghical terminal resolution.

Thanx

---

### Post by robsoles on 2010-11-18
Follow the guide (post #3) but read the correction (post #4) to set the kernel's resolution, try your tty1 and tty2.

How's that?

Edit: You have to reboot before trying tty1 and tty2 :)

---

### Post by Mobidoy on 2010-11-18
> **robsoles said:**
> Follow the guide (post #3) but read the correction (post #4) to set the kernel's resolution, try your tty1 and tty2.

How's that?

Edit: You have to reboot before trying tty1 and tty2 :)

Ok, i have tried it (service start) here is the report:

```
root      1188  0.0  0.0   6128   644 tty4     Ss+  02:12   0:00 /sbin/getty -8 38400 tty4
root      1192  0.0  0.0   6128   652 tty5     Ss+  02:12   0:00 /sbin/getty -8 38400 tty5
root      1200  0.0  0.0   6128   648 tty3     Ss+  02:12   0:00 /sbin/getty -8 38400 tty3
root      1205  0.0  0.0   6128   648 tty6     Ss+  02:12   0:00 /sbin/getty -8 38400 tty6
root      1352  1.2  1.5 173900 61904 tty7     Ss+  02:12   5:25 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-m83X6X/database -nolisten tcp vt7
root     13228  0.0  0.0   6128   648 tty2     Ss+  09:24   0:00 /sbin/getty -8 38400 tty2
root     14014  0.0  0.0   6128   644 tty1     Ss+  09:26   0:00 /sbin/getty -8 38400 tty1
1000     14104  0.0  0.0   9224   876 pts/0    S+   09:27   0:00 grep --color=auto tty

```

I am mixed up a bit, which post #3 and 4 are you talking about ?

---

### Post by robsoles on 2010-11-18
Sorry, posted last thing before I went to bed and forgot to paste the link in: [http://www.uluga.ubuntuforums.org/showthread.php?t=1257791](http://www.uluga.ubuntuforums.org/showthread.php?t=1257791)


It occurs to me this morning though that I am wrong and it won't influence tty1 & tty2 but please try it and tell me which bit I am wrong about for sure :)

---

### Post by santosh83 on 2010-11-18
> **robsoles said:**
> Hey Mobidoy, more info such as which version of Ubuntu and what window manager, updates etc have been applied would be very helpful.

```
sudo service tty1 restart
```if [CTRL]+[ALT]+[F1] doesn't get you a tty after that (or perhaps even if it does) please post response from:

```
ps aux | grep tty
```As an alternative, if you've another PC/Laptop on the same LAN as the machine in question and you are desperate for a terminal that won't crash if gdm (or kde or whatever) is stopped or restarted then you can SSH in and get things done - say so if you want to pursue (or checkout) this method and don't know how.

Hi all,

As I'm having much the same issue, I decided to post here instead of a new thread. I tried the instructions above and CTRL-ALT-F1 (others too) doesn't work. Here is the report from ps:

```
santosh@santosh-desktop:~$ ps aux | grep tty
root       877  1.4  1.9 119884 20120 tty7     Ss+  Nov18   9:10 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-ghPhJP/database -nolisten tcp vt7
root       897  0.0  0.0   6128   512 tty4     Ss+  Nov18   0:00 /sbin/getty -8 38400 tty4
root       901  0.0  0.0   6128   516 tty5     Ss+  Nov18   0:00 /sbin/getty -8 38400 tty5
root       908  0.0  0.0   6128   516 tty2     Ss+  Nov18   0:00 /sbin/getty -8 38400 tty2
root       910  0.0  0.0   6128   516 tty3     Ss+  Nov18   0:00 /sbin/getty -8 38400 tty3
root       913  0.0  0.0   6128   516 tty6     Ss+  Nov18   0:00 /sbin/getty -8 38400 tty6
root      4210  0.0  0.0   6128   652 tty1     Ss+  02:05   0:00 /sbin/getty -8 38400 tty1
santosh   4212  0.0  0.0  11336   872 pts/0    S+   02:06   0:00 grep --color=auto tty
```

My problem is I think the CTRL key is simply not working. When I do CTRL-ALT-F1, the main menu pops up, exactly as if I'd done ALT-F1, and similarly for CTRL-ALT-F2, the Run command dialog pops up. As expected, I can't Copy & Paste with CTRL-C and CTRL-V. In fact, anything that involved the CTRL key is crippled!

I tried pulling out & reattaching the keyboard cable many times but the problem persists.

Any suggestions from anyone will be great appreciated.

---

### Post by theDaveTheRave on 2010-11-18
santosh83

if you want to confirm if the ctrl key is working or not I would suggest trying any copy an paste (ctrl-c.... ctrl-v).

After that you will need to look at one of the logs get to see what is happening, sorry I don't know which one off hand, but i'm sure someone else will know.

a quick look suggest you could either use a keylogger, maybe it will be in /var/log/Xorg.log or you may be able to 'remap' the ctrl key to another key (temporarily) just to see if that helps or not.

good luck.

David

---

### Post by santosh83 on 2010-11-18
> **theDaveTheRave said:**
> santosh83

if you want to confirm if the ctrl key is working or not I would suggest trying any copy an paste (ctrl-c.... ctrl-v).

After that you will need to look at one of the logs get to see what is happening, sorry I don't know which one off hand, but i'm sure someone else will know.

a quick look suggest you could either use a keylogger, maybe it will be in /var/log/Xorg.log or you may be able to 'remap' the ctrl key to another key (temporarily) just to see if that helps or not.

good luck.

David

Hi David,

The CTRL key doesn't work. I've tested it by trying CTRL-C & CTRL-V to copy and paste. In addition I've tried other combinations like CTRL-ALT-F1 for tty1 (which was how I initially was alerted to this problem), CTRL-Q to exit apps and so on. I've even tried typing in the keyboard map that pops up in the keyboard settings item of System->Preferences->Keyboard. When each key is pressed, the corresponding key in the keyboard map lights up.

Both right & left Control keys don't work, as well as the "Win" key (between CTRL & ALT), with that little Windows logo. All other keys work just fine. My keyboard layout is plain USA (English.)

It's really mysterious. If it was a hardware issue then I'd guess that more keys (or the entire keyboard) wont work, but it's only these keys. More strangely, when Ubuntu is shutting down, the display briefly switches to a tty and during that short time, I can very well shift between ttys with CTRL-ALT-F(n)!!

So it seems to be an xserver related issue. Everything was fine until a few days back (when I was using Jaunty.) Perhaps an update broke it? And the problem has carried over to Maverick, despite a clean install.

Has anyone encountered this, or have any suggestions/advice?

I can't see any obvious warning or error in Xorg.log. How do I remap the CTRL key?

---

### Post by robsoles on 2010-11-18
> **santosh83 said:**
> ... CTRL key is crippled!

I tried pulling out & reattaching the keyboard cable many times but the problem persists.

Any suggestions from anyone will be great appreciated.

[s]1) Is it both [CTRL] keys - have you re-tried everything using 'the other [CTRL] key'?[/s]

2) Running Compiz? Have you enabled anything at all relating to [CTRL] key in that?

3) Can you get a hold of a USB keyboard and just plug it in and try some copying and pasting then try [CTRL]+[ALT]+[F1] if pasting works via [CTRL]+[V].

---

### Post by santosh83 on 2010-11-18
> **robsoles said:**
> 1) Is it both [CTRL] keys - have you re-tried everything using 'the other [CTRL] key'?

2) Running Compiz? Have you enabled anything at all relating to [CTRL] key in that?

3) Can you get a hold of a USB keyboard and just plug it in and try some copying and pasting then try [CTRL]+[ALT]+[F1] if pasting works via [CTRL]+[V].

Yes, both CTRL keys are equally dead. I tried all the shortcuts with both CTRL keys. And I'm not running compiz. This is a almost pristine Maverick install. Almost all settings are at what default and I haven't installed any additional packages yet, though I've applied all the security updates.

Hmm. This keyboard is a Logitech PS/2 one, and fairly new too. Will try to get hold of a USB keyboard, and post anything else I can find about this problem. Thanks!

---

### Post by robsoles on 2010-11-18
> **santosh83 said:**
> ...

Hmm. This keyboard is a Logitech PS/2 one, and fairly new too. Will try to get hold of a USB keyboard, and post anything else I can find about this problem. Thanks!

Are there any switches on that keyboard? If there is a discreet one underneath shutdown your PC, flick the switch, boot up and try again - fairly reasonable USB keyboards are between $7 and $15 AU and having a spare is not completely silly.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9742275](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9742275) has some OK stuff regarding re-mapping keys.

---

### Post by santosh83 on 2010-11-18
> **robsoles said:**
> Are there any switches on that keyboard? If there is a discreet one underneath shutdown your PC, flick the switch, boot up and try again - fairly reasonable USB keyboards are between $7 and $15 AU and having a spare is not completely silly.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9742275](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9742275) has some OK stuff regarding re-mapping keys.

There are no switches on the keyboard.

And the problem gets stranger and stranger!

Just to test if it was something specific to the X server, I edited /etc/default/grub and sudo update-grub, to make grub stop and show the menu while booting. The default in Ubuntu is to immediately boot the OS.

So having dropped into a root recovery login, I found surprisingly that while CTRL-ALT-F(n) combinations DO work correctly, CTRL+some_alphabetic_key like CTRL-C or CTRL-X **doesn't** work! The kernel also responds correctly to CTRL+ALT+SysReq+S (Emergency sync), so it seems that while the CTRL key is working in combination with ALT, it isn't working with the plain alphabetic keys.

What could be the cause for this really strange condition? Some wrong setting at the keyboard driver level? Or perhaps the keyboard is simply broken?

Thanks for the link! Will try out the directions.

---

### Post by Mobidoy on 2010-11-18
> **robsoles said:**
> Sorry, posted last thing before I went to bed and forgot to paste the link in: [http://www.uluga.ubuntuforums.org/showthread.php?t=1257791](http://www.uluga.ubuntuforums.org/showthread.php?t=1257791)


It occurs to me this morning though that I am wrong and it won't influence tty1 & tty2 but please try it and tell me which bit I am wrong about for sure :)

It solved it, even tho I have made that procedure yesterday, only difference is that I entered vga=355 (from the other procedure) and now, I have 0x0365 and the keys work.

Now I am on 1024X768 instead of 1440x900 in tty mode.

---

### Post by robsoles on 2010-11-18
> **Mobidoy said:**
> It solved it, even tho I have made that procedure yesterday, only difference is that I entered vga=355 (from the other procedure) and now, I have 0x0365 and the keys work.

...

Beauty!

> **Mobidoy said:**
> ...

Now I am on 1024X768 instead of 1440x900 in tty mode.

Is that resolution for tty1 a problem for you? It more or less behaved as I expected after sleeping on it - mode 0x0365 is supposed to be 1440x900 at 24 bit colour and I bet that is functioning correctly for the Kernel's boot but TTYx is different.

I haven't been able to find where to influence per tty resolution yet but I am sure it's possible and fairly sure I will be embarrassed now whether I find it or someone who knows where it is comes across this thread and tells us!

It is under my nose, I'm sure of it :(

---

### Post by Mobidoy on 2010-11-18
> **robsoles said:**
> Beauty!



Is that resolution for tty1 a problem for you? It more or less behaved as I expected after sleeping on it - mode 0x0365 is supposed to be 1440x900 at 24 bit colour and I bet that is functioning correctly for the Kernel's boot but TTYx is different.

I haven't been able to find where to influence per tty resolution yet but I am sure it's possible and fairly sure I will be embarrassed now whether I find it or someone who knows where it is comes across this thread and tells us!

It is under my nose, I'm sure of it :(

it was not a problem, just being fancy but, it was a typo of my part, tty is in 1440x900x24 now.... thanx for the help

---

