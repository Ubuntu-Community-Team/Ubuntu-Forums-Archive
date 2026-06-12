---
title: "share ubuntu printer with Puppy and misc rant"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by imnotrich on 2007-07-15
I have four desktops and a laptop on my home network: 

1. XP/Dapper dual boot with a Dell AIO 942 (not supported by Ubuntu) 
2. XP with an HP Deskjet 3510.
3. Feisty with an HP Deskjet 970C (also running win3.1 and win98 in virtual box - and they can print too!)
4. Puppy 
5. XP (laptop) 

None of the printers can pull an IP, so they are all installed as  "shared." 

I recently wanted to network the Puppy PC to at least one printer.  I was able to install the 970c locally on the Puppy machine so I know the driver works but for some reason when I reconnect the printer to Feisty I can't share the printer with Puppy. All I get are Samba errors. 

Which is odd, because my windows machines can print to it through Feisty. And setting THAT up was a major headache! 

One quick click on my kvm switch and Feisty cups manager shows a networked printer trying to print, but won't open and show the jobs nor am I able to delete the incorrectly configured printer. CUPS just locks up and I have to open a command window at kill the pid.

Don't mean to be down on Dell, but now that they are shipping Ubuntu on some of their machines they should at least have linux drivers available for their bundled printers. When I run Dapper on my main desktop I can't print there. So instead I print to the 970c in the garage...but that means I have to actually get up and walk out there - a real chore when it is 115 degrees. 

Why is printing (and networking) so difficult? What can I do to fix it?  I need to get this done, so I can move on to my next rainy day project - making my modem work. Or wireless networking, another hopeless task. I'm tearing my hair out!

My family still has not bought my sales pitch about Linux, they will not part with certain windows games but on top of that they see me toil endlessly trying to make stuff work and it scares them. They simply want it to "just work."

---

