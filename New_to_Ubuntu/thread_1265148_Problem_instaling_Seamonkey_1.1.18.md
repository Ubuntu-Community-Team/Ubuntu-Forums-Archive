---
title: "Problem instaling Seamonkey 1.1.18"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by ChadBJX on 2009-09-13
[SIZE=2]Hello again,
I am trying to find a website editing program now and since Kompozer kept on crashing on me I uninstalled it and tried Seamonkey. The one that installed in Add/Remove Programs was version 1.1.17 (or something like that). On launching the browser it took me to the Seamonkey page which told me I was using an older, less secure version and suggested I install 1.1.18. Which I downloaded and followed these instructions ... 

   1. Create a directory named seamonkey1.1.18 (mkdir seamonkey1.1.18) and change to that directory 
(cd seamonkey1.1.18).
   2. Click the link to download the installer file (called seamonkey-1.1.18.en-US.linux-i686.installer.tar.gz).
   3. Change to the SeaMonkey directory (cd seamonkey1.1.18) and decompress the archive with the following command:
      gunzip -dc sea*.tar.gz | tar -xvf -
      (This places the installer in a subdirectory of SeaMonkey named seamonkey-installer.)
   4. Change to the seamonkey-installer directory (cd seamonkey-installer) and run the installer with the 
./seamonkey-installer command.
    PROBLEM STARTS HERE
   5. Follow the instructions in the install wizard for installing SeaMonkey.

This is the response I get when trying to run the installer:
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ ./seamonkey-installer
./seamonkey-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

When I browse the directory it shows the installer there.
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ dir
config.ini     MPL-1.1.txt  seamonkey-installer      xpi
installer.ini  README        seamonkey-installer-bin
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ 

Remembering how Windows loved to hang on to things and cause usage errors, I even rebooted my computer just incase it was a memory issue of some kind.

Any ideas? Corrupt download maybe? Or am I mistyping something?

Thank you in advance,   :(
[/SIZE]

---

### Post by talsemgeest on 2009-09-13
> **ChadBJX said:**
> [SIZE=2]Hello again,
I am trying to find a website editing program now and since Kompozer kept on crashing on me I uninstalled it and tried Seamonkey. The one that installed in Add/Remove Programs was version 1.1.17 (or something like that). On launching the browser it took me to the Seamonkey page which told me I was using an older, less secure version and suggested I install 1.1.18. Which I downloaded and followed these instructions ... 

   1. Create a directory named seamonkey1.1.18 (mkdir seamonkey1.1.18) and change to that directory 
(cd seamonkey1.1.18).
   2. Click the link to download the installer file (called seamonkey-1.1.18.en-US.linux-i686.installer.tar.gz).
   3. Change to the SeaMonkey directory (cd seamonkey1.1.18) and decompress the archive with the following command:
      gunzip -dc sea*.tar.gz | tar -xvf -
      (This places the installer in a subdirectory of SeaMonkey named seamonkey-installer.)
   4. Change to the seamonkey-installer directory (cd seamonkey-installer) and run the installer with the 
./seamonkey-installer command.
    PROBLEM STARTS HERE
   5. Follow the instructions in the install wizard for installing SeaMonkey.

This is the response I get when trying to run the installer:
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ ./seamonkey-installer
./seamonkey-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

When I browse the directory it shows the installer there.
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ dir
config.ini     MPL-1.1.txt  seamonkey-installer      xpi
installer.ini  README        seamonkey-installer-bin
chad@chad-desktop:~/seamonkey1.1.18/seamonkey-installer$ 

Remembering how Windows loved to hang on to things and cause usage errors, I even rebooted my computer just incase it was a memory issue of some kind.

Any ideas? Corrupt download maybe? Or am I mistyping something?

Thank you in advance,   :(
[/SIZE]
You wouldn't happen to be running 64 bit would you? If you are you probably have to install the 32-bit libraries:

```
sudo apt-get install ia32-libs
```

---

### Post by ChadBJX on 2009-09-15
> **talsemgeest said:**
> You wouldn't happen to be running 64 bit would you? If you are you probably have to install the 32-bit libraries:

```
sudo apt-get install ia32-libs
```

I am using 32 bit. We found that out while I was trying to fix a problem with Flash. That did get fixed, thanks to help received here.

Should I just go ahead and use the older version of Seamonkey?

Thank you

---

