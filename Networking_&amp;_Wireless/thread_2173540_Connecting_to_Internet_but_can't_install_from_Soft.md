---
title: "Connecting to Internet but can't install from Software Center or Bash"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by mahmoud_moosa2 on 2013-09-10
Hello everybody,

I installed Ubuntu in my work.

During Setup, There is a window which showing "At least 4.4 GB space is needed" and "Connected to Ethernet".

The strange thing is, once i plug the patch cable the check mark becomes [COLOR=#006400]**Green **[/COLOR]checkmark and after a few seconds its showing gray cross.

I ignored it and coninued then it is successfully installed.

Once i logged into Ubuntu, i changed the proxy in firefox and i can connect to websites without any problem.

Now my problem is, although i can access to websites but when i wanted to install updates from bash Ubuntu cannot connect as shown in the screen shot.

When i tried to download Evoluion for the E-mail from Software Center, the same thing it doesn't start downloading as shown in the screen shot.

Note: we already have a windows domain at work.

Thank you for any help.

Mahmoud

[ATTACH=CONFIG]246151[/ATTACH][ATTACH=CONFIG]246152[/ATTACH][ATTACH=CONFIG]246153[/ATTACH]

---

### Post by Kirboosy on 2013-09-10
> **mahmoud_moosa2 said:**
> Hello everybody,
Once i logged into Ubuntu, i changed the proxy in firefox and i can connect to websites without any problem.

That right there is the answer to your problem. You need to set the** system **to use the proxy. Currently only your web browser is configured properly to use the proxy. So the system is trying to directly access the internet.


If you bring up your network settings from the top right corner you should be able to configure the system to use the proxy properly. (I would send screenshots but I'm currenlty not on a ubuntu machine to do so :( )


Hope that helps!
~Caboose

---

### Post by varunendra on 2013-09-10
> **Caboose885 said:**
> (I would send screenshots but I'm currenlty not on a ubuntu machine to do so :( )

Let me help with that.. :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246159&stc=1&d=1378825391[/IMG]

---

### Post by mahmoud_moosa2 on 2013-09-11
> **Caboose885 said:**
> That right there is the answer to your problem. You need to set the** system **to use the proxy. Currently only your web browser is configured properly to use the proxy. So the system is trying to directly access the internet.


If you bring up your network settings from the top right corner you should be able to configure the system to use the proxy properly. (I would send screenshots but I'm currenlty not on a ubuntu machine to do so :( )


Hope that helps!
~Caboose

you are correct :guitar:

Thank you it is solved.

---

### Post by mahmoud_moosa2 on 2013-09-11
> **varunendra said:**
> Let me help with that.. :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246159&stc=1&d=1378825391[/IMG]

I followed your steps and it is worked successfully.

Thank you good man :guitar:

---

