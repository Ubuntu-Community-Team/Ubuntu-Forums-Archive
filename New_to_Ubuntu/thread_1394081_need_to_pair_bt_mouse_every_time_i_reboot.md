---
title: "need to pair bt mouse every time i reboot"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by blackicebg on 2010-01-30
Hello, 

I am running Ubuntu 9.10 Karmic and have some problems with my bluetooth mouse.

First, bluetooth didn't work out of the box, couldn't pair my mouse, the graphical interface was not working properly. Even that /etc/init.d/bluetooth status reports "bluetooth is running" when i clicked the bt icon it stated "bluetooth is disabled" and there was a big button "turn bluetooth on". Whenever I click it the app hangs and nothing happens... hcitool cc <address> didn't work for me also...

So i installed the bluez-comat to be able to use hidd --search. This way I get my mouse paired and it functions properly until reboot. Then I have to run sudo hidd --search again so it pairs again ...

Is there something I am doing wrong and how can I make the mouse auto-pair upon reboot?

I am using a usb dongle bt adapter

Any suggestions apreciated,
Blackice

---

### Post by cgroza on 2010-01-30
go to system , preferences, startup programs (in some versions) or sessions (in hardy heron) and add the command there... the command will run every time the system starts.good luck

---

