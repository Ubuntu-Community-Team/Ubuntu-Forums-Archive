---
title: "Is there any easy home networking?"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by gottatrieit on 2007-09-05
I have been searching, following directions, and rebooting my machine for the last week or so trying to follow instructions to set up a simple home network between my three Ubuntu Feisty machines!  They are linked through a router and all three have individual internet access through this router.  
	I had a semblance of a network when my wife was using XP, but problems developed with her machine and she finally allowed me to install Ubuntu.
	The instructions that I've followed were from the thread pointed to here: 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+client%2Fserver](http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+client%2Fserver)

and also from the book “Linux for Dummies:ALL-IN-ONE DESK REFERENCE.”  These both pertain to using NFS as a network server/client program.

	Talking earlier today in the LoCo IRC channel for Florida, syberghost informed me I could use just plain file sharing.  I tried, syberghost, but I couldn't even get that to work for some reason.
       Can anyone point me in the direction of a tutorial, how to, or other information that will explain in simple detail how to connect these computers so I can share files and a printer between them?
	Thanks in advance.

---

### Post by kbtarl on 2007-09-05
You might want to check out [THIS THREAD]("http://www.linuxquestions.org/questions/showthread.php?t=549334") from [Linuxquestion]("http://www.linuxquestions.org"). THis thread talks about using [Samba]("http://us4.samba.org/samba/")to share files.

I am just a noobie for sure. Found this doing a Google Search.

---

### Post by gottatrieit on 2007-09-06
kbtarl:
 I had smb working on my wife's XP box before she finally let me put Feisty 7.04 on it. I've also tried nfs and file sharing techniques, and I'm not computer savy enough to make it work without some detailed and specific instructions. 
 I've pretty much decided that because all three computers are in the same room and my two are basically side-by-side and connected by a kvm switch, it's senseless to network them. (I only wanted to because, like Mt. Everestt, they're there! :) )
 My wife's machine is on the other side of the room and I have access to it and I also set  up her printer, so now she's happy as any Penguin can be! :lolflag:
 Thank you for replying and who knows, I may try again anyways!

---

### Post by coldstatue on 2007-09-08
EDIT: A note to the OP - these instructions you linked to may only work with static, specified IPs. I am very new at linux (only 4.5 months as my exclusive OS), but I know there can be issues with domain name recognition, which is why I use IPs in the place of server.domain, as listed in the poster's fstab and manual mounting instructions.

I really hope a genius comes in here to explain. I had NFS and printer sharing working like a dream.. then, it just stopped. I followed (and refollowed, and refollowed) all the steps in the guide you posted. (Though I got them elsewhere - they look exactly the same). There must be some other element that folks are leaving out - a setting elsewhere that can corrupt NFS, or block it. I have my Feisty box, and my wife has a Feisty laptop. Same situation as yours - she gets the Internet direct. We've been without for 2 months. We just gave up, and she emails me files she needs to print. I'll be subscribed to this one. 

I think my problems started when I moved /home to it's own partition, or when I shut off some services, though I turned them all back on.

and a humble request from any helpers - please help us with NFS, as we have either tried Samba and couldn't get reliable service or want to stick with 'nix standards.

Thanks in advance

---

### Post by coldstatue on 2007-09-08
my problem was this - even if firestarter doesn't show in session apps, even if it is not in the systray, it can be on. *smacks forehead* ..... *smacks forehead again*..... *repeatedly*

---

### Post by gottatrieit on 2007-09-09
coldstatue:
 1.) I use static IP's that I've assigned and posted to the router I'm using.
 2.) I just checked my two machines and will check my wife's a little later, but firestarter is not installed on either one.
 3.) I had/have a screenshot of some of my settings, but I can't get them to copy/paste along with the document I placed it in!  (I'm sure that would help give someone a clue as to what I may have done wrong.)
  Thanks for your reply.  I don't use emails, my wife and I just swap floppies or upload to a usb drive to get stuff from one machine to the other, but I think getting it "direct" would still be more fun and a "feather" in my "Look, Mom! See what I can do!" file. roflmao  (It's hell to be almost 60 and still technically challenged!!!)


                                  Rick :redface:

---

### Post by coldstatue on 2007-09-10
Well, Rick. I hate to say that I'm not the guy who can get the info needed from you. I do remember fiddling with my router for some time to get this working, but I'll assume that's not the issue. I have one more question, but then, I hope someone else jumps in.

Under System>Administration>Network Tools, there's a simple ping app. See if you can ping your wife. Can she ping you back? I mean I know you're almost 60, but. OK... sorry.. sorry.. Bad joke.

(BTW - I'm half your age, so... I guess I'm twice as challenged :0)  But hey, Windows is a huge adventure for my parents. At least your using Linux.)

---

### Post by gottatrieit on 2007-09-10
:-D  Hey, cold, if we can't laugh at ourselves, life would be just too boring! Humor keeps us all young!
 Yeah, I can ping all the machines from one to another.  I tried to post a screen shot I made of my settings, but it won't paste into here.
 I probably typed something in wrong.  Also, I've got another idea to try and if it works, I'll let you know.

---

### Post by coldstatue on 2007-09-11
Well, the last thing I can suggest is to make sure your exports info is correct. Also, it would help if you tried to manually mount the shared folder in a console, and post the output here.  If is says there are no rules specified, you have put a space after the ip, before the (ro rw type stuff) That's the one thing I remember screwing up, but the output could be what would allow a person more knowledgeable than myself to get your network up and running.

---

### Post by coldstatue on 2007-09-11
BTW- if you can get the NFS file sharing working, the printer should work, no problem. You may need to fiddle with the settings, but my experience was that fixing the file sharing issues fixed the printer sharing issues.

---

### Post by gottatrieit on 2007-09-11
[SIZE="3"]  ANSWER: Yes there is!

  ttp://ubuntuforums.org/showthread.php?t=218630&highlight=HOWTO+Ridiculously+easy+home+network

Is the post the post I'm referring to.  I just finally finished connecting two of my machines together and will work on the third tomorrow.
Coldstatue, all I had to do was install vsftpd onto the two computers and follow the directions.  I guess following the directions the first time I tried was "too hard" as I did it my way.  Wrong Answer!! roflmao   I finally took the time to read each step, and voila, success at last!!

            Thanks, coldstatue and kbtarl for your respnses. [/SIZE]

---

### Post by coldstatue on 2007-09-12
kbtarl? Isn't that the burnt, crispy stuff left in the bottom of the pan when you finish a tuna casserole? Anyway, glad you got it working! I should have linked to that post. i have read it in the last week. i just assumed you wanted NFS. Hope the printer works for you.
Cheers.

---

### Post by plantman on 2007-11-12
I am needing help connecting to my printer with my laptop. I have a HP Photosmart 3100 connected via USB to my XP desktop. This computer is connected with ethernet cable to wireless DLink router. My laptop is wireless and running Ubuntu 7.10. I can share folders with both machines but no luck printing with the wireless laptop. I am a total newbie with Linux so I need specific instructions.
Thanks in advance...

---

### Post by mtn on 2007-11-12
Hi, not sure this is exactly what you are after, but it might help! I thought I had posted this on another thread but I can't find it now.

I finally got 2 Ubuntu machines sharing a printer over a wireless network using this tutorial: [http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS](http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS)

I had to stop the firewall on the server, using Firestarter, while setting the printer up. I also had to create a new policy to always allow access to the print server (Ubuntu machine) 0n port 631 from the client machine’s IP address.

Once the Ubuntu machine was setup as a server for the printer it took about 5mins to get an Windows XP machine sharing the printer, over the same home network, using this how to: [http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html). The only bits I actually had to use are posted below.

( Note: my network printer address - [http://192.168.2.4:631/printers/LaserJet-1018](http://192.168.2.4:631/printers/LaserJet-1018))

————————————
**Hostname lookup**

Another common step is to ensure that hostname broadcast by CUPS is accessible from the Windows XP machine. If your CUPS machine is accessible using a name rather than just an IP address then you don’t need to do anything for this step. If the CUPS machine is not accessible via it’s hostname then you need to set a mapping between the CUPS hostname and its IP address in the Windows hosts file. Under WindowsXP the host file is in C:\WINDOWS\SYSTEM32\DRIVERS\ETC\HOSTS, in Win2k replace WINDOWS with WINNT. The format is simple:

```
# Example hosts entry
192.168.0.3 rock
```

Under some CUPS server configurations you will be able to use the IP address instead of the hostname, but often only a hostname will work.
Postscript Printing

To use a printer queue as a Postscript printer requires a Windows XP Postscript printer driver, such as the built-in MS Publisher Imagesetter or this freely available one from Adobe.

**Built-in MS Publisher Imagesetter**

To use the MS Publisher Imagesetter driver, use “Add Printer” to add a new network printer, select “Connect to a printer on the Internet…” and enter the URL for your printer queue (e.g. [http://rock:631/printers/Epson](http://rock:631/printers/Epson)). When prompted for a driver select a Manufacturer of “Generic” and the Printer “MS Publisher Imagesetter”.

---

### Post by plantman on 2007-11-19
Thanks! I finally got it working. I could run the printer via usb with my laptop but not on the network. I just checked and rechecked everything and am not sure what exactly worked but I can print with the XP desktop as the server.

---

