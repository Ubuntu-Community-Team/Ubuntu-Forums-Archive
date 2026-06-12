---
title: "how do you copy files to /usr/lib32"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-05-08
WHat is the terminal command. They are 32 bit debs.

---

### Post by scott-ian on 2011-05-08
You do not copy debs, you install them.  
sudo dpkg -i package.deb

---

### Post by TheManno1 on 2011-05-08
family@ubuntu:~$ sudo dpkg -i libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb
Is the command I used

dpkg: error processing libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb

---

### Post by frank604 on 2011-05-08
put file location in as well, like sudo dpkg -i /location/directory/of/file/debfile.deb

---

### Post by Paqman on 2011-05-09
You don't need to use the terminal to install .debs, just double click on them.

---

### Post by TheManno1 on 2011-05-09
There 32 bit files need to run pcsx2 on 64 bit ubuntu.

---

### Post by BrandonC19 on 2011-05-09
If you downloaded it from the net, you mat have to right click the .deb, select "Properties" then the "Permissions" tab and mark it as executable. Or just ```
chmod 777 /path/to/the/.deb
```

---

### Post by Paqman on 2011-05-09
> **TheManno1 said:**
> There 32 bit files need to run pcsx2 on 64 bit ubuntu.

Ah, in that case you do need to use the terminal, and you need to use the --force-architecture flag:
```
sudo dpkg -i --force-architecture /path/to/file
```

---

### Post by TheManno1 on 2011-05-09
libglew1.5_1.5.7.is.1.5.2-1ubuntu2_i386.deb what command to copy it there.

---

### Post by wep940 on 2011-05-09
Are you reading what is being posted?  Did you try Paqman's lastest suggestion?
 
If you have the .deb file in your home folder, the command Paqman shows would look something like this:
 
sudo dpkg -i --force-architecture ~/libglew1.5_1.5.7.is.1.5.2-1ubuntu2_i386.deb
 
As others have noted, you do NOT copy the .deb into the libs - you INSTALL a .deb and it puts it's files where they need to be.  Please, don't use the word COPY - try using the word INSTALL - as in I want to INSTALL the package named libglew1.5_1.5.7.is.1.5.2-1ubuntu2_i386.deb.
 
This is all sounding very much like some of your other posts - people are trying to tell you what to do, you don't seem to do it, then you ask questions that indicate you are still missing some of the fundamentals - try looking up on the net what a .deb file is and how it is installed in various linux distros.  Maybe then you'll understand what is being said.

---

### Post by TheManno1 on 2011-05-13
libwxbase2.8-0_2.8.11.0-0ubuntu8_i386  I have extracted it all now I have to do is place it in that area which requires sudo Is it possible to remove that area's restrictions for ever kinda ike windows.

---

### Post by Jesus_Valdez on 2011-05-13
Why aren't you reading the responses?

Deb aren't suppose to be extracted, they don't work like that.

---

### Post by wildmanne39 on 2011-05-13
> **TheManno1 said:**
> libwxbase2.8-0_2.8.11.0-0ubuntu8_i386  I have extracted it all now I have to do is place it in that area which requires sudo Is it possible to remove that area's restrictions for ever kinda ike windows.

Wow

---

### Post by wep940 on 2011-05-14
This is what we have fought in other posts by this OP about other game console emulators. I don't know if there is a language barrier or what, but they don't understand what is being told to them, they don't follow the advice, and are determined that their way is the way you do things. From past experience, telling this person to install the deb, as we all have been doing, is useless.
 
I have reported this OP in the past, not as bad posts, but rather hoping that someone in the official forum realm might be able to help them understand.
 
Myself and others in some of the other threads have strongly suggested this person lacks some of the basic understanding needed  to do things they are trying to do, and needed to gather a better general knowledge of Linux prior to attempting these things. That suggestion also goes nowhere. I'm sure they didn't do as I suggested and read the net for what a .deb is and how it is installed, or they wouldn't keep being so hard headed.
 
My suggestion: until this OP learns to follow the advice given, and do the steps given, we should no longer answer their threads. It's a harsh step, and one I hestitate doing, but they have shown this same behaviour in other threads. We try to help - they ignore it and demand we give them an answer on how to do it THEIR way.
 
I suppose I'll get reprimanded for this post, but dealing with this OP has shown to be just as frustrating here as in their older threads.
 
EDIT: I am pretty much a novice myself, so I'm not trying to be an expert. I just know from my experience that if I READ and FOLLOW the advice posted to me, things go ok. Refusing to do that and insisting things be your own erroneous way is setting you up for an ubuntu installation that has so much garbage put in so many erroneous places that eventually a reinstall will be needed. *PLEASE* FOR YOUR OWN GOOD FOLLOW AND DO WHAT PEOPLE ARE TELLING YOU - QUIT "FIGHTING" THINGS AND MAKING THINGS EVEN HARDER.

---

### Post by dwasifar on 2011-05-14
> **TheManno1 said:**
> libwxbase2.8-0_2.8.11.0-0ubuntu8_i386  I have extracted it all now I have to do is place it in that area which requires sudo Is it possible to remove that area's restrictions for ever kinda ike windows.

I don't know why I'm trying, having read the thread up to this point, but here I go anyway.

DO NOT copy the files you extracted from the .deb file to /usr/lib32.  In fact, you should delete the extracted files completely, and forget they existed.

DO NOT change the permissions on /usr/lib32 or any other system directory.

Instead, follow the advice that has already been offered you in this thread, which I will sum up for you again:

 - Find the full path to your deb file (I'll use the example /home/manno/Downloads/libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb, change this as needed for the actual path to the .deb file.)
 - Enter this command: **sudo chmod 777 /home/manno/Downloads/libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb** 
 - Then enter this command: **sudo dpkg -i --force-architecture /home/manno/Downloads/libwxbase2.8-0_2.8.11.0-0ubuntu8_i386.deb**

This will INSTALL the package and put all the files where they need to go.  YOU DO NOT NEED TO MANUALLY COPY ANY FILES TO THE SYSTEM DIRECTORIES.

---

### Post by wep940 on 2011-05-16
I'm sure that sometime in the not to distant future we will see another thread from the OP about yet another gaming emulator.  This thread marks the 3rd emulator that I know of that they have opened threads on.  I have no idea if they ever get the others to work, or if they give up because people are telling them how to do it but they don't agree, so they move on to yet another emulator.  
 
I also suggested to this user in the past that they post in the gaming and leisure forum to see if they might get more help there for these gaming emulators.  Since they have opened this thread here I would assume they haven't done that either.

---

