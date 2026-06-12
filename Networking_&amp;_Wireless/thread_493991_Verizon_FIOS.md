---
title: "Verizon FIOS"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by ebazz on 2007-07-06
Hi,
Does anyone know how to get Ubuntu up and running with Verizon FIOs and an ActionTec router?
Ubuntu is not seeing the router that I have.
Any help would be appreciated.
I'm using the latest edition of Ubuntu, and a fairly new computer.
Currently Ii'm exploring the live CD.
Thanks,
Ernie Bazzinotti

---

### Post by Jacob111 on 2008-05-17
bump.  I can see my actiontec FIOS router but it can't seem to get a connection.  It just says the signal strength in 0% and eventually switches automatically to another router in range.  Thankfully some of my neighbors haven't discovered wireless security yet.

---

### Post by RichieV on 2008-05-22
New linux user here, just set up xubuntu on a computer that I haven't used in years and everything works great except for the internet connetion.  I have Verizon FIOS and searching around I see many people have problems with this service and ubuntu.  Has anyone got this to work?

---

### Post by timcredible on 2008-05-22
there's nothing special about your router, but you probably have to set up the router first - on my verizon dsl connection, i had to web into the router and manually add my username/password before it would get on the verizon network.  i had to call verizon to get my username/password, and they gave me some crap about they only support windows, but i said what about my ps3, my psp, my wii, and they backed down and gave me the info.  so, web into the router with a wired connection and make sure it's connected to the verizon network first.

---

### Post by Jacob111 on 2008-05-22
Hey RichieV, I actually got this to work so you're in luck.  Sorry for not posting sooner.  I'm guessing Xubuntu setup is basically the same, so this should get you up:

1. In the menus, go to Applications -> Accessories -> Password and Encryption Keys.  Under the Passwords tab, make sure there is not entry for your network.  If you see something like "Passphrase for wireless network <network name>" then right click it and select "delete key".  Now, you will be prompted for the network settings instead of xubuntu trying the previous (wrong) settings.  Now close that window.

2.  Click on the network manager and select the FIOS network.  You should be prompted for settings.  For security type, select 64 bit WEP hex.  The key type is "open system".  Of course, you'll need the WEP key located on the router.

That should work.

---

### Post by spazticnerfbrain on 2008-05-22
First post (and verizon Fios tech support guy).

Unless someone changed router settings, wireless on the actiontec is on by default. Easy way to check the status is the wireless light (last on right or bottom, depending on whether it's laying down or standing up).

If you need it, router IP for log on is 192.168.1.1 usernam "admin" and password is usually either "password" or "password1" (no quotes, of course).

As the above post said, your wireless key is on a sticker on the router, the WEP key. ESSID on the same sticker should match the one you're trying to connect to. 

If all else fails, a hard reset of the router will always bring it back to default--wireless ON and essid and WEP matching the sticker. Press the reset button on the back of the router for 15-20 seconds. Wait for the internet light (picture of the globe, 4th light) to turn green and you'll be up and running right quick. :)

---

### Post by zfolwick on 2008-05-22
I am having the same trouble!  I've tried everything ya'll have suggested, but no dice.

Can anybody help me?  Same hardware, and the same bs about "not supporting Linux".  Whatever.  I am using the actiontec mi424wr router as well


**EDIT***

IT WORKS!!! IT'S ALIVE!!!

all I had to do was take off the WEP encryption when I logged into 192.168.1.1 with the admin/password1 stuff, then tried to connect in Ubuntu, when that worked, I put encryption back on!

Yay for me.  another small victory against M$!

---

### Post by RichieV on 2008-05-23
Thanks you guys so much for the quick answers. Unfortunately, I'm an idiot and didn't realize exactly what was being said in the original posts.  I actually need help with a wired connection.  

When I type in 192.168.1.1 on this computer (Windows XP) and view the list of connected devices, it does not show that computer.  If I type 192.168.1.1 on the xubuntu machine I get a page load error.  I've tried changing from DHCP to a static IP and playing with some other settings but honestly I really don't know what I'm doing.

---

### Post by Jacob111 on 2008-05-23
I'm not an expert, but I know you should keep things on DHCP.  Static is only when you have to manually assign IP addresses, which is not the case here.  I'm confused about the page load error though.

---

### Post by RichieV on 2008-05-27
I definitely thought troubleshooting a wired connection would be easier, but I guess not (judging from the lack of responses).  I've been playing around with every internet setting i could find, but nothing seems to help.  

Maybe I should look into buying a wireless adapter for my pc, can anyone point me in the right direction for that? Thanks for any help.

---

