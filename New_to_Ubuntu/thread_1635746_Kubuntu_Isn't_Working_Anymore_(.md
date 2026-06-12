---
title: "Kubuntu Isn't Working Anymore :("
date: 2010-12-02
forum: New to Ubuntu
---

### Post by Timo0060 on 2010-12-02
Hello everyone, I installed Kubuntu on my laptop using wubi so i could keep windows 7 and just have it run along with it, but now kubuntu won't start up, it was working for like a month, any help? It would sure be appreciated. Thank you in advance to whoever helps me.

---

### Post by NightwishFan on 2010-12-02
Can you be more specific, does it just loop back to the boot menu when you choose to boot Kubuntu or does it just get a blank screen? Try booting in recovery mode and running a failsafe X session. (If there is that option in 10.10).

---

### Post by Timo0060 on 2010-12-02
Well I originally installed it using wubi, and it worked for a month. Mow at the boot menu I choose to run Ubuntu and it starts and then comes up with the error "no wubibuilder" I think, then it restarts my laptop and does the same thing if i try it again.

---

### Post by NightwishFan on 2010-12-02
You may need to reinstall Wubi. Did you ever shutdown improperly? I will do some digging about this error.

---

### Post by NightwishFan on 2010-12-02
This thread may be of interest:
[http://ubuntuforums.org/showthread.php?t=1494217](http://ubuntuforums.org/showthread.php?t=1494217)

---

### Post by Timo0060 on 2010-12-02
Well it seems like he had the same problem, but I don't understand what was being said, I'm not very good in understanding computer programing terms. By any chance do you know how I could install Kubuntu onto my laptop, and run it along with windows 7 without using wubi?

---

### Post by NightwishFan on 2010-12-02
You can set up a true dual boot. The process is outlined here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

To simplify it in steps (still thumb through the above):

1. Make a Windows recovery cd for Windows 7. [http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

2. Use the Windows partition manager to shrink the Windows 7 partition, and leave empty free space for Kubuntu. [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

3. Download and burn Kubuntu cd. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

4. Run the installer, and when prompted install in "The Largest Free Space".

This is not as complicated as it sounds and is actually pretty fun. If you have any questions please ask.

---

### Post by Timo0060 on 2010-12-02
Thank you so much. That's perfect for me. I think I'll do that when I get a new computer, have you done any digging around for the other error with wubi? the link you gave me was nice, but i didn't understand what was being said.

---

### Post by NightwishFan on 2010-12-02
This is another post about the issue the user said this fixed it. I am unsure and I do not have wubi to play with this issue myself.

Edit (sorry forget link >_>) [http://ubuntuforums.org/showpost.php?p=8989641&postcount=33](http://ubuntuforums.org/showpost.php?p=8989641&postcount=33)

---

### Post by bcbc on 2010-12-02
Try this link:
[http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)

If you have any questions I'll try and answer them.

---

