---
title: "Pin problem with bluetooth"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by bolognese on 2006-11-12
Hello,

I can't get my mobile connected to my computer. No matter what I try to configure the use of pin. The connection is always refused. Who can be of any help.
I am using 6.10 Ubuntu and Kde bluetooth.

Thanks for an help.

B.

---

### Post by kidders on 2006-11-12
Hi there,

What have you tried so far?

On my machine, I usually use a basic PIN wrapper that always just spits out "PIN:1234567" or something. That way, even if my X server isn't running, PIN exchanges always work as expected ... and silently hehe. Depending on exactly what your problem is, something like this might be a good starting point for you.

---

### Post by Peepsalot on 2006-11-12
I just went through this problem the other day, hopefully this helps:
[http://www.ubuntuforums.org/showthread.php?t=297207&highlight=bluetooth](http://www.ubuntuforums.org/showthread.php?t=297207&highlight=bluetooth)

---

### Post by bolognese on 2006-11-13
I hope that you are right. When I am at home I will give it a try. I have read this thread before, but that was before I could make a connection at all. Now I can send a file from my computer to my mobile phone. But not the other way, because of this strange pin issue.
I just want to let you know some other stings I experienced:

hcitool scan....

could not find my bluetooth connection (Dongle) all of a sudden. No matter what I try. The solution was to take it out of the computer and move it to the usb slot next to it :confused:

---

### Post by bolognese on 2006-11-13
Do I have to put passkey-agent --default /usr/bin/bluez-pin in the hcid.conf or must I run it from a command line?
Is the pin helper line no longer needed?

---

### Post by Peepsalot on 2006-11-13
> **bolognese said:**
> Do I have to put passkey-agent --default /usr/bin/bluez-pin in the hcid.conf or must I run it from a command line?
Is the pin helper line no longer needed?
You have to run the "passkey-agent ..." from the command line.

the pin helper line in hcid.conf is worthless.  The version of bluez-utils in the repositories has phased out this config option for some reason.
I found this out myself when I restarted the service then viewed this log
```
sudo /etc/init.d/bluetooth restart
cat /var/log/syslog
```
If you have the pin_helper line in yourhcid.conf at the time, you will see a message that looks like
```

Unknown option 'pin_helper' line 23

```

---

### Post by bolognese on 2006-11-14
When I enter this passkey thing in a terminal window and press enter it won't give me my commandline prompt back. In other words: it hangs.

---

### Post by ac7ss on 2007-02-09
Thanks for all the advice. I finally have my KRZR talking to KDE (Edgy). Problem now is the OBEX (?) sees files instead of directorys. If I save them, I get the directorys with contents. but I cannot send info this way.

---

