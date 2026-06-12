---
title: "How to I Move"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by StBeAc on 2010-10-09
I am new to posting here. A friend "converted me to linux" last Jan. To accommodate my new ATT data device, my computer got upgraded to ubuntu 10.4. (it would not run on 8.4) However, the hard-drive, power supply and video card were all dying on my computer. So the friend built me a new computer running 10.4 with a new hard-drive I purchased. My old hard-drive was also installed in the computer so I could transfer all my file data. Evolution mail was set up for me on the new drive. All 1770 messages as well as all my file folders inside Evolution made it over.  I did have to configure my email accounts. However, I discovered that only one of my 5 address books made it over. The other address books each have 60-100 addresses (organizational addresses) and are hopefully still on the old hard-drive. I am also missing all my calendar inputs.

How do I get these addresses to my new hard-drive so that Evolution can access them? I did try Google-ing my question, but none of the responses seemed to help. I went to  usr/lib/evolution/2.28 on my old hard-drive, but I have no idea what to do now. :confused:


Thanks

---

### Post by andrewthomas on 2010-10-09
it seems to me the information would be in your old home directory.

---

### Post by StBeAc on 2010-10-09
I just looked in my old home directory- all I see are my personal files. Do I need to be in the usr files?

---

### Post by alphacrucis2 on 2010-10-09
> **StBeAc said:**
> I just looked in my old home directory- all I see are my personal files. Do I need to be in the usr files?

Try setting from the nautilus menu View - show hidden files. You will see a bunch of extra folders starting with a full stop under your old home folder. Have a look under .evolution. I don't use evolution myself so I have no idea what the address books are called or what format they are in.

---

### Post by andrewthomas on 2010-10-09
> **alphacrucis2 said:**
> Try setting from the nautilus menu View - show hidden files. You will see a bunch of extra folders starting with a full stop under your old home folder. Have a look under .evolution. I don't use evolution myself so I have no idea what the address books are called or what format they are in.
+1 sorry I forgot to tell you to look at the hidden files.

---

### Post by StBeAc on 2010-10-09
Thank you. Selecing show hidden I was able to find the folder for .evolution--however, the files there do not seem to be the ones I need. I copied all to the new hard-drive even thought they were identical to the directory on the new hard-drive. (from when my friend copied them....)  Would they be hiding somewhere else?

---

### Post by harrisonk on 2010-10-09
Try opening your home folder on the old drive, hit Ctrl + H and you should see some folders with a . in front. (you may have to scroll down) find .evolution and double click it. then double click addressbook then local. post back whats in there.

Harrison

---

