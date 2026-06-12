---
title: "Mobloquer Error"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-04-18
So, I tried to load Mobloquer.
```
clevelandrock@Centurion:~$ mobloquer
```Then this pops up as an error:
```
Required configuration file "/var/log/moblock.log" could not be found in the default path. Please specify a different path.
```Finally, the terminal window looks like this:
```
clevelandrock@Centurion:~$ mobloquer
** Warning: void MoblockSettings::processSettings() Setting "VERSION" has not been defined and was therefore ignored 
** Critical: Logs object has not been intiallized. Check if the path is correct!
** Fatal: A fatal error occured. Please check the file paths. The program will now quit.
Aborted
clevelandrock@Centurion:~$
```Any ideas?

---

### Post by lovinglinux on 2010-04-19
I don't know if mobloquer is being maintained anymore. See [General Moblock Thread](http://ubuntuforums.org/showthread.php?t=803183)

---

### Post by Cleveland Rock on 2010-04-19
Is there something else I can use? Something with a GUI?

---

### Post by lovinglinux on 2010-04-19
> **Cleveland Rock said:**
> Is there something else I can use? Something with a GUI?

I use moblock without a gui. It works great.

There is [iplist](http://iplist.sourceforge.net/), which has a gui.

---

### Post by camporter1 on 2010-04-19
Mobloquer still works fine here. You might try completely purging all the moblock packages and then trying again. Sometimes broken lists can make mobloquer completely unusable.

---

### Post by Cleveland Rock on 2010-04-19
IPblock seems to work. Thanks!

---

### Post by jre on 2010-04-19
Indeed mobloquer is no more developed. But some of your log messages indicate that you just need to start moblock manually once (sudo blockcontrol start). And as it was already stated the crash might relate to a broken blocklist. Try to fix that with "sudo blockcontrol update".

Otherwise either use moblock/blockcontrol without this GUI.
Or make the switch to new PeerGuardian Linux (pgl) (no GUI yet).
Or use iplist.

---

### Post by pt123 on 2010-05-07
I am having problems the last few weeks with Mobloquer unable to contact [www.bluetack.co.uk](www.bluetack.co.uk) to download the blocklists
the error msg is 
no connection to [www.bluetack.co.uk](www.bluetack.co.uk)

---

### Post by jre on 2010-05-09
try the blocklists from iblocklists.com. They also mirror bluetack lists.

---

### Post by pt123 on 2010-05-14
iblocklists.com was blocked in the lists from 
[www.bluetack.co.uk](www.bluetack.co.uk)

---

### Post by jre on 2010-05-15
Then add an exception for iblocklist. Just right-click on its IP in mobloquer and add it to the outgoing whitelist.
If it is a matter of trust: I fully trust fakhir, the maintainer of iblocklist. He's a member of phoenixlabs, has done many great things, and his mirrored bluetack lists are identical to the original ones. So if iblocklist is blocked by bluetack, then I think this is a coincidence, perhaps related to his provider and other customers. These things happen quite often.

---

