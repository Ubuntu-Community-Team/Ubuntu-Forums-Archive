---
title: "Realtek RTL8191SE - WiFi keeps dropping every few minutes..."
date: 2011-04-06
forum: New to Ubuntu
---

### Post by LittleZeasel on 2011-04-06
Hi,

I have just installed Ubuntu 10.10 on my Toshiba Satellite a505-s6033. It has a Realtek RTL 8191se WiFi Card and yesterday, first day after installation everything ran fine and like a charm.

Today, every 5 - 15 minutes my internet goes poof (all my other devices, other laptop, iPhone, etc. stay online and connected), but my Toshiba can't find Internet anymore.

It doesn't tell me the internet is gone, it just can't open webpages anymore, won't stay connected to my messengers, etc. Basically, internet = poof.

Clicking on the network button to Disconnect will disconnect it - but it can't reconnect. It finds the network, but it keeps trying to connect to it without getting anywhere. The only thing that helps is a full shut down of the entire system, wait 30 sec - 1 min, and start the computer again. Doing that every 5 minutes just to be able to read emails is a pain in the neck....

Now... is there  a solution to this? I use the Network Manager that's installed automatically when installing Ubuntu 10.10 and do not use anything else - I have not downloaded or installed any other programs, so basically, at the moment, my Ubuntu is still "as is out of the box"

Any help would be appreciated! 

Thank you,

LZ

---

### Post by LittleZeasel on 2011-04-07
Googling my troubles led to the result of this being a known issue with Ubuntu - Any chances this is going to be fixed with 11.04?

---

### Post by AlexDudko on 2011-04-07
Are there any specific logs? Have you tried another driver?
I have the same device, which works perfectly with SLED (SUSE Linux Enterprise Desktop) - the preinstalled OS and the driver, which was also preinstalled, and Fedora-14 with the latest official driver for Linux (downloaded and compiled myself). Though I haven't tested the device in Ubuntu-10.10: I'm still using Ubuntu-10.04, where it was (as far as I remember) included in kernel (don't remember compiling it), and till now it works like a charm.

---

### Post by LittleZeasel on 2011-04-07
I did try working it on Fedora 14 and used bdiswrapper for compiling without success. Ubuntu was only my second choice. Unf. I am new to Linux and have to rely on step by step instructions on the internet - and for Fed14 and my machine they did not work :( 

Swapped to Ubuntu and I have the Linux driver from the realtek website but haven't found out yet how to exactly get it installed (step by step guids are wonderful but linux commands are not very intuitive and so I don't know how to ammend them for my own personal needs). Also, since Ubunto recignises the network I thought it would work and did the first 8 hours... 

Btw... Internet drops mainly with specific websites. Keenspot, mainly, but also phbb forums etcc. Could there be a connection?

---

### Post by AlexDudko on 2011-04-07
Here is a link from Fedora forums [http://forums.fedoraforum.org/showthread.php?t=259271]("http://forums.fedoraforum.org/showthread.php?t=259271")
There is some information on installing the driver (the procedure in Ubuntu will be the same) and contains a link for downloading the driver. 
You can simply try the driver and if it works - the issue will be solved, otherwise it'll narrow the issue for further debugging.

---

### Post by LittleZeasel on 2011-04-07
Thank you Alex,

The Realtek Driver installed without any errors (which it hadn't done under Fedora 14 or CentOS previously) - unfortunately, my internet still keeps dropping.

Basically for every click on a web page, I have to restart the computer - then it will load that new link I clicked on, and before I can click on the next link, I have to restart again.

So far I found, affected pages are:

Webcomics hosted on Keenspot,
Blogspot
PhpBB Forums
Webcomicks on Smackjeeves

Also the instant messengers preinstalled (Empathy) seems to cause the internet to drop ... 

Any more ideas?

---

### Post by AlexDudko on 2011-04-07
> **LittleZeasel said:**
> 

It doesn't tell me the internet is gone, it just can't open webpages anymore, won't stay connected to my messengers, etc. Basically, internet = poof.

Clicking on the network button to Disconnect will disconnect it - but it can't reconnect. 



This behavior hints it's rather a client issue than a remote server dependent one.

> **LittleZeasel said:**
> 
It finds the network, but it keeps trying to connect to it without getting anywhere.
What log messages are you receiving during this connection attempt? What type of wifi connection do you use? Any encryption?

---

### Post by LittleZeasel on 2011-04-07
> What log messages are you receiving during this connection attempt? What type of wifi connection do you use? Any encryption?

How can I check and send you log messages?
How can I check what encryption?

Today is one of those days, the computer has been running the entire day and the internet didn't drop once.
If I have a couple of more days without the internet dropping, I'll consider it as solved.
Maybe (for whatever reason) the driver install needed 2 restarts before it fired ;) ... Actually, the first restart was just that: A restart. 
The second time I shut the computer off completely, took it off the power for over night (as I usually do) and then started it up this morning again - no issues so far. Maybe that solved it?

Let's be hopeful :) If I don't have any drops over the weekend, I'll consider it solved! Thanks for all your help, Alex... I'd still be curious at the logs, etc. you are talking about, and the respective commands - after all, I do want to learn more about the system I am using :)

Many thanks and best wishes,

LZ

---

### Post by LittleZeasel on 2011-04-08
:( Not fixed... 
Yesterday it started to run reliably and I was hopeful - this morning, in the span of 20 minutes, I had to restart the computer now for the 4th time, as the Internet keeps dropping out on me :(

Soooo.... you asked for logs and stuff... How can I access them in order to post them here?

---

### Post by walt.smith1960 on 2011-04-08
Here are a couple things you can try.  I don't know if they'll help or not.  


[LIST=1]
[*]Enable wireless backports.  Ubuntu doesn't necessarily load updated software or firmware once released.  Backports are technically unsupported but they may have updated drivers for your Realtek device. I had this work with an ASUS Netbook.
[*]If you can get a reliable connection, try downloading and creating a LiveCD of 11.04 Beta.  I have a couple wireless adapters-one an RTL-8192SU-that required extra  tweaking to work in 10.04 & 10.10.  They both work as installed in 11.04 Beta.  11.04 uses an updated kernel which seems to have better support for recently released wifi adapters.
[/LIST]

---

### Post by LittleZeasel on 2011-04-08
How do I enable wireless backports? (command?)

While my wireless isn't/wasn't working, I had plugged my computer into wired - I did try to download 11.04 Beta, but all the download Mirrors gave me download speeds between 1 - and 12 B/s ... yes.. Bites / S ... Estimated Download dime 14 days, 7 hours and 47 minutes ... Brilliant ... 

So far it drops whenever I try to read my favourite webcomics - they are all hosted on PhpBB Forums, keenspot, smackjeeves ... :/ I guess I'll avoid those for until I have a more stable connection - I am trying my online game tonight and see whether that stays up and stable.

---

### Post by walt.smith1960 on 2011-04-09
The simplest way to enable backports is in Synaptic package manager.  Put the term "backports" in the search box and you should see entries for modules & wireless among others.  I've not had a problem but I've seen a couple reports where enabling backports damaged a functioning system. That's a risk of using software that has not been extensively tested.  Having current backups of important things are good for peace of mind.  Of course that's true anytime.

---

### Post by bkratz on 2011-04-09
> **LittleZeasel said:**
> How do I enable wireless backports? (command?)

While my wireless isn't/wasn't working, I had plugged my computer into wired - I did try to download 11.04 Beta, but all the download Mirrors gave me download speeds between 1 - and 12 B/s ... yes.. Bites / S ... Estimated Download dime 14 days, 7 hours and 47 minutes ... Brilliant ... 

So far it drops whenever I try to read my favourite webcomics - they are all hosted on PhpBB Forums, keenspot, smackjeeves ... :/ I guess I'll avoid those for until I have a more stable connection - I am trying my online game tonight and see whether that stays up and stable.

Having problems accessing only certain sites is often a MTU size problem. You might want read the answer section on this site and see if it applies to your situation.

[http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows](http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows)

---

### Post by LittleZeasel on 2011-04-10
Okay... it wasn't the MTU - that is already set to maximum of 1500.

We did take a different approach and used following command:

```

tcpdump -s 0 -i wlan0 -w /home/littlezeasel/tcp.dump

```

In order to get a report of what happened when over the wlan0 to try and find out what might cause the internet to stop running.
Unfortunately, me being an absolute Linux Noob, I can't tell anything from that protocol and the one helping me can't see anything wrong with the log file, apart from recognising WHERE the packages stopped.

I would like to post the relevant part of the protocol, but unfortunately it isn't a text file (it's a file opennable in Wireshark).
The entire thing is 22 MB large and thus not good to be posted - I basically just need the last few lines - anyone know how I can extract those from the file so I can share it, so maybe someone may be able to recognise what is wrong with my stuff? 

Or maybe any other ideas? 

Thanks a lot for all of your ideas - I am trying everything and am looking forward to a solution. Keep them coming, maybe one thing finally will stick :)

LZ

---

