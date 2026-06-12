---
title: "Changing the date format in Mozilla Thunderbird"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by pauloz on 2011-01-19
Hello there.

I've just recently installed ubuntu 10.10 on my netbook and I'm trying out Mozilla Thunderbird mail to see if it's OK.

I noticed the date format is defaulted at mm/dd/yyyy but I want to change it to dd/mm/yyyy. I've looked on the internet but instructions I've read on some sites are not clear.

Can anybody help me please?

---

### Post by ajgreeny on 2011-01-19
I think this is all sorted by the system wide locale and timezone settings you have set.

Where are you, and what settings do you have in other places like the panel calendar and date fields in OpenOffice?

---

### Post by pauloz on 2011-01-19
I'm in Australia and the timezone settings have been entered accordingly. I'm not sure what you mean by the date fields in OpenOffice - I didn't think that would have any bearing. 
Thanks.

---

### Post by pauloz on 2011-01-19
I'm in Australia and the timezone settings have been entered accordingly. I'm not sure what you mean by the date fields in OpenOffice - I didn't think that would have any bearing. 
Thanks.

---

### Post by ajgreeny on 2011-01-19
Check which thunderbird-locale package you have with the package manager.  It sounds as if it's the **en-us** version.  If so add the **en-gb** version, and then remove the en-us.

---

### Post by pauloz on 2011-01-19
Hello again. I went into Synaptic Package Manager and selected English (GB) Language Pack 3.1.99. It is now displaying in Mozilla Thunderbird if you go to Tools>Add-ons>Languages BUT I seem to be going around circles trying to install it. Also, there is no option to remove the en-us version. Any step-by-step help would be appreciated thanks.

---

### Post by ajgreeny on 2011-01-20
If it shows like that in Add-ons, it is already installed.

If you still have the US version showing there as well, click on it and choose "Disable" or simply use synaptic to remove the en-us version of the locale.

---

### Post by pauloz on 2011-01-21
The US version is not showing in Add-ons plus there is no option available to remove the en-us version in the locale. But the date format is still American! Looks like I may have to live with this or use another email client. Thanks for your time.

---

### Post by TopEnder on 2011-01-21
pauloz, Is your time & date format correct on your Desktop (top right).

---

### Post by lotus@terminal on 2011-01-21
You can change the format of your date via the terminal by doing the following,


You need to customise your current locale (en_IE in my  case).  To do this, change directory to /usr/share/i18n/locales.  Here  you will find many locales for many regions.  Choose the locale you wish  to customise and copy it by executing:

 ```
sudo cp en_IE custom
```Next chose the date or time format string you would like.  In my  case it will be &#8220;%d.%m.%Y&#8221;.  You can check and modify this string using  the date command, as in:

 ```
date +%d.%m.%Y
``` If this returns the date in the format you would like, then you know  you have the right format string.  You can find all format codes if you  use &#8220;man date&#8221;.
 The date format string, is specified in the locale file using a  Unicode notation.  Open your custom locale using your favourite text  editor:

 ```
sudo gedit custom
``` The date format is specified on the line beginning &#8220;d_fmt&#8221;, and looks like:
 d_fmt  "<U0025><U0064><U002F><U0025><U006D><U002F><U0025><U0079>" 

You will now have to convert your date format string to Unicode.  You  can do this, by looking up the Unicode equivalent for each character on  [http://asciitable.com/](http://asciitable.com/).  In this  way &#8220;%&#8221; becomes &#8220;<U0025>&#8221;, &#8220;d&#8221; becomes &#8220;<U0064>&#8221;, &#8220;.&#8221;  becomes &#8220;<U002E>&#8221;, and so on.  Replace the d_fmt line with your  new format string:

 d_fmt   "<U0025><U0064><U002E><U0025><U006D><U002E><U0025><U0059>" The same process can be used to modify the datetime format (d_t_fmt),  date format (d_fmt), time format (t_fmt), am and pm format (am_pm), and  standard 12 hour notation (t_fmt_ampm), as well as other locale  settings.

 Save and exit your text editor.  You now have a custom locale in the  file &#8220;custom&#8221;.  In order for the system to use it, you need to compile  it into a system readable locale definition.  This can be done using the  locale compiler by executing:

 ```
sudo localedef -f UTF-8 -i custom custom.UTF-8
```Now the new custom locale is available to the system, you need to  configure the system to use it.  Do this by editing the file  /etc/environment (sudo gedit /etc/environment) and adding (or modifying)  the line:LC_TIME="custom.UTF-8" 

All that remains is to log out and log in again, or restart any system services, to see the new format being applied.

Hope this solves your problem. :)

---

### Post by pauloz on 2011-01-22
Thanks lotus@terminal - that's a lot to do just to change the date format! Anyway, I'll have a go in the next couple of days. Thanks TopEnder for your comments too - the time and date format appear OK on my Desktop. I certainly appreciate all the replies I've received.

---

### Post by rotave on 2011-01-29
Not sure if you've fixed this or not, but I was having the same issue with Thunderbird. The easiest way to fix this is make sure when you login to Gnome that you've selected the correct language for your location/user. If you've set Ubuntu to auto login, then just logout and choose your correct language, then log back in and Thunderbird should have the correct date format.

---

### Post by pauloz on 2011-02-01
Appreciate your response rotave but I decided to ditch Thunderbird. With all due respect, there are plenty of novices, like myself, who use this forum but replies are often too vague or unclear - simple step by step instructions are what we newbies seek. I think there is an assumption among the more trained, gifted, talented, intelligent (call it what you like) that anybody who uses this forum is expected to have a basic understanding of Linux. Well, that certainly is not the case with me (who came straight from Windows) and I suspect plenty of others. It can be very frustrating and I only hope there are people out there who understand this and are prepared to be empathetic in their postings and give simple step by step guidance. If that is the case, Linux will deservedly go from strength to strength. Cheers.

Addendum

1st May 2011 i.e. 1/5/2011!! It's been a few months but after all the huffing and puffing of the above comments, it's just a simple matter of going into System>Administration>Language Support and going into both tabs and install/amend to the local language i.e. in my case English (Australia) and voila! It works! Remember folks - STEP BY STEP instructions for us newbies!

---

### Post by Thad E Ginathom on 2012-12-26
pauloz, I am far from new to Linux, and spent a  decade or two as a Unix systems manager (although I got lazy after retirement and forgot most of it). You may be pleased to know that it was your post that fixed this problem for me! Thanks :)

---

