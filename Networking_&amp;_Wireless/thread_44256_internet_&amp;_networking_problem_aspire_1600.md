---
title: "internet &amp; networking problem aspire 1600"
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by william on 2005-06-25
Hi all!
I've installed the newest Ubuntu on my laptop, an Acer aspire 1600, everything was going great and all the updates and languages support was taken from the internet.
No problems so far, but when it was finished I tried to go on the internet with firefox but it didn't work.. strange because during install the internet was working. I'm getting a legal ip adress from the dhcp, 192.168.1.150  and my network card is installed.. when I was searching the internet for a solution I found this thread: [http://ubuntuforums.org/archive/index.php/t-24077.html](http://ubuntuforums.org/archive/index.php/t-24077.html) 
That's the same problem I think isn't it? The problem is that I don't understand the solution because I'm a real noob with linux... I don't know what to do, can please someone help me?

Kind regards

William

---

### Post by william on 2005-06-25
can anybody tell me how I stop autoloading gdm at startup so I can do apt-get?
thanks!
william

---

### Post by yota on 2006-08-22
Hi William,

I've had the same issue on an aspire 1600; a partial workaround can be this:

[LIST=1]
[*]switch to text based console by pressing CRT+ALT+F1
[*]logon with your username and password
[*]stop gdm with '/etc/init.d/gdm stop'
[*]reinitialize networking with 'sudo /etc/init.d/networking restart'
[/LIST]

at this point the network is functional, and you can apt-get update/upgrade and so on.
The problem is that once you log back on graphic mode the network will stop again... so the pc becomes pretty useless (no web surfing and no mail is too much for 2006!)

If someone has more hints please post them!

---

### Post by betoboullosa on 2007-07-24
I've had a similar problem when I tried to install CentOS 5 in my Acer Aspire 1600 laptop: the network would work only in text mode, but not in graphical mode. 

When I looked at the /var/log/messages file, I could see a "nobody cared" message for the irq 233. It seems that there was a IRQ conflict when the system tried to start the graphical card, and thus it blocked access to the network card. But in the message itself there was a suggestion on how to fix the issue: use the "irqpoll" kernel option during boot. 

I did that and it worked! Just added "irqpoll" to the kernel options in the boot and there was no more IRQ conflict, the network started to work fine for both text and graphical modes.

---

