---
title: "[SOLVED] Dell-Ubuntu, wpa problem, Intel Intel(R) PRO/Wireless 3945, inspiron 6400"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by b16 on 2007-09-07
Hello,

I just bought a Dell Inpiron 6400 preinstalled with ubuntu.

wpa security is not managed by default by the network manager:
the help says:
"Ubuntu does not automatically support WPA encryption, if you require this, there is a WPA guide on the Ubuntu documentation wiki." 
Strange thing is that wpa_supplicant was installed... 

I am not familiar with ubuntu and fear to edit config file seeing that 
the network manager erases modifications (for example in /etc/network/interfaces).

How do I get wpa to work?

Is there a user friendly way to do that?

I tried to configure /etc/wpa_supplicant.conf and edit /etc/network/interfaces
but then the main question becoms:

Does the proprietary "restricted driver" ipw 3945 work with wpa_supplicant?
(I couldn't find it in the wpa_supplicant.conf man)

If so what should be the 
wpa-driver 
declared in the /etc/network/interfaces? (ipw doesn't work).
(Or what is driver in  wpa_supplicant -Bw -D<driver> -ieth1 -c/etc/wpa_supplicant.conf ?)

If not what can be done ?

                                  Thanks,

b.

---

### Post by Zorael on 2007-09-07
You could try [wicd](http://wicd.sourceforge.net/). I haven't tried it with WPA myself, though. At least you'll have a user interface to work with.

---

### Post by 5-HT on 2007-09-07
> **b16 said:**
> 
Does the proprietary "restricted driver" ipw 3945 work with wpa_supplicant?
(I couldn't find it in the wpa_supplicant.conf man)
Yup

> **b16 said:**
> If so what should be the 
wpa-driver 
declared in the /etc/network/interfaces? (ipw doesn't work).
(Or what is driver in  wpa_supplicant -Bw -D<driver> -ieth1 -c/etc/wpa_supplicant.conf ?)

wext

> **b16 said:**
>  If not what can be done ?
Manual config is the most straightforward. Wifi-radar is worth a look as well as wicd. Newer versions of networkmanager will support WPA, but networkmanager is really flaky in my experience with the ipw3945.
cheers,

---

### Post by b16 on 2007-09-10
Thanks for your tips,

finally I got it working with Network manager (which thus supports wpa although the help says it doesn't).

* System --> Network  doesn't give wpa option
but the Network manager applet does... I don't know if it is a bug.
Couldn't find it.

One problem though. If deconnected it seems unable to bring up wifi connection again. (I just started wire connection and then tried to switch 
to wifi (via the applet) but it cannot restablish the connection).

b16

---

### Post by 5-HT on 2007-09-12
> **b16 said:**
> 

One problem though. If deconnected it seems unable to bring up wifi connection again. (I just started wire connection and then tried to switch 
to wifi (via the applet) but it cannot restablish the connection).

b16

Glad you got it! I've had the same issue using networkmanager and didn't bother looking into it  too much as either a manual config or wifi-radar work flawlessly and I didn't want the headache. It might be worthwhile to check bug reports for both networkmanager and Ubuntu to see if this is a known issue.
cheers,

---

