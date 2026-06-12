---
title: "PPPoE configuration problem"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by Gothia on 2007-03-17
Hello,

I´ve installed Ubuntu 6.10 on my laptop today. But I cannot connect to the internet. When I write "*sudo pppoeconf*" in the terminal i came to some kind of text based program. I choose the option "*Yes*" and the program starts to work. After that I've got this message:

[I]Error Message: Sorry, I scanned 2 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem[/I]

I have ADSL and connect with a modem (no router). Everything works fine in Windows XP Professional. When I write "*dpkg -s pppoeconf*" in the terminal everything seems to be okey (Package: pppoeconf, Status: intall ok installed).

What could be wrong..?


/Gothia

---

### Post by Shaunak on 2007-03-18
Even i have the same problem.

whenever i try "sudo ppoeconf" i get an error Message:

Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem

 i believe it has something to do with compatibility issues. I tries following [this]("http://ubuntuforums.org/showthread.php?t=78337") [except option 2] but i still cant get ne internet to work. Everythings running fine under windows.

Help!

---

### Post by Kobalt on 2007-03-18
There is a similar post in this very section, about a pppoeconf issue : 
[http://www.ubuntuforums.org/showthread.php?t=231234](http://www.ubuntuforums.org/showthread.php?t=231234)
Have you tried the solution proposed by Aleph42 yet ?

---

### Post by Shaunak on 2007-03-19
Tried it, dosnt work.

---

### Post by n0iz3 on 2007-06-26
i have the same problem.. any updates on how to solve this ?

---

