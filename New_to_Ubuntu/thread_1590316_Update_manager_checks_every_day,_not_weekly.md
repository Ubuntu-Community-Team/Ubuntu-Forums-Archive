---
title: "Update manager checks every day, not weekly"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by GoldenAxe on 2010-10-07
Hi

Simple one this: my Update Manager checks for updates every day, and since there's almost always something to update I have to authorise the update.

Yet I have the setting at "Weekly". I want it to check weekly, not every day.

So why is it checking everyday if I've specified weekly only?

I use two PCs with Ubuntu installed, so I'm having to authorise updates about 14 times a week. Too much!

How can I get it to only check for updates weekly? Why it not listening to the Update Manager Setting?

Any help gratefully received!

---

### Post by jtarin on 2010-10-07
I know this does not answer your question....I had the same problems ..settings not being respected, so I turned off notify and do mine manually about once a week. If there is software on the updates list you do not use and other applications are not affected by them I just uninstall them to avoid update notices about unused software.

---

### Post by GoldenAxe on 2010-10-07
Thanks, I might do the same. It's not a big problem, just a little niggle I've come to resent (and *why* are the settings  ignored? Bah humbug!).

---

### Post by jtarin on 2010-10-07
Might adjust to get only certain types of updates from certain sources.....this will eliminate updates so often too.

---

### Post by GoldenAxe on 2010-10-07
Yes, I do seem to have an awful lot of updates. Thanks,

---

### Post by beew on 2010-10-07
You can set the update schedule to whatever you like. On the top panel go to Applications > System Tools > *Configuration Editor. Open it and on the left panel choose apps to open the drop down menu, scroll down to update-notifier and click. On the right panel you will see the item "regular_auto_launch_interval", highlight it and click edit to choose the interval for update notification.

* If you don't find "Configuration Editor", go to System > Preference > Main Menu. From the left panel choose "System Tools" and you will find "Configuration Editor" on the right panel, just check the box and its launcher will appear in the System Tools menu. I don't know why it is not checked by default.

---

