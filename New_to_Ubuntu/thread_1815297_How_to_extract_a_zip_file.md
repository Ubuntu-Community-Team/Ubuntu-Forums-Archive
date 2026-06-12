---
title: "How to extract a zip file?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-07-31
I'm trying to load the driver for my Lexmark x6650 printer from the Lexmark website but they are asking me to "extract the zip file"? See below.  How do I do this????



A. RUNNING THE GUI INSTALLER SCRIPT IN THE TERMINAL
Open up your favorite terminal (xterm, konsole, gnome-terminal, etc)
Extract the zip file
Use the following command to install the driver 
#./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
Follow the instruction in the installation screen.

B. RUNNING THE GUI INSTALLER SCRIPT
Do not attach the printer via USB to the Linux machine.
Extract the zip file.
lexmark-inkjet-[xx]-driver-[x.x.x].i386.deb.sh
Run the installer script file by double-clicking on the file icon and then click the "Run in Terminal" button or run the script file via command-line.
Follow the instructions in the installer screen.

---

### Post by 3rdalbum on 2011-07-31
Double click the file you downloaded. It will open in Archive Manager. Click the Extract button and specify a location to save it to.

---

### Post by Rasa1111 on 2011-07-31
Double click the .zip file.

It will open.

Click the "extract" button, Specify where you want it to be saved to.

Close.

Done.

edit: oops, didnt even see 3rd albums post. lol. d'oh!

---

### Post by amjjawad on 2011-07-31
Right Click on your file and choose "Extract Here" - See the attached Screenshot.

---

### Post by beew on 2011-07-31
> **amjjawad said:**
> Right Click on your file and choose "Extract Here" - See the attached Screenshot.

If you want to choose the destination to extract to, click instead Open With Archive Manager and then choose Extract.

---

### Post by JacquesPotter on 2011-07-31
Thanks. That got me where I need to be. I have come up with another problem. When I run through the lexmark tutorial it asks for my admin password but it's saying that Im providing the wrong one. I'm not. I've tried it several times and made sure the caps lock was off and the num lock was on. Still no go. Any suggestions?

Please let me know if I need to start a new thread. Thanks.

---

### Post by Rasa1111 on 2011-07-31
ohh man, I didnt even pay attention to it being a Lexmark. 

To be honest..
I have never gotten a lexmark working properly in Ubuntu/Linux , (though many people have) *So it can be done..*
Ive just never had success with it. 

But other printers, like HP's and such..
Ive never had a problem with..
they all work right out of the box, no need for drivers, install discs, or anything else. 

Guess I've only attempted to get 2 different Lexmark printers working on Linux..
But I failed both times, miserably. lol

I have read many success stories from people getting a lexmark going though,
So please don't let me comment put you off , Just sharing my personal experience with them. 

It would probably be best to start a new thread for it if you don't get it figured out. 
Simply because you'd probably get more help that way. 

Good luck, Hope you get it going!

---

### Post by AlphaLexman on 2011-07-31
> **JacquesPotter said:**
> I have come up with another problem. When I run through the lexmark tutorial it asks for my [COLOR="Red"]admin[/COLOR] password but it's saying that Im providing the wrong one. I'm not. I've tried it several times and made sure the caps lock was off and the num lock was on. Still no go. Any suggestions?
In your original post, the command was preceeded by a '**#**' prompt, which means you need to be the '**root**' user, not just have '**root priviledges**'. The 'sudo' command does the latter whereas 'su -' does the prior.

Switch or login to 'root' and try again.

Good Luck!

---

### Post by sunwatt on 2012-03-21
I followed this thread, and tried the manager, the extract button is not active.

I right clicked my zip file selected extract here, and it gives me this error message.

Ubuntu 11.10, System76 Starling

Help please.

Thanks

Jim

---

### Post by Perfect Storm on 2012-03-22
> **sunwatt said:**
> I followed this thread, and tried the manager, the extract button is not active.

I right clicked my zip file selected extract here, and it gives me this error message.

Ubuntu 11.10, System76 Starling

Help please.

Thanks

Jim

What error did you get?

---

### Post by sunwatt on 2012-03-22
I uploaded a screenshot, it showed it was there, but its not.

Trying again

And also pasting


7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /home/jim/Downloads/wit.zip: Can not open file as archive

Errors: 1

---

### Post by Perfect Storm on 2012-03-22
> **sunwatt said:**
> I uploaded a screenshot, it showed it was there, but its not.

Trying again

And also pasting


7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /home/jim/Downloads/wit.zip: Can not open file as archive

Errors: 1

You need to download a 'plugin' to open/extract 7zip files.
Either search in Ubuntu Software Center for p7zip or download it via the terminal:
```
sudo apt-get install p7zip-full
```

---

### Post by sunwatt on 2012-03-22
Thank you.

Ok did the bash, got this error


7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /home/jim/Downloads/wit.zip: Can not open file as archive

Errors: 1

---

### Post by Perfect Storm on 2012-03-23
Try:
```
cd ~Downloads
7z x wit.zip -o wit
```

---

### Post by sunwatt on 2012-03-23
I missed something....

jim@jim-Starling-Netbok:~$ cd ~Downloads
bash: cd: ~Downloads: No such file or directory
jim@jim-Starling-Netbok:~$ 


Help please

---

### Post by nothingspecial on 2012-03-23
```
cd ~/Downloads
```

---

### Post by sunwatt on 2012-03-23
jim@jim-Starling-Netbok:~$ cd ~/Downloads
jim@jim-Starling-Netbok:~/Downloads$ 7z x wit.zip -o wit


Error:
Incorrect command line
jim@jim-Starling-Netbok:~/Downloads$

---

### Post by oldos2er on 2012-03-23
When you're in the ~/Downloads folder, could you run ```
unzip -t wit.zip
``` and post the output? Just wondering if the zip file is corrupt.

---

### Post by sunwatt on 2012-03-23
Thank you for your patience!

jim@jim-Starling-Netbok:~$ cd ~/Downloads
jim@jim-Starling-Netbok:~/Downloads$ unzip -t wit.zip
Archive:  wit.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of wit.zip or
        wit.zip.zip, and cannot find wit.zip.ZIP, period.
jim@jim-Starling-Netbok:~/Downloads$

---

### Post by ranger1021994 on 2012-03-23
Even i think that the zip maybe corrupt...
GUI normally does all d work..so dat u can escape terminal stuff.. :) :)

---

### Post by oldos2er on 2012-03-23
> **sunwatt said:**
> jim@jim-Starling-Netbok:~$ cd ~/Downloads
jim@jim-Starling-Netbok:~/Downloads$ unzip -t wit.zip
Archive:  wit.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of wit.zip or
        wit.zip.zip, and cannot find wit.zip.ZIP, period.
jim@jim-Starling-Netbok:~/Downloads$

I think you should try downloading the file again.

---

### Post by Mark Phelps on 2012-03-24
Sometimes you get that same error message if the archive is password protected and you don't supply the proper password.

---

