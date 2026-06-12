---
title: "Wireless not connecting automatically once disconnected"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by navaneethkn on 2010-01-22
Hello,

When system is started, ubunutu is automatically connecting to the wireless connection. If power goes, wireless router will be off and ubuntu will show network disconnected notification. But once the router is back, ubuntu is not connecting to it automatically. When I select the wireless network name from the "NetworkManager Applet" and click on it will show you are disconnected from the network. 

It will be able to connect properly if I do a system restart. Any idea to solve this issue? If not, how can I connect to a network via command line?

Thanks

---

### Post by myth1914 on 2010-01-22
I have a similar issue with my Vaio.  I installed Wicd to manage my network connections and while I still get the occasional drop out, it 9x out of 10 reconnects automatically.

aptitude install wicd

---

### Post by warfacegod on 2010-01-22
> **myth1914 said:**
> I have a similar issue with my Vaio.  I installed Wicd to manage my network connections and while I still get the occasional drop out, it 9x out of 10 reconnects automatically.

aptitude install wicd

Installing Wicd automatically removes Network Manager which is not recommended.

---

### Post by Totergott on 2010-01-23
My problem with my network is that Ubuntu 9.10 disconnects after about 15-25 minutes of logging in.  What I'm doing now is restarting computer to get connection back.  I haven't done anything that would have changed those settings.  This never happend when I had virtualized it before installing.  Any ideas :confused:

---

### Post by warfacegod on 2010-01-23
System> Admin.> Hardware Driver> and activate the recommended wireless driver if there is one.

---

### Post by Totergott on 2010-01-25
I checked the drivers and there was no update for the wireless
The problem had stopped until just recently where it tries to connect to the router, but after 4 times of entering the WPA2 code it still just wouldn't connect.

And is there a way for the wireless manager to at least remember what the code is so I don't have to put in all 26 characters >.<

---

### Post by okhascorpio on 2010-01-26
having same problem here, (64 bit Karmic with recommended sta driver)
tried wicd, better than network-manager. but occasional dropping of connection still exists. happens more often when downloading torrents.

---

### Post by jackdale on 2010-01-27
Same Problem Here:
Karmic 64bit.  Also  have kubuntu-desktop installed...using wireless
Ubuntu must start before the network or it will not connect
Ubuntu will not re-connect to the network if I turn off the router and then back on
Any clues how to do it from CLI?

Edit to add:
To do it from the CLI, check this out [HERE]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html").

---

### Post by Totergott on 2010-02-03
This is getting ridiculous.  I don't understand how I randomly get disconnected on my network, yet when I'm on another network, it won't ever disconnect.  I've had to go back to Windows because of this issue.

---

### Post by The Cog on 2010-02-03
> **Totergott said:**
> This is getting ridiculous.  I don't understand how I randomly get disconnected on my network, yet when I'm on another network, it won't ever disconnect.  I've had to go back to Windows because of this issue.

Did you try wicd as suggested by myth1914? In my experience, it's vastly more reliable than Network Manager. It even works if the GUI won't start.

---

### Post by Totergott on 2010-02-04
> **The Cog said:**
> Did you try wicd as suggested by myth1914? In my experience, it's vastly more reliable than Network Manager. It even works if the GUI won't start.
 
Yes I tried what myth did on both occasions of when I had ubuntu installed.  I did try the wicd and the problem still occured.  I also went and tried other Linux distributions, and I get the same problem.  I gave up on ubuntu about a couple hours ago and just went back to Windows since it's the only thing that works for what I need.  I appreciate the help, but I guess this laptop isn't meant for Linux.   Thanks for your guy's/gal's help.

---

### Post by okhascorpio on 2010-02-10
Hi,

[work-around] right-click network icon-> Edit Connections -> wireless
delet "Auto-<your-wireless-name>" then go back and select your wireless point from list. Connects back instantly.

---

### Post by Neural Nut@work on 2010-02-10
I kinda went through it recently, but i told myself no windows so stuck it out and it paid off ;)

Couple of things please try:
1. If you configured yiour wireless using a special module like "ndiswrapper" ensure to add that word in ```
/etc/modules
```

2. If there was a series of commands you wrote to set it up then put it in ```
/etc/rc.local
``` as a script.

I dont think the raw Ubuntu GUI is comparable to Windows 7; but the flavour of Unix is in using it as a server. Dont give up! :)

3. (Probably the most important) dhclient is responsible for getting an IP Address; I've observed it re negotiates your IP address after a time interval. MAYBE when that interval lapses some setting is not right and the negotiation fails. You have to ```
man dhclient
``` to see if you can play with the interval settings.

..given the above 3, I hope you find your fix! I wish I could give a GUI solution but maybe this would work out better.

---

### Post by jackdale on 2010-02-24
Simple work-around:

1) Click the NetworkManager applet
2) Click "Connect to Hidden Wireless Network"
3) Put your details.

Now under [YOUR NETWORK NAME] you have two choices:

Auto [Network name]
[Network name]

This means that the auto picks it up whenever you start the computer, but if you get cut off (because not enough signal, or you turn off the router, etc), you can just click on NetworkManager, then click on your network name and chose the Network name from the menu (ie as opposed to choosing the "auto")

No problems since.

---

