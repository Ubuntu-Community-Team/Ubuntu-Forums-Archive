---
title: "How to know if modem is working?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Ethelbert2 on 2007-03-02
[SIZE="3"][COLOR="DarkGreen"][FONT="Georgia"]Using Xubuntu on an old p3 with 192RAM.

While I am trying to get a wifi card going (separate posting) I am also trying to make a modem work (as a fallback position to get at least some connection to the Internet).

It has an Intel 536 chipset and I found a very good walkthrough for installing the driver for this in the Ubuntu wiki hardware section.

I did it and things seemed to work right. So now my card is listed on the PCI list. 

I plugged in the telephone line.

I used the network manager GUI to configure it and enable it but am then left hanging. Nothing seems to happen.

Firstly I have no idea if it is working or not. How can I tell? 

There is no button to press to make it connect or disconnect. 

Calling up Firefox does not bring up a dial-up connection dialogue. (Both these things happen in Win XP etc dare I mention).

How do I do know if all is well and I have simply missed out something or do I have to do other stuff (maybe change the name I entered - I used "dev/modem" but it might be something else). 

Advice would be appreciated.[/FONT][/COLOR][/SIZE]

---

### Post by cookfromfrozen on 2007-03-02
Hi

If it shows up in the "Networking" applet when it didn't before, there is a good chance it is installed correctly so it should just be a case of configuring it properly now.

There is a good interface for configuring modems called "gnome-ppp".  It isn't installed by default, but it should install from the CD-ROM (see your wireless thread) or you'll be able to get it if you get your wireless working.

You can install it by selecting the "gnome-ppp" package from Synaptic or by the following command in a terminal:

```
sudo apt-get install gnome-ppp
```

You can start it by typing this (in a terminal):

```
gksu gnome-ppp
```

You could create an icon for it later. 

This should help you to detect the modem and see if it will dial out etc.

---

### Post by Ethelbert2 on 2007-03-04
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]
Thanks to the veru busy cookfromfrozen who answered two threads I have.

I intended to use the modem to download stuff to get a wifi going (see other thread) but in the event got the wifi first.  Anyway that meant I could get gnome-ppp (not there on the DC or the Ubuntu dvd so needed Internet) [/FONT][/SIZE]
[SIZE="1"][COLOR="YellowGreen"]
[For those without Internet, I think you can find it as a deb file to downlaod somewhere else and carry over on a usb or whatever, which you can double click to install. 
But it has about a dozen dependencies which you would have to check you have, or download as well.  Fortunately I short-circuited that. There may be more complications too].[/COLOR][/SIZE]

[FONT="Georgia"][SIZE="3"]The GUI let me configure the modem easily but when I pressed the connect button it says "cannot open modem".

I think the drivers loaded Ok - as per the wiki page on modems -   and I know that 536 is correct because I had previously tested this computer with WinXP which found the drivers automatically on the Internet and 536 is what it got - and then it did connect successfully on the line. 

Back in Xubuntu the modem shows up in Network Manager too. But though everything filled in - nothing. And using gnome-ppp which is a little better as an interface, just "cannot open"

Please does anyone know what the problem might be?

[/SIZE][/FONT] [/COLOR]

---

### Post by Ethelbert2 on 2007-03-05
[SIZE="3"][FONT="Georgia"][COLOR="DarkGreen"]Excuse one last try bumping up this message - but I am still getting the cannot open modem message even though I seem to have successfully loaded drivers - can it be  wrong version of the drivers? (I think the latest is there and the modem is quite old so that should do the trick) - or is there something else that has to be done.

I have sent off a log file to winmodems website too but any advice would be useful.[/COLOR][/FONT][/SIZE]

---

### Post by Bushfire on 2007-03-05
Posting the log from gnome-ppp would be helpful methinks, though I'm trying to get dial up working myself.

--Bernard.

---

