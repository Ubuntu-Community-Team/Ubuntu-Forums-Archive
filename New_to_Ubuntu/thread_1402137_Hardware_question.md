---
title: "Hardware question"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by augie2051 on 2010-02-08
Here is a question i am not sure if anyone can/will help me with.  My wife still uses a M!crs@ft Laptop and is having an issue.  For some reason her computer is not detecting her network adapter neither the wlan or etho. I replaced the wlan thinking that was the issue and it worked for a while but is not working again.  Any ideas on what can be causing the problem?  Even when i go to Device manager the network adapter isn't recognized.  Any help would be appreciated......

---

### Post by zeroseven0183 on 2010-02-08
Would you mind if I ask how old is the laptop?

How about the USB ports? Are they working perfectly?

What happens when you run a LiveCD on that machine and check if the WLAN is working?

---

### Post by pizza-is-good on 2010-02-08
I agree with post #2.

Also, have windows try to find an updated driver for your network card.

~pizza

---

### Post by augie2051 on 2010-02-08
The laptop is a little older than a year old.  i have updated the drivers and the live cd doesnt recognize the adapter either

---

### Post by pizza-is-good on 2010-02-08
Is it a Dell?

I had an issue with the Intel Network card a while back, but that was only in windows....

Try removing the card, restarting the computer, and then put it back in and start it again. Will that make it work for a while again?

Make sure all the Hardware drivers are enabled
System>>Administration>>Hardware Drivers

---

### Post by ajaysutton on 2010-02-08
I'd boot with a live CD and see if Ubuntu detects it.  That'll tell you very quickly if your problem is Windows or hardware.

---

### Post by augie2051 on 2010-02-08
> **pizza-is-good said:**
> Is it a Dell?

I had an issue with the Intel Network card a while back, but that was only in windows....

Try removing the card, restarting the computer, and then put it back in and start it again. Will that make it work for a while again?

Make sure all the Hardware drivers are enabled
System>>Administration>>Hardware Drivers

It is a Dell.  I will try that they may be why it worked after i installed the new card.  Should i buy new computer?

---

### Post by 440corbon on 2010-02-08
I don't know if this helps. but, For my wifes lappy running windows I have to plug the cable modem and my computer into the numbered ports. I can't hook the ethernet off the modem into the ethernet port on the wireless modem. For some reason windows doesn't like it. I have a wubi install of ubuntu on there and it will work either way.

---

### Post by lyall on 2010-02-08
> **augie2051 said:**
> Here is a question i am not sure if anyone can/will help me with.  My wife still uses a M!crs@ft Laptop and is having an issue.  For some reason her computer is not detecting her network adapter neither the wlan or etho. I replaced the wlan thinking that was the issue and it worked for a while but is not working again.  Any ideas on what can be causing the problem?  Even when i go to Device manager the network adapter isn't recognized.  Any help would be appreciated......

you have malware, virus, trojans and/or adware problems

if you have to have windows on it, wipe the hard drive and reinstall windows
it would be faster than to trying to clean all the problems

to remove malware use Malwarebytes' Anti-Malware at [http://www.malwarebytes.org/]("http://www.malwarebytes.org/")

to remove adware use Ad-aware from [http://www.lavasoft.com/]("http://www.lavasoft.com/")

to remove trojans see [http://www.techsupportalert.com/best-free-trojan-scanner-trojan-remover.htm]("http://www.techsupportalert.com/best-free-trojan-scanner-trojan-remover.htm")

and you still need a good anti-virus program 
see the following sites
[http://free.avg.com/us-en/homepage]("http://free.avg.com/us-en/homepage")
[http://www.avast.com/index]("http://www.avast.com/index")


download them and copy them to  CD or memory stick
and install on the windows machine and ran them
at less 2 or more times each, until you get no more reports of any problems

this will take a long time
after you got it clean ( you hope) you will have to ran them again a less once a week/month as long as we have windows

there are other programs to help keep the windows machine some what clean
it is the nature of windows

if you copy or save you old data - files, pictures, music, etc  from the windows machine please run the above programs on them.
copying to CD them to a different pc the file are write protect (read only)
you will have to remove the read only permissions for them then ran the above program to clean them

copying the file to a memory stick you can clean them 
they are not write protected like on CDs

***OH yeah*** if you have made back up from the laptop you should try and clean them too, before you try to use them or your problems will just come back
again, again, again................

You can also take it to the Greek squad and and would be cheaper to buy a new laptop
then you have your own laptop to install Ubuntu on (if you brought her a new one)

I hope this little bit info helps you

good luck and have fun learning

---

### Post by warfacegod on 2010-02-09
Telling someone they have spyware and viruses considering what little information has actually been posted about this issue is seriously jumping the gun. Telling them wipe their hard drive because of it is down right irresponsible.

---

### Post by Jazzy_Jeff on 2010-02-09
> **warfacegod said:**
> Telling someone they have spyware and viruses considering what little information has actually been posted about this issue is seriously jumping the gun. Telling them wipe their hard drive because of it is down right irresponsible.

I agree, there is nothing pointing to a virus or malware. He stated the live cd does not see the adapter either. Sounds like a hardware problem somewhere.

---

### Post by zeroseven0183 on 2010-02-09
> **augie2051 said:**
> It is a Dell.  I will try that they may be why it worked after i installed the new card.  Should i buy new computer?

I don't think you need to buy a new computer until we sort out things first. It's becoming more and more obvious that this problem is hardware-related. It could probably motherboard issue.

If it's still under warranty (although it's already a year old) then you need to ask the manufacturer to check it.

---

### Post by warfacegod on 2010-02-09
On my laptop, last year, my hard drive started failing. It caused all sorts of other hardware to misbehave including:

Sound card.
Ethernet and wireless cards.
1 of 2 RAM cards stopped being recognized.
LCD would shut down randomly.

And that's just to name a few. I tested the drive 3 times from 2 different LiveCDs and each time it the results were grim. When I replaced the drive, I was pleasantly surprised that all of my hardware was working properly again.

As a test, I put the old drive into another laptop. I wiped it and did a fresh install of 9.04 and the other hardware issues still remained.

I'm not saying to immediately go get another HDD but testing your drive is certainly worth looking into.

---

### Post by lyall on 2010-02-09
as warfacegod said it could be a hard drive issue

I am PC tech.  I have seen this problem more than 20 times in the last 6 months at work.  I have ran CheckIt Pro on them and all hardware checked okay

running checkIt Pro, malwarebits, ccleaner, easy cleaner, McAfee Anti-Virus and other programs to clean the pc which can take up to 6 hours to clean it, on a 40 to 60 GB hard drive.  Larger hard drive do take longer to check and clean.

As a last resort I re-image them, but I have to sometime save their data.  I can re-image a PC/Laptop in less than 30 minutes and 30 more minutes getting it set back up for them, including setting up their printers (1 to 5 network printers)

To check the condition  of a hard drive.  First find out the make and model.
Than go to the manufacture's web site and find software to check the condition of the hard drive, most of them offer a free download to ran the diagnostics to find out if the drive is good, bad or failing.
Seagate offer one the does work with other manufactures hard drives.
see link [http://www.seagate.com/www/en-us/support/downloads/seatools]("http://www.seagate.com/www/en-us/support/downloads/seatools")

good luck and have fun learning

---

### Post by warfacegod on 2010-02-09
> **lyall said:**
> as warfacegod said it could be a hard drive issue

I am PC tech.  I have seen this problem more than 20 times in the last 6 months at work.  I have ran CheckIt Pro on them and all hardware checked okay

running checkIt Pro, malwarebits, ccleaner, easy cleaner, McAfee Anti-Virus and other programs to clean the pc which can take up to 6 hours to clean it, on a 40 to 60 GB hard drive.  Larger hard drive do take longer to check and clean.

As a last resort I re-image them, but I have to sometime save their data.  I can re-image a PC/Laptop in less than 30 minutes and 30 more minutes getting it set back up for them, including setting up their printers (1 to 5 network printers)

To check the condition  of a hard drive.  First find out the make and model.
Than go to the manufacture's web site and find software to check the condition of the hard drive, most of them offer a free download to ran the diagnostics to find out if the drive is good, bad or failing.
Seagate offer one the does work with other manufactures hard drives.
see link [http://www.seagate.com/www/en-us/support/downloads/seatools]("http://www.seagate.com/www/en-us/support/downloads/seatools")

good luck and have fun learning

Glary Utilities is another absolutely fantastic app for fixing Windows. I will never again (aside from never using Windows again) use McAfee software after discovering that their firewall stays on *after* removing the program. Took me three days to figure that out. I had to install it again, turn off the Firewall, and then remove it. That is exactly the kind of idiocy that helped me decide to leave Windows.

---

### Post by augie2051 on 2010-02-10
Thanks for all the input.  I am starting to think its a motherboard issue.  The crazy thing is that it works sometimes and sometimes doesn't.  If i unplug the wlan card and re-plug it works again or if i reboot sometimes it works too.  If it werent such a new and good computer i would just scrap it for parts and get her a new one.  at this point i seem to be running out of options.  I wish she would let me convert it to ubuntu........

---

### Post by augie2051 on 2010-02-11
Ok so now today when I ran the liveboot again it told me the hard disk had several errors and needs to be replaced.  Can I just re map with ubuntu and maybe fix this problem without replacing the hard drive?

---

### Post by warfacegod on 2010-02-11
> **augie2051 said:**
> Ok so now today when I ran the liveboot again it told me the hard disk had several errors and needs to be replaced.  Can I just re map with ubuntu and maybe fix this problem without replacing the hard drive?

Palimpset has a tendency to throw false positives. Use gsmartcontrol to test it. If they both say your drive is going bad then I'd listen:

```
sudo apt-get install gsmartcontrol
```

---

### Post by augie2051 on 2010-02-11
> **warfacegod said:**
> Palimpset has a tendency to throw false positives. Use gsmartcontrol to test it. If they both say your drive is going bad then I'd listen:

```
sudo apt-get install gsmartcontrol
```

I will try is gsmartcontrol a GUI if not do i have to test from terminal?

---

### Post by warfacegod on 2010-02-11
> **augie2051 said:**
> I will try is gsmartcontrol a GUI if not do i have to test from terminal?

Gsmart has a GUI. You'll find it in the System Tools menu after install.

---

### Post by augie2051 on 2010-02-11
I tried to install gsmart and got teh following error:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Never seen this on my machine before.....

---

### Post by warfacegod on 2010-02-11
> **augie2051 said:**
> I tried to install gsmart and got teh following error:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Never seen this on my machine before.....

Usually means you've got Synaptic or Update Manager open.

---

### Post by augie2051 on 2010-02-11
Sorry but now this is getting frustrating.  I downloaded but receied the following error when i opened it: 

Failed to execute child process "su-to-root" (No such file or directory)

---

