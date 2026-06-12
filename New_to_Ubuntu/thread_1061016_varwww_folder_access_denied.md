---
title: "var\www\ folder access denied"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by sundarrajan on 2009-02-05
i m in a need to configure the web page displayed by Apache 2 web server displaying "It Works"

I try to change the index.html in /var/www/ to modify the content and tried to establish my web page that i have designed with my content to be shared in internet ....

When i tried to do like that ubuntu is prompting me that u do not have enough previleges to do this action .

But i am the administrator of my system help me to get rid of this problem.

Thanks for u in advance !!!!

Help me to catch whats the exact problem is going on ....

I have to configure the webpage that will be displayed by my webserver in default which every one needs.

I am new to ubuntu .......:(:(:(

---

### Post by taurus on 2009-02-05
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Troll_the_Great on 2009-02-05
You are not the administrator in Linux, you are just a user.Root is the administrator.You can temporary receive administrative privileges by typing "sudo" in front of the commands that need such privileges.   
In your case open nautilus as root (hit Alt+F2 and type "gksu nautilus" or "sudo nautilus" in a terminal), navigate to that folder and modify whatever you want.Just be careful though.When you open nautilus as root you can change or delete ANYTHING so you can really mess your system up. 
Cheers!

---

### Post by sundarrajan on 2009-02-05
thanks a lot i ll try

---

### Post by indytim on 2009-02-05
You can also change the folder user and group ownership to your login id.  See man chgrp and man chown for details.

IndyTim

---

### Post by sundarrajan on 2009-02-05
:D:D:D:D

Thank u very much its working!!!!

As i m new to ubuntu i even dont know how to say thanks for the user who have posted

Thank u very much

---

