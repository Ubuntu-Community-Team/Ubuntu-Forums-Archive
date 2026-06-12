---
title: "Bluetooth not working"
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by helm10101 on 2016-02-03
I tried to send pictures from my smartphone to the laptop running Ubuntu 15.10.
they both paired, but upon sending file, I got a message on the desktop that Ubuntu 15.10 had an internal error, and that the files were not sent.

Now when I press "browse files" nothing happens.

What is the problem?

Thanks

---

### Post by davehenson on 2016-02-03
so this got me wondering so I gave it a try w/ my samsung android. I was able to send a file from Ub15.10 to my phone with no problem.  However when I tried to send a picture from my phone to my notebook, I received the error on my phone "unable to transfer file". 

One thing I noticed is that my phone says it is only connected to the notebook as "media audio".  but I can still send a pdf FROM the notebook to the phone with no problem.

I did find that you need to go into "Personal File sharing" application and enable "receive files in Downloads over bluetooth". But even after doing that, I still get failed transfer to my computer.

---

### Post by davehenson on 2016-02-03
Success!!!  

First of all you have to enable the receive in Personal File Sharing as mentioned above.  after doing that, I rebooted both my phone and my computer and it still did not work. 
[https://askubuntu.com/questions/131570/how-do-you-make-ubuntu-accept-files-sent-over-bluetooth](https://askubuntu.com/questions/131570/how-do-you-make-ubuntu-accept-files-sent-over-bluetooth)

THEN..... I installed Blueman from the software center. Still did not work. I then logged out, logged back in and it worked!  I have to admit the Blueman app is much nicer than the default in Unity. 
[https://askubuntu.com/questions/211006/connection-unsuccessful-transfering-a-file-via-bluetooth-from-android-phone](https://askubuntu.com/questions/211006/connection-unsuccessful-transfering-a-file-via-bluetooth-from-android-phone)

---

### Post by helm10101 on 2016-02-05
Thank you, davehenson, it worked !

---

