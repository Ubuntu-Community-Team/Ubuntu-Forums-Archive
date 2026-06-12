---
title: "[SOLVED] Atheros AR5009 wireless problem"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by banana jama on 2008-10-27
i have a hp pavilion laptop. it has a atheros ar5009 wireless card built in but its not working with ubuntu. how do i make this work with ubuntu help me please.

---

### Post by XxDarkSinzxX on 2008-10-27
I just installed it on my other computer which is an acer and im having the same problem as him but my card is also Atheros but its a  Atheros 802.11 wireless Lan Card. It says Proprietary drivers are bieng used to make this computer work properly. But its not working. Under devices there it says Atheros Hardware Acess Layer (HAL) too. There both enabled and they have a check with a In Use Status. So can anyone please help,it would be great if i had internet working on it.

---

### Post by riminicat on 2008-10-27
Hey if you can connect to the internet using an Ethernet cable do that.  When you are online google the ar5007 driver files for windows.  Then get build essential, you should be able to get that on the terminal by typing Sudo apt-get install build essential.

One you have that you'll need ndiswrapper and ndisgtk which can both be installed from the terminal.

Once you have the programs above you can use them to install the driver, just type ndishtk into the terminal to start it.

Good Luck!

You have one of the most difficult wireless cards to work with in my experience.

---

### Post by banana jama on 2008-10-28
i downloaded ndiswrapper and ndisgtk but nothing happened. do i just type there names in terminal  and if yes then what. im very new to linux (downloaded ubuntu yesterday) is it possible for you to post the command lines im suppose to enter in terminal.

---

### Post by banana jama on 2008-11-02
I DID IT !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! I GOT WIFI!!!!!!!!!! HAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA!!!!!!!!!!!!!!!! thanks to everyone who help me out. i figure out that the ndiswrapper wasn't working properly and i followed this link to get there[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847") but thanks to everyone who gave me suggestions and code to help me solve this problem. this forum rules!!!! UBUNTU IS THE GREATEST!!!!!!!!!!!! this problem is offically solved!!!

---

