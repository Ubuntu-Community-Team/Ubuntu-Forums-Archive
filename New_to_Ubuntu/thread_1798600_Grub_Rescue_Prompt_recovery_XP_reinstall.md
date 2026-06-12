---
title: "Grub Rescue Prompt recovery XP reinstall"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Swanybee on 2011-07-06
I am stuck with only the grub rescue > Prompt. 

I duel loaded 10.04 onto XP in dual partition. I had a corruption of XP that caused it to run very slow so tried UBUNTU and loaded 10.04 in second partition , it ran fine. I used Firefox and updated only to find that although coms link was established Firefox did not access the web. 

I decided to cut my losses and remove the The grub MRI and deleted stupidly the Ubuntu partition only to find that the grub rescue section in place. I obtained a legal XP installation Disc only to find my Tosh CD Reader inoperative. Using a USB CD reader I find that my BIOS can't load but can see it.

ls gets (hd0) (hd0,msdos1)/ and an 'ls' on that gets 'error: unknown file system'

Where do I go from here ( Oh I did set the BIOS to read remote)

---

### Post by Rubi1200 on 2011-07-08
Hi and welcome to the forums :-)

Are you able to get as far as following the instructions I will post now?

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by MG&amp;TL on 2011-07-08
I got this the other day. As an alternative to Rubi's suggestion, what worked for me was 'install ubuntu alongside windows' via the live cd, then there is partition/filesystem for grub to 'see' and therefore boots. Unfortunately, I haven't found a way to cleanly remove Ubuntu without re-installing windows. My laptop came without a windows cd. I'm assuming you have to wipe all traces of ubuntu, including swap and stuff, from windows.:confused:

---

