---
title: "1Mb/s wireless speed on startup"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by jammin2222 on 2008-09-20
Hi peeps
Im using Ubuntu 8.04

I'm hoping this should be simple. I have got my wireless network connected eventually after a week of troubles. The biggest trouble being between the pc and my chair.
 Each time I reboot the laptop the wireless connection is set to a stupidly lame 1Mb/s. (mega slow) I can change this using: 

sudo iwconfig wlan0 rate 54M 

and then clicking on my network name to reconnect. Its then reported at 54mb/s and seems to run normally until i reboot and have to do it all over again.

how do i get the setting to stick across all user accounts? I have tried this:

sudo iwconfig wlan0 rate 54m auto 

but this doesn't change the connection speed at all and dose nothing at start up either.

 I'm kind of hopeless with the terminal at the moment so please be gentle and make it idiot proof if at all possible, as I'm an idiot on a humongous  scale :)

I'm guessing i have to save the line of text as an executable file and add it to the startup programs somehow? Or maybe not, Im an idiot don't forget lol

Cheers guys

Ben

---

### Post by Another Monkey on 2008-09-20
I've spotted the same thing - I'm wondering if it has anything to do with the driver?  I just bought a new Edimax pc card for the lappy as the other Belkin dongle I have seems to fry USB ports.

Weird thing is, if I do "iwconfig" at the terminal I show 54mb/s; and I am certainly seeing transfer speeds much higher than 1m/s.  I wonder if there is a bug in the GUI?

Also, [this thread (has potential workaround)]("http://ubuntuforums.org/showthread.php?t=768301") lead me to [this bug]("http://https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660").

I also checked out [speedtest.net]("http://www.speedtest.net/") and that showed 6051kb/s download with a 377kb/s upload over the wireless.  That about right for my connection.  I think the GUI is talking mince.

I am using the rt61pci driver on a wireless running WPA.  Dunno if any of this helps.

---

### Post by jammin2222 on 2008-09-20
my network card is a Belkin F5D7010 and the system says its using the rt2500 driver, so it might be a bug in the gui as we are using different drivers/cards.

It seems funny that somebody would set a default to be the worst available option when programming a driver. who's ever thought "I want my network to go really slow please?" I'm semi sure they wouldn't deliberately make it do that and makes me think there is a problem with something. how i am meant troubleshoot things using the terminal without learning every aspect of Linux ill never know.

I can only hope that future distributions have more GUI's that help you set up and manage your system and keep it running at its best. 

it looks like i will have to manually enter the command to set the bit rate each time i log on. Annoying 

unless somebody can tell me how i can run
```
sudo iwconfig wlan0 rate 54M
```each time before i log in?

Thanks guys n gals

Ben

---

### Post by lswb on 2008-09-20
"unless somebody can tell me how i can run

sudo iwconfig wlan0 rate 54M

each time before i log in?"

Put that line in /etc/rc.local before the exit line but don't use sudo. There are some comments in /etc/rc.local that explain.

---

### Post by Another Monkey on 2008-09-20
Assuming the worst is standard practice in many fields of IT. The worst is the lowest common denominator, so is more likely to work.

I am just a bit disheartened that such an obvious bug got past Ubuntu QA.  This would never have happened with a Microsoft product (joke).

---

### Post by jammin2222 on 2008-09-20
Thanks for the info but im stuck. I found the rc.local file using the GUI not the terminal as i haven't a clue how that works. I double clicked it and the only option that did anything was Display. I entered the command in and clicked save but it said i don't have permission. I know i have done something wrong.

Stumped again

Thanks once again 

Ben

---

### Post by lswb on 2008-09-20
Sorry. The files in /etc belong to root so they cannot be edited as a regular user. One way to do this is to open a terminal and type

gksudo gedit /etc/rc.local

---

### Post by jammin2222 on 2008-09-21
Thank you so much that has solved it. i can now boot up without having to goto the terminal each time. 

Thank you Thank you Thank you 

:guitar:

Ben

---

### Post by canplaythegame on 2010-06-04
> **lswb said:**
> "unless somebody can tell me how i can run

sudo iwconfig wlan0 rate 54M

each time before i log in?"

Put that line in /etc/rc.local before the exit line but don't use sudo. There are some comments in /etc/rc.local that explain.


i am very new to linux and searched for networking speed problems
this iwconfig rate 54M thingy has fixed it a little
still not as fast as my windows transfer speed
but i went to edit rc.local file and it says this file by default does nothing :confused:

i am using a ubuntu 10.04
dual boot with vista
when i just recently bought a netgear readynasduo
i started to transfer stuff across 
using ubuntu i was getting 100kb/s
using vista i was getting 3mb/s
now with this fix ubuntu is getting 1.3mb/s

is there anything else i should look at

daniel d

---

