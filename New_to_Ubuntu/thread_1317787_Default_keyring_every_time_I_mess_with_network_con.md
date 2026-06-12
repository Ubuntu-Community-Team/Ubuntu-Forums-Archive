---
title: "Default keyring every time I mess with network connections"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by SocoJoe87 on 2009-11-07
I have had Ubuntu (dual boot with xp) for over a year now. I have only messed around with it slightly, because I still can't get the wireless to pick up. I ran the line sudo (sorry can't remember the rest), to check to see if my wireless was ENABLED, DISABLED, CLAIMED.... It came back as DISABLED, but the troubleshooting guide helped me with squat after that. What do I have to do to get it enabled and working? It works perfectly on the PC side, what I am on now.


Also every time I mess with the "Wireless" in the network tab it keeps popping up "application 'nm-connection-editor' (c/usr/bin/nm-connection-editor) wants access to the default keyring". I have no idea what the password is for this? I have tried everything and nothing works. Any help would be greatly appreciated cuz as you can tell this is obviously frustrating the piss out of me and making me not want to use the Ubuntu side of my machine.

---

### Post by quinnten83 on 2009-11-07
> **SocoJoe87 said:**
> I have had Ubuntu (dual boot with xp) for over a year now. I have only messed around with it slightly, because I still can't get the wireless to pick up. I ran the line sudo (sorry can't remember the rest), to check to see if my wireless was ENABLED, DISABLED, CLAIMED.... It came back as DISABLED, but the troubleshooting guide helped me with squat after that. What do I have to do to get it enabled and working? It works perfectly on the PC side, what I am on now.


Also every time I mess with the "Wireless" in the network tab it keeps popping up "application 'nm-connection-editor' (c/usr/bin/nm-connection-editor) wants access to the default keyring". I have no idea what the password is for this? I have tried everything and nothing works. Any help would be greatly appreciated cuz as you can tell this is obviously frustrating the piss out of me and making me not want to use the Ubuntu side of my machine.

First approach, ask nicely!!
okay.
default keyring is kinda like a password manager for your applications.
You can store your passwords in it and everytime a program needs a password to perform a function they can look in that password manager, rather than constantly asking you to enter it.

Unfortunately (and I also have this problem), whenever you have to connect to a wireless point, the nm-applet, that which controls the wireless connection isn't allowed to access your keyring and so it has to ask you to unlock it. This causes the prompt. The first time you tried to use the wireless it probably asked you to give it a password. If you forgot that one, your best bet is to remove the keyring. Right now I can't remember how that is done. Chances are, you left it blank, so if it asks for a password to unlock, just press enter.

Also bear in mind that some wireless cards receive no support from the company that makes them. You just might have one of those cards in which case you are royally screwed.

---

### Post by SocoJoe87 on 2009-11-07
> **quinnten83 said:**
> First approach, ask nicely!!
okay.
default keyring is kinda like a password manager for your applications.
You can store your passwords in it and everytime a program needs a password to perform a function they can look in that password manager, rather than constantly asking you to enter it.

Unfortunately (and I also have this problem), whenever you have to connect to a wireless point, the nm-applet, that which controls the wireless connection isn't allowed to access your keyring and so it has to ask you to unlock it. This causes the prompt. The first time you tried to use the wireless it probably asked you to give it a password. If you forgot that one, your best bet is to remove the keyring. Right now I can't remember how that is done. Chances are, you left it blank, so if it asks for a password to unlock, just press enter.

Also bear in mind that some wireless cards receive no support from the company that makes them. You just might have one of those cards in which case you are royally screwed.

I did ask nicely? Sorry if you read it wrong and took it the wrong way.

I have tried keeping the keyring blank and that didn't work either, but thanks for that. I will look around and see if there is a way to reset the keyring or delete it.

Would upgrading to 9.10 help? I am sure keeping the most up to date version wouldn't hurt anyway.


Thanks

---

### Post by winotree on 2009-11-07
> Would upgrading to 9.10 help? No.  That's the default for the gnome network manager as **quinnten83 **explained.

EDIT - On reflection I see how this could be misunderstood -- no, the default behavior of **nm** wont change; yes, > keeping the most up to date version wouldn't hurt anyway.
NOTE TO SELF - Always ingest massive amounts of coffee *prior to posting in forums...  *;)

---

### Post by SocoJoe87 on 2009-11-07
ok, so is there anyway to enable my wireless network? Maybe some code I could input into the terminal? Or maybe a way to delete the keyring so I can set a new password? I saw a command when searching:

rm -/.gnome2/keyrings/default.keyring


but it just gives me invalid? could someone point me in the direction of the folder where this lies, so maybe I could delete it and set a new one?


thanks.

---

### Post by sachin10190 on 2009-11-07
in same command replace default.keyring with login.keyring or manually delete login.keyring in /home/.gnome2/keyrings....tht would do

---

### Post by SocoJoe87 on 2009-11-08
> **sachin10190 said:**
> in same command replace default.keyring with login.keyring or manually delete login.keyring in /home/.gnome2/keyrings....tht would do

Still not working, gave me 
"rm: invalid option - - '/'
Try 'rm - help' for more information.

I am running Ubuntu 8.10, just saw that, and my wireless card comes up as:

BCM4318 [AirForce One 54g] 802.11g Wirless LAN Controller
driver=b43-pci-bridged

Also says it's "disabled".

This is a tower desktop, I have a after-market card in there, would the drivers not be loaded? Or do I need to install them and how would I go about doing that?

Thanks again for the help.

---

### Post by Perturbed Penguin on 2009-12-04
Perhaps I wasn't having the exact same problem but for me all it took to fix this was to right-click on the wireless icon, go to 'edit connections', select the troublesome connection, and make sure 'available to all users' is checked at the bottom. You will, I think, have to do this for any saved networks which have a password saved. I am running 9.10 so perhaps this isn't an option in older versions of Ubuntu but I would guess that it is. Hope this works for everyone else!

---

### Post by hobo14 on 2009-12-04
There are other ways to fix the keyring problem (just search here) but the easiest way is System > Preferences > StartupApps and stop it running on startup.

---

