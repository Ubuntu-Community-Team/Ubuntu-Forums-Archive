---
title: "How to I clear this entry from Update Manager?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-10-29
Dear All,
An entry of lipopenexr6 has appeared in my update manager several weeks back. However, it failed to download (...forbidden...) and it has remained in that state. It does neither download, nor it gets cleared. 

(Please see the attached image). 


Could you please tell me how do I clear this stubborn entry? Thanks in advance for your response.



(I have edited my post, I solved the issue by downloading the file manually and then installing it.)

---

### Post by northern lights on 2009-10-30
Please run```
sudo aptitude update
```and thereafter```
sudo aptitude safe-upgrade
```Post the output of the second command, please.

---

