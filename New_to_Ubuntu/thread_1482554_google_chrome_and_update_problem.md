---
title: "google chrome and update problem"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by arisgano on 2010-05-13
i had just updated my ubuntu 9.10 to 10.04, when i start using google, it says like this "Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and that you have permission to read and write its contents." both OPERA and CHROME cannot remember any account and passwords EVERYTIME I login.
 when i tried to update my system... "Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct." then the window will automatically close.

Almost every software in my system right now are not working properly, especially my VLC becuz it always STACKED.
 I UPGRADED MY SYSTEM THRU THE UPDATE MANAGER. 
 Is there any way i can DOWNGRADE my system, becuz i'm experiencing lot of bugs in lucid compared to karmic. i just want the karmic without LOSING all the softwares i already have right now. becuz when upgraded to LUCID, it takes 1.5 GB in size, and that's a lot of time. Booting in karmic is faster than lucid. I JUST REALLY WANT TO DOWNGRADE MY COMPUTER.

---

### Post by cariboo on 2010-05-13
From the sounds of it the system didn't upgrade correctly. Start in recovery mode, by pressing the shift key at startup and select recovery mode using the arrow keys. At the menu select drop to root prompt with networking using the arrow keys. Once at the prompt type:

```
apt-get -f install
```

once that has completed at the prompt type:

```
aptitude update && aptitude safe-upgrade
```

Third party repositories are disabled during the upgrade process, you may have to re-enable them before upgrading third party programs.

---

