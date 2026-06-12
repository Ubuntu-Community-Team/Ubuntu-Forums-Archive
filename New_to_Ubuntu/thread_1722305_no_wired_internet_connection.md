---
title: "no wired internet connection"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by seandangerwhite on 2011-04-05
i have had wireless Internet ok at my last house but now i am trying to plug in a wired connection it wont pick it up. can anyone help? 
many thanks

---

### Post by Zanderist on 2011-04-05
Try a different cable.

---

### Post by seandangerwhite on 2011-04-05
the LEDs light up at the plug when its in so its picking something up. should i still try another lead?          cheers

---

### Post by Zanderist on 2011-04-06
> **seandangerwhite said:**
> the LEDs light up at the plug when its in so its picking something up. should i still try another lead?          cheers
If you have a voltmeter, test for continuity across each of the contacts of the cat5 cable. Then try cleaning the contacts to ensure the best possible connection.

Normally if I can't get a wired connection to the Internet it's most likely related to something being wrong with the cable.

Another issue could be that you 'eth0' is not set up properly for the internet, I'm not that skilled in setting up an eth0, so I couldn't really help you there.

---

### Post by josephmills on 2011-04-06
If you have more then one port on your router you can plug one end of your cat5 cable into port 1 and the other into port 2 if they both light up then the cable is usually good. Could you go to your Terminal and post and type in ```
lspci
```and paste it here.

---

