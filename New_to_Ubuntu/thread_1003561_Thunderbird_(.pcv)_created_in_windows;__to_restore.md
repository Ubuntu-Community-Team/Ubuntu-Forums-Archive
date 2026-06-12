---
title: "Thunderbird (.pcv) created in windows;  to restore in Ubuntu"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by BangaloreBoy on 2008-12-06
I am an ABSOLUTE beginner. I have JUST migrated to Ubuntu, thanks to my cousin.

[LIST=1]
[*]I had backed up my Thunderbird mailboxes, addresses, settings, etc. using MozBackup in Windows. This created the requisite .pcv file.
[*]Now, I have set up Thundirbird in Ubuntu and need to restore the .pcv file.
[*]I have copied the file to my computer. I looked up information on the net to help me restore the .pcv, but nothing has helped me so far.
[*]I also found something about putting the .pcv file in the ~/.thunderbird folder. Alas, I am not able to find any such folder.
[/LIST]

Would someone please help me achieve this task by providing guidance in non-technical (i.e., **[COLOR="DarkOrchid"]in simple English[/COLOR]**) language? I'd be most grateful. 

Thanks.

---

### Post by Moop on 2008-12-06
I'm not sure about restoring a .pcv file but you can find the thunderbird folder in your home directory. It's hidden so you will need to show hidden files from the view tab or just hit ctrl-h.

---

### Post by zwaardmeester on 2008-12-06
First you would have to install the Thunderbird program. Go to Applications, Add/Remove, search for Thunderbird, install the package called "Mozilla Thunderbird Mail/News". Now it can be found under Applications, Internet.

Unfortunately, the MozBackup program is not available in Linux. However, you can try to restore the settings by yourself (or let the cousin help you). To do this:

1) Create a new folder in your homefolder, call it "temp"
2) Copy the .pcv file to this folder
3) Right-click on it, select "Rename" and change the extension pcv to zip
4) Right-click on the zip-file, select "Extract Here"

Please write down what the names are of the files and folders that appear now. Let us know.

---

### Post by BangaloreBoy on 2008-12-06
Thanks, Moop and Zwaardmeester for your prompt and helpful replies. 

I did locate the .mozilla-thunderbird folder.

Here, I created a folder called temp into which i copied the .pcv file.

I did upack the .pcv file into the temp folder and these came out:

**FILES:**
[LIST]*.mab  -- addressbooks, i guess.
[*]*.rdf
[*]*.dat
[*]*.sqlite
[*]*.db
[/LIST]

**FOLDERS:**
[LIST]
[*]*.slt
[*]extensions
[*]Mail (containing 1 subfolder for each email address i used; each subfolder, in turn, contained *.msf and some other files)
[/LIST]

I then copied these files and folders into .mozilla-thunderbird and launched thunderbird. 

No dice. It did not read the mails or folders in. 

This is the state of affairs at this time.

Looking forward to being able to use my thunderbird soon... and not saying "UNCLE" to B. Gates -- he of the megazillion bucks!

-- end ot transmission --

---

### Post by Moop on 2008-12-07
The way I  transfer my mail and settings is to copy the entire contents of the profile folder from one install to the profile folder for the new install. If you still have access to a windows machine use mozilla backup to restore your profile. Then copy the contents of your profile folder in windows. Open your profile folder in Ubuntu (usually named someting like "tox8vxcv.default" and delete everything, then paste the contents you saved from windows. Start Thunderbird and everything should be there. 

I use Thunderbird and have done this many times and it always works. I've never used mozilla backup.

---

### Post by TRANQU111TY on 2009-01-01
> **Moop said:**
> The way I  transfer my mail and settings is to copy the entire contents of the profile folder from one install to the profile folder for the new install. If you still have access to a windows machine use mozilla backup to restore your profile. Then copy the contents of your profile folder in windows. Open your profile folder in Ubuntu (usually named someting like "tox8vxcv.default" and delete everything, then paste the contents you saved from windows. Start Thunderbird and everything should be there. 

I use Thunderbird and have done this many times and it always works. I've never used mozilla backup.

What is the Thunderbird directory to copy the profile into on Ubuntu?

---

### Post by jschodde on 2009-09-19
_INTRODUCTION_
Here's how I restored my Thunderbird settings and data from Windows XP into Ubuntu 9.04. I no longer have a Windows machine to transfer the old profile data from. My workaround is explained below.

_ASSUMPTIONS_
This process assumes you did a complete backup using MozBackup (i.e. all checkboxes selected at time of back in your Windows environment).

Ubuntu 9.04
Thunderbird 2.0.0.23 (both Windows and Linux)
Wine 1.01

_PROCEDURE_
1. Installed Wine

2. Installed Thunderbird under Wine

3. Installed MozBackup under Wine

4. Installed Thunderbird (Ubuntu)

5. Transferred my .pcv file from my external backup drive to my home folder. I did not extract the files.

6. Launched MozBackup (Wine) and restored the backup into Thunderbird (Wine). Note: I did not launch Thunderbird (Wine) after this. I just left it alone.

7. Located the Thunderbird (Wine) profile data under: [B]/home/jeff/.wine/drive_c/windows/profiles/jeff/Application Data/Thunderbird/profiles/*
[/B] (replace "jeff" with relevant folder name).

8. In my case the profile folder was named "1x5548kh.default". I did a Right-Click>Copy for this folder.

9. Opened my home folder and hit Ctrl+H to show hidden files.

10. Opened the **/home/.mozilla-thunderbird** folder. If you already have a profile, see Note 1 below.

11. Right-Click>Paste the "1x5548kh.default" folder into the **/home/.mozilla-thunderbird** folder.

12. Launch Thunderbird (Ubuntu). You should have all your account data and emails ready to go. In fact, Thunderbird started to download emails immediately!

**Note 1**: If you already have a "<ID>.default" folder, you'll need to modify the profiles.ini file to use the one just copied. Look for "Path=" and change it to match your folder name you just copied.

Example of my profiles.ini file:

[I][General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
[B]
Path=1x5548kh.default
[/B][/I]

---

