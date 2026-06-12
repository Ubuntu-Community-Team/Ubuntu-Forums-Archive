---
title: "Nautilus – rename is broken"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by zedi on 2009-12-12
When during rename you press delete button to delete character or selected few characters  the file (or folder) you are trying to rename is deleted instead. So far, I've been able to find deleted items in Trash and restore them. 
When renaming with cut & paste or printing characters everything is fine.
Just to make sure it's Nautilus problem, I installed Thunar and sure enough rename works OK – and you can delete characters. BTW, I love bulk rename capabilities of Thunar.
I really like Nautilus, so I googled (& bing-ed) a lot in last couple days and found 1 post with an alike problem, but no solutions were given.
I don't know if its relevant, but the day Nautilus start behaving this irritating way I was playing with new themes and some Compiz settings. Now everything is back to my old settings, when Nautilus was OK.

Zedi

---

### Post by zedi on 2009-12-14
I tried on General Help forum but for 3 days now, nobody answered – maybe this one will be more lucky. 
When during rename you press delete button to delete character or selected few characters the file (or folder) you are trying to rename is deleted instead. So far, I've been able to find deleted items in Trash and restore them. When renaming with cut & paste or printing characters (without using delete) everything is fine.
Just to make sure it's Nautilus problem, I installed Thunar and sure enough rename works OK – and you can delete characters. 
BTW, I love bulk rename capabilities of Thunar.
I really like Nautilus, so I googled (& bing-ed) a lot in last couple days and found 1 post with an alike problem, but no solutions were given.
I don't know if its relevant, but the day Nautilus start behaving this irritating way I was playing with new themes and some Compiz settings. Now everything is back to my old settings, when Nautilus was OK.

---

### Post by cariboo on 2009-12-14
Please don't create multiple threads on the same subject, I have merged your two threads. It is acceptable to bump your thread 24 hours after you created it, if you haven't had any response.

---

### Post by 4Orbs on 2009-12-14
Some of the custom themes I have used would cause weird behavior when right-clicking files in Nautilus. Maybe switch back to a default Ubuntu theme and it will work well. If that is the problem then I suggest you avoid themes using the "compact menu".

---

### Post by zedi on 2009-12-14
I'm very sorry for accidental creating 2 threads on the same subject. I was trying to edit my tread (spelling) and something went wrong. I don't know why it happened.
To **4Orbs:**
I switched to the 'Human theme'; I understand that's  a default Ubuntu theme. Unfortunately, its still deleting the file instead a characters, even after rebooting. So it didn't work!
BTW, I was using compact themes before without any problems. I like those – they neat and compact. 
Also, which application is responsible for themes? I mean, which folder in ~ to look in or which apps to reinstall?

---

### Post by ankspo71 on 2009-12-14
> **zedi said:**
> When during rename you press delete button to delete character or selected few characters  the file (or folder) you are trying to rename is deleted instead. So far, I've been able to find deleted items in Trash and restore them. 
When renaming with cut & paste or printing characters everything is fine.
Just to make sure it's Nautilus problem, I installed Thunar and sure enough rename works OK &#8211; and you can delete characters. BTW, I love bulk rename capabilities of Thunar.
I really like Nautilus, so I googled (& bing-ed) a lot in last couple days and found 1 post with an alike problem, but no solutions were given.
I don't know if its relevant, but the day Nautilus start behaving this irritating way I was playing with new themes and some Compiz settings. Now everything is back to my old settings, when Nautilus was OK.

Zedi


Hi, I don't use the delete button on my keyboard because it deletes all of the selected characters in the name. If nothing is highlighted in the name*, nothing gets deleted. Use the backspace key instead. 

* What I meant was if I have already edited the name (or left clicked inside the text box)
 so that the previously highlighted characters are no longer highlighted, no text gets deleted. 

PS, I like the bulk renaming feature of Thunar too. I haven't had any problems having both nautilus and thunar installed at the same time, but I haven't tried to replace nautilus with thunar though.
James

---

### Post by 4Orbs on 2009-12-14
I didn't mean to imply that all themes using the compact menu were bad, just that the only themes I encountered right-click weirdness with were all using the compact menu. If switching to the default theme didn't solve the problem then I believe the theme is probably not the source of the problem. Your last question, I'm not sure what you are asking. System-wide used themes are located in the /usr/share/themes folder, individual user themes are located in the ~/.themes (hidden) folder.

---

### Post by zedi on 2009-12-14
**ankspo71**
  (or maybe James)
Thank you very much for the tip! Backspace works and I think I'll be using it a lot. But, quote: 'it deletes all of the selected characters in the name.' That is the problem – it shouldn't.
And quote: ' If nothing is highlighted in the name, nothing gets deleted.' Not true – even if nothing is  highlighted and you use delete button (to delete a characters in front of the courser) its deleting a file (or folder).
Anyway, why Thunar can do proper job but Nautilus can not? Is it a bug?

**4Orbs**
To clarify: - when application is giving you trouble, sometimes you can delete a suspicious file in a apps folder or reinstall an apps to fix it. In this case, I would have to probably reinstall whole Desktop and that is to much.

---

### Post by ankspo71 on 2009-12-14
Hi, 
yes naultilus should not be deleting any files or folders if you are trying to rename files and folders, even if you are using the delete button. However, I can left click select (or draw a box around) any file on my desktop and press the delete button and it will delete the file or folder, but not if I right click on the file and select rename first. It works the same way if I open a folder window. Shift + Delete will delete them permanently, by not sending them to the trash. The delete button by itself sends them to the trash.

If you are telling naultius to rename a file... but it deletes it instead, then I think this is a possible dangerous bug that should be reported. If you are telling nautilus to rename a file, only the text in the name of the folder or file will be highlighted, not the entire folder or file itself.

james or ankspo71 is fine. I use my real name james heavily on another forum and I keep using my name here as a force of habit :).

---

### Post by zedi on 2009-12-14
**James,**
How do I report a possible dangerous bug?

---

### Post by lavinog on 2009-12-14
> **zedi said:**
> **James,**
How do I report a possible dangerous bug?

In nautilus, click help, then report a problem.
You will need a launchpad account.

---

### Post by lavinog on 2009-12-14
[when renaming a file, Shift-del removes the file, not the text](https://bugs.launchpad.net/nautilus/+bug/61240)

---

### Post by ankspo71 on 2009-12-14
Hi,
Here is some good info about reporting bugs...
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
James

---

### Post by ankspo71 on 2009-12-14
> **lavinog said:**
> [when renaming a file, Shift-del removes the file, not the text]("https://bugs.launchpad.net/nautilus/+bug/61240")

Hey, you're right. I never noticed that.
I can duplicate this problem in Ubuntu 10.04 Alpha 1
I have just added a comment for this bug on launchpad.

---

### Post by zedi on 2009-12-14
I reported the bug. Lets hope it will be fixed, soon.
Zedi

---

### Post by zedi on 2009-12-18
Bump.
I'm still hoping somebody will help me. Its very annoying!
Maybe its not Nautilus. Just found out, the same thing is happening when trying to rename file on the desktop, without opening Nautilus.
Could it be, because I removed Evolution, Bluetooth & Mono?

---

### Post by lavinog on 2009-12-18
The desktop is still nautilus.
There isn't much you can do except don't use the delete key until it is fixed.
It is most likely not going to be fixed until lucid.
Use the backspace key in the meantime.

---

