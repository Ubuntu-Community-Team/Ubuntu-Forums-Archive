---
title: "Security features disabled"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by mr best buy on 2011-07-27
I installed  the netbook version 10.04 on an old gateway laptop (8 years old)
When I installed it, a message flashed by so fact I could not read it.  Something about making  changes to a profile. 
I found that Firefox tells me that the security feature  has been disabled.  When fire fox ons into  the start page it uses [http://.](http://.)....  However when I log into Google or my account [https://,](https://,) it gives me  the error message that security has been disabled.  I go to the menu and check the setting and it is checked for all the settings, aka the Google. documentations.I load Chrome it and it works just fine. (I do not like Chrome)  So I uninstall and uninstall fire fox.  No help.  
When I loaded this version of Ubunutu I got a message about doing something to a profile when I got it loaded. It was some message about the desktop. Then I got a message that some drivers are missing and I could get them but they are not free.
Have I given enough information?

---

### Post by mr best buy on 2011-07-27
More information
" Could not initilize the application's security component.  Most likely cause is  problems with files in your application profile directory.  Please check that this directory has no read/write restructions  and your hard drive is not full or near full. Exit the application and fix the problem.......

---

### Post by mr best buy on 2011-07-27
I go to file system  etc  firefox and upen the folder.  I see two sub folders.  I right click on them and under permission they tell me I cannot make changes because I am not the owner

---

### Post by mr best buy on 2011-07-27
Here is the message
Secure Connection Failed

An error occurred during a connection to [www.google.com](www.google.com).

Can't connect securely because the SSL protocol has been disabled.

(Error code: ssl_error_ssl_disabled)
        


    *   The page you are trying to view can not be shown because the authenticity of the received data could not be verified.

    *   Please contact the web site owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.

---

### Post by mikewhatever on 2011-07-27
To check the permissions of your Firefox profile, run the following:
```
ls -l .mozilla/firefox/

ls -l .mozilla/firefox/*.default/
```

Have you tried running Firefox as root earlier?

---

