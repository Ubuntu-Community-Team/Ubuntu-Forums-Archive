---
title: "Thunderbird - Point profile to different location"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Charlie629 on 2010-05-11
I'm totally new to Ubuntu.  I installed Thunderbird and I'm trying to modify the profile to point to a location in Windows.  I've done this to Windows Vista and Xp that are on different partitions. 
First, I can't find Thunderbird profile in Ubuntu.  Where is it located and is the file named the same as in Windows, "profile.ini"?  Any help will be appreciated.  Remember, I'm new to Ubuntu.  
Thanks in advance.

---

### Post by vallvi on 2010-05-11
try click on 'show hidden files' under 'view' in your home folder and look for the .thunderbird (or .mozilla-thunderbird) directories where your mail, profiles, etc. are located

---

### Post by ubunterooster on 2010-05-11
as for part 2 of your question, it is profile.ini just like MS Windows

---

### Post by Charlie629 on 2010-05-11
Thanks for your quick replies, however, pointing to a folder in Windows from Ubuntu doesn't seem to work.  I pointed to:
"c:\Documents and Settings\DiskA\AppData\Roaming\Thunderbird\Profiles\zhgm4xj1.default".  It seems Ubuntu doesn't like it and locks up.  I tried finding the folder from Ubuntu and couldn't find it.  I installed Ubuntu 10.04 inside of my c:\Windows Vista partition.  Oddly, I can find files in my d:\Windows Xp Pro partition.
Thanks again for your help.

---

### Post by ubunterooster on 2010-05-11
You would want to copy the folder to Ubuntu via USB or such medium as Ubuntu can't access a partition it is inside of

---

### Post by Charlie629 on 2010-05-11
Thanks ubunterooster for your quick reply.  Am I correct?  If I reconfigure Thunderbird in my Windows d:/ partition with my profile there, then I should be able to point Thunderbird profile.ini in Ubuntu to it.  I'll just have to figure the language Ubuntu uses for the folder.
Thanks again.

---

### Post by ubunterooster on 2010-05-11
I think that the profile has to be in the Mozilla folder but I've never tried it otherwise, so I can't be sure.

Maybe if you use a shortcut link....idk

---

### Post by Charlie629 on 2010-05-11
I didn't make myself clear.  I presently have Thunderbird installed in Vista on my c:/ partition.  I have Xp Pro on my d:/ partition and have Thunderbird there point to c:/.   I'm thinking of removing Thunderbird from Vista in c:/ and installing it in Xp Pro on d:/.  Then I'll point Vista and Ubuntu to the d:/ partition.   I know Vista will work.  I'm worrying whether Ubuntu modification of profile.ini will point to Thunderbird in d:/.   
Thanks again.

---

### Post by ubunterooster on 2010-05-11
Wow, I never heard of doing that before....Theoretically it should. Make sure drive D is mounted before starting Mozilla, though, or Mozilla will want to make a new profile

---

### Post by Charlie629 on 2010-05-11
I already had Vista in c:/ and Xp Pro in d:/ for over a year.  I pointed the profile in d:/ to c:/.  That way my mail is updated and the same whether I use Vista or Xp Pro.  I just installed Ubuntu this past week and wanted to do the same so that all three operating systems would have Thunderbird's mail read from the same file.  I'll give it a try this week or next and let you know how it works out.  Thanks again.

---

