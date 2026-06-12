---
title: "[SOLVED] WPA/WEP failed to authenticate"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by mcarni on 2008-11-20
Hi Guys,

The first thing I did yesterday after checking in at the hotel was to check the wi-fi connection.
I turned my  computer on, network manager detected the wifi network, it said it needs an encryption key, I input the key and went on trying to authenticate but with no luck.(desperately I tried all options passphrase/key and even caps lock on as someone suggested on a different post)
I followed some of the posts and I tried to configure manually iwconfig. I also installed WICD which forced me to remove network manager but still no luck.
I'm now writing from my work laptop (windows XP)which I regret to say connected to the network in 2 minutes.
I would really hope to get this connection problem solved as soon as I can since  my wife and I are relocating to Germany and the idea was that while I was at work she would have searched the internet for flats....

thank you so much for your help

M

just in case you need it these are the details of the connection from XP

---

### Post by frankleeee on 2008-11-20
If your default keyring is not accepting what your putting in you can delete it from gnome2-keyring in the home folder and set a new one. It is kind of hard to tell where the problem is from your description.

---

### Post by mcarni on 2008-11-20
thanks for your email,

please let me know what info I can give you, I would not know what to send you at the moment but if you let me know I will be able to send it over in few hours as soon as I'm back in the hotel.
As far as i can say, there is something wrong with the wifi key, or somehow the communication of the wifi key between my computer and the router. When I select the network I want to connect to, I get prompted for a password, after clicking ok I used to have network manager saying "waiting for key to be authenticate" but in the end after 1-2 minutes the only thing that happened was that I got prompted again for the wifi key.
I now replaced network manager with WICD, different kind of graphical look, but same results, I select the network, input the wifi key, it tries to connect and then it fails.

thanks

M

---

### Post by frankleeee on 2008-11-20
> **mcarni said:**
> thanks for your email,

please let me know what info I can give you, I would not know what to send you at the moment but if you let me know I will be able to send it over in few hours as soon as I'm back in the hotel.
As far as i can say, there is something wrong with the wifi key, or somehow the communication of the wifi key between my computer and the router. When I select the network I want to connect to, I get prompted for a password, after clicking ok I used to have network manager saying "waiting for key to be authenticate" but in the end after 1-2 minutes the only thing that happened was that I got prompted again for the wifi key.
I now replaced network manager with WICD, different kind of graphical look, but same results, I select the network, input the wifi key, it tries to connect and then it fails.

thanks

M

Both laptops that I own I had to reset the key after upgrading just go to gnome 2 in your home folder and delete the one there and it will prompt you for a new one.

---

### Post by mcarni on 2008-11-20
Hi Frankleeee,

just removed login.keyring from gnome2 but still no luck.

I tried one thing though that worked out pretty well.
I booted from the 8.10 live cd, I was planning to install it during christmas. This time the graphical interface of network manager was slightly different but it IT WORKED.
I do have wifi working now.

Thank you so much for your help
It is great that in the ubuntu community you can find nice people like you, always ready to help

M

---

### Post by frankleeee on 2008-11-20
> **mcarni said:**
> Hi Frankleeee,

just removed login.keyring from gnome2 but still no luck.

I tried one thing though that worked out pretty well.
I booted from the 8.10 live cd, I was planning to install it during christmas. This time the graphical interface of network manager was slightly different but it IT WORKED.
I do have wifi working now.

Thank you so much for your help
It is great that in the ubuntu community you can find nice people like you, always ready to help

M

On one laptop a upgrade via the update manager the network manager disappeared in one day, so I installed wicd, then that failed so I reinstalled the NM and with a change in /etc/network/interfaces to as this link suggests have had no problems with NM.
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by mcarni on 2008-11-21
Thanks,

I bookmarked the link you gave me, I really appreciate your help, glad to tell you that everything is up and running fine.
We can eventually look for a place here :)

thanks

m

---

