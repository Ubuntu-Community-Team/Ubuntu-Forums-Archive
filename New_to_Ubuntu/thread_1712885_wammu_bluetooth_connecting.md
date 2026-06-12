---
title: "wammu bluetooth connecting"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by mafi127 on 2011-03-23
I have problem connecting my phone to wammu, it search and find my phone, but after it finis then it says no phone found. In system tray there is bluetooth icon and when I search my phone there it will find my phone and I can connect to it. I dont underestand why wammu cant connect to my phone. 

wammu log:

[PHP]
Wammu is now searching for phone:
Discovering Bluetooth devices using PyBluez
Checking 00:1E:3A:37:ED:F0 (Nokia E75) - Guessed as Nokia - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All Bluetooth devices discovered, connection tests still in progress...
Finished 00:1E:3A:37:ED:F0 (Nokia E75) - Guessed as Nokia - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All finished, found 0 phones
No phone has been found!

[/PHP]


Any ideas plz?

---

### Post by mafi127 on 2011-04-03
some1?

---

### Post by rndlusr on 2011-04-04
You have to pair your phone with the computer first. Go to "Configure new device" in the computer's bluetooth menu. When it finds the phone, click on "Continue" and the computer will give you a secret number that you have to enter on the phone when it prompts you. Now the computer and phone know and trust each other. Then the connection is tested, and you will probably have to confirm several times on the phone. When you see the phone in the bluetooth menu (under "Devices"), it is paired and you can begin to set up Wammu.

Wammu manuals and support: [http://wammu.eu/support/](http://wammu.eu/support/)

---

### Post by mafi127 on 2011-04-04
This is all done, I have seted "trusted" connection in phone menu. everything works like it should. I can even send files whit bluetooth from computer to phone. but when I want to connect my phone whit wammu it says 

[PHP]Wammu is now searching for phone:
Discovering Bluetooth devices using PyBluez
Checking 00:1E:3A:37:ED:F0 (Nokia E75) - Guessed as Nokia - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All Bluetooth devices discovered, connection tests still in progress...
Finished 00:1E:3A:37:ED:F0 (Nokia E75) - Guessed as Nokia - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'blueobex']
All finished, found 0 phones
No phone has been found!
[/PHP]

I says it found phone and then it says no phone found :confused:.

can some1 help me to fix this plz :(

---

### Post by mafi127 on 2011-04-04
Ok, I tested other bluetooth tools also, like gAnyRemote and sync non of them cant get connected whit bluetooth. only the gnome default bluetooth manager is connected. gAnyremoute says

 "Can not get port to connect to. Is there any device available?"
But phone is connected whit computer.:confused:

---

### Post by mafi127 on 2012-01-31
Some1? still got the same problem in ubuntu 11.10

---

