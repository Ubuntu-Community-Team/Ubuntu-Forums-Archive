---
title: "HOW TO make XAMMP work with Hardy Heron with no network connection"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by thenetduck on 2008-08-07
Hi 
If you have intalled Xampp with hardy heron, you might have noticed that you need to be connected to a network for it to work. After months of frustration, I have finally found a solution. No worries, its a simple solution so listen up my Xampp deprived friends, out of the dust a solution has risen.... 

Problem: Xampp won't work if you don't have a network connection in Hardy Heron. 

Solution: Configure your computer to use Automatic DHCP. 

Heres How: 
In your system try there should be a network icon. Click on that and select Manual configuration. 

From there, unlock it with your password....

Selected "Wired Connection" and click properties located top right. 

UN-SELECT the "Enable Roaming" option and  under configuration scroll down to "automatic configuration (dhcp)" use that one. Ubuntu will then automatically configure your network for you and Xampp will now work like a charm. 

I hope this helps everyone. I spent a lot of time trying to figure out why things were not working, as a result, I lost a lot of time programming my PHP.

The Net Duck

---

