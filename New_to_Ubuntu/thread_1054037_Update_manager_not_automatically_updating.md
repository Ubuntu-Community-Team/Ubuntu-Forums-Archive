---
title: "Update manager not automatically updating"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by ag65151 on 2009-01-29
In the past, Update Manager would automatically know if there were updates that needed to be installed. But since I upgraded to Intrepid, I have to manually tell it to do so. 

I have looked through the menu's in Software Sources and it is set to automatically go, but it doesn't do it. Any suggestions?

---

### Post by avtolle on 2009-01-29
Is the Update Manager daemon activated on start-up under System>Preferences>Sessions?

---

### Post by zebanon on 2009-01-29
try this 
go to System >Administration> Update Manager
now this will open the update manager.Now click the check button and u will see a small icon of update manager on top right side of your panel
Right click on that icon and select Preferences>update
Select options that suits you best

---

### Post by ag65151 on 2009-01-29
avtolle: Is the "update manger" daemon the same as the "update notifier"? What is the actual daemon name so I can check with ps?

zebanon: That is the same as opening System->Administration->Software Sources. And the settings are the way I want them with daily checks for updates.

Thanks for trying to help.

---

### Post by avtolle on 2009-01-29
IIRC, it is called update-notifier.

---

### Post by ag65151 on 2009-01-29
Yes, update-notifier is running.

---

