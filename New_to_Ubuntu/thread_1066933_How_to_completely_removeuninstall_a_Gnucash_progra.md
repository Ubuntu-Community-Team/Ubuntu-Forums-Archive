---
title: "How to completely remove/uninstall a Gnucash program"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by LindaLou on 2009-02-11
I installed Gnucash via Add/Remove and after several days of working with the program decided that I wanted to start fresh, begin at the beginning. So, I got to Add/Remove and remove Gnucash that way.  I then go back and select the application for install.  Fine.  When I select Gnucash from Applications > Office, the exact same Gnucash appears - meaning, the one I removed and wanted to get ride of!  How do I remove the application and have a "fresh" Gnucash ready for use?

---

### Post by davideotape on 2009-02-11
I'm guessing that you want to get rid of all your settings, yes?

In that case, go to synaptic manager (under administration), and search for gnucash. There should be an entry that has a green box next to it, meaning that it is installed. If you right click on it and click "completely remove", it will get rid of the old configuration files too. Then, it's just a case of installing it again using add/remove programs.

Hope that helps :D

David

---

### Post by donkyhotay on 2009-02-11
You could also try deleting the ~/.gnucash folder if it exists. Thats where most programs store user settings.

---

### Post by zacktu on 2009-02-11
I use Gnucash, but don't recall whether data files are also removed when you uninstall.  You might check to see whether they're still there.  Your new installation might still be reading your old data files.

---

### Post by LindaLou on 2009-02-12
Hi Davideotape,  yes, you are correct in saying that I want to get rid of all settings. 
I tried you instructions. However, when I installed gnucash again, the same information/data that I had originally entered appaered. In other words, I still don't have a "fresh" Gnucash, I'm still looking at the same data that I entered (e.g. Acounts Payable entries, Accounts Receivable entries, etc.)

---

### Post by LindaLou on 2009-02-12
Hi davideotape, yes, you are correct in saying that I want to get rid of all settings, all data (e.g.Accnts Rcv entries, Accnts Pybl entries, etc).
I did apply your instructions and unfortunately, when I reinstalled gnucash, the exact same entries/data appeared when gnucash opened.

Donkyhotay, I'm not familiar with how to delete the files that you mentioned. (still a newbie).  Would you give me step by step instructions on how to do this?

Thanks to all.

---

### Post by Neural oD on 2009-02-12
I haven't used gnu cash - but the settings **should** under ~/.gnucash - or something similar. Get into the terminal - type in:
 ls -a
hopefully you will see something like: .gnucash   - if it's there then type in this: 
rm -r .gnucash
that should do it for you

---

### Post by billgoldberg on 2009-02-12
> **LindaLou said:**
> I installed Gnucash via Add/Remove and after several days of working with the program decided that I wanted to start fresh, begin at the beginning. So, I got to Add/Remove and remove Gnucash that way.  I then go back and select the application for install.  Fine.  When I select Gnucash from Applications > Office, the exact same Gnucash appears - meaning, the one I removed and wanted to get ride of!  How do I remove the application and have a "fresh" Gnucash ready for use?

You can use the cli for that or synaptic.

```
sudo apt-get autoremove gnucash --purge
```

In synaptic, use "completely remove package".

---

### Post by geirha on 2009-02-12
Just to clarify here. When you use a GUI application, it will put all the data it needs to save inside your home-directory, usually in a hidden directory of the same name (~/.gnucash as mentioned) or under ~/.config/, another hidden directory. This is because applications normally only have write access to your home directory and /tmp (and /tmp as the name suggests is temporary. It gets wiped each time you boot).

Now, the package managers (add/remove, synaptic, apt-get, etc.) never touches your home directory, so the data stored in your home folder will not get removed, even if you purge the package.

Go to your homedirectory with nautilus, hit Ctrl+h to toggle showing hidden files, and look for .gnucash and .config/gnucash. If you find it, either delete it or rename it.

---

### Post by LindaLou on 2009-02-25
Hi All,

I followed billgoldberg's instructions re synaptic/Mark for complete removal.  I installed gnucash again,and was still looking at the same entries/work that I want to get rid off.  

I went back to Add/Remove and removed gnucash again and then followed geirha instructions for Home Directory/Nautilus.  I found the folder .gnucash and deleted it.  Did not find the .config/gnucash.

Installed gnucash again thru the Add/Remove. After I closed the info window a warning message appeared saying that it the home directory could not be found.  gnucash popped open. to a blank Account page.  I did not get the "wizard".  I am able to make entries. I did a search for customers and vendors and nothing came up. 

I await your comments.

---

### Post by Najmudin on 2009-02-25
I'm not sure but try to select: "File > New > New File" to start the wizard again , in case you already deleted the .gnucash folder in your home folder.
I hope that can help.

---

### Post by geirha on 2009-02-25
I installed gnucash, logged into the guest account, made a list of all files in the home-folder before running gnucash.
```

find ~ >/tmp/before.txt

```
Then I ran gnucash, got the wizard, went through the wizard and added some data, then I closed gnucash and made a list of the files in the home-folder again.
```
find ~ >/tmp/after.txt
```

Running a diff between the two showed that it in addition to adding configuration in .gnucash, it also stored some information in gconf
```
diff -u /tmp/before.txt /tmp/after.txt
```

To remove the configuration stored in gconf, you can run the following command:
```
gconftool-2 --recursive-unset /apps/gnucash
```

After running the above command, and removing ~/.gnucash, starting gnucash gave the wizard again as if it had never been run. There's no need to reinstall the package.

---

### Post by LindaLou on 2009-02-25
Thank you geirha!!!\\:D/  Wonderful!!  I followed your instructions - code and remove gnucash - and voile!!  New Gnucash and the Wizard!!  Greatly appreciated!!!:D

---

