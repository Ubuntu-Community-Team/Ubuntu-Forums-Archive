---
title: "Lost wireless with knetworkmanager - Can't get it back!!!"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by madcow72 on 2007-01-13
Hello!  I'm using Kubuntu 6.10 with an installed D-Link PCI54G wireless card, connecting to a Netgear WGR614 router.  Using the Wireless Assistant Manager that comes pre-packaged with Kubuntu and entering my WEP key allowed me to connect with the router out-of-the-box.  

I then installed knetworkmanager to allow me to save my WEP key settings after a reboot, but as soon as I installed it, I lost the ability to connect to my router!  I've tried entering all of the same security settings into knetworkmanager, rebooting, uninstalling knetworkmanager, and even disabliing WEP protection on the router.  But I cannot reconnect!  

I can still see my network, so I know the card is working.  Every time I try to connect, however, I just get an error saying that it can't connect.  Any suggestions would be great!

---

### Post by madcow72 on 2007-01-13
Okay - partially solved.  After removing knetworkmanager, rebooting, and disabling WEP protection from the router, I am able to connect insecurely.  Unfortunately, no attempts to add the WEP key protection are allowing me to connect.
More on that later if I get it to work.

---

### Post by daller on 2007-02-04
I'm running Kubuntu 7.04 where knetworkmanager is installed per default!

Some time ago my wireless also stopped working!

I can't see any networks in knetworkmanager, and a simple ifup also fails...

Any ideas?

---

### Post by daller on 2007-02-06
The most important thing to get the wireless back up, is the following:

* Open /etc/network/interfaces
* Remove or comment out all instances of wireless setups
* Save and close the file
* restart (well shouldn't be neccessary, but it's the easiest way to reset it all :D)

...At least it got my wireless back up!

---

### Post by madcow72 on 2007-02-08
Hey daller,

Thanks for the suggestions!  I had already tried commenting out any mentions to networks in /etc/networks/interfaces and restarting.  That didn't seem to do anything for me, unfortunately.  However, I did this after uninstalling knetworkmanager, and possibly using various other approaches to get the network running.  In the end, (I know it seems silly, but I had to get the network running with at least WEP protection), I backed up /home and reinstalled 6.10 -> It works again!  I have to manually connect to the network everytime I restart the computer, but it's worth it to have everything running!

I wish I were talented enough to figure this out, but what we really need is a checklist of which settings need to be in place for wireless configurations to work under a set of certain conditions.  Like I said above, I kept trying combinations of different tricks or network managers hoping to hit upon the right one...but no.

Thanks again for your input!

---

### Post by daller on 2007-02-08
Well, I can only say that this will be solved perfectly with feisty, even now in it's beta stage, I have a great wireless-support with knetworkmanager!

IMO feisty is more than stable enough for everyday use! (haven't experienced a single crash, which is kinda weird considering the stage of feisty! - I really do a LOT of tweaking!) - But don't tell the admins that I told you so! :D (Officially feisty is only stable when we reach April! :D)

Good luck!

---

### Post by madcow72 on 2007-02-12
Hey daller!

You know, that's actually good to hear about feisty!  I may consider installing it to start checking it out.  Sounds like a very productive way for me to waste more time!  Knowing that I have everything backed up, I may try that on my work machine, which is the computer I spend most of my time on.  Once again, I appreciate your input. :)

---

### Post by Fungyo on 2007-03-06
the post from daller was the solution that worked for myself.

cheers :)

---

### Post by tanguyr on 2007-04-30
> **daller said:**
> The most important thing to get the wireless back up, is the following:

* Open /etc/network/interfaces
* Remove or comment out all instances of wireless setups
* Save and close the file
* restart (well shouldn't be neccessary, but it's the easiest way to reset it all :D)

...At least it got my wireless back up!

=D>=D>THANK YOU DALLER!=D>=D>

that fixed me up, i can now leave my desk!

---

