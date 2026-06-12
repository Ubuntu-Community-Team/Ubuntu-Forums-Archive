---
title: "Build common directory?"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by pensioner77 on 2010-04-12
I have a Canon Pixma ip4500 printer which does not operate fully with the driver already installed with Ubuntu,but I have found that Canon have a deb based driver available on the web. Therefore I am trying use the "CompilingEasyHowTo" information from Ubuntu help,but I am stuck quite early at the point where I am supposed to build a common directory, suggest as /usr/local/src . I do not know how I am supposed to do this!As an OAP novice any help would be appreciated.

---

### Post by ubername on 2010-04-12
If you have a .deb file, you don't need to compile etc. Clicking on it should start the installation.

---

### Post by e4uforums on 2010-04-12
This should create the directory for you:

```
sudo mkdir /usr/local/src
```

However, the .deb file works sort of like an .exe file does in Windows - just double click on the .deb and the installation should begin.  No compiling necessary  :)

---

### Post by pensioner77 on 2010-04-13
Thanks ubername & e4uforums, the problem is that the downloaded driver has 5 items --2 have a deb suffix and the other three have tar.tar. suffixes.The deb ones appear in the Synaptic Manager after double clicking but the others just say not a deb package!! I have also tried the command you recommended ( the mkdir one ) but obtained the message "command not found"

---

### Post by nothingspecial on 2010-04-13
Please go to the web page where you found the drivers and copy and paste the address here - the thing at the top of the screen that starts http://

I`ll have a look at it for you.

---

### Post by pensioner77 on 2010-04-14
Thank you "nothingspecial" the site is 
/software.canon-europe.com/products/0010484.asp
Thank you in nticipation.

---

### Post by nothingspecial on 2010-04-14
Ok sir. One of the tar files, cnijfilter-common-2.80-1.tar.tar,  is the same driver in source code format. You do not need to worry about that since you have the debs.

The other, guideip4500series-pd-2.80-1.tar.tar, is the manual.

To extract that copy and paste into the terminal
```

tar -xvf guideip4500series-pd-2.80-1.tar.tar
```

Get to it from your places menu, right click the extracted file (the one without tar.tar at the end) and choose to open it with firefox.

I`ve never had a printer problem so I don`t have much experience making them work. The instructions in the manual, and therefore the driver, are very old (in linux terms). They may not work.

One thing the manual does say, is that you have to install the deb files in the correct order. I don`t know weather or not you have done this. To make this easier for me and you, I`m now going to write aload of gobbldygook for you to copy and paste 1 line at a time into your terminal. Most of it is from the manual you just extracted.

 Drag all the files you have downloaded and extracted into your home folder.

```
cd
sudo dpkg -P cnijfilter-ip4500series
sudo dpkg -P cnijfilter-common
sudo dpkg -i cnijfilter-common_2.80-x_i386.deb
sudo dpkg -i cnijfilter-ip4500series_2.80-x_i386.deb
sudo service cups restart
```

Then in your menu go system > preferences > printing and see if Ubuntu recognises your printer.

---

### Post by pensioner77 on 2010-04-16
Thanks, "Nothingspecial" I have been trying to follow your instructions but now the Terminal refuses to accept my password. I only have two which I use for various applications and I have tried both unsuccessfully. I cannot understand it as I have to use it to download all the Updates. Also how do I access the Downloads window I am doing it by purposely downloading a PDF file. You alos mention seeing if my Printer is recognised, it is the default printer but the problem is that the driver used by Ubuntu,a universal one does not give the correct colours, far to dark, and the full range of details,eg.Ink levels,maintenance,set up options etc.,are not available which is why I am trying to install a dedicated driver. I have the full use on XP but I prefer to use Ubuntu when possible.

---

### Post by nothingspecial on 2010-04-16
> **pensioner77 said:**
> I have been trying to follow your instructions but now the Terminal refuses to accept my password.

You don`t see your password when you type it in the terminal. Just press the correct keys in order and hit enter.

---

### Post by pensioner77 on 2010-04-18
Again thanks Nothingspecial,but I am still in trouble.The first lines of your instructions were accepted in my Terminal but at cnjfilter-common-2.80-x_i386.deb. I received the statement no file or directory,then the message error ancountered while processing the file! In my Home Folder I have the following files shown.
guide 4500 series pd-2.80-1
guide 4500 series pd-2.80-1 tar.tar
faq-pd-2.80-1 tar.tar
cnifilter ip4500 series-2.80-1_i386.deb
cnifilter-common-2.80-1 tar.tar
cnifilter-common_2.80-1_i386.deb
I do not know if that helps?
As I have said my printer is recognised as the default and works under the Unix system,but this does not give me the full potential of my printer and especially not the correct colours.

---

### Post by nothingspecial on 2010-04-18
Loose the -x_ that doesn`t apply or just double click them. But you must click them in the correct order.

---

### Post by pensioner77 on 2010-04-19
Thankyou "nothingspecial" for your patience. I tried removing the-x_ but it still said it could not find the files or it was an incorrect command. So I doubled clicked on the deb. files in Home folder and they installed?? but the resultant printing was no different,far to dark if any colour is used.I will have to be resigned to only use the printer on the Linux partition for black & white and switch to the XP partition for any colour or ink status check etc.

---

### Post by nothingspecial on 2010-04-19
In that case, it may be better if you marked this thread - solved, which you can do, with the thread tools button.

After all, you now have the thing you wanted installing, installed.

But, like I said, I`m no expert on printers.

I`d start a new thread in hardware & laptops or general help, maybe someone with your printer (or a general printing geek) will see it.

Cheers.

---

