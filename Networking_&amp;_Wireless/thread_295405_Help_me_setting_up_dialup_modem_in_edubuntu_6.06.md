---
title: "Help me setting up dialup modem in edubuntu 6.06"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by kamalarora2kin on 2006-11-08
shifted to another thread

---

### Post by Mark_in_Hollywood on 2006-11-14
I'm using Ubuntu, so bear with me about some of the below. I don't know the names of certain things in your system. That is in Ubuntu the text editor is GEdit. I don't know that name in Edubuntu. I'm hoping you know a little computerese and we won't get lost here.

I'm guessing a little here, because you didn't give quite enough info, but let's try to get you online first, and maybe worry about details second.

In a terminal or console do:

sudo wvdialconf wvdial.conf

your modem/port will be scanned and the software will automatically write it's "findings" to the system.

It should also bring up a text editor window. Remove any REMs from the following lines:

User Name

Password

Phone number

add your User Name, Password and Phone Number. SAVE the file.

Again, in a terminal or console do:

sudo wvdial

the program will ask for your password. Give it. The system should dial and start the pppd (ppp daemon).

Once the terminal window shows a connection speed and 7 lines with odd characters in them, you can surf or use apt-get, synaptic or whatever.

If this doesn't work, please post the name of your modem model, and model number. I need to know if you have a hardware (controller) based modem and not a software-Win-Modem.

---

### Post by kamalarora2kin on 2006-11-15
shifted to another thread

---

### Post by rksenthilkumaar on 2006-11-15
HI!
I also need help in setting up a Dialer for my Modem 
(SmartAX MT 882).
I'm actually using a Dataone (BSNL) connection. The Modem is connected to my computer via LAN card.
The card has been detected & also I'm able to configure my Modem with a Static IP for it to work.

But I don't have any knowledge about creating a dialer. In my XP, even though I use Broadband, I connect to net only through dialer. The Modem used to be on always & only when needed I log on!

So please help me set up a Dialer!

---

### Post by Mark_in_Hollywood on 2006-11-15
kamalarora2kin:

If you want to use the modem in Edubuntu, I need to know if it's a hardware or software based modem. That is, the modem card has hardware to connect within Linux/Edubuntu to get on the 'net. Some modems are "software" or Microsoft-Windows only modems. They substitute part of Windows for hardware. If you want my help, you must tell me the name and model of your modem. Also, Google the name, model and HCL (HCL mean hardware compatability list) if your modem is hardware it will say so in HCL, if it isn't it will probably not say that.

Next, please see Google: Wiki Ubuntu DialupModem. It may still help. 

Please surf over to:

[http://linmodems.technion.ac.il/#details](http://linmodems.technion.ac.il/#details)

and read what they have to say there. That site may be the best on the 'net.

---

### Post by Mark_in_Hollywood on 2006-11-15
Please re-post your questions in a separate thread. This one is complex enough without helping two people separately.

Thanks.

---

