---
title: "upgrade problems"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Bigadada_saba on 2009-05-06
i did sudo apt-get update 
 and sudo apt-get upgrade  but the update manager does not show the button to let me upgrade the system. i just tels me that my system is up to date how can i get this system upgraded?

---

### Post by nhasian on 2009-05-06
are you trying to upgrade from one distribution to another?  like ubuntu 8.10 to 9.04 for example?  If so you need to go to System->Administration->Software Sources, click on the Updates tab and make sure the Releaes upgrade is set to 'Normal releases' not 'Long term support releases only'

---

### Post by Bigadada_saba on 2009-05-06
i did that and still nothing

---

### Post by lindsay7 on 2009-05-06
If you are trying to go from 8!0 to 9>04, have you tried alt + f2 and type "update-manager -d"

---

### Post by Bigadada_saba on 2009-05-06
thanks  its working now.

---

### Post by netwarriorwy on 2009-05-06
When i wanted to upgrade to 9.04 from 8.10 I went to:

> 
1. System->Administration->Update Manager
2. Check for updates if so updated the system.
3. Automatically appeared a button to upgrade to 9.04


Btw my release upgrades insides updates are set to normal releases

I hope that helps :-k

---

