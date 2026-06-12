---
title: "Run as Root"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by soopisgoodfood on 2007-05-14
i finally figured out out to use ndiswrapper and i tried to use it with the .inf file for my driver and it says:

Unable to create directory /etc/ndiswrapper/e100exp.Make sure you are running as root



but when i try to use root it asks for password and i have no clue what the root password is:confused: :confused: 

do i have to run as root?
if so, how do i find the password?

---

### Post by Kobalt on 2007-05-14
You must have set the password during your installation. Try the password you enter with your user name at log in for example ;)

Here is some doc about root and sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by soopisgoodfood on 2007-05-14
> **Kobalt said:**
> You must have set the password during your installation. Try the password you enter with your user name at log in for example ;)

Here is some doc about root and sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

thank you for that link.

now i am using root but it is giving me a different message when i try to use ndiswrapper:

"couldn't copy e100exp.inf at /usr/sbin/ndiswrapper line 135"


:confused: :confused:

---

### Post by DaH-RaT on 2007-09-21
i had troubles with ndiswrapper also.
i thought i was doing things correctly, until i read this post here :
[http://ubuntuforums.org/showthread.php?t=483548](http://ubuntuforums.org/showthread.php?t=483548)

im not sure if this will help you, but i hope it does :)

---

