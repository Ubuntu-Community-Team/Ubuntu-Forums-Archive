---
title: "Borked my 11.04 upgrade due to power outage"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by ga5im on 2011-05-02
Hi, guys.
In grand newbie style, i just finished downloading 11.04 and wanted to upgrade my install of 10.04. booted my live cd, chose upgrade and off we went. After 2 0 minutes of being stuck at [wiping swap space], the power went out and i was forced to wait for it to return. Upon booting, i restarted the install only to find out i supposedly had 11.04 installed. I booted into the OS and upon logging in, i got an error message of Could not update ICEauthority file /home/ga5im/.ICEauthority . All attempts to get into the gui have failed. I am guessing the install didnt complete and i now have a fairly useless system. 
I dont want to wipe and do a clean install cos i have files i cant afford to lose. Is there any way i can repair this problem and get to Nutty Narwhal bliss?
Thanks in advance

---

### Post by dniMretsaM on 2011-05-02
You could install Natty on a different partition and recover your data that way. Then you can delete the partition with the faulty install to get the rest of your HD space.

---

### Post by ga5im on 2011-05-02
Thanks for the quick reply
That would be the fastest and easiest way, but i have a pretty slow internet connection and it would take at least a week to get all my apps and modifications back, which is why i upgraded in the first place. Is there any other option that allows me to fix the install?

---

### Post by dniMretsaM on 2011-05-02
I do not know. You could just make a list of the programs you and and paste them into terminal
```
sudo apt-get install package1 package2 package3 etc
```
If you do that just before you go to bed at night, you should have all your packages when you get up in the morning. I don't think there are any programs that you can use to fix a broken install. I could be wrong however. I know that's a hard concept to grasp, but it COULD happen (jk, jk).

---

### Post by ga5im on 2011-05-02
Yep. I also just tried to use the live option to get at my files. No joy. Tells me i dont have read permission. Looks like even if i do a side-by-side install i wont be able to get at my files. I would really hate to have to format. Truth is the connection is really sucky. Installing my apps took over a week with all night downloads.

---

### Post by dniMretsaM on 2011-05-02
Did you try to access them with root permission? And you must have a seriously slow connection and a lot of large apps.

---

### Post by ga5im on 2011-05-02
Thanks! That did the trick.. Off to copy my precious files... Oh, any idea where i can find the bookmarks storage folder for firefox 4?

---

### Post by dniMretsaM on 2011-05-02
Yeah, just copy the .mozilla folder from your home directory (it's a hidden file, press Ctrl+H to see it). It contains everything like bookmarks, userChrome.css, about:config settings, pretty much everything from your FF profile. Glad you got it to work! The Live CD is a wonderful thing.

---

### Post by ga5im on 2011-05-03
Just got back after a good night's sleep and ready to go. Thanks for the help. Ubuntu is a gr8 place to be...

---

### Post by Linux&amp;Gsus on 2011-05-03
While you are at it, copy all hidden folders from your home folder over to your backup. All those folders starting with a '.' This is were the apps store all the settings, etc.
I got that good advise from ~Plue just a few days ago. There is a lot of stuff to be found in those hidden files and folders.

---

### Post by dniMretsaM on 2011-05-03
Glad you got it to work dude (dudette w/e)! And yeah, if you didn't already delete everything, follow L&G's advice.

---

