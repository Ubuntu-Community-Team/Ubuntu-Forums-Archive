---
title: "college wifi not connecting"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by paridoth on 2007-02-15
i have ubuntu and windows xp dual booting on my acer aspire 3002lci
i am using the broadcom airforce built in wireless G for both of the operating systems for wifi. in ubuntu i use ndiswrapper and gtk wifi, and in windows i use the broadcom drivers and broadcom utility.

at my college there is a college wide wireless internet. they claim that it is OS independent. the wifi itself is unencrypted, you are suposed to connect to it, then open a web browser and authenticate with your user name and password, then the Internet works. this process works in windows, but in ubuntu DHCP fails and i cannot get to the identification page with firefox (in windows firefox automatically goes there when opened, in ubuntu i don't have an ip so firefox cant go there even if it wanted to.

is there a step i am missing or is this maybe because of ndiswrapper? thanks for any help you can give

---

### Post by Floppyjoe on 2007-02-15
Can you connect to other unencrypted networks?

---

### Post by paridoth on 2007-02-15
it connects to my encrypted wifi at home, i can disable the encryption and try to connect to it if it matters though?

---

### Post by Floppyjoe on 2007-02-15
That's probably not necessary. I was just trying to make sure your wifi worked elsewhere. There seems to be many college students that have trouble connecting to their schools wifi. Maybe if you search the forums here you will find a solution to your problem. I don't know of any offhand but I seem to remember reading a post about this somewhere before.

---

### Post by foureight84 on 2007-02-15
it's not connecting probably because there's a mac filter turned on to only allow students access. what you should do is access your school's tech website and see if they are indeed implementing this. i'm pretty certain this is why you can't connect to it.

---

### Post by paridoth on 2007-02-15
why would it let me connect on windows then? and it seems they allow only students with the login screen, as it requires i enter my last name and student number on my student ID

---

### Post by Floppyjoe on 2007-02-16
Maybe this is one of those DNS issues where you ned to have the right DNS server IP's set up in Ubuntu.

---

### Post by tubasoldier on 2007-02-16
I have to actually connect to the network at my school using wifi-radar or wlassisant. Then I could authenticate myself. It would not connect to their network automatically for some reason.

---

