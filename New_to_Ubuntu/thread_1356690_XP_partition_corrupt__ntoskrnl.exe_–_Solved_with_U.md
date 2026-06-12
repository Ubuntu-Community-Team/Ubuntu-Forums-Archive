---
title: "XP partition corrupt  ntoskrnl.exe – Solved with Ubuntu"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Costas100 on 2009-12-16
The following problem is now solved for me, but I do have a couple of situations (near the end of this thread) that any help will turn me in to 100% Ubuntu.

I wish to report the following because many dual boot people may face this problem at one point or another:
When I tried to boot on my windows XP Pro partition I received the following error:
<Windows root>\system32\ntoskrnl.exe is missing or corrupt  Please re-install a copy of the above file.

My first attempt to fix this was to search the web on what to do, I found various methods all involving using the installation CD and then proceed to install this file and possibly do a boot.ini fix or atotal XP reinstall.

Being worried that this may affect my dual boot I searched my original Windows CD for this file and found it as ntoskrnl.ex_ as an archive file. Tried to extract it in Ubuntu but it was not recognized from my Archive Manager. 

Fortunately I had another computer with XP home installed, I placed the archive file in a flash stick and managed to extract the file using the windows 7-Zip program. Then came back to the computer with the problem and using Ubuntu I replaced the corrupt file in a few seconds. Windows XP Pro is now working again.

**The only two reasons I am still using Windows is: **
[LIST]
[*]I am doing some recording from TV using a Plextor PX-TV402U digital video recorder, which I understand maybe compatible with MythTV but I never managed to make MythTV to work. If any one knows of a simple and detailed tutorial, it will eliminate one of my windows needs.
[*]I am using Virtual Dub for minor editing (cut sections and re-compress to divX) various clips. I understand that this maybe possible to do with AviDemux but to this point I am not very successful especially with re-compressing.
[/LIST]
If I solve these two problems then it is forever goodbye windows for me.
Good luck to all and thank you for any suggestions.
Costas

**[CENTER]Ubuntu is the greatest software that I have ever tried and we should spread the word to all People around the World.[/CENTER]**

---

### Post by cariboo on 2009-12-16
The drivers for your device, is [here]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver"), once you have the driver installed and working, just install mythtv from the repositories and you should be good.

---

