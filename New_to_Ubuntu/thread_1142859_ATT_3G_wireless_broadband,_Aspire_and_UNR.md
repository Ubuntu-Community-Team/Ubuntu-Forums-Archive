---
title: "ATT 3G wireless broadband, Aspire and UNR"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by faronhicks on 2009-04-29
I have recently purchased the Acer Aspire One from Radio Shack.  It has an internal SIM card (exactly like the ones used in ATT phones) to provide access to ATT's wireless 3G network. It also has, Lord help us, Windows XP.  Installing Ubuntu Net Remix 9.04 is a MUST. My only issue is how to configure for my ATT 3G broadband account. Wi-fi works fine. I have not been able to get any successful help from ATT or Aspire. It currently connects with the Acer 3G Connection Manager in Windows. Any help or suggestions would be great. I would love to do a full install of UNR and wipe Windows completely.

Thank you in advance.

---

### Post by LowSky on 2009-04-29
create a live CD or LiveUSB of 9.04 and see if it works out of the box before installing. 9.04 network applets has a tab for mobile networks, so maybe it will be plug and play...

if not let us know and we can run some commands to try to find out what chipset the PC uses

---

### Post by faronhicks on 2009-05-01
I'm currently running UNR 9.04 from a USB Drive. I didn't want to do full install until I was sure about being able to connect. I tried all 3 options for ATT that were available, but was unsuccessful with each.

---

### Post by killerdogg77 on 2009-05-01
when set up AT&T with the network manager you have to clear  the APN box i think . I forget witch one it is exatly but i had to leave one of the settings empty. I using a sierra wireless usb though it might be different.

---

### Post by faronhicks on 2009-05-03
> **killerdogg77 said:**
> when set up AT&T with the network manager you have to clear  the APN box i think . I forget witch one it is exatly but i had to leave one of the settings empty. I using a sierra wireless usb though it might be different.
Well, I got a little closer but no luck.  It may be because of the internal sim.  OK, next idea, how about if I use Wine to run the ATT connection manager app that came with the netbook? What do you guys think?

---

### Post by killerdogg77 on 2009-05-04
Try```
lspci -k
```   and see if you network card is loading the driver for it.
Found this [http://ubuntuforums.org/showthread.php?t=1147782&highlight=at%26amp%3Bt+wireless]("http://ubuntuforums.org/showthread.php?t=1147782&highlight=at%26amp%3Bt+wireless") not sure if its the card as yours thought worth a look.

---

### Post by GreenChiliRelleno on 2009-06-07
Any luck getting the 3g connection in UNR?
I'm in the same boat. I recently got the great deal for the Acer netbook @ Radio Shack, and I'm going to replace the installed OS (winXP) with UNR this week.

In your research, did you enter the connection info for ATT 3g into Ubuntu's Network Manager? e.g.

  APN: wap.cingular
  Username: [email]WAP@CINGULARGRPS.COM[/email]
  Password: CINGULAR1

I had to re-enter this info to change the profile in Acer's Connection Manager (Windows) to allow me to use my B-berry's SIM for data only.

---

### Post by TruckMonkey on 2009-09-12
Hey everybody, has anyone had success in getting the ATT 3G connection to work?  I would love to load UNR but really need this connection to be available for work...

cheers!

---

### Post by williamts99 on 2009-09-12
Yes, I use it daily, but I also use the USB 3g card.

---

