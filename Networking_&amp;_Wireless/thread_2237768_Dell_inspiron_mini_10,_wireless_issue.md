---
title: "Dell inspiron mini 10, wireless issue"
date: 2014-08-03
forum: Networking &amp; Wireless
---

### Post by HR70s on 2014-08-03
I have a Dell inspiron mini 10, Intel Atom CPU n280 i.66GHz x2  disk space is 17.3 GB.
   I'm running duel boot Windows XP and Ubuntu 10.4.
Problem:  I upgraded to 10.4 3 weeks ago and everything was working great until yesterday when in ubuntu it wouldn't connect to my wireless router [Netgear] I have it set to auto 
connect for my router but it it keeps asking me for the password. I enter the password and I see the WI-FI searching and after a few minutes it comes back up and asks for the
password again got any ideas please BTW The WI-FI works fine if I boot into windows XP  .

---

### Post by dave131 on 2014-08-03
Please post back the output of:

lspci | grep Network

---

### Post by HR70s on 2014-08-03
I don't much about ubuntu I don't know what | spci | grep Network is. Is that a sudo command? By the way what is that at the bottom of your post " I'm just a dumb guy "
Thanks for the reply

---

### Post by Adam_GUI on 2014-08-03
> **HR70s said:**
> I have a Dell inspiron mini 10, Intel Atom CPU n280 i.66GHz x2  disk space is 17.3 GB.
   I'm running duel boot Windows XP and Ubuntu 10.4.
Problem:  I upgraded to 10.4 3 weeks ago and everything was working great until yesterday when in ubuntu it wouldn't connect to my wireless router [Netgear] I have it set to auto 
connect for my router but it it keeps asking me for the password. I enter the password and I see the WI-FI searching and after a few minutes it comes back up and asks for the
password again got any ideas please BTW The WI-FI works fine if I boot into windows XP  .

A Dell Inspiron Mini 10?
These are some turbulent waters.
But, no fear!  I'm a sandal wearing hippie that's been down this set of rapids many times.

First, are you sure you've got the correct wireless driver?
It should be the Broadcom-wl.
Three packages there:
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source.

More importantly, Ubuntu 10.04 is past end-of-life support. (As is Windows XP.)
While I'd usually recommend just jumping to your preferred spin of Ubuntu 14.04, the current LTS,
If you've got an Inspiron Mini 1010, that sucker has that awful bugbear of a GMA500 video chip.
I'd recommend jumping to Debian 7.5.  [Found here.]("https://www.debian.org/CD/")

---

### Post by Bucky Ball on 2014-08-04
Unless you're running a server version of 10.04 it is well out of supported. Canonical and the forums don't provide support for out-of-date releases and if you wish to continue with 10.04 I'd stay off-line and expect further breakage as time goes by. Advise you upgrade to a supported release (by backing up and a clean install of 12.04 or 14.04. Please read here:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

The majority of fixes you attempt may not work on an EOL release. There are no active repositories to update packages from, and that includes security updates.

---

### Post by HR70s on 2014-08-04
I want to apologize I stated incorrectly. I updated to 12.04LTS from 10.10 remix
I will look for what driver I have if I can find it.

---

### Post by varunendra on 2014-08-04
> **HR70s said:**
> I don't much about ubuntu I don't know what | spci | grep Network is. Is that a sudo command? By the way what is that at the bottom of your post " I'm just a dumb guy "

That was a command "lspci | grep Network" to be entered in a 'Terminal' (which you can open by pressing 'Ctrl-Alt-T' or from menu that your OS provides) - note that there is only one Pipe (|) symbol between "lspci" and "grep", and it is a small "L" in "lspci".

Much better, to see which card and driver you have (it *may* be different than broadcom), run this command in a terminal (you may copy-paste it to avoid typo) -
```
lspci -nnk | grep -iA2 net
```
..and post back the output here.

Oh, and "I'm just a dumb guy" was not the part of the post of dave, it was just his signature line :)

---

### Post by dave131 on 2014-08-05
> **HR70s said:**
> I don't much about ubuntu I don't know what | spci | grep Network is. Is that a sudo command? By the way what is that at the bottom of your post " I'm just a dumb guy "
Thanks for the reply

It's a terminal command - open a terminal window and paste it the below:

lspci | grep Network

Then press return.  The first part of that is actually a lower case "l" - the lspci is a command asking to list all devices on the computer's PCI bus.  The straight up and down bar "|" (above the "\" on my laptop keyboard) is a piping symbol - it's used to redirect the output of the previous command.  In this case, the output is redirected to the grep command - it's a little much to explain grep here - but in this case grep will only output a line containing the string shown - in this case "Network" (case matters).  So, the result of the above is to list all PCI devices that have the word "Network" in them.

This will give a single line for each of your network adapters, which includes a description showing what the adapter is so we can help you get a driver for it or do other things that might be needed to make it work.  I don't have the knowledge to help you on that part of things, but the information from the above is what is needed for someone else to start helping you.

As for the "I'm just a dumb guy" thing - that's what I put in for my signature in my forum profile - e.g., I'm just describing who I am! ;)

Best of luck!

---

### Post by Bucky Ball on 2014-08-06
We're all just dumb people here, but we get smarter by talking to and learning from each other, which is what it's all about. 

I'm actually a musicologist faking it as a mod in my spare time ... x ;)

---

### Post by HR70s on 2014-08-06
It comes up: 03:00.0 Network controller: Broadcom Corporation BCM 4312 802.11b/g Lp-PHY [ Rev 01 }

---

### Post by HR70s on 2014-08-06
Yea your right. we all have gifts The Barter Systems work for for me. Thanks!

---

### Post by Hadaka on 2014-08-06
Hi, your card..
 Broadcom Corporation BCM 4312 802.11b/g Lp-PHY [ Rev 01 } 
has the possibility of more than one driver, to best determine
what driver would be better for your system, as with all Broadcom cards
we need to see the PCI-ID. please COPY and paste the following.
```
lspci -n | grep 0280 | awk '{print$3}'
```
post the output
thanks.

---

### Post by HR70s on 2014-08-07
I was looking at all the wireless network setting once more to see if I missed anything. and saw nothing. Just for the heck of it I turned 
airplane mode on and back off and the WI-FI started working. I have no clue why! So I turned the netbook off and back on and the WI-FI 
auto started as it should. There's a bug someplace. For now I guess it's solved, I'm probably like you guys not knowing why bothers me

---

