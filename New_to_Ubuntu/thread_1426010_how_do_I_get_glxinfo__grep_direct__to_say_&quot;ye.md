---
title: "how do I get glxinfo | grep direct  to say &quot;yes&quot;"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by limiz on 2010-03-09
This is what happen:```
limoon@limazu:~$ glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

I have a ati RV410 [Radeon X700 Pro (PCIE)].
And I have all the needed lib. ( or at less I think I do)

I need this to say yes to get some native linux game to run. Any help will be welcome.

Edit: Using Ubuntu 9.10!!!

---

### Post by MechaMechanism on 2010-03-19
> **limiz said:**
> This is what happen:```
limoon@limazu:~$ glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```I have a ati RV410 [Radeon X700 Pro (PCIE)].
And I have all the needed lib. ( or at less I think I do)

I need this to say yes to get some native linux game to run. Any help will be welcome.

Edit: Using Ubuntu 9.10!!!Go to menu "System" > "Administration" > "Hardware Drivers" and see if there are any hardware drivers for your card available.  If there are drivers available then install and reboot.  Let me know how it goes.

---

