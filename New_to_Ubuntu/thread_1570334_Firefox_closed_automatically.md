---
title: "Firefox closed automatically"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by its_bigB on 2010-09-08
Hi all,

Since last evening I've a wired issue. Once I open the FireFox after certain time it's automatically closed. Then I re-open it and the same happened. Still it's the same. Then I tried to uninstall and install it's again. But it's not allowed me to uninstall it too.

What should I do? Is anyone comes with such as issue?

Thanks
its_biB

---

### Post by Achilles124 on 2010-09-08
run firefox from terminal. If firefox closes again, the read the error message in your terminal. 

If you don't know what it means, then paste your message here in this thread.

---

### Post by mapes12 on 2010-09-08
Launch FF in safe mode ```
firefox --safe-mode
``` reset to default settings from the pop up window. Close FF. Re launch it normally. Fixed?

---

### Post by lovinglinux on 2010-09-08
Keep in mind that when you close the last tab in Firefox, it closes the entire browser by default. If that is the case, then type **about[noparse]:[/noparse]config** in the address bar, then type **browser.tabs.closeWindowWithLastTab** in the filter field. then double-click the result to make it **false**.

That should prevent Firefox from closing when you close the last tab.

If that isn't the problem, then please specify if the browser closes on a specific page or content type.

You can troubleshoot the problem using safe mode or a clean profile, as already suggested. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Report back with the results.

---

### Post by its_bigB on 2010-09-10
> **mapes12 said:**
> Launch FF in safe mode ```
firefox --safe-mode
``` reset to default settings from the pop up window. Close FF. Re launch it normally. Fixed?

I tried this but it didn't work too.

---

### Post by its_bigB on 2010-09-10
> **lovinglinux said:**
> Keep in mind that when you close the last tab in Firefox, it closes the entire browser by default. If that is the case, then type **about[noparse]:[/noparse]config** in the address bar, then type **browser.tabs.closeWindowWithLastTab** in the filter field. then double-click the result to make it **false**.

That should prevent Firefox from closing when you close the last tab.

If that isn't the problem, then please specify if the browser closes on a specific page or content type.

You can troubleshoot the problem using safe mode or a clean profile, as already suggested. See Firefox [[COLOR=Sienna]**General Troubleshooting Steps**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html") tutorial.

Report back with the results.

Actually what I've done was, reinstall the Firefox. So far so good. 

I'm new to Ubuntu and I wonder where I can find the system log, like in Windows. I searched but couldn't find anything related to that. Do I need to install any plugin or something like that?

---

### Post by lovinglinux on 2010-09-10
> **its_bigB said:**
> Actually what I've done was, reinstall the Firefox. So far so good. 

I'm new to Ubuntu and I wonder where I can find the system log, like in Windows. I searched but couldn't find anything related to that. Do I need to install any plugin or something like that?

Got to "System >> Administration >> Log Viewer".

---

### Post by 73ckn797 on 2010-09-10
I have had Firefox act just like you describe and found it was always after an update. Upon reboot everything was fine.

---

### Post by its_bigB on 2010-09-15
> **lovinglinux said:**
> Got to "System >> Administration >> Log Viewer".

I've found it. But seems to me I've to spend some times to get a better idea about the logs. Thanks anyway.

---

### Post by its_bigB on 2010-09-15
Hi all, actually after couple of days same thing happen to me again. It's automatically close down. I'm really wired about this.

---

