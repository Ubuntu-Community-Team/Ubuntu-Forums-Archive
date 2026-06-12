---
title: "some files can not be copied under shared folder"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by mightyocean on 2009-09-27
Hello:

I am having a strange problem here. I have shared a folder on my Ubuntu machine, and have no problem copying the files in the folder to my Vista and win7 machines, except one html file. 

Every time I try to copy the file to Vista machine, an error message pops with "you need permission to perform this action"

why? Thank you in advance for any help.

---

### Post by oboedad55 on 2009-09-27
> **mightyocean said:**
> Hello:

I am having a strange problem here. I have shared a folder on my Ubuntu machine, and have no problem copying the files in the folder to my Vista and win7 machines, except one html file. 

Every time I try to copy the file to Vista machine, an error message pops with "you need permission to perform this action"

why? Thank you in advance for any help.

Which html file is it?

---

### Post by mapes12 on 2009-09-27
If there is a padlock icon on the file you need to change the permission to your user account. The GUI way is to launch nautilus with root permission ```
gksudo nautilus
``` then navigate to the file. Right click it then select the permission tab and make the change.

---

### Post by mightyocean on 2009-09-27
> **mapes12 said:**
> If there is a padlock icon on the file you need to change the permission to your user account. The GUI way is to launch nautilus with root permission ```
gksudo nautilus
``` then navigate to the file. Right click it then select the permission tab and make the change.

it works. Open the file in nautilus and found Group and Others did not have access to the file. 

thank you!!

---

