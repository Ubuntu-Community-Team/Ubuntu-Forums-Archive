---
title: "boot hangs at ?DHCP? getting an IP address"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by Dilbernator on 2006-07-20
Greetings,

I am new to linux, and am trying to boot from the LIVE cd.  It gets to a point in the boot that it hangs, and will not go on.  When I tried with Knoppix cd, it hung up at the point where it was trying to get an IP address from the firewall/DHCP server.  I believe that the server has already assigned an address to the card.  

How can I get the boot to continue?
How do I make linux see the address, or not wait for one to be assigned?  

I hope enough information has been given - if you need more, I will try to supply it.

---

### Post by harisund on 2006-07-20
What are you connecting your machine to? A router? 

From what you have mentioned, it looks as if either the network card is not identified and is crashing at that spot (unlikely) or your router is not correctly giving an IP address to your computer when the LiveCD requests it. 

What OS are you using now? (Before booting the LiveCD). What sort of an internet are you having? In other words, how are you connected?

---

### Post by christhemonkey on 2006-07-20
Can you type Ctrl+C to skip this bootup service?

---

### Post by endfx on 2006-07-20
Alot of times you can just hit "control c" to skip that part.

Now you should be able to boot into linux, but you won't have network
connection. Perhaps you are connecting through a router/firewall that doesn't
use dhcp, i.e. addresses are assigned statically.

Once you get into linux you can use the system -> administration -> networking  to assign yourself a static ip.

Let me know how it goes.

---

### Post by Dilbernator on 2006-07-20
In response to various question, I am using Windows 2000 pro on this machine.  It has no problem with the DHCP served IP addres.  I am not sure that is what is happening with Ubuntu, I just see it with Knoppix.  Is there any way to get Ubuntu to be verbose as it starts up so I can see the error?  

I will try the Ctrl + C  and see if it will continue past that part of the boot.  I thought I had already tried that, but ...    I will try again.

I am currently connecting to my home LAN via ethernet.  The firewall is an old DLINK that serves IP addresses in a range.  This PC has an address as a windows computer, but won't seem to get one as a linux pc.

Thanks for your responses

---

### Post by endfx on 2006-07-21
To get ubuntu to be verbose you have to:

Boot the computer. When you get the to grub menu, select the kernel and hit 'e' to edit boot options. Then select the line similar to:

kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash


Hit 'e' again
Now remove the "quite splash" part and bit "enter" now press 'b' to boot the kernel. Now this is as verbose as your gonna get.

Note: Modifying the boot options like this will only take effect for this boot. Next time you boot your computer it will be back to normal, so you will have to modify them again.
Any changes to boot options you want to make permanently you have to modify /boot/grub/menu.lst

---

### Post by Dilbernator on 2006-07-21
Thanks for the information.  I will try all that you have posted.  It will have to wait a week, as I will be out of town now.  I will try when I get back and post results.  

Thanks again!

---

