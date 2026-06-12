---
title: "Ubuntu 13.10 Wi Fi Keeps asking for authentication"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by Amon_Rivsky on 2014-02-07
I've recently installed Ubuntu 13.10 and everything seems okay except one thing. When I try to connect with my router, it fails to do so and keeps asking password everytime, I keep entering the right one and it just won't work. The only thing I can do about it is to open my wi-fi without password but I wouldn't want to do that. I usually use wpa/wpa2 personal encryption. Please tell me which commands I should type to see info about it. Thanks. Also I googled some solutions but none of them worked for me.

---

### Post by Gaweph on 2014-02-07
If you look here (older question but sounds the same):

[http://askubuntu.com/questions/64903/network-manager-forgets-wireless-password-after-sleeping-or-powering-off](http://askubuntu.com/questions/64903/network-manager-forgets-wireless-password-after-sleeping-or-powering-off)

The provided answer seems to be:

> "Go to your network connections. From there click on wireless tab. Choose your connection and then click the edit button. Make sure your password is entered then click on the wireless security tab. Then check the box in the bottom left corner that says available to all users."

Does this work in 13.10?

---

### Post by varunendra on 2014-02-07
Welcome to the forums Amon_Rivsky !

> **Amon_Rivsky said:**
> I usually use **[COLOR="#FF0000"]wpa/wpa2[/COLOR]** personal encryption.

Try making it pure WPA2-AES(CCMP) only. The WPA/WPA2 mixed mode requires TKIP and can be problematic sometimes. If that doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

