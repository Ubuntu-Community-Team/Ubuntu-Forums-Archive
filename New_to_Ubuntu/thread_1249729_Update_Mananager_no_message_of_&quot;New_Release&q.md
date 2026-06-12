---
title: "Update Mananager: no message of &quot;New Release&quot;"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by tperwez on 2009-08-25
Hi Everyone,

I have a few simple (I think) questions that I hope people on the Forum can help me resolve:

1. I am planning to upgrade from Ubuntu 8.10 to 9.04 because I think I will have to upgrade to 9.04 if I eventually want to upgrade to 9.10. However, my Update Manager does not give me the message that a new release is available. I have done all updates etc as per instructions:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Thus, I cannot proceed further. Why does my Update Manager not behave as in the instructions? What can I do to make it do as in the instructions?

2. I would like to save all my settings and data in a USB drive before I begin the upgrade to 9.04. What is the best method for doing it? Perhaps something on the command-line that will copy everything (including hidden files etc) to the USB would be ideal

I would appreciate any help I can get. Regards,

Tariq

---

### Post by oldos2er on 2009-08-25
Have you tried **gksu update-manager --dist-upgrade** ?

---

### Post by corncob on 2009-08-25
The first thing I would try would be to open Update Manager and then click on the SETTINGS button.  I would then go to the Updates tab and, at the bottom, in the Release Upgrade section, make sure "normal releases" is selected.

---

### Post by tperwez on 2009-08-25
> **corncob said:**
> The first thing I would try would be to open Update Manager and then click on the SETTINGS button.  I would then go to the Updates tab and, at the bottom, in the Release Upgrade section, make sure "normal releases" is selected.

My Update Manager window does not have any such tabs or menus. However, while poking around in the Synaptic Package Manager, I found out that the Settings option was set to notify only LT releases (I do not know why). I have changed it to normal releases and now the Update Manager does notify of a new release. I believe this is exactly the solution you proposed. Thanks for responding to my question.

I would still like to know how to copy all my data and settings (including hidden files) to a USB drive. I think some command line solution will be more suited to this.

Regards,

Tariq

---

### Post by tperwez on 2009-08-25
> **oldos2er said:**
> Have you tried **gksu update-manager --dist-upgrade** ?

Thanks for this suggestion. I do like to use the commandline option whenever available. Regards,

Tariq

---

### Post by slakkie on 2009-08-25
If you want to use the command line:

```

echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
sudo aptitude install update-manager-core
sudo aptitude update && sudo aptitude safe-upgrade
sudo do-release-upgrade

```

These are the actions you need to perform to upgrade from LTS to non-LTS.

---

