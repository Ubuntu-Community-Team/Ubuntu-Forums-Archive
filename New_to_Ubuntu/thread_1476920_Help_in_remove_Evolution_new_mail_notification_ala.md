---
title: "Help in remove Evolution new mail notification alarm from the notification area"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2010-05-08
I just want to know how to remove the Evolution new mail notification alarm from the notification area with out removing the sound icon.

I tried to do it earlier and ended up removing the whole thing and re-installing the system just to get the sound icon back.

I don't need that icon there 'cos I don't use evolution.

---

### Post by germanix on 2010-05-08
I am not sure if I understood your question correctly, but if you mean tht you would like to remove the envelope icon without removing anything else then this is what you have to do:
Open up the terminal and type the following:
sudo aptitude purge indicator-messages   
then press enter
you will be asked for your password.
Enter your password, it will then ask if it should continue, answer with y for yes.
This will remove the envelope icon. You will not see the immediate removel but it will not be there anymore after a newstart.

---

### Post by sadaruwan12 on 2010-05-09
> **germanix said:**
> I am not sure if I understood your question correctly, but if you mean tht you would like to remove the envelope icon without removing anything else then this is what you have to do:
Open up the terminal and type the following:
sudo aptitude purge indicator-messages   
then press enter
you will be asked for your password.
Enter your password, it will then ask if it should continue, answer with y for yes.
This will remove the envelope icon. You will not see the immediate removel but it will not be there anymore after a newstart.

Thank you it worked.

---

