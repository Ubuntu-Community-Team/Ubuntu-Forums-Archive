---
title: "Can Recieve but not Send in Evolution"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by camelface on 2011-01-30
Hi guys, I'm trying to set up a Gmail and Hotmail account in my Evolution. 

Both are recieving perfectly well but I cannot send with either of them. I have followed the procedures as written on a post in the linuxowns website, that is I have set up the imap and smtp for gmail and pop and smtp for gmail but it has not worked. 

I have the correct username down, SSL, the right servers, etc. 

When I click send and recieve, it says on the bottom status bar "Sending Complete 100%" but in the middle window, the progress bar stays at zero. 

Edit: Actually it seems I can send with the gmail account, but the messages were sent after a 15 minute delay... weird, anyway to fix this?

---

### Post by HermanAB on 2011-01-30
Weird.  I cannot tell you what the problem is, but the latest Thunderbird is worth trying.  It has a very good autoconfiguration and test wizard.

---

### Post by ebasa on 2011-01-30
for hot mail:
server=smtp.live.com:587
use TLS encryption
Authentication=PLAIN

don't use gmail so no idea

---

### Post by camelface on 2011-01-30
Ok, perfect. Both work now. 

I had seen in an older post something similar to you but with a different number after the :

I tried that number from the old post and it didn't work. Now it works with the number you have put, does live.com change this regularly?

---

### Post by gordie69 on 2011-01-30
Camelface on evolution what interface such as pop did select I'm using pop but gmail and hotmail use its not pop try one of the other options that should work for you

good luck

I've tried thunderbird but never had much luck so I seem to have good luck with evolution

---

