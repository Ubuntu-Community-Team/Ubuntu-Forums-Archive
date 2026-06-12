---
title: "Dual boot syncing questions"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by sprocket10 on 2010-06-27
Well, I finally took the initiative to install Ubuntu. I like everything so far, but I'm having trouble setting up syncing between my two OSes on my laptop: windows7 and Ubuntu 10.04 Lucid Lynx. I use almost the same programs on both OSes and I'm using a shared partition to store all data between.

Firefox: I got my bookmarks to sync by using the Firefox Sync add-on. 

Lightning add-on to Thunderbird: I'm working on getting the calendar events to sync. Is there any way to make this work? I wanna be able to view my events on my calendar on both OSes. I haven't been able to find a decent solution doing forum searches.

---

### Post by wilee-nilee on 2010-06-27
> **sprocket10 said:**
> Well, I finally took the initiative to install Ubuntu. I like everything so far, but I'm having trouble setting up syncing between my two OSes on my laptop: windows7 and Ubuntu 10.04 Lucid Lynx. I use almost the same programs on both OSes and I'm using a shared partition to store all data between.

Firefox: I got my bookmarks to sync by using the Firefox Sync add-on. 

Lightning add-on to Thunderbird: I'm working on getting the calendar events to sync. Is there any way to make this work? I wanna be able to view my events on my calendar on both OSes. I haven't been able to find a decent solution doing forum searches.

I use the foxmarks addon for bookmarks in FF, always works.

---

### Post by oldfred on 2010-06-28
I moved my Firefox and Thunderbird profiles to a shared NTFS partition and changed profile.ini in both windows & Ubuntu to point to it.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Older
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)


I do not use calendar, but a while back I did see some issues with trying to share that. You may want to double check.

---

### Post by Paqman on 2010-06-28
> **sprocket10 said:**
> 
Lightning add-on to Thunderbird: I'm working on getting the calendar events to sync. Is there any way to make this work? I wanna be able to view my events on my calendar on both OSes. I haven't been able to find a decent solution doing forum searches.

You could use a Google calendar. Both copies of Lightening could sync to the same online calendar. IIRC you need to install another plugin into Thunderbird to get write access to your GCal.

---

### Post by sprocket10 on 2010-06-29
Thanks for the help, I've got firefox and thunderbird seeing the same profiles. Now, I know of two calendar options I can try.

I run Sunbird 0.9 on windows and it works fine. So, I could install sunbird 0.9 on ubuntu and point them to the same profile. This would work if I could get sunbird to install in ubuntu. I've downloaded the 0.9 tar file:

sunbird-0.9.en-US.linux-i686.tar.gz

on my desktop. I'm not sure how to proceed to install the program. I know I'll eventually need to make a launcher, but I'm not sure what the interim step is. This is what I'd rather do than using the Lightning extension.

I'll add a screenshot for help!

---

### Post by Rubi1200 on 2010-06-29
> **sprocket10 said:**
> 

I run Sunbird 0.9 on windows and it works fine. So, I could install sunbird 0.9 on ubuntu and point them to the same profile. This would work if I could get sunbird to install in ubuntu. I've downloaded the 0.9 tar file:

sunbird-0.9.en-US.linux-i686.tar.gz

on my desktop. I'm not sure how to proceed to install the program. I know I'll eventually need to make a launcher, but I'm not sure what the interim step is. This is what I'd rather do than using the Lightning extension.

I'll add a screenshot for help!

Why download the tar file? I installed Sunbird 0.9 from the Software Center.

---

### Post by sprocket10 on 2010-06-29
sunbird is not available in the software center in lucid lynx 10.04

see screenshot attached

---

### Post by sprocket10 on 2010-06-30
Also, I tried following some links looking for a .deb file, to no avail.

---

### Post by sprocket10 on 2010-07-01
bump, because the other instructions I saw were for version 0.8   :(

---

