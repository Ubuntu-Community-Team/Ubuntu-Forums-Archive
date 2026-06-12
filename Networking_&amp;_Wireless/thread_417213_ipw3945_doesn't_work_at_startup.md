---
title: "ipw3945 doesn't work at startup"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by smchugh on 2007-04-21
I am somewhat new to linux, but I understand the basics.  I have just upgraded from 6.10 to 7.04.  In Edgy everything with wireless worked fine from the second I first logged in to my new system.  With Feisty however, the wireless did not work at first.  After restarting the service, and my laptop, several times it finally worked.  The main issue is that it doesn't automatically work at startup.  I noticed that the startup sequence hangs at a point, and after starting up in the linux equivalent of safe-mode I found that the hang is when it's trying to setup network configuration.  After a while it says "OK" but when I login the wireless doesn't work.  IF I restart the process however with the gui network tool then it will start working.  I use a WEP hexadecimal password for the network.  The only difference I can think of between the two versions is this restricted drivers manager.  Please let me know how I can make the wireless card set up in the startup sequence.  Thanks

---

### Post by zarmando on 2007-04-23
[**** THIS WORKAROUND ONLY WORKS IF YOUR CARD IS ALREADY DETECTED, IF YOU CAN DETECT NETWORKS, etc. BUT STILL CAN'T CONNECT****


-A- **Make sure the card is ON ** (fn+F2 on my keyboard, Inspiron 6400 laptop)
1- "Right click" on the network manager Icon
2- Enable (check) the "enable Wireless"

-B-
Left click on the Icon, choose your network - It should be detected

-C-
Then
1- Disable (uncheck) the "Enable networking" option
2- re-enable (recheck) "Enable networking".

It should then connect.
If it doesn't work, retry C, retry again. Be patient. Make sure the proper network is selected

Strange workaround. But it's a workaround that works...!!! At least for me.

Z.

---

### Post by smchugh on 2007-04-23
This fix didn't work.  Before or after I've enabled wireless by disabling and enabling wireless in the network option under administration, "enable wireless," or anything to do with wireless, doesn't show up when I right click the network manager icon.  I tried simply disabling and enabling "enable network," but that didn't fix the problem either.  Any other ideas?

---

### Post by zarmando on 2007-04-23
OK. I don't have the time to help right now, but I suggest you try **everything else in the thread**. edit : SORRY... It's another thread. I can't find it right now, but I posted in it. Some other poster, Sabi, goes through a long diagnostic process. Try to find the thread. Ok... Got it : [http://ubuntuforums.org/showthread.php?t=404705]("http://ubuntuforums.org/showthread.php?t=404705")

If your card is not even detected -- which seems to be the case -- nothing will be possible. You need to make sure that the proprietary driver is installed and working properly. In my case, everything was working except that it wouldn't connect to my network. My fix is only to address that particular issue.

Make sure your card is ON. Check you BIOs, use the keyboard switch if you have one (fn+F2 in my case).

---

### Post by smchugh on 2007-04-23
Thanks zarmando!  I looked through the post and found this:

> Ensure that the wireless entry shows roaming enabled.

Then, on the right side of the system menu bar you should see a network icon. Right click on it to ensure wireless is enabled. Then left click and you should see a list of access points to connect with.

To save anyone else some trouble I'll explain what happened.  I was upgrading from Edgy where you need to use system -> administration -> network, so I disabled roaming and put in my WEP information.  This worked fine while logged in, but Feisty seems to expect people will use network manager.  Therefore when I was trying to work around network manager I assume it got confused.

So, HOW TO SETUP WIRELESS IN FEISTY:
1) Enable roaming for the wireless properties in system -> administration -> network
2) Right-click the network manager icon and enable wireless
4) Left-click the network manager icon and select your wireless network
5) enter all your WEP or WPA information
6) create a password for your keyring

Now everytime you log in it'll ask for the keyring password, and then everything should work.  If this pisses you off like me, then do the following:

1) open a terminal
2) Install libpam-keyring by typing:
> sudo apt-get install libpam-keyring
3) Open the the gdm file by typing:
> gksudo gedit /etc/pam.d/gdm
4) Add the following line to the end:
> @include common-pamkeyring
5) Go to system -> administration -> keyring manager and delete the keyring, not just the key, that contains your wep key
6) restart your computer
7) when prompted after login, reenter your WEP or WPA information

Everything should be good to go.  I'm not sure if this is necesary but I also opened system -> administration -> keyring manager and clicked "always allow," but I don't think this is necessary.  Hope this helps!

---

### Post by timking on 2007-04-24
I'm having the same problem with ipw3945 in Kubuntu 7.04.  Can someone tell me the equivalent of system --> administration --> network in KDE?  I don't see an "enable roaming" in system settings --> network settings.

Thanks,
Tim King

---

### Post by Thomaseov on 2007-04-26
smchugh,

steps 5-7 are the missing magic ingredients.  Thanks.  You are the dude.  I was struggling on how to get wireless working for all the user accounts on a computer without having people know the wireless password.  

Cheers mate.

Thomas

---

