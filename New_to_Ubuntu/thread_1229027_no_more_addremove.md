---
title: "no more add/remove"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Chris Morin on 2009-08-01
Hi, i've been fiddling around with ubuntu (thats the reason i installed it in the first place and i seem to have messed things up. On my main user account (this first one I made when installing ubuntu), the add/remove application option under the applications drop down is no longer there. when i tried to run gnome-app-install from the terminal, it ran but when it finally came to installing software it failed. thinking i knew what i was doing, i added my main user mentioned above to the admin group via the terminal and now i can install apps but add/remove aplications is no longer in the drop down list. note that i am really don't know if adding chris to the admin group had anything to do with being able to install programs (i actually doubt it) because i tried installing the programs a few weeks after. 

To sum things up, i would like to have the add/remove back in my applications drop down and i would like to ensure that my main user had all of the administative permissions that he originally had (in an effort to learn about linux i was playing with groups and stuff and added my main user to groups via the termial (and when playing with that it does this wierd thing where when u add to a group you have to include all the groups the user is already in, and i didnt do that))

Also, on a possibly related note (the user thing), when i open System>Administration>Users and groups, and i click on unlock, it hangs for a while and then says "Could not authenticate \n   an unexpected error has occured"

thanks for the help

---

### Post by Dark Aspect on 2009-08-01
> **Chris Morin said:**
> Hi, i've been fiddling around with ubuntu (thats the reason i installed it in the first place and i seem to have messed things up. On my main user account (this first one I made when installing ubuntu), the add/remove application option under the applications drop down is no longer there. when i tried to run gnome-app-install from the terminal, it ran but when it finally came to installing software it failed. thinking i knew what i was doing, i added my main user mentioned above to the admin group via the terminal and now i can install apps but add/remove aplications is no longer in the drop down list. note that i am really don't know if adding chris to the admin group had anything to do with being able to install programs (i actually doubt it) because i tried installing the programs a few weeks after. 

To sum things up, i would like to have the add/remove back in my applications drop down and i would like to ensure that my main user had all of the administative permissions that he originally had (in an effort to learn about linux i was playing with groups and stuff and added my main user to groups via the termial (and when playing with that it does this wierd thing where when u add to a group you have to include all the groups the user is already in, and i didnt do that))

Also, on a possibly related note (the user thing), when i open System>Administration>Users and groups, and i click on unlock, it hangs for a while and then says "Could not authenticate \n   an unexpected error has occured"

thanks for the help

Sounds like you may want to reinstall, something is messed up with permissions more than likely, have you tried

```
sudo gnome-app-install
```

---

