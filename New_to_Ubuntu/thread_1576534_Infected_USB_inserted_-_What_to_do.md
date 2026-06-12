---
title: "Infected USB inserted - What to do?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by AW603 on 2010-09-17
My son inserted a USB stick he had used on his school system on to our  Ubuntu system.  We always scan an inserted USB whenever it has been in  another machine,  and although ClamAV reported clean, BitDefender  reported a trojan in a hidden file called ***MENINIKO\netreba.exe***.  A scan with Jotti comfimed (18/20 scans) the issue, and I let Bitdefender delete the file, and I formatted the USB stick. 

I'm fairly new to Ubuntu, and although I know that the problem file can't execute within Ubuntu, do I need to be worried?

BTW Wine is on the system, is it at all possible that the trojan could have infected that?

Thanks, and sorry if the are dumb questions:redface:

---

### Post by frank002 on 2010-09-17
No question is a dumb question. No need to worry about a Windows virus affecting Linux.

---

### Post by Rubi1200 on 2010-09-17
As far as I know, Wine could only be affected if you were running it as root.

Your questions are not dumb and your precautions are praiseworthy; I wish more people would be this sensible!

---

### Post by sikander3786 on 2010-09-17
All you need to do is "Not to worry". No fears here. Still if you want to scan the files that are going through your PC to your friends, colleagues, you might like to scan them in order to prevent their "Windows" from getting infected. Still they'll have no effect on your install nor they can affect wine. There have been discussion on this. Some think this ways, the others that way. See,

[http://ubuntuforums.org/showthread.php?t=128768](http://ubuntuforums.org/showthread.php?t=128768)

Use clamav or anyother antivirus to serve the purpose.

Regards.

---

### Post by Lateralis on 2010-09-17
Windows executables cannot be run in Linux unless you run it using Wine.  Even then, you actually have to tell Wine to run the virus.  Running other Windows software in Wine shouldn't make a difference.  And even if you do run the virus in Wine, the virus cannot really do anything.

---

### Post by AW603 on 2010-09-17
Thanks.  Am I right in thinking that Windows virus/trojans or programmes for that matter can't open or function at all within Ubuntu without my permission? 

Also is it possible for any traces of this trojan could left on my system - I don't want to spread any trojans to someone elses Windows machine either by USB or any other way.

Edit- Sorry all I missed your posts then -Thanks

---

### Post by AW603 on 2010-09-17
Thanks for all your help:D

---

### Post by endotherm on 2010-09-17
> **AW603 said:**
> Thanks.  Am I right in thinking that Windows virus/trojans or programmes for that matter can't open or function at all within Ubuntu without my permission? 

Also is it possible for any traces of this trojan could left on my system - I don't want to spread any trojans to someone elses Windows machine either by USB or any other way.

Edit- Sorry all I missed your posts then -Thanks
that is the case now. it used to be that wine had to have execute priv but the exe;s that it loads didn't. now it is my understanding that wine requires teh exe itself to permit execution. not sure how that would affect non-linux partitions that don't support owner or rwx permissions though. 

in the end, you can rest reasonably assured that your PC is fine.

---

### Post by Gone fishing on 2010-09-17
You are safe! A Win32 virus will not work in Ubuntu and probably not even in the wine environment - and any case would be effortless to clean.

Just open the flash disk an remove all the files you don't want. All the autoruns, pifs and rubbish you don't recognize as useful etc. 

You could then if you wished install an AV just to check files - no risk to you, but just in case a file could infect another windows PC. Antivir, AVG, Avast and Clam all have Linux AVs

---

### Post by Elfy on 2010-09-17
From one of those _really_ long posts/threads that [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054") writes from time to time 

> A few comments on wine

Discussions about running Windows viruses on wine crop up from time to time and it is possible to run some Windows viruses on wine.

See these links :

    * McAfee Avert Labs Blog
    * Running Windows viruses in wine


So what do you need to know about Windows viruses if you want to run wine?

1. First, the "golden rule" : DO NOT RUN WINE AS ROOT. If you are NOT running wine as root then wine will not have the necessary permissions to affect system files.

2. So, if you are running wine as a user, a Windows virus will be confined to your home directory.

3. You can further confine the "fake c drive" located at ~/.wine if you remove any symbolic links outside ~/.wine. With a default installation there is link with a default installation / configuration of wine :

[QUOTE]* ~/.wine/dosdevices/z: -> links to /


A link from ~/.wine/dosdevices to the root directory ( / ) should concern you for obvious reasons.

You can remove it with :


```
unlink ~/.wine/dosdevices/z:
```

Do not worry, that command will not affect wine at all, I run it all the time

You may need to make a link in ~/.wine/dosdevices to your cdrom and/or you may be tempted to link to your home directory, but I advise against keeping using these links (beyond the time needed for actually installing applications).

I advise against any links to removable devices (it should not be *that* difficult to copy files needed to the appropriate location in ~/.wine/drive_c ).

4. Consider running an antivirus program and scanning ~/.wine and any removable devices or other locations you use outside of ~/.wine to store programs or data to be used with wine. Scan any data / applications you use with Windows.

5. Consider confining wine with Apparmor.

6. Be sure to file a bug report with the wine project as they have a very active security team (it is unrealistic, however, to expect the wine team to be able to protect you from all Windows viruses all the time). Wine Bug Reports

7. Take the same precautions with wine as you would with Windows. Do not install untrusted applications from untrusted sources.

If you follow the above advice, Windows viruses will be confined to ~/.wine and they do not have permission to change system files. This means to remove them you simply:

Code:

rm -rf ~/.wine

Please take care, this command deletes everything in your wine directory including all data and all applications.

You then need to restore your wine directory from a known good backup (you do keep backups ?).[/QUOTE]

The whole post is here - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by ubudog on 2010-09-17
Don't worry, you should be fine.  Windows viruses/trojans/etc can't infect Linux. :p  And I don't think it would run itself in Wine either, but you can be sure:
```
ps ax | grep wine
```

---

