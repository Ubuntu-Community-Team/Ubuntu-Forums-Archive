---
title: "Dude this..."
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by PiO on 2005-04-22
Distro of linux is making me really angry... Everytime im trying to make my static ip work it fails... now i might be doing something wrong but anyhow.... i edited interfaces with my ip, i entered dns servers from my cable provider to resolve.conf that didint work, i tried changing settings in networking control panel everytime i enter password it says its invalid even though i can still log in under root in terminal under the same passord... so that didnt work, i tried setting up telnet or rather instll it with the get-app ssh .. .. . that didint work... is this distro in Beta version...? Everytime i tried installing other distros i have never had so many problems... i mean dont get me wrong i like the fact that this distro comes on one cd only but i mean common... this is redicules...

Venting sorry...
Peter  ](*,)

---

### Post by heimo on 2005-04-22
If your network is down, those other things (installing with apt-get from repositories) will fail too. You could install those from CD, maybe using Synaptic package manager.

Other people have had problems setting static ip addresses too, but it's not at all impossible. It'd really help to have more information, log files, output of commands that fail, copy of interfaces file, output of lspci and so on. I'd be glad to help you as I tried in the thread you posted earlier, but you didn't come back with any more information.
 
Did those tests in my first reply go though? Were you able to write to interfaces? What did you put in there? Maybe if you'd give some feedback, it'd be easier to help. "Venting" probably helps you, but what good is it to us? Please, let's try to get this problem solved.

---

### Post by adun on 2005-04-22
You read about sudo?
Even if yout set a root pw, apps like synaptic are configured to use sudo...

---

### Post by PiO on 2005-04-22
Hey,
Sorry i didint mean to act like that, i will gather all of the information and repost it... :)

---

