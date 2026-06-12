---
title: "UMTS o2 mobile stick, i get internet signal but cant access through the browser."
date: 2010-03-28
forum: New to Ubuntu
---

### Post by chaka72 on 2010-03-28
Hello,

I have a internet signal but cant access internet in the browser.

I am looking for help in using a usb umts  o2 mobile stick 3G huwaei 160 for accessing the internet while using  ubuntu. I have spent hours on the internet the past 3 months trying to  find solutions but no help. I have read through all the documentation, i  have read all through the wiki about connecting to umts and that dont  help me either. Last week i wanted to write a thread in the forum but  as i read through the previous threads it was obvious that i wont get  any help there either for example in one thread someone was asking for  the same solution that i am looking for and all he got as an answer was  that he should check other threads because they dont feel like  discussing the same issue over and over again but after re-checking the  threads there was no help.

My problem is that i have a internet  signal but i cant access the internet via the browser and the browser is  not in offline mode. I have checked the vpn option but nothing helps. I  am also using the live-cd version because my hard drive is broke. I am using ubuntu 9.10 or higher.

Also,  the only way for me to utilize the live cd is selecting f6 after  selecting a language and placing an x by acp off, its the first option  under f6.

Please give me any help, thanks.

---

### Post by NickJones on 2010-03-28
Firstly, try going into Terminal and typing ```
ping www.google.com
``` if sucessful it should list a bunch of IPs and times. If not, then you don't have Internet. 

If that is the case, make sure you Sim is in your Modem, perhaps try it on another computer, if it does work there then we know it's a problem with Ubuntu. Did you configure it to be with your o2 network or did you just plug it in?

---

### Post by PocketDog on 2010-03-28
I've the same problem. I just reboot, and if the blue connected light on the dongle doesn't stay lit (on the Gnome login screen), I reboot again until it does. Sometimes, even with a steady blue light, I can't ping. So I reboot again...

Huge pain in the bottom, but it works. Eventually.

---

### Post by chaka72 on 2010-03-28
> **NickJones said:**
> Firstly, try going into Terminal and typing ```
ping www.google.com
``` if sucessful it should list a bunch of IPs and times. If not, then you don't have Internet. 

If that is the case, make sure you Sim is in your Modem, perhaps try it on another computer, if it does work there then we know it's a problem with Ubuntu. Did you configure it to be with your o2 network or did you just plug it in?


Hi, thanks for your help.

I just plugged the stick in, it immediatly recongnized the stick, i selected the country i am in and out of a list i chose o2 pay-by-time and hit ok. Afterwords after i enter the pin it (ubuntu) shows me that i am online with signal strength and everything.

I am firing up the live ubuntu cd now and i will try the ping yout told me about and let youi know.

Ok with the ping i get an error message host not found but i swear i have an internet connection, even the stick is lit up blue, theres a connection but the connection isnt able to access the internet somehow.

---

