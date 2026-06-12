---
title: "Wireless network card disapeared"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by Gaerrent on 2008-01-25
This morning when I turned my laptop on, the wireless network was gone. 

lshw shows no wireless network card at all, as if it didnt exist.

I have a Atheros ar5bxb63 card, which I got working a couple of weeks ago with a madwifi driver: madwifi-ng-r2756+ar5007.

Can anybody please expain what might have happened.

---

### Post by Hightide on 2008-01-25
Hi Gaerrent

have a look at try this how to, it may help.

[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

:)

---

### Post by Gaerrent on 2008-01-25
thanks, but the problem is that my computer don recognize a card at all. lshw for example gives no indication at alla of a wireless card. And the strangest thing is that it worked perfectly last night and since then I have done nothing strange at all, it just worked last night and today it&#347; gone.

---

### Post by texasjim on 2008-01-27
> **Gaerrent said:**
> thanks, but the problem is that my computer don recognize a card at all. lshw for example gives no indication at alla of a wireless card. And the strangest thing is that it worked perfectly last night and since then I have done nothing strange at all, it just worked last night and today it&#347; gone.

I just resolved a similar problem with  my Atheros adapter. It showed in lspci but nowhere in ifconfig or iwconfig.

Solution: Re-install Madwifi from Gutsy repo.  Still don't know where it went. but it's back now.

  Good luck
   Jim

---

### Post by Gaerrent on 2008-01-27
I have now solved the mystery of the vanishing wlan card!

The reason was the little switch on the front of the computer. For some reasen can this only be switched when the computer is not running so if it is off when the computer starts up, the card is disabled.

Is there any way to dissable this little stupid switch, so that the wlan always is on and cannot be switched off by misstake? (I do realize this is no Ubuntu-qustion strictly speking)

---

