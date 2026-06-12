---
title: "WPA issues"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by raichle on 2007-04-26
Hi all,

I have read through the forums/stickys extensively and still cannot connect to WPA networks.  

I have wpa_supplicant, wpa_gui, network-manager-gnome, and network-manager installed. 

Although I have tried a few different methods, the most recent directions that I followed are [here.]("http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html")

here is what my interface file reads:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

Can anyone help me out here?

Thanks!

---

### Post by sdide on 2007-04-26
You definately need to uncomment some of those entries in /etc/network/interfaces

do a 
~# lshw -C network | grep "logical name"
or 
~# cat /etc/iftab

the devices returned, should be uncommented in /etc/network/interfaces

---

### Post by raichle on 2007-04-26
but the directions I linked to specifically say to comment them out or remove them.  I am able to connect to non-wpa networks with these commented out, is this still important?

---

### Post by sdide on 2007-04-26
how do you connect? 
What commands are you using, or what daemon is doing it for you?

---

### Post by raichle on 2007-04-26
All I do is left-click the network icon and select a non-wpa network and I can connect without a problem .   With a WPA network I am prompted to enter a password but even when I enter the correct one, it does not work.

---

### Post by Sensei_V on 2007-04-26
I've been having the very same problem.  I've been trying various settings in both Ubuntu and my wireless router.  Most of the time when I used the NetworkManager applet to select my network, it would prompt me for a password and then crunch on it for a long time before giving up.  It always connected fine when there were no security settings on the router, but I don't like the idea of leaving the network open.

Finally, by a stroke of luck, I attempted to connect in the same way (only this time I had hidden all the windows with the show desktop button, though I don't know what difference that makes) I had a dialog come up that asked me for a new keyring password, like the [instructions]("http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html")  referenced in the first post of this thread mentioned (except I did my best to undo everything I did from that website since it didn't work).

After setting up a new keyring, I was connected!!!:guitar:

I'm posting this message now wirelessly and encrypted.  I haven't looked into how keyrings work yet, but I recommend it for everyone struggling with WPA.  We'll see if it sticks.  If not, I'll have to make some more offerings to the computer gods...

---

### Post by Sensei_V on 2007-04-26
Update:
Here is what I did to get the keyring thing to work. I wanted to document everything  I know.  It's pretty long, and those of you with plenty of experience will laugh, but this is the level of explanation that I wish I had five days ago.

Use System > Administration > Keyring Manager ( or type "gnome-keyring-manager" into a terminal) to create a new keyring called "default".  Closing the manager and reopening it should cause the keyring title to show up bold in the Keyrings list (which you can bring up from the View menu or by pressing F9).  I think this means that the keyring is actually accepted by the system as the default keyring.

I can't see how to add keys to the keyring from the manager, but now NetworkManager is more likely to ask for access to your default keyring so that it can save the wireless passphrase there.  I just kept attempting to connect, making sure to have no windows visible since the password prompts tend to show up behind other windows and are easy to miss.  Unfortunately, there is no option in the network password prompt to add the password to the keyring, but sometimes NetworkManager asks for permission to access the default keyring.  Once this happens you are home free and the NetworkManager applet icon should change to show wireless signal strength and your connection should work.

My wireless connection stayed active when I logged out and logged back in, even when I logged in as a different user.  This was not true, however, when I logged in as a different user after a reboot, so I had to go through the same procedure for each user.  After reboot, I am usually asked for my keyring password when I try to connect to the network, which sometimes happens by default, but not always.  I haven't tried it yet, but there is a thread explaining how to [automatically unlock the keyring]("http://ubuntuforums.org/showthread.php?t=320308") before nm-applet starts on login.  I'll report back after I try that.

Just as some background, I'd like to share what I had to do to get to the point that I could even see wireless networks and connect to unencrypted routers, just in case someone else needs help in that area.

First I installed the GUI for ndiswrapper from apt-get called ndisgtk.  This places the item "Windows Wireless Drivers" in the System > Administration menu.  Use this to install the Windoze driver for your wireless card.  If you have trouble with this, there are countless other threads with help about ndiswrapper, including whether your card is compatible with ndiswrapper, as well as options for installing open source drivers if they are available.

I also had to enable wireless roaming mode using the System > Administration > Network program.  This changed the nm-applet into a menu that can be used to switch between wireless networks.  When I tried only using the Network program to define what network ESSID to use, I didn't have options for WPA, just for WEP, which I was never able to get working, even when I had my router running in WEP mode.  The nm-applet, however, is able to recognize what type of encryption is used and ask you for the appropriate password type, although it does give you some choices.

Well, that brings me back to where I started at the beginning of this post.  I hope it will save you some time, especially since I've spent several days working on it.  It's not perfect, as I got disconnected while I was writing it and had to restart the computer just to get the connection back, but it's better than I've had for the last month, which is no wireless access.

Good luck!  I hope you begin enjoying wireless freedom soon!

---

### Post by sdide on 2007-04-27
I'm sorry, I'm not a NetworkManager expert... maybe someone, can help here.

---

### Post by raichle on 2007-04-27
I will have to go home and try all  this out, but I wanted to say thanks for all the detailed help... Hopefully it works and I will be able to reply from my encrypted network :).

---

### Post by raichle on 2007-04-28
sigh.... still no luck.  I am not prompted to add it to my keychain and it never connects...any other suggestions?

---

### Post by raichle on 2007-04-30
*bump.... anyone?

---

### Post by Sensei_V on 2007-05-01
Sorry, this is how I was able to get it to work.  I had to try many times in a row.  You might try disabling the wireless in between attempts, or even logging out and back in between trying to connect.  I don't have a more concrete answer... I guess this is what happens when newbies help other newbies.

If anyone else has a good explanation of how to get the NetworkManager to access the keyring, please provide one.  The fix I have used is really pretty random and needs an expert's help to clarify.

---

### Post by joeindio on 2007-06-28
I'm also having trouble getting NM to save a WEP key in the keyring. I'm using Feisty and whatever I do, NM never asks me to add the damn key!!!

Anyway, I once had it working, it did ask me for the password and then wouldn't connect. I found out that the key wasn't being saved correctly in the keyring, e.g. if the key is "blue", it would show up as "qewr2314213rwe" or something like that.

Try to go into the keyring manager and edit manually the password for your wireless connection, e.g. setting it back to "blue". It was working for me...

Hope this helps. Now if I could just get that damn nm-applet to add the key to the keyring...

---

### Post by Beacon11 on 2008-04-30
Sensei, that was an absolutely ridiculous post (the long one describing about needing to minimize all windows, etc). I almost laughed when I saw it! Crap... guess what... it worked :P . I feel retarded now. I've used linux for a while now, and I'm at a loss as to why when I simply minimize everything, it works wonderfully. I'm typing this from my WPA-protected internet. Thank you for the write-up.

---

### Post by Sensei_V on 2008-05-01
I'm glad you got it working.  Wow, that was a year ago that I first got that working, and I think this is the last thread I posted to since then.  I actually haven't had to do that anymore since I upgraded to Gutsy 7.10, so I assumed it got fixed, which is why it's surprising that you were having the same problem.

I don't think it's the minimizing that solves the problem, it's resetting the keychain, but since the keychain windows don't steal the focus, it's hard to spot.... I think, it was a long time ago.

---

### Post by Beacon11 on 2008-05-01
Well, honestly I didn't follow your whole tutorial... literally all I did was minimize all the windows, and voila, everything worked. Funky? Definitely. For all I know, rebooting did it... but I've done that a lot. No idea what happened, but as soon as I minimized everything, it worked. No resetting of the keychain involved. What do you think about that?

---

