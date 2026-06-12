---
title: "Wireless on Start"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by notwen on 2007-04-03
Hello, I have  fresh install of Feisty Beta PPC on a 700mhz G3 iBook.  I'm wanting my wireless to connect upon startup.  I have to click on my network icon and manually connect every time.  I've noticed that I'm prompted for my key every time, even though it is showing up stored in my keyring.  If this has already been covered I apologize.  Any info/advice or links to a thread w/ this asituation would greatly be appreciated. Thanks. =]

---

### Post by lbyrd33 on 2007-04-03
Im not at my computer right now but I am pretty sure that if you open up network manager and then double click on your wireless network and one of the options there should be to activate on startup.

---

### Post by notwen on 2007-04-03
Under Network Settings I have wireless as my default connection, have my essid specified w/ key.  I'm looking under the Connections, General, DNS, & Host tabs and not seeing anything.  =\

---

### Post by flossgeek on 2007-04-03
I find in Feisty, you can make it automatically connect to your default connection by going to the sessions tool and saving the current session, once you are connected to your preferred network. Make sure you have no apps runing though otherwise they will start up when you start your next session. 

As for gnome keyring manager always prompting, you could try this:- [http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

I myself will be looking for away around this, password prompt.

---

### Post by notwen on 2007-04-03
Wooo, thanks flossgeek I'll make the changes here at work, but won't be able to verify all is working until I go home.  I'll be sure to post when I get home, hopefully right after booting and w/o having a keyring prompt. Thanks. =]

---

### Post by flossgeek on 2007-04-03
Actually I'm not sure it did appear to work for me but I think this just depends on my neigbours routers state. So I'm taking me words back, the save the session does not work for enabling your default wireless network. 

Back to step one I'm afraid...

---

### Post by notwen on 2007-04-06
Anyone else having similar issues?   I am still unable to figure out why my wireless won't connect upon startup, and I am still getting prompted by the keyring when I have to manually connect to my wireless router.  Any info would be appreciated, thanks. =]

---

### Post by flossgeek on 2007-04-07
With regards to using libpam-keyring library you need to ensure your GNOME Keyring manager uses the same password as your ROOT password. If it isn't it wont work, change your GNOME Key ring password by opening the application in the "System>Admin" menu and delete your keyrings.

Next time you logged in you will be prompted for SSID again, so have that ready, libpam-keyring should then automatically use your root password for gnome-keyring manager, hence not prompting for a password each time.

---

