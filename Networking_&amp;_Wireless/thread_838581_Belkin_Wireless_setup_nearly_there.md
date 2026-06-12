---
title: "Belkin Wireless setup nearly there"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by FoxIII on 2008-06-23
I've nearly set up my wireless network with my Belkin F5D7000.

I can right click on the network icon in the taskbar and see the wireless network, but when I try and connect to it and enter the password, it does not connect.

For more info., the place which is causing the current headache is;

[http://www.thumoo.com/images/screenshot1.png](http://www.thumoo.com/images/screenshot1.png)

If anyone can shed any light, it would be greatly appreciated!

TIA

---

### Post by jualin on 2008-06-23
can you post the screenshot again since is not loading.
Maybe you can try installing wpasupplicant from synaptic or simply from the terminal > sudo apt-get install wpasupplicant. Also try disabling it the Wireless Security (WEP or WPA) in your router and try connecting to it to see if it works. Another thing that I would do is double check the password that you are writing. And the current type of encryption that you are using to connect. 
For instance I once had a problem connecting to a Wireless Network because I was using WEP 128 Bits and needed to use WEP Hex type of encryption. Hope this helps.

---

### Post by FoxIII on 2008-06-23
Thanks for the reply jualin.

Yes, I got the filename wrong. The correct link is;

[http://www.thumoo.com/images/snapshot1.png](http://www.thumoo.com/images/snapshot1.png)

I am unable to make any changes to the router as I'm sharing it and don't have access to it. The password is correct (tried several times).

I am using 128bit encryption. Again, I cannot change anything on the router itself. Only on my computer.

I shall give the wpasupplicant a try and see if that helps at all. Will let you know...

---

### Post by jualin on 2008-06-23
Try changing the "Encryption" on your computer from WPA to WEP. If the password is an actaul word like "thepasswordforchurch" the the encryption is more likely a WPA but if the password is a number like "2341888" then the encryption can be WEP. Try changing that on your computer to see if you get lucky.

---

