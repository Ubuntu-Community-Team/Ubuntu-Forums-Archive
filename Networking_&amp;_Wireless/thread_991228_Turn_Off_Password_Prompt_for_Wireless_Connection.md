---
title: "Turn Off Password Prompt for Wireless Connection"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by jereece on 2008-11-23
I finally got wireless to work on my Acer Extensa 5620z, but now every time I boot up it wants to prompt me for a password to connect.  I have searched everywhere but don't see a way to remember the password or not prompt me for it.  How can I turn this prompt off and automatically connect to my wireless network?

Thanks,
Jim

---

### Post by spd106 on 2008-11-25
Make sure that you have the network settings saved in the Network Editor part of Network-Manager.

Simply right-click the applet and select Edit Networks... If there isn't a network with your SSID, add one.

---

### Post by aysiu on 2008-11-25
Any chance you have autologin enabled?

---

### Post by jereece on 2008-11-25
Yes I have auto login turned on.  I did not want to have to log in each time I booted.

---

### Post by aysiu on 2008-11-25
Go to /home/*username*/.gnome2/

And rename the *keyrings* directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.

---

### Post by jereece on 2008-11-25
Just for clarification, I am not talking about the system login.  I am talking about once I am fully booted and my laptop is trying to connect to my network.  That's the password I want to change.  When I initially set up my network in Network Manager it prompted me to set up a password (not the password on my router).  I had no options.  It prompts me for this password to allow my laptop to connect to the network.  That's the password I want to disable. 

So do I still need to do as you suggest?

Thanks for the clarification.

Jim

---

### Post by aysiu on 2008-11-25
Yes, that is exactly what I'm talking about as well.

---

### Post by Argeroth on 2008-11-26
> **aysiu said:**
> Go to /home/*username*/.gnome2/

And rename the *keyrings* directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.u

Thank you!!!!!  I had the same issue myself and found this thread in a search.  Problem solved :)

---

### Post by andrew.mckevitt on 2008-11-26
> **aysiu said:**
> Go to /home/*username*/.gnome2/

And rename the *keyrings* directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.


Auto login but then have to sign into keyring, that was so annoying. Thanks for that tip, really helped.

---

### Post by jereece on 2008-12-03
That worked.  Originally I did not see the folder, then I looked to see if it was hidden and it was, so after unhiding folders I was able to rename the folder.  Then after rebooting, I had to go into Network Manager, log onto my router and then it prompted me for the keyring password.  So I finally got this working right.

Thanks for all the help.

Jim

---

### Post by tore68 on 2008-12-19
That fixed my annoying network logon prompt.. Thanx

---

### Post by therrmann on 2008-12-21
> **aysiu said:**
> Go to /home/*username*/.gnome2/

And rename the *keyrings* directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.
Thanks, that worked for me too, on my ASUS eee.  It was so annoying, especially since it would not take my system password for some reason.
Excellent!

---

### Post by tollboy on 2011-06-13
> **aysiu said:**
> Go to /home/*username*/.gnome2/

And rename the *keyrings* directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.


Worked for me.:popcorn:
Thanks alot.

---

