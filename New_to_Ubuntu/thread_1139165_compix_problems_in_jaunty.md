---
title: "compix problems in jaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by sh00p_da_wh00p on 2009-04-26
Hello,

I seem to have trouble enabling compiz effects. I have run compiz-check and everything appears to be fine. When I try enabling the effects through preference>appearence>visual effects, I get a window saying 'searching for drivers' and after a couple of seconds everything disappears except for my mouse and the wallpaper. Compiz-switch has the same effect, it's just quicker.

Also, when i run sudo apt-get update, i get an error message saying there are public keys unavailable. the exact messages are: > W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CE90D8983E731F79
W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783W: You may want to run apt-get update to correct these problems. 

1. Could these problems be related?
2. How could I go about fixing them?
3. I'm new to linux, so the simpler the explanation, the better.

Thanks in advance.

---

### Post by lovinglinux on 2009-04-26
First, is not "compix" is "compiz". If you use the first you will get errors in the terminal output.

It seems that you haven't enabled the restricted driver for your card. They are not installed by default due to legal issues.

Open "System >> Administration >> Hardware Drivers" and enable the most recent version for your graphics card.

---

### Post by sh00p_da_wh00p on 2009-04-26
fixed, thanks for pointing it out
when i go to System >> Administration >> Hardware Drivers there's nothing listed
is there a way to have the system recognize my hardware and list the possible drivers?

---

### Post by lovinglinux on 2009-04-26
> **sh00p_da_wh00p said:**
> fixed, thanks for pointing it out
when i go to System >> Administration >> Hardware Drivers there's nothing listed
is there a way to have the system recognize my hardware and list the possible drivers?

You need to enable the proprietary driver repository first. Open "System >> Adminsitration >> Software Sources" and tick "Proprietary drivers for devices (restricted)" option. Then "System >> Administration >> Update Manager" and click "Check". Then go back to the "Hardware Driver" tool and they should be listed.

---

### Post by sh00p_da_wh00p on 2009-04-26
i did everything you said there, everything worked fine, no error messages or anything, but still nothing listed in the proprietary drivers

---

### Post by lovinglinux on 2009-04-26
> **sh00p_da_wh00p said:**
> i did everything you said there, everything worked fine, no error messages or anything, but still nothing listed in the proprietary drivers

Then I guess there isn't any drive for your card. Do you know your card manufacturer and model?

---

### Post by sh00p_da_wh00p on 2009-04-26
its an intel card that came with the computer, better details im not sure about and don't know how to find
it might just be a bug in 9.04 because im starting to see similar problems in other 9.04 users after looking around. thanks for your help so far, though

---

### Post by hacksies on 2009-04-27
i got the same problem. I have an intel 910gml. no drivers are listed.

NM i got it working. search for medibuntu-keyring. compiz works fine

---

### Post by sh00p_da_wh00p on 2009-04-27
Ok, I installed the latest medibuntu-keyring, but still no drivers are listed, nor does compiz work. I'm considering switching to Intrepid Ibex soon if this doesn't go well.

---

