---
title: "Does deleting thunderbird delete lightning?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by nh5y on 2009-10-24
I've been having problems with thunderbird, so I spontaneously decided to uninstall it with the intent of reinstalling it.  but i forgot how much i rely on my calendar, and i didn't back it up or anything before uninstalling thunderbird.

is there a chance that my calendar (via lightning) is still on my computer somewhere?

if so, will someone give me step-by-step instructions on how to retrieve it?

thanks in advance,

natasha

---

### Post by MelDJ on 2009-10-24
maybe you could reinstall lightning from the mozilla site and hopefully your configurations are still saved in your computer [http://www.mozilla.org/projects/calendar/](http://www.mozilla.org/projects/calendar/)

---

### Post by mike555 on 2009-10-24
It kinda depends if you did a complete uninstall or just a reg. uninstall ........... best thing is to try it ...... if your preferences are still in your /home folder it should be ok .......... another option if that doesn't work is to get a separate calendar program , like " Sunbird " ...  [http://www.mozilla.org/projects/calendar/sunbird/](http://www.mozilla.org/projects/calendar/sunbird/)

---

### Post by nh5y on 2009-10-24
IT WORKED!

thanks!

now i just have to figure out why my thunderbird insists on using the same email address to send, even though i have two separate accounts configured.  i've tried everything that i've read online and nothing works!

---

### Post by nh5y on 2009-10-24
thanks for everyone's quick replies :)

---

### Post by rampageoberon on 2009-10-24
Your thunderbird profile will be stored in your home folder - ~/.mozilla-thunderbird.

If it did not remove the profile when uninstalling thunderbird then the settings/data will still be available.

The below codewill tell you how many profiles are stored there, and the file ~/.mozilla-thunderbird/profiles.ini will tell you which default profile is being used.

```
ls ~/.mozilla-thunderbird
```

If there is only one profile in that folder and that is the default one then try open thunderbird to see if your calendar is still available. If there are 2 please post back - the way I usually use is to load that profile and copy data that I need. Not sure how to extract data in other ways.

---

### Post by rampageoberon on 2009-10-24
> **nh5y said:**
> IT WORKED!

thanks!

now i just have to figure out why my thunderbird insists on using the same email address to send, even though i have two separate accounts configured.  i've tried everything that i've read online and nothing works!

Well under account settings, you need to specify which SMTP server to use on each account for sending - which will require you to have created 2 SMTP entries under the SMTP section in the account settings.

Hope that helps.

---

### Post by nh5y on 2009-10-24
yeah, i've got the two smtp servers set up, i even got the "correct identity" add-on... but nothing seems to work for some reason!  thanks for the help, though.  if you have any other ideas, i'm most definitely open to suggestions!

---

