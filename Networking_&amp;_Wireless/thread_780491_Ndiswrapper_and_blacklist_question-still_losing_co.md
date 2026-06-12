---
title: "Ndiswrapper and blacklist question-still losing connection occasionally"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by tomsa on 2008-05-03
I am running gutsy on a gateway t-1625 laptop with the dreaded rtl8187 wifi card.  I have been able to get wifi using Ndiswrapper pretty successfully. When I do any heavy downloading (bittorrent, etc.) it has a habit of disconnecting at random, and I have to reboot to get a connection again.  I have been digging around these forums looking for soluions for this, but I'm not quite there yet.  I think the reason for this is after a while, something goes haywire, and my computer no longer recognizes the wireless card.  When I open up the system->administration->windows wireless drivers menu, it tells me that there's no hardware present.  Could it have something to do with my blacklist?  Does my computer keep trying to load other cards or drivers?  the reason I ask is when I run the command

```
 ndiswrapper -l
``` 

I get this as the output

```
WARNING: /etc/modprobe.d/blacklist line 31: ignoring bad line starting with 'rtl'
WARNING: /etc/modprobe.d/blacklist line 32: ignoring bad line starting with 'r8187'
net8187b : driver installed
        device (0BDA:8189) present

```

Am I barking up the wrong tree here, or am I on to something?

---

### Post by Ayuthia on 2008-05-03
> **tomsa said:**
> I am running gutsy on a gateway t-1625 laptop with the dreaded rtl8187 wifi card.  I have been able to get wifi using Ndiswrapper pretty successfully. When I do any heavy downloading (bittorrent, etc.) it has a habit of disconnecting at random, and I have to reboot to get a connection again.  I have been digging around these forums looking for soluions for this, but I'm not quite there yet.  I think the reason for this is after a while, something goes haywire, and my computer no longer recognizes the wireless card.  When I open up the system->administration->windows wireless drivers menu, it tells me that there's no hardware present.  Could it have something to do with my blacklist?  Does my computer keep trying to load other cards or drivers?  the reason I ask is when I run the command

```
 ndiswrapper -l
``` 

I get this as the output

```
WARNING: /etc/modprobe.d/blacklist line 31: ignoring bad line starting with 'rtl'
WARNING: /etc/modprobe.d/blacklist line 32: ignoring bad line starting with 'r8187'
net8187b : driver installed
        device (0BDA:8189) present

```

Am I barking up the wrong tree here, or am I on to something?

Well you are going somewhere.  You need to check line 31 and 32 in /etc/modprobe.d/blacklist.  It does not like the information in those lines.  /etc/modprobe.d/blacklist is a file that prevents modules from loading.  Each line should just have a module listed or else a # at the beginning of the line (used for comments).  Anything else will generate an error.

If you are not for sure about what to do, post lines 30 -33 from /etc/modprobe.d/blacklist.  You can do this by going to the terminal and typing:
```
gedit /etc/modprobe.d/blacklist
```or you can open gedit from the menu and open the /etc/modprobe.d/blacklist file.  This will only give you read permission.

---

### Post by tomsa on 2008-05-03
Okay, now I'm confused all over again.  Lines 29 through 32 of etc/modprobe.d/blacklist look like this:

```
blacklist bcm43xx
blacklist net8187b
rtl
r8187
```

I'm guessing that I should just put the word "blacklist" in front of rtl and r8187, and that will fix the error.  

My new question is now, why is it that my wifi works when line 30 reads 

```
blacklist net8187b
```

and when I go to the system->administration->windows wireless drivers menu  It first gives me an error message that says "hardware not present", then after I click OK it says: 

Currently installed windows drivers:
net8187b
hardware installed: yes

At the moment I am inclined to leave everything alone as I have had a pretty sizable torrent running with no issues for about 6 hours.  At the same time, I like to fix things (almost to a fault) what does all of that stuff I posted actually mean??
](*,)

---

### Post by Ayuthia on 2008-05-03
> **tomsa said:**
> Okay, now I'm confused all over again.  Lines 29 through 32 of etc/modprobe.d/blacklist look like this:

```
blacklist bcm43xx
blacklist net8187b
rtl
r8187
```

I'm guessing that I should just put the word "blacklist" in front of rtl and r8187, and that will fix the error.

You are correct.  There should be a blacklist in front of it.

> My new question is now, why is it that my wifi works when line 30 reads 

```
blacklist net8187b
```

and when I go to the system->administration->windows wireless drivers menu  It first gives me an error message that says "hardware not present", then after I click OK it says: 

Currently installed windows drivers:
net8187b
hardware installed: yes

At the moment I am inclined to leave everything alone as I have had a pretty sizable torrent running with no issues for about 6 hours.  At the same time, I like to fix things (almost to a fault) what does all of that stuff I posted actually mean??
](*,)

The blacklist net8187b means that module is not to be loaded and used.  The Windows Wireless drivers menu is actually an NDISwrapper helper screen.  What is happening is that you are actually using ndiswrapper as your module and this screen is saying that net8187b is being wrapped by ndiswrapper.  Your actual module is ndiswrapper.  

What normally happens is that the net8187b module will talk to the wireless card and translates the information to the operating system.  The problem is that you cannot get the net8187b module to work.  So what you have done is use NDISwrapper to be your translator.  NDISwrapper is going to use the net8187b driver like a dictionary.  NDISwrapper will talk to the wireless card, translate it using the net8187b driver, and then pass the information back to the operating system.

So, going back to your question.  If you do the following:
```
lsmod|grep -i -e ndiswrapper -e net8187b
```
lsmod provides a listing of all the active modules.  What we are doing is looking for any module that starts with ndiswrapper or net8187b.  You will see that net8187b should not appear, but ndiswrapper should.  However, if you remove the blacklist net8187b from /etc/modprobe.d/blacklist and rebooted, you will see net8187b show up.  However I don't recommend that you try it. :)

I hope that helps.  If not, sorry for the long answer...

---

### Post by tomsa on 2008-05-04
Nope- that's great!  I understand much better now. Thanks for the help!
:-D

---

