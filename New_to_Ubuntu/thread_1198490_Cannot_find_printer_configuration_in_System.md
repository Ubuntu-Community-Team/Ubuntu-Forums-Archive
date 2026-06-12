---
title: "Cannot find printer configuration in System"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by ythaaa on 2009-06-27
Hi, 

everything was ok a while ago before i installed something. I do not really remember what i installed... i think i upgraded something related to kde library.

After that, many of my application is gone. For instance, my default software manager is gone. i have to reinstall synaptic.

ok that is not the main problem now, but the thing is i can no longer find printer configuration icon under System> Admin>       .....    is there anyway i can fix this or call up the configuration using command line ?

thankssssss..

---

### Post by northern lights on 2009-06-27
> **ythaaa said:**
> ok that is not the main problem now, but the thing is i can no longer find printer configuration icon under System> Admin>       .....    is there anyway i can fix this or call up the configuration using command line ?

```
gksu system-config-printer

```

---

### Post by ythaaa on 2009-06-27
hi i tried the command..... something runs for a while as indicated by my cursor.... but after that nothing shows up... and everything goes back normal........

---

### Post by northern lights on 2009-06-27
There's nothing faulty with the command itsself.

However, note that you should be prompted for a password before the app opens.

Also be advised that I replied to you assuming that your on Jaunty and gnome. If either is not true, please specify distro/release and/or desktop environment.

---

### Post by ythaaa on 2009-06-27
i realized i do not have system-config-printer     

i not sure how i lost that package.... i reinstalled the package... and now i can call up the configuration using the command above..... thanks

---

### Post by northern lights on 2009-06-27
> **ythaaa said:**
> i realized i do not have system-config-printer     

i not sure how i lost that package.... i reinstalled the package... and now i can call up the configuration using the command above.....Fair enough. However, given that the package was not installed earlier, you should also be able to access it via the menu again also.

---

### Post by philinux on 2009-06-27
If you are using kubuntu it might be a good idea to reinstall 
kubuntu-desktop from synaptic.

---

### Post by ythaaa on 2009-06-27
yes... i have been trying to do that........ but i do not specifically how should i do that...... now that i know.... i realized i lost a lot of package during my 'adventure' into ubuntu....

thanks for all the help......

---

