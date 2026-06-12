---
title: "Wifi conection stablished but no access to Internet"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by miguelquiros on 2008-09-20
Hello, it is quite possible that this subject (or similar) has been posted before but I do not hit the correct keywords for performing a search (any indication of a previous thread with the subject will be welcomed).
I have a laptop with Ubuntu Hardy and I have been able to connect to different wifi access points without too many problems.
But these days I have been in a hotel with free wifi access. Network manager spots the signal and apparently connects automatically. I can see (with ifconfig) that I have been assigned a IP address but, if I open Firefox and try to connect to any page, a "connecting to www.whatever.com" message appears and nothing else, blank screen and after a while Firefox gives up. Evolution also fails to connect to the pop server. Trying to connect to my work computer via ssh does not work either.
The curious thing is that I get ping replies from all these computers ([www.whatever.com](www.whatever.com), pop server and ssh server), which seems to indicate that the connection is working but there is some strange sort of filter or firewall or whatever that blocks any connection (except for ping, as far as I have tested). Other people in the hotel with Windows laptops connected immediately and navigated without any problem.
Has anyone experienced this problem before? Any clue about what the problem might be and possible solution? I have already left the hotel, so I cannot perform any test any more but I any indication would be welcomed in case I find the problem again at any other place.
Thanks for any clue.

---

### Post by dhj1974 on 2008-11-03
I've had the same problem.  I think it has to do with authentication from the Hotel's service.  I had my windows laptop along and noticed that if I try to log on using only FireFox browser on my Windows machine, I can't get to the Hotel's prompt to Accept whatever agreement they have and then let me to the internet.  When I use the Internet Explorer browser it triggers something in their system, I get the prompt, agree and then I have internet access.  After that I can shut down IE and use FireFox to go anywhere.  But there's something about triggering that agreement screen.

---

