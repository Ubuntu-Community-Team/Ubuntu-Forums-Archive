---
title: "adding a script to startup"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by ozzyprv on 2010-05-23
I am trying to add a script to the Startup Applications but it is not working.
Script resides at /home/myusername/
Script name: .my_script.sh
I am adding this to the Startup Applications command field: ~/.my_script.sh

So far it does not work. Do I have to specify the whole path (/home/myusername/.my_script.sh)?

Thanks.

---

### Post by inameiname on 2010-05-23
I actually just figured out this myself, so maybe I can help. In my case it was a random wallpaper that changes at startup, and I used this:

To add '.my_script.sh' to the Startup Applications:

Go to System > Preferences > Startup Applications

'Add' it using the following parameters:

Name: Whatever you want
Command: /home/myusername/.my_script.sh
Comment: Whatever you want

..should work just fine. But sounds like you've already done that.

..I've noticed that sometimes you must put in the full command, other times you can use "~/" just fine. Also, if your ".my_script.sh" does not have the ".sh" shown, then don't put it in your command as well, even if it is a shell script. 

I suggest to just try the full command and see if that works first. Then maybe check the end part of the script to see if it matches with that in the command. And of course, I doubt I have to mention manually opening the script just to make sure it works fine.

---

### Post by ozzyprv on 2010-05-31
> **inameiname said:**
> 



I suggest to just try the full command and see if that works first. 

The full path approach worked. Thanks for the suggestion.

---

### Post by inameiname on 2010-05-31
No prob.

---

