---
title: "help me figure out these instructions for my print server"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by DingsBumps on 2007-12-17
I am relatively new to Ubuntu, but I love it and I've decided to abandon XP for it. The last thing that still keeps me booting into XP every so often is to print a document. I own trendnet te100-mp1u print server. On trendnet's website I found (not well written) instructions that I need help figuring out.

Here the page (warning:3mb pdf) [uhh... click here?]("http://www.trendware.com/asp/download_manager/inc_downloading.asp?iFile=9835")                Page 38 starts their Unix/Linux documentation.

My printer is a Dell A940 Multifunction, but I don't need to be able to use the multifunction, I just want to be able to print. What I really need is a starting point in those instructions as there seems to be 5 sets of instructions to do the same thing.

Thanks!

---

### Post by csat on 2007-12-17
You will probably find some help visiting this link below:

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

---

### Post by daengbo on 2007-12-18
The basic idea for your setup is on p.44 in section 6.D. The Ubuntu printer dialog is different (and easier).

Go to System -> Administration -> Printing and click on New Printer.
Choose IPP and put in the IP address manually. I think this means that you don't need to muck around with the /etc/hosts file mentioned earlier in the manual.

If you know the name of the queue, enter it. IF not, choose Find Queue. Finish the new printer setup and print a test page.

That should work for you.

---

### Post by DingsBumps on 2007-12-18
Thanks for the replies,

I went to the new printed dialog, put the ip in, hit find queue... and a message popped up and said No Queues Found. 
Also, when I opened the new printed dialog, it searched for printers and found mine, so that was an option in the left hand pane. I picked it, hit forward, and it asked me for a driver.

 I picked my model of printed, but there were two submodels/subtypes/whatever. I tried picking one and tried printing a test page, no luck, tried the other driver, no luck. 

I'm going to try the OpenPrinting link and I'll also try and find my old driver disk, but I'm not really sure thats the problem. What I'm afraid of is that the print server is an oddball. In windows, it needed a program running (in the systray) to print. I'm really afraid that I might need to use the program.

Any other ideas?

---

### Post by ant1060 on 2008-07-12
Hi! Here's how to get the driver for the Dell A940 and the whole thing up and running with a minimum of fuss. I got mine going after waiting about three years! Just click on the link and follow the steps (which look complicated but just work :) )
[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)
Good luck!

---

