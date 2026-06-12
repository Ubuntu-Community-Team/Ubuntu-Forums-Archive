---
title: "installing Google Earth (a rather n00b question)"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by mystik_spiral on 2010-03-13
I use this site to guide me:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth)

Trying to install Google Earth. I copied past the two first set of codes individually and packages opened up and yadda yadda.

now in the terminal, it says: You can now install the package with e.g. sudo dpkg -i <package>.deb

I lastly copy/pasted into the terminal: sudo dpkg -i <package>.deb ...and it says "No such file or directory"

please advise.

thanks!

---

### Post by Jarmen_Deffs on 2010-03-13
I just downloaded it through my browser, and double clicked on the file to install....[http://earth.google.com/intl/en/thanks.html#os=linux](http://earth.google.com/intl/en/thanks.html#os=linux)


Are you actually entering "<package>" into the terminal?  Anything surrounded by <> is meant as a variable for you to fill.  In this case it meant the name of the .deb file.

Eg: sudo dpkg -i myGoogleErthFile.deb

---

### Post by mystik_spiral on 2010-03-13
dpkg: error processing myGoogleErthFile.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 myGoogleErthFile.deb

---

### Post by howefield on 2010-03-13
> **mystik_spiral said:**
> No such file or directory

Substitute myGoogleErthFile.deb with the actual name of your package...

---

### Post by mystik_spiral on 2010-03-13
additionally, when I click on your link, a window opens up it saying:

This link needs to be opened with an application. Choose application. I have nothing to choose from. I just installed Ubuntu days ago. Looks like I need an application to help me install things?

---

### Post by achase79 on 2010-03-13
Just double click on the .deb file you downloaded or right click and select gdebi

This is the gui version of installing individual packages.  Another way would have been to add the medibuntu repositories by going to [http://medibuntu.org]("http://medibuntu.org") and following their instructions.  Then you could install it using software center

---

### Post by Jarmen_Deffs on 2010-03-13
I put the "Eg" there because it was just an_ example_.  I don't actually know the name of the file.

You can see the OS trying to tell you the problem: "no such file or directory" - in other words, you got the file name wrong.

I assume the file has been downloaded to your home directory, have a look there, or just follow the link I posted in your browser, and that will download an install file to whereever your browser downloads to by default (check where in the browser preferences).

---

### Post by ankspo71 on 2010-03-13
Hi,
Is it a bin file? I'm asking because when I go download it from the above links, it  automatically downloads me a file with a .bin extension. 
If it is a bin file you you can open a terminal and type:
```
sh ./GoogleEarthLinux5.1.3533.1731.bin
```
(providing you are using the terminal in the correct directory)
When asked to accept the license, use the tab key to switch focus to the  OK button.
Hope this helps.

---

### Post by Jarmen_Deffs on 2010-03-13
> **mystik_spiral said:**
> additionally, when I click on your link, a window opens up it saying:

This link needs to be opened with an application. Choose application. I have nothing to choose from. I just installed Ubuntu days ago. Looks like I need an application to help me install things?

?
Weird...
Are you using firefox?  I get a dialogue box that lets me save the file.

---

### Post by mystik_spiral on 2010-03-13
it's a .bin file.

it downloads in a firefox window, I open it up and that's when it asks me to select an application to open the file with.

---

### Post by mystik_spiral on 2010-03-13
> **ankspo71 said:**
> Hi,
Is it a bin file? I'm asking because when I go download it from the above links, it  automatically downloads me a file with a .bin extension. 
If it is a bin file you you can open a terminal and type:
```
sh ./GoogleEarthLinux5.1.3533.1731.bin
```(providing you are using the terminal in the correct directory)
When asked to accept the license, use the tab key to switch focus to the  OK button.
Hope this helps.
sh: Can't open ./GoogleEarthLinux5.1.3533.1731.bin

---

### Post by NightwishFan on 2010-03-13
Right click the file, go to permissions and allow it to execute as a program. You could also add the medibuntu repository and just install google earth from the package manager.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After you allow it to run as a program you can do this command. (I advise medibuntu, but if you want to use bin file)
```
./GoogleEarthLinux5.1.3533.1731.bin
```

---

### Post by Jarmen_Deffs on 2010-03-13
> **mystik_spiral said:**
> it's a .bin file.

it downloads in a firefox window, I open it up and that's when it asks me to select an application to open the file with.

Ok, that's not the same as "when I click on your link it says you need an application..."etc

So you 've given up looking for the .deb file and have downloaded the .bin file?
If so, do what someone else just posted: go to the directory with the .bin file in terminal, and type "sh ./GoogleEarthLinux.bin"  <--but make sure this filename is correct, or it won't work!

---

### Post by ankspo71 on 2010-03-13
Where is the file now? On your desktop? Download Folder? 

Use these commands to get to the correct folder

cd Desktop

cd Downloads

then when you are in the right folder, try that sh command again.
hopefully it will work this time.

---

### Post by Jarmen_Deffs on 2010-03-13
> **mystik_spiral said:**
> sh: Can't open ./GoogleEarthLinux5.1.3533.1731.bin

Same story. Don't just blindly copy and paste. GoogleEarthLinux5.1.3533.1731.bin was the name of his file, mine is GoogleEarthLinux.bin, check yours and use the correct filename. (and make sure the terminal is in the correct directory, of course)

Enter "ls" into the terminal to see the files in the current directory.

---

### Post by NightwishFan on 2010-03-13
Read my post above, also as mentioned here, make sure it is the correct file name. You can autocomplete names using the tab key. Also, after you make it as executable, try just clicking it in the file manager and hitting run.

---

### Post by ankspo71 on 2010-03-13
Jarmen Deffs is right. I double checked. Ignore the version number I posted. Make sure you type the filename exactly as you see it on the file you have downloaded.

Sorry, I gave you the filename to my version on accident rather than the filename from the link. (I always tag on version info into the filenames of all my downloads)

---

### Post by mystik_spiral on 2010-03-13
> **NightwishFan said:**
> **Right click the file, go to permissions and allow it to execute as a program.** You could also add the medibuntu repository and just install google earth from the package manager.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After you allow it to run as a program you can do this command. (I advise medibuntu, but if you want to use bin file)
```
./GoogleEarthLinux5.1.3533.1731.bin
```
The file is already allowed to be executed. I'll try your other link later.

Sorry, it looks like I asked at a bad time as I have to go to work pretty much right now. I'll try out all of your ideas later.

Thanks!

---

### Post by mystik_spiral on 2010-03-13
> **Jarmen_Deffs said:**
> Same story. **Don't just blindly copy and paste. **GoogleEarthLinux5.1.3533.1731.bin was the name of his file, mine is GoogleEarthLinux.bin, check yours and use the correct filename. (and make sure the terminal is in the correct directory, of course)

Enter "ls" into the terminal to see the files in the current directory.
Sorry. I am in a rush, which is why I'm not really thinking and trying to get this done as quickly as possible.

I'll be back tomorrow. thanks all

---

### Post by mystik_spiral on 2010-03-14
> **Jarmen_Deffs said:**
> Ok, that's not the same as "when I click on your link it says you need an application..."etc

So you 've given up looking for the .deb file and have downloaded the .bin file?
If so, do what someone else just posted: go to the directory with the .bin file in terminal, and type "sh ./GoogleEarthLinux.bin"  <--but make sure this filename is correct, or it won't work!
Now that I'm not in a rush to go to work, I can finally take the time to read over responses here, most notably this smart *** remark seen here. This is the first time I've used a Linux OS **in my life **so some of you need to put your egos in check and not get all agitated because a newbie doesn't quite know what he's doing yet.

So I found the actual file name in the terminal by typing in "ls": googleearth_5.1.3533.1731+0.5.6-1_i386.deb. Supposedly, it's in my desktop but I do not see it there at all.

I'm supposed to be working with the .deb file now as opposed to .bin file, right? i've received a variation of responses here and don't know what i'm doing. This is my first attempt at downloading anything using Ubuntu before, so I would appreciate if the hostility was lowered a bit and any pretentious jerks avoided this thread entirely. 

thank you

---

### Post by 1991sudarshan on 2010-03-14
did  you switch to directory where the .deb file is present?

---

### Post by mystik_spiral on 2010-03-14
Got it. thanks.

---

### Post by NightwishFan on 2010-03-14
Did you get it to work?

---

