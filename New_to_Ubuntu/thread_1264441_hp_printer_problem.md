---
title: "hp printer problem"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2009-09-12
Hi All,
Just bought an HP F4280 printer, followed a thread and downloaded the latest hplip (I think that's what it's called), finished with a perfect test page and now it doesn't work. When I tried to print something a box said it was processing the job, then seconds later a box said it had printed sucessfully, but with no print. The HP icon listed all of the 'sucessful' jobs it had printed with none actually happening. I restarted the printer to no effect. I rebooted the computer and I got a box saying 'no system tray on this system, unable to start, exiting' and the HP symbol disappeared. 
When I try to print now I get nothing. Clicking on the print icon it says it is processing then within seconds it is held. If I try to either release the jopb or cancel it I get 'Cups server error - client error not possible'
I'm not very computerate. Can anyone help in simple language?
Thanks

---

### Post by astrakhan on 2009-09-12
my first thought is to try reinstalling hplip since it worked after you first installed it.

---

### Post by perce on 2009-09-12
Did you check if it worked with the version of HPLIP who comes preinstalled, before installing a newer one?

In the print configuration menu there are some Deskjet F4*** listed, but not F4280. Have you tried chosing a different one, like F4113? often it works even if you don't choose the exact same model.

---

### Post by Dermot Doyle on 2009-09-12
Hi,
perce - I dod try to print first and it didn't work with the installed hplip. When I went to install the new version it said that I had the older version already installed, but that I could use the new one with some bug fixes. Also you're right it doesn't mention the F4280 exactly, but chooses the closest one. It seems to start with the F4200 series and go from there. I assume it knows more than I do about which driver to use, but you could be right. I would have to go back into the list.
astrakhan - In fact I have reinstalled it since the first time I didn't notice the test page option and wanted to try it. 
Am I missing something here? If I sucessfully ran a test page from the hplip install operation, surely that means the printer is working, usb port is working and the printer software is working. I don't know what else there is.

---

### Post by philinux on 2009-09-12
Remove/delete the printer from system>admin>printing then add it back.

---

### Post by Dermot Doyle on 2009-09-12
Thanks for the help. I have marked this thread as solved because I just got the printer working. For what it's worth to anyone else with an HP F4280 once you have the latest hplip installed, go to the printer configuration under system-admin and change the make and model to the F4213 (click 'change' and select the model from the drop down list). Worked for me.

---

