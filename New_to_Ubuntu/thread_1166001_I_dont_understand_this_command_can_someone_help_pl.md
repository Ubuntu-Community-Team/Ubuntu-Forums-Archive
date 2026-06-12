---
title: "I dont understand this command can someone help please?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by listerdl on 2009-05-21
Hi, thanks for reading this.

My original problem was that my flash was very slow with ubuntu, (I am running intrepid).

I was advised to install this code:

[HTML]sudo apt-get install ubuntu-restricted-extras[/HTML]

This then installed some Java and it came to a terms and conditions page that seemed to want me to agree to the terms but I couldnt work out how to agree.

When I closed the terminal, the package manager icon became a red stop sign and the message was as follows:

[HTML]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/HTML]

Does anyone know how to fix this?

Thanks!

---

### Post by DLG102282 on 2009-05-21
You scroll all the way down and select agree. If you only want flash installed just enter ```
sudo apt-get install flashplugin-nonfree
```in a terminal window.

---

### Post by steve-shinn on 2009-05-21
Run the command in the error message ie 'dpkg --configure -a' (without quotation marks)

---

### Post by kpkeerthi on 2009-05-21
You need to run it like this at the command prompt
```
sudo dpkg --configure -a
```

When the Sun licence agreement pops up, scroll down to the bottom and press [TAB] key and then [ENTER] to accept the license.

---

### Post by clive littlewood on 2009-05-21
Hi

When you get to the "accept" page for java just tab to "yes" and enter.

The message you got was because the parts of the package were not installed.

As said just enter sudo dpkg --configure -a in a terminal ( thats Apps > Accessories > terminal ) and all will be well.

Hope this helps

Clive

Edit:        Beat me to it kpkeerthi !!!!!!

---

### Post by sisco311 on 2009-05-21
If you don't like the Dialog interface, you can change it to the gnome frontend:

```
sudo dpkg-reconfigure -f gnome debconf
```

EDIT: i'm very slow today. :)

---

### Post by listerdl on 2009-05-22
Thanks that worked

---

### Post by msuplee on 2009-05-23
Thanks! Worked for me too. Does anyone know what caused that "manual install" message, though? I was running an update and had to shut down during it. I am guessing that was it?

---

### Post by Sef on 2009-05-23
> Does anyone know what caused that "manual install" message, though? I was running an update and had to shut down during it. I am guessing that was it?

Yes, you are correct.

---

