---
title: "Excuse my French"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Mariane on 2010-06-04
I bought my laptop in France with a US keyboard since then I have never been able to convince it that it is not French. 

sudo dpkg-reconfigure -phigh xserver-conf 
is an example among many. I tried it and it set the keyboard to France layout. Which is really weird. I restored the old xserver-conf. 

The "Desktop" icon is another example. I have both a "Desktop" icon and a "Bureau" icon, bureau means desktop in French. The corresponding folder is called "Desktop" but if I delete the "Bureau" icon it is recreated. 

It is not really a problem most of the time, but once my terminal started speaking French and I had to sort it out, and I have had problems with Open Office Calc because French people write their numbers differently. To say "1.2" they write "1,2". 

Somewhere deep inside, my laptop is convinced that it is French and has occasional bursts of patriotism. 

Any idea? 

Mariane

---

### Post by lavinog on 2010-06-04
Was ubuntu preinstalled?

---

### Post by Bachstelze on 2010-06-04
Probably a locale problem. What do you have under System > Administration > Language Support?

---

### Post by jnorthr on 2010-06-04
do all the characters on your keyboard map to the correct glyph ? Like US $ on ur kbd actually does print a dollar sign ? or do some of the keys print french glyphs ?

---

### Post by Mariane on 2010-06-04
Ubuntu was pre-installed. 
System-admin-langage has English
The keyboard is fine, a dollar is a dollar :) 

Mariane

---

### Post by sandyd on 2010-06-04
```

sudo apt-get remove language-pack-fr*
sudo apt-get install language-pack-en language-pack-en-base manpages
sudo dpkg-reconfigure locales
```and yeah... I didn't check, but im pretty sure the language code is fr...

---

### Post by Mariane on 2010-06-04
Aaargh! No, I meant something else, not the 
"System > Administration > Language Support"

I went to check this and it told me it was not installed properly. So I told it to install itself and I saw loads of French files coming in, Open Office help in French for example. I clicked "Cancel", which was ignored, so then I had to quickly switch off the computer manually before it could finish installing all these unwanted files - and probably reverting to French once again! 

As usually first it downloads and then it installs, I have some chance that no damage is done. I do hate it when the computer becomes convinced that it knows better than the user what it should be doing and so keeps on doing it even if the user tells it to stop. I'll switch it back on without networking options, so even if it tries to resume downloading French it won't be able to do it. 

Mariane

---

### Post by simosx on 2010-06-04
> **Mariane said:**
> Aaargh! No, I meant something else, not the 
"System > Administration > Language Support"

I went to check this and it told me it was not installed properly. So I told it to install itself and I saw loads of French files coming in, Open Office help in French for example. I clicked "Cancel", which was ignored, so then I had to quickly switch off the computer manually before it could finish installing all these unwanted files - and probably reverting to French once again! 

As usually first it downloads and then it installs, I have some chance that no damage is done. I do hate it when the computer becomes convinced that it knows better than the user what it should be doing and so keeps on doing it even if the user tells it to stop. I'll switch it back on without networking options, so even if it tries to resume downloading French it won't be able to do it. 

Mariane
> 
Actually the keyboard layout details are not tied to the language support settings.
What you need to do is fix the layout settings in System/Preferences/Keyboard/Layouts

You can also extract those settings and paste them here in order to help you. You extract the settings with command (use Applications/Accessories/Terminal to open a terminal window):

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

(disregard the above; I misread the title. If you want the French locale to work, you need to install the full localisation files for the language, then set the language to French).

---

### Post by Mariane on 2010-06-04
Carlee, thank you ever so much. 
After running your 3 commands I was able to let the system>admin>lang install itself and it did not try to download any French. 

Mariane

---

