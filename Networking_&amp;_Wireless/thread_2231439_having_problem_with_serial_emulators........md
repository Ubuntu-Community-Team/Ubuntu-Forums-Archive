---
title: "having problem with serial emulators......."
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by syedmohdabbasmehdi on 2014-06-25
hello everybody!

i am using a prolific PL2303 USB to TTL converter, and i am trying to connect my avr microcontroller's UART to my computer using it over /dev/ttyUSB0 1200-8-N-1. but the serial emulators are showing strange behaviour, they are not displaying the output correctly, garbages are being displayed. i also tried connecting an arduino uno over 9600-8-N-1, there again garbage values are being displayed. the important thing to note is that, even though the strings that should be displayed are not too short, the garbage values displayed are quite short( 3-4 characters), the garbage contains the first bit of the string (that should have been displayed) somewhere in between, and all the other bits are some strange symbols(no characters or digits)(something like a hexagon with a question mark in its center). i am certain the problem is in my computer(ubuntu 14.04) because when i connect different development boards/kits/microcontrollers together, they work perfectly. also to strengthen my point, the same boards and microcontrollers were working perfectly with my ubuntu 14.04 (both with 'serial port terminal' and 'cutecom') a few days back. the outputs displayed were perfectly as they should be. but they are not working now.

i guess this is due to some updates i installed using 'apt-get upgrade'.

can anyone please help me with this.

i am in an urgent need since i have to complete my project.


thank you.

---

