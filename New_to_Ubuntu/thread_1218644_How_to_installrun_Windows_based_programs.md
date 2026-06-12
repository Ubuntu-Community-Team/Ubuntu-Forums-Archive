---
title: "How to install/run Windows based programs"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by carmacksm on 2009-07-20
How do you install/load windows based programs in Ubuntu?

---

### Post by Ad88Ab99 on 2009-07-20
go to applications>add or remove
search for wine click on it and choose apply
now u can install windows application the way u normally do in windows, and they will be located in application>wine and click on the word/icon to run it
most, but not all windows application will run on linux, if you want games, then wine might not work

---

### Post by Volt9000 on 2009-07-20
Although you *can* install and run Windows applications in Linux, your degree of success will vary greatly.

Check out [http://www.winehq.com](http://www.winehq.com) and you can search for the software you want to install.

---

### Post by .Zero. on 2009-07-20
so does this mean that linux may get attacked by Viruses?

---

### Post by mynameinc on 2009-07-20
> **.Zero. said:**
> so does this mean that linux may get attacked by Viruses?

No... Wine Is Not an Emulator.

---

### Post by llamabr on 2009-07-20
Wine is so rarely the correct answer.  What is it you want to do with a windows program.  Often, with a bit of searching, or by asking us, you can find a native application that will do what you want, and that will work more successfully than trying to mess with wine.

---

### Post by Zero++ on 2009-07-20
If you really need a windows program you could install [Sun Virtual Box]("http://ubuntuforums.org/www.virtualbox.org/"), install Windows in the virtual box and install the program.

---

### Post by SunnyRabbiera on 2009-07-20
> **.Zero. said:**
> so does this mean that linux may get attacked by Viruses?

No, even though windows viruses can be run in wine (and people have done it on purpose to see how far a virus can go) its easy enough to avoid.
Linux is practically bulletproof against windows viruses though.

---

### Post by Serdal22 on 2009-07-20
Dear Friends,
 
First of all I would like to thank all of you for your precious time to help and enlighten us. I am grateful to you, indeed:popcorn:.
 
I used to download wine applications either deb or tar or rpm via some p2p wbesites. I have tried to do so to give Ubuntu 9.04 or 9.10 a try but no success:(. I visited winehq.org website, then clicked on Ubuntu, then I got lost. I read everything to be able to download Wine for Ubuntu 9.04 but no success:confused:. Could you please paste the download page's website so I can download Wine for Ubuntu 9.04?
 
I used the live version of same Ubuntu and tried to find Wine in the menu but I couldn't find it:(.
 
Any help will be appreciated greatly, and thanks in advance:D.
 
Serdal

---

### Post by llamabr on 2009-07-20
winehq, as I understand it, just tells you which programs work with wine.

To install wine, try:

```
sudo apt-get install wine
```

from the terminal

---

### Post by SunnyRabbiera on 2009-07-20
it should be as easy as following the instructions:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

DONT INSTALL WINE LIKE A WINDOWS APP!
I know its a hard habit to break but use the repository instruction, its simple enough.

---

### Post by Serdal22 on 2009-07-20
Dear Llamabar,
 
Thank you very much for your prompt reply. I am not very familiar with terminal. As far as I understand, I will open terminal, and those are the texts I will type, then hit enter. Am I correct?
 
Thank you once again.
 
Serdal

---

### Post by Serdal22 on 2009-07-20
Dear SunnyRabiera,
 
Thank you very much for your reply and info. All right, I will try winehq website again and will try to read the instructions once more. I hope this time I can do it. 
 
Regards,
 
Serdal

---

### Post by SunnyRabbiera on 2009-07-20
Just keep in mind: a lot of posters here will give out terminal instructions, i try to provide GUI instructions when possible.

---

### Post by eriqjaffe on 2009-07-20
> **Serdal22 said:**
> As far as I understand, I will open terminal, and those are the texts I will type, then hit enter. Am I correct?Correct.  You will also be prompted for your password - simply use the same password you use to log in to Ubuntu.  Just as a note, you will not see any characters appear on the screen while you type your password - this is by design, so don't worry about it.

---

### Post by Serdal22 on 2009-07-21
Dear Sunny Rabbiera and Eriqiaffe,
 
Thank you very much for the info and replies. 
 
All right, I had used the terminal before with some other (Suse and Fedora Core 4) Linux distros. So I will be able to open and type the text as Llambr had mentioned, then click on enter key. 
 
And also I will try again to pick the wine application in the system->Admin->add softwares menu if I can not succeed in the terminal mode.
 
Please forgive me if my replies delay since I don't have internet connection at home anymore. But I will check and reply your valuable posts and replies as often and fast as I can.
 
Very best regards,
 
Serdal

---

### Post by Mark Phelps on 2009-07-22
You might be able to save yourself a LOT of problems if you simply go to the CodeWeavers link provided and do a search on the applications you want to run. If you get a response indicating there are no results, that means they have NOT been tested and therefore, are most likely NOT to work.  If you get ratings of Platinum or Gold, you'll be OK; otherwise, you're wasting your time installing Wine.

BTW, if you're primary motivation in using Ubuntu is to run MS Windows programs, you're most likely going to be sadly disappointed with your Wine-based experiences.

---

