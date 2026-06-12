---
title: "No wireless :("
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by leonard71 on 2007-05-16
Alrighty, a recent power outage somehow decided to corrupt my windows configuration.  So rather than reinstall Windows I decided to have some fun with Ubuntu.

The wireless card I have for my desktop is the ASUS WL-138g V2.  I did have it working when I was running XP Pro so I know it's functional but now that I have Ubuntu it doesn't seem to be working.  The system does seem to recognize that I have a wireless card.  When I go into the device manager it lists it as BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.  When I click the little computer icon at the top it won't let me click wireless networks but when I click on manual connection I can go into the properties of the wireless connection.  But the odd thing to me is, when I run ifconfig in the terminal eth0 (wired connection) shows up but I don't see eth1 (wireless) at all.  it doesn't even show up there and I assume it should...I'm not too good at linux. :<

Anyway, I tried manually giving it an IP address and putting in my router broadcast name.  (I am cisco networking certified so I know that information was correct. :D)  And it didn't get a connection that way either.  I took all the encryption off my router so I know that wouldn't be getting in the way either.  Soooo before I say screw it all and go back to windows, can anyone help me?

---

### Post by encompass on 2007-05-17
Are your runnig fesity 7.04? if so try this....
This guy was happy... maybe you too?  Be sre to search the forums before posting...
[http://ubuntuforums.org/showthread.php?p=2636352](http://ubuntuforums.org/showthread.php?p=2636352)

---

### Post by leonard71 on 2007-05-17
Ya I'm running 7.04 but for where my computer is, it would be a real pain to move it so I could plug it into the router.  So at this point my computer can't be connected to the internet until the wireless works.  I was hoping for a solution where I didn't have to move the computer but it appears Linux is just that dependent on an internet connection.  And that kinda blows.  :(  I might just go back to windows because it's not really worth moving my beast of a machine just for this little project.

---

### Post by encompass on 2007-05-17
So is windows when it's wireless drivers don't work.  You can download each peice your self.  Look in synaptic and when you click ont he file to install it will give you a list of dependancies... right them down and download them yourself.  Burn them to a cd rom and install each one manually.

---

### Post by leonard71 on 2007-05-17
Alrighty I finally decided to get my lazy butt in gear and take my computer to where I can hook it in.  I updated everything and ran the stuff in the first link and it did help a lot.  My wireless card now recognizes my router and says it's connected at 61% but I have no internet.  :(  When I attempt to ping my router from the terminal, it says network is unreachable.  Any suggestions?

---

### Post by encompass on 2007-05-18
Does your wireless connections have any encryption?  If so, turn all of it off, and see if you can connect then.  What program are you using to connect to the internet with?  The network manager, thats program you run from the top right of the screen.  Or standard network-admin screen found in system administration network?

---

### Post by leonard71 on 2007-05-18
I got it to work!  I came home from work at lunch and turned my computer on and messed with it a bit and couldn't get it to connect but I left my computer going.  I just got home and reconnected and it's working now!  It's pretty slow but that's more to do with the wireless card and not linux.  I had the same issue of it being slow when it ran on windows.

Thank you for your help!  :guitar:

---

