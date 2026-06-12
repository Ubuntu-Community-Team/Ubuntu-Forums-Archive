---
title: "t-mobile"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by michaelA1330 on 2010-01-06
hey 
im trying to geta t-mobile mobile broadband adaptop working
and for the love of god its impossible , iv tried connecting it to the wirless in the tray but it wont fisplay at all 
iv evn tried running the windows software through wine but it just says its starting then
closes or gives me a runtime error  

any help would be much appresiated 

p.s im running 9.04

---

### Post by manosx on 2010-01-06
If you have the T-Mobile Web 'n Walk Stick there is a solution.

[http://raymii.org/cms/index.php?cat=tutorial&title=Make_Your_Option_225_Work_with_Ubuntu](http://raymii.org/cms/index.php?cat=tutorial&title=Make_Your_Option_225_Work_with_Ubuntu)

---

### Post by michaelA1330 on 2010-01-06
but i dont have a web and walk stick 
i think if i can get the software running ti should work , any advice

or do linux driver for it exist ?

---

### Post by warfacegod on 2010-01-06
I would call T-Mobile have them help you. After all, they sold you a product and/or service, they are responsible for making sure it works.

---

### Post by michaelA1330 on 2010-01-06
but there is nothing on the packageing about linux only wondows then mac :S

---

### Post by manosx on 2010-01-06
I found this:
[http://community.zdnet.co.uk/blog/0,1000000567,10014701o-2000498448b,00.htm](http://community.zdnet.co.uk/blog/0,1000000567,10014701o-2000498448b,00.htm)
It suggests it should be in Network Connections tray after you plug it in..

If not, maybe right click on Network Connections, go to Mobile Broadband tab and Add it?

---

### Post by michaelA1330 on 2010-01-06
iv tried adding it but it just wont connect , it wont even display my mobile broadband connection

---

### Post by manosx on 2010-01-06
ok, i guess the device is listed when you do
lsusb
? 
what is the device?
did you try searching for that specific device?

---

### Post by garryknight on 2010-01-06
Michael: If you can find out the device number (by doing lsusb in a console) you can see if it's listed here: [http://www.betavine.net/bvportal/resources/datacards/devices](http://www.betavine.net/bvportal/resources/datacards/devices)
If it is, the vodafone-mobile-connect software will work with it, and it's specifically written to work with Linux.

---

