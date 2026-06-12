---
title: "Okay, What's going on with Lucid today?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Georgia boy on 2010-05-23
This morning I had trouble signing in. Wouldn't log on at all. Forced quit,then I was able to turn on and log in.

 Then when I went to print my printer has disappeared. Could only see print to file. Did a shut down on printer and computer, disconnected printer and reconnected. Turned printer back on, and then PC. Printer showed when sending to print. 

Turned everything off to go out shopping. Came back, turned on and then had same problem with printer. Tried to shut down. Wouldn't let me shut down. Had to do a force down. 
Tried everything with printer again but no go. Checked my installed software, shows CUPS, HPLIP installed. But still don't show anything to print to except to file. Check the System>Admin>Printing. Checked printer, everything is grayed out. 

Did a shut down again(which for some reason did a proper shut down) and disconnected and reconnected cables again. To no avail! I did the lsusb and got this:

thomas@thomas-desktop:~$ lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:1411 Hewlett-Packard PSC 750
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
thomas@thomas-desktop:~$ 

So, what gives? What's going on with Lucid lately. I noticed that others have been having problems with starting, shutting down and also with their printers also disappearing after having been working since installing Lucid as mine have.

Thanks for all help. Please keep things simple for my pea brain. :)


Thanks

Tom

---

### Post by uRock on 2010-05-23
History is good. Did you install or upgrade yesterday? Do a kernel upgrade recently? Let someone else on your system?

> **Georgia boy said:**
> Did a fresh, complete hard drive install the weekend that Lucid came out. Only updates I've done are the ones that they send to us, nothing else. Also, I'm the only one on this computer. Sorry, didn't think to tell you guys this. I was frustrated when I wrote this thread. 

Tom

Can't blame you for being a bit angry. Hopefully someone will come along that knows how to fix what you are dealing with.

Good luck,
uRock

---

### Post by Georgia boy on 2010-05-23
Did a fresh, complete hard drive install the weekend that Lucid came out. Only updates I've done are the ones that they send to us, nothing else. Also, I'm the only one on this computer. Sorry, didn't think to tell you guys this. I was frustrated when I wrote this thread. 

Tom

---

### Post by Georgia boy on 2010-05-24
Still can't get printer to show. When I go to the "printing" in admin and click on the items all are grayed out. When I clicked the help it told me that it couldn't find the cups spooler running to go to system>admin>services and look for the cups-service. Couldn't find the services under admin nor anywhere else. 
Forgot to mention it's a HP PSC 750. It was working when Lucid was installed last month. Just quit being seen yesterday.

Help?

Thanks

Tom

---

### Post by Georgia boy on 2010-05-25
Okay, I kept searching and reading. Found in another thread where someone did this:sudo service cups start. Gave it a shot because some of the other things I had tried weren't working. And so far it is working. As you can tell, I'm still learning. 

Have a wonderful day everyone!!

Thanks


Tom

Note: So far this is a temp fix for me. When I reboot the printer disappears again and I have to do the sudo service cups start again to show the printer.

Tom

---

### Post by pdlethbridge on 2010-05-25
Can you put that in boot up manager? There is a cups command that can be turned on and off.
If you don't have boot up manager, go to synaptic and look for BUM and install it.

---

### Post by Thacker on 2010-06-02
Hi
Had the same problem - cured by installing 'hplip' from Synaptic
Hope this helps:)

---

