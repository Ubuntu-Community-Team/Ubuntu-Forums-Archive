---
title: "Internet Connection Problem"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by simon_7_1_8 on 2005-10-19
Hi guys, im completly new to Linux, and have just used/installed linux for the first time. From what iv seen so far, it is much better than windows xp... but i am having trouble connecting to the internet. 

I am trying to connect through a PCI ethernet card, and a D-link DSL-604T Router. I have looked at similar threads in the forum, and tried some of the suggestions put forward, but these do not seem to help

could someone please advise me what to check next?

thanks!
simon

---

### Post by Vanish00 on 2005-10-19
Simon, I'm having the same problem too.  I can use my Windows XP to go on internet but once i'm on Ubuntu I can't connect to anything.  I'm new to Linux as well any looking forward to some help on this problem.  Whenever I ping a site like yahoo.com I get a msg. about I can't connect.  This msg. comes right up too.

---

### Post by xmastree on 2005-10-19
Firstly, make sure that your Network card is set to DHCP (that's the default, so unless you changed it, it should be).

You'll find that in **System > Administration > Networking**. If It is, try Deactivating then Activating again. That ought to refresh the settings.
Make sure that 'default gateway' is set to **eth0** (assuming there's only one NIC installed).

Go to **Applications > Network Tools** Select the devices tab, select eth0 and see if it has been assigned an ip address.

Do you know the ip address of your router? Try to ping it.

---

### Post by simon_7_1_8 on 2005-10-20
xmastree: i have tried your suggestions, and all the settings seem to be correct. i am writing this from my laptop (windows xp) which is connecting to the internet perfectly, but my desktop pc (ubuntu) will not. 

The computer is assigned an IP address, and i can access my routers configuration page in firefox by typing 192.168.1.1 on the desktop, so my network connection seems to be functioning correctly

---

### Post by xmastree on 2005-10-20
> i can access my routers configuration page in firefox by typing 192.168.1.1Well that's a good sign. What happens if you type in a url?

---

### Post by simon_7_1_8 on 2005-10-20
:???: well its working now... and iv done nothing! firefox keeps timing out though when loading web pages: what can cause this?

---

### Post by xmastree on 2005-10-20
Well it could be one of those coincidence things, like when your isp goes down at the same time as you install a new video card...

I'd look at proxy settings, DNS settings, that kind of thing.

---

### Post by drtvasudevan on 2005-10-20
i have had a lot of problems getting the internet go.
finally found a solution.
this happens with firefox almost always. i have seen the same problem in many distroes.

solution:
type about:config in the address bar [place where you type in the url.]
look for "network.dns.disableIPv6": set "false"
right click on this line and select toggle.
it is reset to "true"
close firefox.
launch firefox now and you can connect.
dont ask me why!
let me know if you succeed.

tv

---

### Post by Slagerij on 2005-10-20
My firefox exhibited the same problem - I was unable to browse anything although I had a valid internet connection.  I could apt-get update, ifconfig looked right, even lynx worked just fine.

I did the about:config adjustment and it fixed my firefox.

Thank you!

---

### Post by simon_7_1_8 on 2005-10-24
thanks everyone, all seems to be sorted now :cool:

---

