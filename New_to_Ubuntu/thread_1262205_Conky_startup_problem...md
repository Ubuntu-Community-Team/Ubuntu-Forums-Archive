---
title: "Conky startup problem.."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-09
How to start conky during  startup?I have added a command "conky" in startup application list.But its not working...

---

### Post by arochester on 2009-09-09
Look at "HowTo: A Beginners Guide to Setting up Conky" on [http://linux-hardcore.com/index.php?topic=1878.0](http://linux-hardcore.com/index.php?topic=1878.0) 

Scroll down to "STEP 2 - Setting up conky to autostart on boot."

Otherwise you could post on [http://linux-hardcore.com/index.php?board=80.0](http://linux-hardcore.com/index.php?board=80.0)

---

### Post by karthick87 on 2009-09-10
This worked for me thankyou..

#!/bin/bash
sleep 10 && conky;

---

### Post by binbash on 2009-09-10
change 10 with 30. It will be better.

---

