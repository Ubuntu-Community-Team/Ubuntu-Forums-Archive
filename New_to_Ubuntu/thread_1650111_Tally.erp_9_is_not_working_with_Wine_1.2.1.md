---
title: "Tally.erp 9 is not working with Wine 1.2.1"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by gopi134 on 2010-12-21
Please help me to resolve following issues.
Issue 1:
I  am using Ubuntu Maverick. and Wine 1.2.1. I tried to install Tally.erp  9. Although installation completes successfully, when I run the  application, system hangs ( all the right side and top buttons in  tally.erp won't come at all!! only black color is seen.
Please tell me which version of wine I should use?
Issue 2:
Will the feature " Exporting data from to Excel" works fine in ubuntu?
Thanx.

---

### Post by Wtower on 2010-12-21
I hope there is someboby in this forum that can help you, but I think you should better check with WineHQ appdb for that particular application. The link is 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18517](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18517)

Now as for the feature you mention, I assume you talk about OpenOffice Calc, which does have a useful exporting feature.

Regards

---

### Post by kiers on 2011-01-09
It is common. Apparently Tally is not a well written s/w.

It runs v. slowly in educational mode under wine.

DId you ever fix it?
K.

---

### Post by rvchari on 2011-01-09
if you r trying tally erp9 for the first time then you should follow this thread => [http://ubuntuforums.org/showthread.php?t=1660190](http://ubuntuforums.org/showthread.php?t=1660190).

i have checked and done everything. software soads well in education mode (which i used for trial) if i copy the Data folder on to c: in .wine it works, but i wanted to connect over lan to access and work with my laptop which i couldnt, the above thread should throw some light to what u need. perhaps u can run as single user on ur local machine. my wine version is 1.2.2

---

### Post by kiers on 2011-01-09
> **rvchari said:**
> if you r trying tally erp9 for the first time then you should follow this thread => [http://ubuntuforums.org/showthread.php?t=1660190](http://ubuntuforums.org/showthread.php?t=1660190).

i have checked and done everything. software soads well in education mode (which i used for trial) if i copy the Data folder on to c: in .wine it works, but i wanted to connect over lan to access and work with my laptop which i couldnt, the above thread should throw some light to what u need. perhaps u can run as single user on ur local machine. my wine version is 1.2.2

Hi Rvchari,
yes but i am NOT running tally in a networked mode! i am not trying to save anything to a network drive! Just my local Pseudo "C" DRIVE on ubuntu system.

are you saying Tally by default goes out over the net to save your work?? maybe that's why it runs slow?

But from your posts i don't find that you are complaining of slowness! how come? which version ubuntu, wine, tally.

---

### Post by rvchari on 2011-01-09
its in my previous post buddy, ubuntu maverick (shown along my id) wine 1.2.2, tally erp 9 loads perfectly well and i can create data folder in my pseudo c: of tally in .wine. it also runs fine without hitch. i m not an accounts guy, i tried it coz i can ask the accounts guy to use ubuntu which is safe in comparision to resource hungry windows. thats all...

tally 7.2 as well as erp9 both installs cleanly and runs perfect with local pseudo c: as u need it.

i am a complete user of ubuntu and office works on tally. whenever i want to access files i have to either boot on to my windows (i am using dual boot for reasons like this) or go to another machine thats a thin client connected to office server.

i wanted to avoid doing this so i started my jugglery with wine and i have come this near....

---

### Post by kiers on 2011-01-10
RVChari, you are a shao-lin penguiin (linux) kung fu master (LOL. i'm a fan of the Hong Kong "drunken monkey" kung-fu movie series w young Jackie Chan).

Did you have to add any extra DLL files from windoze tally installation into your Wine directory to make it work???
Also, which compatibility mode are u running Wine under: XP, Vista, or Win 7 with Tally ERP 9?

---

### Post by rvchari on 2011-01-10
thanx for the compliments kiers...
i followed the following steps... may b the required dll or whatever residual junk windows needs takes it up !!!
i installed ie8 thru wine then safari for windows. i tried executing safari.exe and it was fairly fast. i need ie coz whenver i try to change proxy settings in safari, it doesnt let me do, says i shud change in ie !!! so i use ie for that !!!

after this checking, check out .wine/drive_c/windows directory, it shud have sufficient junk to run exe files !!! (sorry for calling junk buddy...)

install tally.erp thru wine and it will install in the .wine/drive_c with program files menu under wine (u can locate from start menu > wine > programs.

tally runs perfect without hitch (i tried 7.2 as well as erp9) my only hitch is => i want to check statements in tally thats installed in office (office lan) Data folder is available when i browse thru wine explorer in tally directory but it doesnt load even after i locate and select the company...

but when i copy and paste the folder in local pseudo c, it loads !!! which i dont want to do)

---

### Post by rvchari on 2011-01-10
if i get an oppurtunity, i ll love to load tally on a ubuntu server thru wine and c if it can be accessed by ubuntu laptop !!! just to have a try so it will be a starting point to initiate people into opensource (sturdy OS) !!!

---

