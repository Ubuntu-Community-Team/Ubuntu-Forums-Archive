---
title: "problem with linksys E1200"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by Jean-C on 2011-08-09
I need help.  I just instaled Kubuntu 11.04 on my computer.  I updated my pre-installed applications with:  sudo apt-get update and it worked fine.  My computer see the router perfectly, i can even configure the router on the internet but for a reason or an other, i can't pass through the router and get access to the Web.

If i connect my internet directly to the computer, my connection work.

It also seem that the router see the internet connection.

My problem is between the router and Kubuntu.

Any help would be appreciate.

Thank's

---

### Post by fslezak on 2011-08-09
Are you using a wired or wireless connection?

---

### Post by Jean-C on 2011-08-09
I am using a wired connection for now.  I will eventually connect 3 wireless computer on the same router.  Any idea of the problem?

---

### Post by Mark Phelps on 2011-08-10
> **Jean-C said:**
> If i connect my internet directly to the computer, my connection work.

Whenever I've seen this problem, the following is what has happened:
1) Internet service was established with the PC connected directly to the cable modem
2) The Internet service tech contacted their shop and passed along the Mac address of the network interface in the PC.  They then entered that address into their customer config database.
3) After that, the PC connects to the Internet with no problem
4) Person buys a router, puts that into the network link between the PC and the cable modem -- and no longer gets an Internet connection.

If THIS is what is happening to you, then your Internet Service Provider (ISP) is using Mac address filtering to authenticate their customers.  Note: If you ask them, they will most probably DENY this.

You have two ways to solve this:
1) Contact the ISP, tell them you have a router now.  They will ask you for the Mac address of the router.  It will be on a label somewhere on the router.  They will then change their database info and that router will connect to the Internet.
2) Find out the Mac address of your PC network connection.  Write that down.  Login to the router admin screen.  Find the config screen that allows you to set the Mac address of the router.  Write down the existing Router Mac address.  Then, use that screen to change it to your PC's Mac address. Save the config changes.  Reboot your PC.  If it still does not get an IP address, then reboot the router, wait 30 seconds, reboot your PC and try again.

---

### Post by amjjawad on 2011-08-10
Do you have another machine with another OS installed on? if yes, see if you can connect to your Linksys via Wireless Connection.

My guess is your Linksys needs to be configured correctly.

---

### Post by Jean-C on 2011-08-11
I finally spoke with Cisco.  They don't give out alot of informations...

Their brand new Kernel is supported by linux once installed activated and conmfigured. (Without any kind of drivers)

So i decided to use their cd from an xp based computer to configure their router.  I had nothing to do but waiting for cisco connect to finish.  Once done, i tried mY linux connection and it was working.

I removed the application of the XP computer after and everything is still working well.

I am planning to install a virtual machine with window's XP on it (Using an old CD of my...ex XP computer)

Cisco peoples told me it would work.

On interesting thing is that you must turn off all security but WEP on the computer and request it to take the configuration of the router.  Next, you have to configure a new Web key in the router and use the same one in the computer.

Leave SSI broadcasting **on **in the router and use the broadcast button to search for your computers.

once found, on the router, you allow the computer SSID and BINGO.

Thank's everybody.

(I think we will have to get use to have a virtual Window's as most of the hardware suppliers are getting their softwares to work only with Window's and MAC.  Any manual configuration include unusual commands to make the hardware work.  In this case, if you don't press the broadcast button in the router web interface, you won't make it with this router even with Window's.

I hope it is going to help someof you as Cisco is now including Cisco connect with all of their new products.

---

### Post by amjjawad on 2011-08-11
Glad you managed to fix it :)

---

