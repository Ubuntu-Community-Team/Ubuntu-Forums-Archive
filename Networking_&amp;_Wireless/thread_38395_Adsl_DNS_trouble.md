---
title: "Adsl DNS trouble"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by getafix on 2005-05-31
Hello 
I"m having a strange trouble. I am using adsl connection with my 312 eci modem-router. The router configured to have a bridge connection so i am using the ppp0e dialer. From some reasons i can't configured my Ubuntu box to work with it as a router but that's not the issue. When i connect to the internet first of all i need to run the
- route add default ppp0 -
even though i have add it to my if-up script. Nevertheless it works only when i run manually every time. Using the roaring penguin as in slackware with an adsl-start command doesn't work either. That's the first one. 
The second one is that after a while the browser stops surfing when i check i can't even send ping to the hostname but i can to an i ip adress. Running the 
command again says that SIOCADDRT: File exists so i need to close the connection and start over again. It takes about 10-15 minutes for it to disconnect. I have tried to change the nameservers for any ISP there is in Israel but it just didn't helped. 
The issue is that i stay connected but wuthout any abillity to surf or connect to any hostname.
I can't figure out what to do. 
Any help will be appreciated

---

### Post by grim42 on 2005-05-31
I can't help with your specific questions, and sorry to change the subject ... but what is the problem that occurs when configuring Ubuntu to use the modem as a router? Normally this is the easiest way to do this?

---

