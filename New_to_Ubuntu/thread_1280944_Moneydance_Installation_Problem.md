---
title: "Moneydance Installation Problem"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by KoolBear on 2009-10-02
Hi!  I have looked at the various Moneydance installation threads and tried the suggestions.  Unfortunately, I still can't install Moneydance.  When I type sudo sh moneydance_linux_x86wj.sh I get the following (after I type in my password):
Unpacking JRE ...
Preparing JRE ...
moneydance_linux_x86wj.sh:  228:  bin/unpack200:  not found
Error unpacking jar files.  Aborting.
You might need administrative priviledges for this operation.

I have Ubuntu 9.04 (64-bit) installed.  Does Moneydance only work with the 32-bit version?  Any suggestions would be appreciated.  Thank you.

---

### Post by pspotts on 2009-10-02
Yes, Moneydance works on 64-bit machines; I used it with 9.04-64bit. And I'm having the same problem that you are, with 9.10B. Trying to activate Moneydance as superuser fails to solve the problem. Interestingly, the file it says it can't find, unpack200, is sitting pretty in .../Moneydance/jre/bin. I've tried changing the Moneydance start-up script by using the full path to unpack200, but that fails as well, with the same error message. So we Moneydance fans are looking for a bit 'o help here...

With best regards,

Pete

---

### Post by pspotts on 2009-10-02
OK, here's the fix. Install the ia32-lib libraries and the ia32-sun-java6-bin. You can use Synaptic to download and install the packages. Moneydance will fire up right away.

Pete

---

### Post by KoolBear on 2009-10-04
Pete,
    Thank you very much for your helpful suggestions.  I apologize for the delay in my response.  I had to learn how to use synaptic in order to follow your instructions.

    Anyway, I was finally able to run the installer and I think Moneydance installed properly because it shows up in my Applications/Other/Moneydance menu but when I select Moneydance, the application does not open.

    I'm very new with Ubuntu (and linux) but I am guessing that I am missing some other files to run Moneydance.  Any suggestions anyone?

---

