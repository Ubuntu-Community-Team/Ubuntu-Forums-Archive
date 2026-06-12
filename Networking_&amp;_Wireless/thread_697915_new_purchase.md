---
title: "new purchase"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by lady35wigs on 2008-02-15
help me please.
I have just bought a acer 4315 laptop with linux operations and i have broadband wifi internet with bigpond. i have desktop pc connected but i cant get any web pages on lap top. saying firefox cannot display this page. ive looked at your forums but just cant understand and dont know where to start

---

### Post by stevejesus on 2008-02-15
So, are you asying that you can't connect on either the Desktop OR the laptop?

---

### Post by stevejesus on 2008-02-15
I know your laptop has the Atheros wireless chipset, which you should be able to install the driver with the Restricted Driver manager.  If that if unavailable for some reason, you can do this...
```
sudo apt-get install linux-restricted-modules
```

---

### Post by lady35wigs on 2008-02-15
where do i type that

---

### Post by lady35wigs on 2008-02-15
it says : couldnt find package

---

### Post by peterh_oz on 2008-03-02
I bought same device yesterday.  Firstly, can you see the wireless network?  If you can, choose a WPA password of 25 characters.  I initially had a 63 character password but it wouldn't connect.  When I switched to 25 it worked.  Anything over 0 is plenty secure as long as you have a VERY random WPA password.

The drivers etc are already installed - there is nothing to instal.  Make sure you leave it on Roaming Mode.  Hope that helps.

---

