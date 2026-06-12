---
title: "Sounf is not coming after hibernate in Ubuntu 8.04 LTS"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-07-03
Hi All,

    I'm facing an issue in my Ubuntu 8.04 LTS, When I hibernate and start the system again sound is not coming. How can I rectify this issue. I'm very curious to know what is the reason for it. I'm very new to Linux, so I expect a detail explanation. Please anyone help me for this 

Regards,
Vipin.Balakrishnan.
I Love Linux

---

### Post by sadaruwan12 on 2009-07-03
OK, It's me again like to know did you did a full system update before you start using it.

---

### Post by AsusEEEPC on 2009-07-03
Go to the terminal and type "alsamixer" without the quotes. That is a program which allows you to control your volume a bit more then the normal Volume Control.

---

### Post by philinux on 2009-07-03
Intrepid fixed this bugette for me. In Hardy I had to do this from the terminal.

```
sudo alsa force-reload
```

Better than rebooting.

---

### Post by vipin.balakrishnan on 2009-07-03
Hi All,

  I have up-to-date version of Ubuntu -8.04 LTS. Then also problem is there. Is there any fix available for it without typing a command.

Best Regards,
Vipin Balakrishnan
I Love Linux

---

### Post by philinux on 2009-07-03
> **vipin.balakrishnan said:**
> Hi All,

  I have up-to-date version of Ubuntu -8.04 LTS. Then also problem is there. Is there any fix available for it without typing a command.

Best Regards,
Vipin Balakrishnan
I Love Linux

[http://www.google.co.uk/search?q=hardy+hibernate+sound+bug&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=hardy+hibernate+sound+bug&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

