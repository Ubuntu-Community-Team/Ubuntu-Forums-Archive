---
title: "WMP54G, WPA2 and Gutsy"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Electricboots on 2008-01-16
Hello,

I've searched a bit on these forums and on the Web, I couldn't find a solution to my issue.

I have a new computer with a Linksys WMP54G 4.1 wireless LAN card.  The computer is running Ubuntu Gutsy.

With the default drivers, I can scan and see various SSIDs, including my own.

I configured my Linksys router (running HyperWRT Thibor) to use WPA2-Personal w/ AES and to broadcast the SSID.

I installed libpam-gnome-keyring.

I followed instructions on post #2 of [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834).

My connection works and I can browse the Web, however I seem to have a problem with the WPA2 authentication.

When the computer boots, it always prompts me to enter the keyring password for nm-applet, even after I installed libpam-gnome-keyring.  Not only that, after I enter it (and it's the same as my user password), the Network icon switches to two little grey balls with a blue swirly thing.  It says like that for a while, then it prompts me for my WPA2 passphrase.  I enter it, then the lower grey balls becomes green and shortly after I'm connected.

I thought at first that maybe my keyring was wrong, so I decided to "start from scratch".

First, I disabled Networking by clicking on the Networking icon and unchecking "Enable Networking".  Then at a command prompt, I did:
```

rm ~/.gnome2/keyrings/default.keyring
gconftool --recursive-unset /system/networking/wireless/networks

```

I tried the above steps many times.  Each time I carefully type the same passphrase and same password for my keyring, but the problem stays there.  :(  

Basically, when the computer boots, I don't want to have to enter the keyring password and/or the WPA2 passphrase everytime.

Any ideas?


Edit:  Hmm this is weird.  The last two times I rebooted, it asked me for the WPA2 passphrase twice, then asked me for the keyring password, and then it connected.

---

### Post by wieman01 on 2008-01-17
If you plan to use Network Manager, then don't follow the instruction you have posted above (WPA tutorial). The instructions are exclusive, so you either use one or the other, not both. 

So to start from scratch please remove all relevant lines from "/etc/network/interfaces" or - if you are uncertain - post the contents here so that I can do it for you.

---

### Post by Electricboots on 2008-01-17
My /etc/network/interfaces file only has the loopback entry:

```
auto lo
iface lo inet loopback
```

I only followed post #2 of your thread, about the script to restart networking during boot up. I didn't do anything from post #1 of the thread.

I just tried ndiswrapper (with the drivers I downloaded from the Linksys web site) instead of the rt61pci driver, but it gives me the same problem, and on top of that, I lose one signal strength bar. :(

---

### Post by wieman01 on 2008-01-17
You don't need to follow post #2 of my thread if NM does the job for you. 

So the only issue remaining is that you have to enter your password every time you restart the PC?

---

### Post by Electricboots on 2008-01-17
Right now, on boot up, usually it'll prompt me to enter the WPA2 passphrase twice, and then it'll ask for the keyring password.

Since I installed libpam-gnome-keyring and since I set the keyring password to be the same as my login password, I thought that I wouldn't get prompted anything at all.

Even before installing libpam-gnome-keyring, from what I understand, it's only supposed to prompt me for the keyring password and that's it.

This computer is to be eventually used as a HTPC, so that's why I want the wireless network to just work without prompts.

---

### Post by wieman01 on 2008-01-17
> **Electricboots said:**
> This computer is to be eventually used as a HTPC, so that's why I want the wireless network to just work without prompts.
If that is the case, then upgrading to Gutsy will be an option. The version of NM used in Gutsy can do exactly that.

One drawback, however, is that Gutsy's Ralink drivers have deteriorated, so there is a pretty good chance that your wireless adapter won't work out of the box...

---

### Post by Electricboots on 2008-01-17
Yeah, this is a Gutsy machine already.

I tried the "out of the box" drivers first and right now I'm using ndiswrapper.  I have the same problem with both. :(

---

### Post by wieman01 on 2008-01-17
That is strange. Does NM not give you the option to store the password in an 'unprotected' manner so that the system does not ask you for any keyring password, etc.?

---

### Post by Electricboots on 2008-01-17
I've fiddled with nm a little more.  Seems that I can only connect with roaming mode.

If I try to manual configure nm for my wireless connection, it won't connect.  When I have roaming mode ON, if I right click on the network icon, I see two checkboxes: 'Enable Networking' and 'Enable Wireless'.

If I have roaming OFF, I only see the 'Enable Networking' checkbox.

I'm not sure if this is related to my original problem or if this is a new problem altogether.

Edit: to answer your question, when I connect to my router (while using roaming mode), I don't see any option anywhere to save the passphrase.

---

### Post by wieman01 on 2008-01-17
Since I don't use NM anymore, I would have to pass the question to the next person. You could contact Kevdog for instance, he is very knowledgeable and might be able to help you out from here. You could send him the link to this thread by PM.

---

### Post by Electricboots on 2008-01-17
I dunno, I just decided to give up on nm. :)  I've been working on this all day and not getting anywhere.

I just followed your HOWTO and it works good now. :)

---

### Post by wieman01 on 2008-01-17
> **Electricboots said:**
> I dunno, I just decided to give up on nm. :)  I've been working on this all day and not getting anywhere.

I just followed your HOWTO and it works good now. :)
Fair enough. :-)

---

### Post by wieman01 on 2008-01-17
Just to close this thread, I found [this]("http://ubuntuforums.org/showthread.php?t=463639").

---

