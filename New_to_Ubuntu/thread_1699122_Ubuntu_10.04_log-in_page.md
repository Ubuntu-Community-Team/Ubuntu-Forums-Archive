---
title: "Ubuntu 10.04 log-in page"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by fbs061288 on 2011-03-03
I just installed my Ubuntu 10.04 and wanted to hide the user list during the log-in page...what I did was to do this in the command line:

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set /apps/gdm/simple-greeter/disable_user_list True

When I logged out it indeed hid the userlist, BUT! I dont want to click anymore the "log-in" before I can type the username and password. When i reboot, I want to directly see the username so I can type it. I dont want to have to click the log-in before I am asked to type the username...

Is that possible???

---

### Post by fbs061288 on 2011-03-03
I just installed my Ubuntu 10.04 and wanted to hide the user list during the log-in page...what I did was to do this in the command line:

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set /apps/gdm/simple-greeter/disable_user_list True

When I logged out it indeed hid the userlist, BUT! I dont want to click anymore the "log-in" before I can type the username and password. When i reboot, I want to directly see the username so I can type it. I dont want to have to click the log-in before I am asked to type the username...

Is that possible???

---

### Post by grahammechanical on 2011-03-03
First, by hiding the users list do you not prevent other users from logging in? If so, why have other users?

Second, if you are the only user, then go to System>Administration Login Screen and tick Login as ... automatically.

Regards.

---

### Post by fbs061288 on 2011-03-03
This unit is going to be deployed to KFC branches and we want the store manager to manually type his/her username and password. BUT we have sysad/admin users on that server so we dont want the manager to see our names. The goal is for ubuntu to boot and show the username prompt just like in dapper.

---

### Post by fbs061288 on 2011-03-03
**Ubuntu 10.04 log-in page** 			
 			 			 		   		 		 		I just  installed my Ubuntu 10.04 and wanted to hide the user list during the  log-in page...what I did was to do this in the command line:

sudo gconftool-2 --direct --config-source  xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set  /apps/gdm/simple-greeter/disable_user_list True

When I logged out it indeed hid the userlist, BUT! I dont want to click  anymore the "log-in" before I can type the username and password. When i  reboot, I want to directly see the username so I can type it. I dont  want to have to click the log-in before I am asked to type the  username...

Is that possible???

---

### Post by overdrank on 2011-03-03
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

