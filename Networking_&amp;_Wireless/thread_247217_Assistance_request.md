---
title: "Assistance request"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by glennc on 2006-08-30
Hello,
  I have Ubuntu 6.06 on a primary drive dual booting with W2K on a slave. With W2K I can connect with WPA through my Compusa (Realtek rtl8185) Wireless card to my router. With Ubuntu I can only connect with Open Sytem WEP. I tried NetworkManager - no luck only prompts for WEP encryption. Used ndiswrapper with the correct Windows driver and 'Networking' - no luck it only shows the WEP encryption. I believe I used the above options correctly from info found in these threads.
   Can anyone assist in getting my WPA-PSK running? All suggestions/ideas/WAG's appreciated.
glennc

---

### Post by Beej on 2006-08-31
I don't know the answer, but from experience you'll get a better response if you repost with a more descriptive title.

---

### Post by glennc on 2006-09-05
Hello Beej,
  Thanks for the response! There is somebody out there, just nod if you can... Anyway will take your advise and do a more concise job of it. Take care Sir!
glennc

---

### Post by lupine_nickt on 2006-09-05
Have you tried wpa_supplicant? 

xF,

...Nick

---

### Post by glennc on 2006-09-05
Hello lupine_nickt,
  I have redone my question in another thread. The short answer is no, not enough horsepower. I've been trying various Linux's (Kububtu/OpenLinuxOs/Mepis/Fedora) and currently am lost. Will  work my way back around to that, hopefully with knowledgeable assistance......?

---

### Post by garrye on 2006-09-05
> **glennc said:**
> Hello,
  I have Ubuntu 6.06 on a primary drive dual booting with W2K on a slave. With W2K I can connect with WPA through my Compusa (Realtek rtl8185) Wireless card to my router. With Ubuntu I can only connect with Open Sytem WEP. I tried NetworkManager - no luck only prompts for WEP encryption. Used ndiswrapper with the correct Windows driver and 'Networking' - no luck it only shows the WEP encryption. I believe I used the above options correctly from info found in these threads.
   Can anyone assist in getting my WPA-PSK running? All suggestions/ideas/WAG's appreciated.
glennc

Yep wpa_supplicant is what you need alright.  Hope you like reading and tinkering!!  Had one helluva time with mine but got it working like a charm now.  Still haven't managed to get Network Manager Gnome working with it but have wpa_supplicant working as a daemon that starts automatically whenever I bring up my wireless connection.  Now that I have it working on one I'm gonna mess it up and come back out of the mess with it capable of connecting to one of two available networks.  Maybe wpa_gui is the answer or wifi radar don't know.

---

### Post by glennc on 2006-09-05
Hello garrye,
  I'm glad to know that it's at least narrowed down to wpa_supplicant. Thanks. Can you point me to where I might find simple'ish instructions for it's use? I am a little too over my head as yet. Took me two weeks to get this far](*,)  .
  Since I can connect and my card and driver's appear to be seen by linux, I am quessing I don't need further anguish with ndiswrapper or such. I couldn't get WPA on the W2K until I upgraded the driver's? Help....

---

