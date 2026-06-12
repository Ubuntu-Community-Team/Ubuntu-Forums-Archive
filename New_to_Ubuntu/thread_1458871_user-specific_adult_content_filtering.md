---
title: "user-specific adult content filtering"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Ceresetta on 2010-04-20
I have set up an account for my daughter on my laptop. I would like to prevent her from accessing adult materials while not making it impossible for other users to do so. I looked at the OpenDNS option, but it seems it will limit content to the computer generally and not just to specific users. Can content be filtered in a user-specific manner?
Thanks

---

### Post by LowSky on 2010-04-20
Hmmm... Dansguardian  I dont believe in webfiltering so I have no idea how well it will work or if you can make it user specific
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

hope this helps

---

### Post by Steven_S on 2010-04-20
I have thought about the same question while planning to have my kids use the desktop (they are 3 and 5). I'm currently looking into solutions to disallow them to use firefox and install a child-safe browser that is accessible on their account (which would auto-login). At least: that is the plan - I haven't "shopped around" or implemented it yet. 

Maybe you could read this outside thread too:[http://www.techtalkz.com/ubuntu-linux/64559-net-nanny.html](http://www.techtalkz.com/ubuntu-linux/64559-net-nanny.html)

---

### Post by Ceresetta on 2010-04-23
Someone recommended OpenDNS and I went through the motions, only figuring out (maybe, ...like I can figure any of this out...) at the end that the settings would apply to all users of the computer and not just to my daughter. So I undid all the changes I thought I had made. Now I can't connect to my home wireless network anymore. The computer no longer "sees" the network. 
 
If I open the "edit connections" window I see: 
"Wired" tab (nothing, although previously there had been something)
"Wireless" tab (the name I typed in of my home network, the computer didn't "find" it automatically)
 
I highlight the name of the home network and click "Edit..."
 
"Wireless" tab: 
SSID has name of network (again, not because the computer detected it)
Mode: infrastructure
BSSID: (blank)
MAC address: (blank)
MTU: automatic
and I have checked "available to all users" (seemed like the thing to do)
 
"IPv4 settings" tab:
Method: shared to other computers (previously it was "Automatic (DHCP)", which I had changed to "Automatic (DHCP) addresses only" when I tried OpenDNS, setting it back to "Automatic (DHCP)" before hitting the "apply" button. In any case, even if I set it to "Automatic (DHCP)" it doesn't work)
 
So that's the deal. Anyone got any ideas of how I messed up?

---

### Post by arrrghhh on 2010-04-23
OpenDNS should not have changed anything on the router (Well, other than the DNS settings).  Connect via a wire, see if you can login to the router and check the settings.  Worse comes to worse, do a hard reset on the router (there's a reset PIN on the back of the router that sets ALL settings back to default, so yes you will have to reconfigure the settings on the router.)

---

### Post by carrarin on 2010-04-23
User specific? Somebody likes porn :)

---

### Post by pricetech on 2010-04-23
You think ??

Seriously OP, Open DNS shouldn't have changed anything except the DNS addresses you use either in your router or on your computer.  (maybe both if you did it that way)

But no, there is no user specific setting in Open DNS.  It filters your Internet connection.

---

### Post by nothingspecial on 2010-04-23
There are a few firefox extensions that will do this.

None of them are perfect and all of them (that I have tried) fail, when I have tested them heavily.

I`m using procon latte at the moment but as my kids grow older, I know it is not going to be enough.

Therefore, in our house, the kids do not go on the internet unless me, or Mrs Special are in the room with them.

If you like being an evil parent (as I am described sometimes), you might be interested in timekpr, which limits the time spent on the computer daily.

My kids get one hour.[URL="https://launchpad.net/timekpr"]

timekpr[/URL]

---

### Post by pricetech on 2010-04-23
> **nothingspecial said:**
> Mrs Special

Her first name is "Something" ???

---

### Post by nothingspecial on 2010-04-23
Haha

Most of the time :P

---

### Post by Ceresetta on 2010-04-24
There are two other computers in the house that work just fine (Windows). It would stand to reason that the problem is with some setting on the Ubuntu computer. 
 
What I originally did was to open the network manager from the top-right of the screen. For some reason it only listed a "wired" connection even though it was using an wireless connection. So I began implementing the OpenDNS settings by editing that. When I clicked on the IPv4 tab, the "Automatic (DHCP)" option was in the combo box, so I had to select the "Automatic (DHCP) addresses only" so I could type in the two whatever-you-call-them (e.g., 198.67.220.220). It was about at that point that I realized that it was going to affect the whole computer and not just one user profile and so I decided to forget it. I put the combo box back to "Automatic (DHCP)" and either hit "apply" or "cancel" (sorry, don't remember). 
 
Whereas prior to that, I turn on the computer and it automatically connected to the wireless network, now I turn it on and it doesn't see it at all.

---

### Post by KIAaze on 2010-04-24
My pretty extensive list of solutions:
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

---

### Post by Ceresetta on 2010-04-24
Two obvious questions:
 
1. With its default settings, the computer saw the network and all I had to do was type in the password. Isn't there some way to reset everything back to default? (Already at this point, I would have saved a lot of time just reinstalling Ubuntu!)
 
2. Isn't there some utility that looks for available networks?

---

### Post by Ceresetta on 2010-04-27
This issue has been resolved. Thanks everyone!

---

### Post by KIAaze on 2010-04-27
> **Ceresetta said:**
> This issue has been resolved. Thanks everyone!

Please post the solution in case others have the same problem. :)

---

