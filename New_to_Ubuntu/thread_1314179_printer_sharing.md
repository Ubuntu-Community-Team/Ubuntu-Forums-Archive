---
title: "printer sharing"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Utahreddirt on 2009-11-04
I want to use a Ubuntu PC as a file server/print server on my local network.
 
I successfully attached an HP printer to my new Ubuntu PC.  It is connected to my local network and I can access the file server on Ubuntu via my Vista PC, but I can't connect to the Ubuntu printer.  The printer is shared and I set "publish shared printers...".  I see the printer in Vista, but I get the following error when I try to connect:  "Windows cannot connect to the printer.  Operation could not be completed (error 0x0000000d)"
 
What am I missing?

---

### Post by danill2008 on 2009-11-04
> **Utahreddirt said:**
> I want to use a Ubuntu PC as a file server/print server on my local network.
 
I successfully attached an HP printer to my new Ubuntu PC.  It is connected to my local network and I can access the file server on Ubuntu via my Vista PC, but I can't connect to the Ubuntu printer.  The printer is shared and I set "publish shared printers...".  I see the printer in Vista, but I get the following error when I try to connect:  "Windows cannot connect to the printer.  Operation could not be completed (error 0x0000000d)"
 
What am I missing?

Have you tried running CUPS? It can be located at [http://localhost:631/](http://localhost:631/) ;)

---

### Post by Utahreddirt on 2009-11-04
I ran CUPS and added the USB attached printer.  How do I access it from my Vista PC?  I tried "adding new printer/network" - but, it didn't show up.
Thanks,
Utahreddirt

---

### Post by JayKay3000 on 2009-11-04
Dunno bout vista but if you go to 'my network places' and view workgroup computers then acess the machine with the shared printer, find it, right click on it and click connect that adds a shared printer over a network. 

Infact i'm gonna try this cups thing because I want to do this too :popcorn:

---

### Post by Utahreddirt on 2009-11-04
I can see the printer from the Vista PC.  But, when I try to connect, I get an error.

---

### Post by thiefy on 2009-11-06
[Utahreddirt]("http://art.ubuntuforums.org/member.php?u=945377")

i get the exact same problem as you and i see no answer.
printing and sharing worked fine in jaunty... not now with karmic.


i have a folder shared on the karmic pc,
i can see that folder on the windows pc.
then, i can see the printer i have shared also, but  i get that (error 0x0000000d) like you posted.

i don't get why karmic has made it so hard to share a printer so winders pruters can print to it.

anyone able to help?
ps. that cups info link is not helpful for our problem...

---

### Post by Scunnered on 2009-11-06
I have set up my printer, an Epson connected by USB to my laptopusing Karmic to permit printing from another wireless connected laptop using Windows XP.

I followed NetworkPrintingFromWinXP from the Ubuntu documentation.  I would imagine that although this was written for XP that it will work with Vista.  Perhaps if you give this a try it will work

You could also have a look at Top things to do after installing Ubuntu Linux 9.10 Karmic Koala at [http://www.reddit.com/tb/9z2xk/](http://www.reddit.com/tb/9z2xk/) which could also assist

All the best of luck

---

### Post by JonathanAquino on 2009-11-07
After upgrading from Jaunty to Karmic, I found that I had to repeat the "Ubuntu Print Server" instructions in [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) before I could print to it from WinXP.

---

### Post by perce on 2009-11-07
A possible way to share printers is described here: 

[http://http://ubuntuforums.org/showthread.php?t=1248007]("http://http://ubuntuforums.org/showthread.php?t=1248007")

---

### Post by snwyvern on 2009-11-13
Hi there-- Has anybody found a solution for this yet, or at least a cause? I did a do-release-upgrade on my home server and it broke (just...) my printer share. The rest of the SMB stuff is working fine, but I get that same 0x0000000d error when I attempt to print, or to re-add the printer. 
 
I (too) have deleted it from cups and samba using the web-interface, re-added it... Still the same error. 
 
Any ideas?

---

### Post by snwyvern on 2009-11-16
FYI... I was able to come to a work-around with my system. I still have yet to figure the cause (other than doing the server upgrade to the latest version with do-release-upgrade)... But I am able to use the "net" command in Windows (7) to bind the //server/printer to an imaginary LPT... Which works without error, but if I browse directly to the printer and try to add/print that way... It doesn't work and produces that same error.
 
 
 
... Hope this can help someone?

---

### Post by gertc on 2009-11-21
Same problem here. A Canon printer connected to my linux server, shared using samba and cups. Printing worked fine before I upgraded to Karmic. In fact, it still works from a Windows XP client. But not from a Vista 64 client.
The workaround mentioned above (net use) seems to work though.

---

### Post by snwyvern on 2009-11-21
I'm almost certian that this is related to the same issue where a Vista64 or Windows7 64 backup will fail if the "system image backup" option is also checked...
 
... *sigh*
 
I'm not a "power user" how do I go about submitting a bug report for these issues? (I really don't want to screw up my home server to acomplish info-gathering)

---

### Post by Apewall on 2009-12-03
Was having this same issue and came across [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/482836](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/482836)

I will try the work around mentioned in this thread later.  Disappointed that such a feature is broken for vista/7

Windows 7 here on the client machine.

---

### Post by KMPryor on 2009-12-05
I too am looking for a solution.  Same "Windows can not connect to the printer. Operation could not be completed (error 0x0000000d)."  Printer is local to Ubuntu 9.10 and am trying to print from Windows Vista Home Premium (64 bit) . I used to be able to printer from the windows box but now I cant, not sure if the problem started when I upgraded to 9.10.  Thanks in advanced for any support!

---

### Post by phane on 2010-01-18
Canon MP-190 attached to a machine running Ubuntu 9.10 x86 connected via USB.  Worked fine in 9.04 (and all installed versions prior all the way back to 6.10), no other changes.  All 3 computers I have running Windows 7 Home Premium 64 bit encounter the exact same error since upgrading the host machine to 9.10.  I've seen several updates to samba since the upgrade and installed them all, none have fixed this.

One computer I have running Ubuntu 9.10 x64 can print to it just fine, so the problem seems isolated to my Windows machines, which are all running 64 bit 7 Home Premium.

Cups and samba settings all check out.

---

### Post by lyall on 2010-01-20
does the printer have an ethernet connection on it?
if it does run a ethernet cable to it and set it up as a network print.
it stops a lot of problems

if not you can buy a USB Print Server
that way your printer would not have to go thru a PC.

it would be one way around your problem

good luck and have fun learning

---

### Post by ibrahimuwc on 2010-03-02
I had the same problem with Windows 7 (64 bit) and a Brother HL 2040 shared via USB on Ubuntu 9.10 via Samba & CUPS.

I followed the following instructions on my Windows 64 bit machine

run cmd
type: net use lpt2 \\servername\shareprintername

You might be asked to provide the admin username and password of your Ubuntu 9.10

The you will see a message telling the operation was successful

Then go to Control Control Panel --> Add Local printer

Choose the lpt2 port, choose the printer you are trying to add, and use the local printer driver installed the Windows machine.

That's it.

---

### Post by mindbullet on 2010-03-21
Thank you thank you thank you!  That solved my 0x0000000d error!  I was soooo frustrated.  I have two other Win 7 laptops and they find and print to my HP no problem.  This was driving me up a wall!

---

