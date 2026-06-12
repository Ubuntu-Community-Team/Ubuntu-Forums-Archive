---
title: "WPA2 + WinXP + Ubuntu"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by gejr on 2007-02-26
I have WPA2 Personal encryption with AES on the router turned on. Ubuntu connects nicely through NetworkManager, but I can't get the Windows XP machine to connect. It complains about the length/format of the password I think. It wants it to have a certain number of bits and stuff. I don't really understand this. Must I change my password in some way to accommodate XP? Or is there another way?

---

### Post by wieman01 on 2007-02-26
> **gejr said:**
> I have WPA2 Personal encryption with AES on the router turned on. Ubuntu connects nicely through NetworkManager, but I can't get the Windows XP machine to connect. It complains about the length/format of the password I think. It wants it to have a certain number of bits and stuff. I don't really understand this. Must I change my password in some way to accommodate XP? Or is there another way?
Can you attach a screenshot of your settings in XP (properties)? XP should not be a problem at all provided that you have installed SP2 and that the WPA2-PSK/AES option is there.

---

### Post by gejr on 2007-02-26
I found some settings on WPA-PSK.. So I had to settle with only WPA, not WPA2. It's okay I guess...My options are "Open", "Shared", "WPA" and "WPA-PSK".. I chose WPA-PSK. Not sure what's the cons/pros of the different types. I have SP2, but can't find any mention on WPA2 :/

---

### Post by wieman01 on 2007-02-26
> **gejr said:**
> I found some settings on WPA-PSK.. So I had to settle with only WPA, not WPA2. It's okay I guess...My options are "Open", "Shared", "WPA" and "WPA-PSK".. I chose WPA-PSK. Not sure what's the cons/pros of the different types. I have SP2, but can't find any mention on WPA2 :/
You will need this patch: [http://www.microsoft.com/downloads/details.aspx?familyid=662BB74D-E7C1-48D6-95EE-1459234F4483&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?familyid=662BB74D-E7C1-48D6-95EE-1459234F4483&displaylang=en")

You can download the corresponding patch here: [http://www.autourdupc.com/index.php?sPage=/Logiciel/WINXP/WinXP.htm]("http://www.autourdupc.com/index.php?sPage=/Logiciel/WINXP/WinXP.htm")

Also make sure that you have the latest driver for your wireless adapter. That'll make a difference as well.

---

