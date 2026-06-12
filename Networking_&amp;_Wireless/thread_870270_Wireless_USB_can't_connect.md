---
title: "Wireless USB can't connect"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by avram on 2008-07-25
Hi everyone, 
-i appreciate any help-
I followed this tutorial on how to install my new USB wireless.
[http://www.paulie-pages.com/?p=31]("http://www.paulie-pages.com/?p=31")
it all went okay until i had to type ```
sudo modprobe ndiswrapper
``` everytime I started my computer. I was told to edit the /etc/modules file and to add 'ndiswrapper' on a new line. this worked but it won't connect to the network. It worked before i edited the init.d file when i typed 'sudo modprobe ndiswrapper'

 So, pretty much it isn't connecting after i edited the modules file

Anyone know how to fix?

thanks in advance :)

---

### Post by ModelM on 2008-07-26
/etc/init.d/ is a directory, not a file.

In any case you need to add the one word "ndiswrapper" to the end of the file:

/etc/modules

Assuming ndiswrapper is properly configured, this will load it at boot time and you should be in business.

---

### Post by avram on 2008-07-29
sorry that is what i meant. /etc/modules

i just chanegd it again and restarted and it still doesnt connect even after adding 'ndiswrapper' to the modules file...

it keeps trying to connect but continues to fail..

---

### Post by ModelM on 2008-07-29
If, as you say, the wireless adapter is "trying to connect", that means the driver is installed & running. You'll probably need to look elsewhere for your problem.

Tell us more about your network - to begin does it use encryption?

---

### Post by avram on 2008-07-29
thanks for the reply, and No I'm not using any encryption. I'm using wirelss USB Linksys WUSB54GSC wireless adapter and I'm using a netgear router...

---

### Post by ModelM on 2008-07-29
So if I have this right, you have an indicator of adequate signal strength, but the connection fails, correct? Are you using the built-in network manager to connect, or have you installed Wicd or some other?

---

### Post by avram on 2008-07-29
yeah, thats right i get four out of 5 bars of signal strength and yes i'm using the built in network manager, it tries to connect automatically though when i start-up. when it fails i try to connect again but it fails again and again..

---

### Post by timjohn7 on 2008-07-29
Try Wicd.  It connected to my Netgear Router with no problem whatsoever.  Also try madwifi as your driver.

---

### Post by ModelM on 2008-07-29
I'm not going to tell you to switch, but you might want to have a read at this webpage:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Lots of folks say it works better for them. I use it not because it works "better", but because it has a few extra controls I like to be able to manually fiddle with.

The instructions for installation on the website are very clear & it's easy enough to switch back if you choose.

Anyway, you can have a look & see what you think.

---

### Post by avram on 2008-07-29
I installed and tried WICD but i didn't get any luck with that either. When i tried to connect to my network which it found with decent signal strength it's status was 'obtaining IP address' but it failed to connect again... 

any idea? lol

---

### Post by ModelM on 2008-07-29
I don't know how much you know about networking so if this is confusing, just say so.

I'd try, in wicd, click on the little triangle on the left side next to your network name, open it & type in a static IP address.

If DHCP is the problem, this will get us past that & we'll know.

---

### Post by timjohn7 on 2008-07-30
> **avram said:**
> I installed and tried WICD but i didn't get any luck with that either. When i tried to connect to my network which it found with decent signal strength it's status was 'obtaining IP address' but it failed to connect again... 

any idea? lol

Do you have MAC Filtering switched on (on the router), and if so, have you added your new card's MAC address to the list of permitted connectors?

---

### Post by avram on 2008-07-31
hey guys, 
i tried putting a static IP into wicD, the same IP as on my netgear router and it failed, when i went onto my netgear settings on my windows computer (which i'm on now) it says I get my IP dynamically from my ISP.

I'm not quite sure how to check if i have MAC filtering on but i see on ym settings i have a MAC address?..

thanks for your replies..

---

### Post by ModelM on 2008-07-31
No two devices on a network can successfully have the same ip address. When you enter a static address into wicd, it cannot be the same address as the router.

Let's say your router is 192.168.1.1

Enter an ip into wicd of

192.168.1.101

That second from last number must match - if it's a zero in the router, it must also be a zero in your address - so in that case your address would be:

192.168.0.101

---

### Post by avram on 2008-07-31
Okay, thanks I'll try it now...

I tried it and it failed again.. ?.?

---

### Post by timjohn7 on 2008-07-31
> **avram said:**
> hey guys, 
i tried putting a static IP into wicD, the same IP as on my netgear router and it failed, when i went onto my netgear settings on my windows computer (which i'm on now) it says I get my IP dynamically from my ISP.

I'm not quite sure how to check if i have MAC filtering on but i see on ym settings i have a MAC address?..

thanks for your replies..

I have a Netgear DG834G and if your router software is the same, go to Setup>Wireless Settings>
1.  Select Enable Wireless Access Point
2.  Select Setup Access List
3.  Select Turn Access Control On (Note: You can check whether this is your problem by deselecting this and trying to connect)
4.  Find the MAC address of your USB Card\Computer, and add it manually to the list of Available Wireless Stations.
5.  Save settings and logout.
6.  Try to connect.

Hope this helps

---

### Post by avram on 2008-08-01
I followed the instructions timjohn7 and i still had no luck.. i can't think of anything else to try?

---

