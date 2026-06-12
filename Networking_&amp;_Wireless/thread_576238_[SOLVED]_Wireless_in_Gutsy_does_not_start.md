---
title: "[SOLVED] Wireless in Gutsy does not start"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by vcbranco on 2007-10-15
When I boot the OS, the wireless lan does not start when configured by WPA.
I need to restart the network (sudo /etc/init.d/networking restart) in the console.
After I do that works well
If I configure by WEP the wireless network starts normaly with the OS boot
I tryed everything I know without but I can not solve the problem

Any ideas?

Many thanks in advance

---

### Post by vcbranco on 2007-10-15
anyone?

---

### Post by openaddict on 2007-10-15
Your startup scripts might not be calling /etc/init.d/wpa-ifupdown

---

### Post by vcbranco on 2007-10-15
It is possible

How can I correct that?

Best regards

---

### Post by vcbranco on 2007-10-16
Anyone can help?
What did I need to check/change in the file?

---

### Post by vcbranco on 2007-10-21
Anyone?

---

### Post by saxsux on 2007-10-22
I'm having the same problem.
The Gutsy release notes say that "If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually", but I have no idea what that means! :oops:

---

### Post by vcbranco on 2007-10-23
I have the interfaces file configured manualy and I need always restart the network.

I think is related but I don't know how can I solve this problem

---

### Post by rtg on 2007-10-31
As a workaround, comment out
```

ACTION=="add",         RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup -- --allow auto $env{INTERFACE}"

```
inside /etc/udev/rules.d/85-ifupdown.rules.

It turns out that as soon as driver module gets loaded into the kernel, udev starts ifup which is not capable of bringing wpa_supplicant but still marks the interface as up (writing wlan0=wlan0 to the interfaces state list). During the boot sequence ifup is started again but won't do anything as the interface is already marked as "up".

Hope this helps at least somehow. I have a PCMCIA device which is never removed though... 

If you comment that section out, you will not have your network started automatically if you insert your usb card so you will have to restart networking after that. In case your card is not going to be wandering anywhere, this can be pretty safe.

---

### Post by vcbranco on 2007-11-01
Great

Now is working well

Many Thanks

For all who have that problem the correct file name is "85-ifupdown.rules"

---

### Post by rtg on 2007-11-03
I have filed a bug under [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/159138](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/159138) about this problem, I hope this will be fixed in subsequent releases :)

---

### Post by sewmyheadon on 2007-11-12
Thanks rtg :) - that's just what I was looking for and it took care of the problem.  Would certainly like to see this straightened out by default, though.

---

### Post by tonyhawz on 2007-11-13
what I had to do in order to solve that was adding :

```

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

to /etc/network/interfaces , since they were not there.

the odd thing is that now the network manager applet doesn't show me the signal strength any more.
ill keep investigating

---

### Post by Tea, anyone? on 2007-12-12
Fantastic!  Thanks rtg!

One more Ubuntu annoyance dealt with for this newbie :)

---

### Post by ilektron on 2008-01-16
Ah! Thank goodness! Finally.  I googled this and searched, but couldn't find anything.  Then, when submitting a post of the forums, they suggested some similar posts.

Another annoyance fixed for a fairly proficient Ubuntu user.

Thank you!

---

### Post by carney1979 on 2008-01-17
Using rtg's suggested fix on my Gutsy laptop - worked perfectly! Network is up by the time Gnome starts, I can still see signal strengths, etc. All works well, thanks!

Now if I could just get Gnome to boot a little faster.....

David

---

### Post by PaulRay on 2008-02-23
Thank you so much! Your good deed last year helped me this year. 
The commenting was an easy fix to a problem that was driving me, and many others apparently, nuts. 

You :guitar:

---

### Post by Starcrafter on 2008-04-06
I installed the latest 8.04 beta release and after enabling my wifi drivers in ndiswrapper my wifi worked but did not start at bootup.

Commenting out the line in this thread fixed the problem!

This is really great but really needs to be fixed in 8.04...

---

### Post by nkri on 2008-05-27
Thank you SO MUCH!!:)  
After only a couple of days with Hardy, this issue was really starting to get on my nerves...

---

### Post by rtg on 2008-06-25
Next Ubuntu release should have this working out-of-the-box. See [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/44194](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/44194)

---

