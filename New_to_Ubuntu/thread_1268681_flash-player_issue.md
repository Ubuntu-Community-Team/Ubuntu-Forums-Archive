---
title: "flash-player issue"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by orky7 on 2009-09-17
hi, to keep it short i will write in points:
1- flash works on the original firefox.
2- replace the firefox by a latest firefox "not" through ubuntu update. but i have done it  properly as stated in the ubuntu.help website i still have the backup of original firefox. 
3. in new firefox flash not working so i uninstall and reinstall flash via synaptic.
4. still flash don't work so i installed 64bit flash( my machine is 64 bit) and put the .so file in the plugin folder of firefox and flash work fine but 64 bit flash is buggy 

so i want to know how to link flash player with my firefox /chrome browser

---

### Post by Moop on 2009-09-17
Actually 64 bit flash works better than the 32bit with ndiswrapper etc. Try un-installing every other version of flash and keeping only the 64bit.

---

### Post by orky7 on 2009-09-17
64 bit is working but with some sites it is giving problem so i want the 32bit with the wrapper so how to do it

---

### Post by Moop on 2009-09-17
It depends on how you installed the newer firefox. It would have been better to just upgrade firefox through Synaptic. If the version you want isn't available you can use a ppa that has the version you want. 

[https://launchpad.net/~fta/+archive/ppa]("https://launchpad.net/%7Efta/+archive/ppa")

---

### Post by Hospadar on 2009-09-17
You might try downloading and installing flasplayer yourself (from adobe's website).

The flashplugin-installer ubuntu package puts the flash library in /usr/somwehere (i.e. system wide) but the firefox you installed probably isn't set up to look there for extensions.

The flashplugin from adobe will put the library in your user directory (~/.mozilla/somewhere I believe) which I suspect is more likely to work with your non-packaged firefox.

---

### Post by XCan on 2009-09-17
For the flashplayer you download from Adobe's homepage, just extract it and put libflashplayer.so into ```
 ~/.mozilla/plugins 
``` You may need to create the plugins dir if it doesn't exist.

---

