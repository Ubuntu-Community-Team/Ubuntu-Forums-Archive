---
title: "Getting WPA to work with a Linksys WPC54G"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by tompagenet on 2006-10-14
I have this week installed Ubuntu 6.0.6 and am trying to get my Linksys WPC54G v1.2 wireless card to work. I use WPA on my home network, but when I tried to install the network manager, as shown here:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

by typing:

sudo apt-get install network-manager-gnome

I get told the package cannot be found.

I tried doing it through the Add/Remove... option on the home menu, but although the package appears there I find that I can't use it - this is the message I get if I try to select it:

[I]network-manager-gnome' is not available in any software channel:

The appliction might not support your architecture[/I]

Can anyone help me with this - I am very new, but not sure where I'm going wrong with what seems like quite a simple command.

---

### Post by Melcar on 2006-10-14
Are you sure you have the necessary repositories enabeled?  You need an active internet connection to download network manager.

---

### Post by tompagenet on 2006-10-15
Thanks for your response, Melcar. I have tried the process with my router connected directly via ethernet cable, but it has not worked. How do I enable the required repositories?

---

### Post by Melcar on 2006-10-17
Go to Software Properties in the Administration menu.  Click on Add New and check all the boxes.  After closing the window all your repositories will be updated.

[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html")

---

