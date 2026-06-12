---
title: "Network Manager Gnome only displays in bottom right tray ??"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by s-bris on 2007-02-06
Hi,

I am having plenty of troubles getting wireless networking to work.  It rather depressing when for the last 5 years it has taken me about 5 minutes to get WPA to work on any windows notebook or server.  I have previously posted all my config files etc...

Anyway, I saw a post that said Network Manager was as easy and useful as the Windows network wireless manager.

I installed it and can only see a little icon down the bottom right in the tray area where the date is located and the power display and shutdown button is located.  (I flipped it to the bottom from the original install).

When I click on it it only has :

1.) Enable Networking (with a tick in front of it)
2.) Conenction information (all greyed out)
3.) About

Am I missing something.... this certainly doesn;t sem equivalent to the wireless network setup that is on windows ???

cheers
steve

---

### Post by etienne.navarro on 2007-02-07
If you **left** click on it, you'll see all the wireless networks available. Select one of them.

If you don't see any wireless connections listed, then your wireless is probably not setup right.

Open a terminal (Applications --> Accessories --> Terminal) and type
```
iwconfig
```You should see a list of all your networking devices and whether or not they support wireless communication. Normally its eth1. If everything says "no wireless extensions" then your wireless card is not setup properly.

To check what card you have, in the terminal type
```
lspci
```and look for anything that identifies your wireless card. Once you got that information, search the forums for help.

---

