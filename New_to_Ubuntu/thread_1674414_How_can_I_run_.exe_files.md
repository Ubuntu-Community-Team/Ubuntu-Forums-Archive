---
title: "How can I run .exe files?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by ajcurran94 on 2011-01-23
I downloaded Wine, but I still can't run the .exe file that I downloaded.

It gives me the following error:
The file '/home/alexander/Desktop/Modio/Modio.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Can someone tell me how I can run the file?

---

### Post by tgm4883 on 2011-01-23
> **ajcurran94 said:**
> I downloaded Wine, but I still can't run the .exe file that I downloaded.

It gives me the following error:
The file '/home/alexander/Desktop/Modio/Modio.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Can someone tell me how I can run the file?

Right click the exe, go to properties. Check the box next to executable

---

### Post by ajcurran94 on 2011-01-23
Thanks.  It still won't open though.  It doesn't give me any error message, but when I try to run it, nothing happens.

---

### Post by Vaphell on 2011-01-23
drop to terminal, wine is more talkative when launched there, maybe something important will be printed out.
simply highlight that /home/alexander/Desktop/Modio/Modio.exe and paste it with middle-click in the terminal window.

---

### Post by adeee on 2011-01-23
just paste this command in your terminal

sudo chmod 777 /path/to/your/file

/path/to/your/file means whereever your file is stored.

---

### Post by matt_symes on 2011-01-23
Hi

Is the exe on an NTFS or vvvvvvFAT partition?

Kind regards

---

### Post by jerrynewt on 2011-01-23
OOORRR after changing the .exe file to executable -- just right click on the file and choose "Open With Wine Windows Program Loader" and Wine will start it right up !! Good luck

---

### Post by ajcurran94 on 2011-01-23
I have no idea what that means, I still don't know how to use the terminal.

---

### Post by NightwishFan on 2011-01-23
If you marked the executable bit as instructed above (go to file properties etc) and the program still doesn't run, it likely is just not compatible with Wine (at least without work involved) it probably needs a missing DLL file or The VB C++ runtime. Short answer is, wont work, find an alternative. Long answer is look for some tutorials. Someone can probably help if you still have any specific questions.

---

### Post by adeee on 2011-01-23
> **ajcurran94 said:**
> I have no idea what that means, I still don't know how to use the terminal.

Go to Applications-->Accessories-->terminal

then paste this command

sudo chmod 777 /path/to/your/file

/path/to/your/file means whereever your file is stored. 	
for example

if your exaple.exe stored in desktop then command is 

sudo chmod 777 /Desktop/example.exe

after that run the file.

---

### Post by ajcurran94 on 2011-01-23
I tried that, but still nothing happens.  

Here is the command I used, tell me if i typed it wrong.

sudo chmod 777 /home/alexander/Desktop/Modio/Modio.exe

---

### Post by matt_symes on 2011-01-23
Hi

What is the name of the exe and where did you download it from?

Maybe someone will try to install it and then tell you the steps they took to install or why it did not install.

Kind regards

---

### Post by Vaphell on 2011-01-23
in terminal run
```
wine /home/alexander/Desktop/Modio/Modio.exe
```
there should be plenty of output - errors, warnings and stuff

---

### Post by xXQuadPolarXx on 2012-05-24
> **ajcurran94 said:**
> I downloaded Wine, but I still can't run the .exe file that I downloaded.

It gives me the following error:
The file '/home/alexander/Desktop/Modio/Modio.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Can someone tell me how I can run the file?

Why are you cheating on xbox anyway? Don't you know that when you get caught using 3rd party tools like modio you will be banned from xbox live?

On note of not being able to run exe files, not all exe files are compatible under Wine...

---

### Post by Mark Phelps on 2012-05-24
If you're talking about the tech game Modio, it's very likely that will not work  It's not listed at all in the WineHQ application compatibility database and games, in general, work very poorly, if at all, with Wine.

If you want specific support on gaming with Wine, you would do better posting in the Wine subforum than in this section.

---

