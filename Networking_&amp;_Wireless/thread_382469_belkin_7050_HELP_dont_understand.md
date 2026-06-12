---
title: "belkin 7050 HELP dont understand"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by nielsonp on 2007-03-12
hi
i have just loaded up ubuntu 6.10 to my spare lappy, but can't get the thing going. i tried to follow instructions from this site: [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux#comment-3426](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux#comment-3426).

i have been having troubles however and am still stuck on the wired connection, it doesn't appear in the networking window and i understand that it is supposed to work straight out of the box on ubuntu 6.10.

or, i have just found instructions here would somebody be kind enough to write them out so that i am able to understand what to do because i am a bit confused with those instructions, here is the URL: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73#head-cfea35eda750890a23c58873b4183271cc3a650c](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73#head-cfea35eda750890a23c58873b4183271cc3a650c)

please help ASAP
thanks,
Nielson

---

### Post by siciliancasanova on 2007-03-12
What is your output for this:

```
lspci

lsusb
```

?

---

### Post by nielsonp on 2007-03-12
Wow! thanks for the reply

guess what, it is there but not registering anywhere but on that command (as far as i know) :confused: 

heres what it said:

Bus 001 Device 005: ID 050d: 705c Belkin Components
Bus 001 Device 001: ID 0000 : 0000

hope that helps you fix my problem :s

---

### Post by siciliancasanova on 2007-03-12
Have you downloaded the latest driver for it?  If not try my thread [here]("http://ubuntuforums.org/showthread.php?t=381594").  It's a pci card but it doesn't matter, at least give it a try and see if it works.  Just replace the part where it says to "install linksys driver" to your driver for your card.

---

### Post by nielsonp on 2007-03-12
can i ask now that i have installed WINE where do i find it????:confused:

---

### Post by siciliancasanova on 2007-03-12
Just right click on any .exe that you have and there should be an option to open it in wine

---

### Post by nielsonp on 2007-03-12
ok,
what happened is i couldn't find WINE and I couldn't find the program anywhere. so now what i did is i found on the WINE website an IRC channel listing so i got an IRC client and they helped me with WINE.
so now i have the installer running and i had a message at the end saying something i cant remember so i tired it again, i thought it was having problems because i had the device plugged in accidently (i'm in console i just typed wine /media/cdrom0/files/setup.exe) and now i have a message saying error: -1603 Fatal error during installation.
Consult Windows Installer Help (Msi.chm) MSDN for more information. what does all this mean could u pls help?
thanks
Nielson

---

### Post by nielsonp on 2007-03-12
just an update...

i restarted the computer and repeated the provided steps from the IRC chat i had and it went through the whole installation and at the end the error meesage reads as follows:

(title bar of window) Unhandled Exception
(message) Description: Dll function call crashed: install. EnumerateDevice Setup will now terminate. 

and then it gives me the option to click ok.

---

