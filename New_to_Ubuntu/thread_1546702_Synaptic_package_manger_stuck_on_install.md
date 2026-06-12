---
title: "Synaptic package manger stuck on install"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by superninja on 2010-08-05
I go into Synaptic Package Manager and there is 1 upgrade available and it is for Freepats (the MIDI sound program) and I click apply and it downloads okay I think but then when it comes to the install it gets stuck, I've let it run all night and I've restarted my computer and tried again. I am running ubuntu 10.04 on a Sony VAIO laptop model # PCG-V505BX. I can post a screenshot of what the installer looks like too, if that helps. Any help is greatly appreciated.

---

### Post by superninja on 2010-08-05
Here is a screenshot of what synaptic is stuck on. I hope this helps :)

---

### Post by superninja on 2010-08-06
I think the problem might be with the freepats package, is there any way to not upgrade this package? I have tried to remove it but it says that it is in unstable condition and that I should reinstall it then remove it. But reinstalling it isn't working.

---

### Post by ranch hand on 2010-08-06
The first thing to try, I think, in these situations is;
```

sudo dpkg --configure -a

```
and see what happens.

Something should even if it is just a better list of errors.  If you get an errors list post it here.

If all you get is another command prompt I think I would reboot to recovery and use the "dpkg fix broken packages" option.

---

### Post by Bofill82 on 2010-08-06
Open a terminal:
 
sudo dpkg --configure -a
sudo dpkg -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by superninja on 2010-08-06
I have not tried the commands yet but I have tried the "fix the broken packages" and that won't work because synaptic does not think it is broken so it is classified as "upgradeable" not "broken", but I will try the commands, thank you very much :).

---

### Post by superninja on 2010-08-07
Updating from the command line worked :)!! I have a question though, what does the command "sudo dpkg -f install" do? Thank you very much

---

### Post by QLee on 2010-08-07
[QUOTE=superninja]Updating from the command line worked :)!! I have a question though, what does the command "sudo dpkg -f install" do? Thank you very much[/QUOTE]

I'd like to answer you with a bit more than you asked, but it might help.

Regarding the advice that poster Bofill gave:

This was to configure any packages that might have failed to configure:
sudo dpkg --configure -a

This was to "fix" the "install":
sudo dpkg -f install

This was to update your sources list to ensure your system knew which version number of files is the highest available version:
sudo apt-get update

This is to upgrade your system to the highest available version:
sudo apt-get upgrade

One possibility for what you experienced is that there could have been a difference from what your system thought was the correct version and what version was available in the repositories and to your system. That's not the only possibility, though.


Edit: I should also mention for clarity, freepats are the sound fonts, not a "program".

---

### Post by superninja on 2010-08-07
Cool, thank you very much. That definitely clears it up for me. Thank you

---

