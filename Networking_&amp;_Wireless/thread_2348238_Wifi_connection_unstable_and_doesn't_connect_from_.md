---
title: "Wifi connection unstable and doesn't connect from hibernation, Ubuntu 16.04"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by exhile on 2017-01-02
My Internet adapter intermittently connects and it has trouble establishing a connection after resuming from hibernation. 

My Chrome browser states the following:
```
DNS_PROBE_FINISHED_NO_INTERNET    
```

I've attatched the wireless-info.txt to this post as to what the Networking & Wireless sticky said.

---

### Post by wildmanne39 on 2017-01-02
Please use normal fonts.
Thanks

---

### Post by exhile on 2017-01-02
I never changed the default fonts when I posted.

Also, concerning my wireless problem, when I restart the computer, my internet adapter connects.  I have to do this all the time when I don't connect after resuming from hibernation.  So my computer is connecting but not from hibernation.

---

### Post by exhile on 2017-01-03
So my wireless network adapter uses the Realtek RTL8192CU driver.  I searched for some similar network issues with the same driver and found a few, however the problems were prior to 16.04 being released.  Should I wait until 16.04.2 comes out on Jan. 19th to see if the problem will be fixed or is there a better solution?

---

### Post by exhile on 2017-01-03
Moderators, I was able to solve my connectivity issue on my own by reading previous threads with the same problem like is one: [https://ubuntuforums.org/showthread.php?t=2333606&highlight=rtl8192cu](https://ubuntuforums.org/showthread.php?t=2333606&highlight=rtl8192cu) This link helped me as I followed the instructions of how to install a new network adapter driver: [http://askubuntu.com/questions/456759/asus-usb-n13-wireless-adapter-problems-with-ubuntu-14-04](http://askubuntu.com/questions/456759/asus-usb-n13-wireless-adapter-problems-with-ubuntu-14-04)

---

### Post by oldos2er on 2017-01-03
Would you please mark your thread 'Solved' using Thread Tools at the top of the page? Thanks.

---

