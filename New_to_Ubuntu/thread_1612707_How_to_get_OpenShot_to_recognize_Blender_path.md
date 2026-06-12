---
title: "How to get OpenShot to recognize Blender path"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by DayLite on 2010-11-03
I installed the latest OpenShot Video Editor 1.2.2 to use 3D Animated Titles   It requires Blender. The stable version will not work so I downloaded the beta version and put it in my home folder. My problem is that I cannot get OpenShot to know the correct path.  I get this message when I want to use 3D animation.
> Blender, the free open source 3D content creation suite is required for this action ([http://www.blender.org](http://www.blender.org)).

Please check the preferences in OpenShot and be sure the Blender executable is correct.  This setting should be the path of the 'blender' executable on your computer.  Also, please be sure that it is pointing to Blender version 2.5 or greater.

Blender Path:
blender

Version Detected:
2.49

The version it detects is in my share folder. I don't understand how to get permission to move Blender 2.54 beta from my home folder to where it has to go for OpenShot to use it?

---

### Post by mgmiller on 2010-11-03
I had the same problem.  Uninstall the blender version from the repository.  You can leave the downloaded version in your home directory.  I have mine in ~/blender/blender-2.54.

In open shot,  go to Edit > Preferences and in the Blender executable box input your path.  Mine reads:  /home/marty/blender/blender-2.54/blender  Obviously, yours will not say marty, it will use your name.  I also found it did **no**t work if I just put it ~/blender/blender-2.54/blender.  I had to use the whole path as above.

---

### Post by DayLite on 2010-11-03
> **mgmiller said:**
> I had the same problem.  Uninstall the blender version from the repository.  You can leave the downloaded version in your home directory.  I have mine in ~/blender/blender-2.54.

In open shot,  go to Edit > Preferences and in the Blender executable box input your path.  Mine reads:  /home/marty/blender/blender-2.54/blender  Obviously, yours will not say marty, it will use your name.  I also found it did **no**t work if I just put it ~/blender/blender-2.54/blender.  I had to use the whole path as above.

I uninstalled the blender version in the repository, and did exactly what you told me and it still doesn't work.

---

### Post by mgmiller on 2010-11-04
Can you paste in here the path line you are using in OpenShot?  Also, please tell me where you have the blender 2.54 folder located.

---

### Post by DayLite on 2010-11-04
> **mgmiller said:**
> Can you paste in here the path line you are using in OpenShot?  Also, please tell me where you have the blender 2.54 folder located.

/usr/bin/openshot

/home/joan/blender25/blender

---

### Post by mgmiller on 2010-11-05
/usr/bin/openshot is the path to the openshot executable.  This is **not** the path that should be used in the blender executable box.

In the blender executable box, simply enter the path to the blender executable.  In your case..../home/joan/blender25/blender

The only other problem I can think of is that the last word in your path "blender" is a folder name rather then a file name.  The last blender should be the 50.8 MB blender executable file. 

Lets make sure it's a good path.  Can you post the output of the following command?
Open a terminal and paste in:
```
ls ~/blender25
```

---

### Post by DayLite on 2010-11-05
> **mgmiller said:**
> /usr/bin/openshot is the path to the openshot executable.  This is **not** the path that should be used in the blender executable box.

In the blender executable box, simply enter the path to the blender executable.  In your case..../home/joan/blender25/blender

The only other problem I can think of is that the last word in your path "blender" is a folder name rather then a file name.  The last blender should be the 50.8 MB blender executable file. 

Lets make sure it's a good path.  Can you post the output of the following command?
Open a terminal and paste in:
```
ls ~/blender25
```

This is the results:

```
joan@joan-desktop:~$ ls ~/blender25
blender-2.55-beta-linux-glibc27-i686
blender-2.55-beta-linux-glibc27-i686.tar.bz2

```[IMG]http://inlinethumb21.webshots.com/36372/2256372350056553245S600x600Q85.jpg[/IMG]


The installation instruction found in the 'ReadMe.html' instructs:
> [COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]**Linux, FreeBSD, Irix, Solaris: **Unpack the distribution, copy the .blender directory from it to your home directory. Then run the Blender executable.
Install scripts by putting them in the .blender/scripts inside your home folder.[/FONT][/FONT][/COLOR]

I don't understand it? When I click on the gears icon it launches Blender.

---

### Post by tock on 2010-11-05
I'm having the same issue. The 64 bit ver isn't available on the blender site so I found the repo at ppa:cheleb/blender-svn.  It installs ok and runs typing "blender" in the terminal but I get the same error with openshot.  I also tried /usr/bin/blender with the same results.

---

### Post by DayLite on 2010-11-05
> **tock said:**
> I'm having the same issue. The 64 bit ver isn't available on the blender site so I found the repo at ppa:cheleb/blender-svn.  It installs ok and runs typing "blender" in the terminal but I get the same error with openshot.  I also tried /usr/bin/blender with the same results.

We really need **help** from this forum.

---

### Post by tock on 2010-11-05
looks like we have to wait for openshot to update their program before blender 2.55 will work

---

### Post by DayLite on 2010-11-05
> **tock said:**
> looks like we have to wait for openshot to update their program before blender 2.55 will work

Why do you say that? Blender is the program that needs to get out of the testing stage, and get to the stable version.

This doesn't work, either: [https://answers.launchpad.net/openshot/+faq/1299](https://answers.launchpad.net/openshot/+faq/1299)

---

### Post by mgmiller on 2010-11-05
OK, I see your problem.  You are not pointing at the blender executable, you are one folder too high.Your path is not long enough.  Try using:
/home/joan/blender25/blender-2.55-beta-linux-glibc27-i686/blender

alternatively, just move everything in the  "blender-2.55-beta-linux-glibc27-i686" directory up one level into your "bender25" folder and use the shorter path I gave you earlier.

I am using version 2.54 of blender in 64 bit with no problems.

---

### Post by DayLite on 2010-11-05
> **mgmiller said:**
> OK, I see your problem.  You are not pointing at the blender executable, you are one folder too high.Your path is not long enough.  Try using:
/home/joan/blender25/blender-2.55-beta-linux-glibc27-i686/blender

alternatively, just move everything in the  "blender-2.55-beta-linux-glibc27-i686" directory up one level into your "bender25" folder and use the shorter path I gave you earlier.

I took everything out of the "blender-2.55-beta-linux-glibc27-i686"  and moved it to home/joan/blender25, then deleted the folder as nothing was left in it.

In the terminal it says no such folder or directory found. What is weird is that when I click on the blender25 folder and it opens, I find the (gear icon) and click on it and it opens the program. Yet I don't understand why it doesn't recognize it in the terminal?

I type in the terminal: home/joan/Blender25/blender

---

### Post by mgmiller on 2010-11-05
> I type in the terminal: home/joan/Blender25/blender....In the terminal it says no such folder or directory found.You are missing the leading/  you should be typing ```
/home/joan/Blender25/blender
```

That should work.
                                                                                                   

I suspect we are getting off track a bit.  Please also give me another screen shot of the output of 
```
ls ~/blender25 
```

---

### Post by DayLite on 2010-11-05
I got it to work by typing: blender25/blender

That's all

---

### Post by mgmiller on 2010-11-05
> I got it to work by typing: blender25/blender

It would depend on where your terminal was running from as to how it responds to commands.  The "correct" full path would be /home/joan/blender25/blender

Note the / at the beginning, it's very important that it be there.

Just type that whole thing into the blender executable box in OpenShot.  Make sure there is nothing else in that box first.  You have been trying different things in there, so delete anything else that's in the box before copying in the line above.

---

### Post by DayLite on 2010-11-05
> **mgmiller said:**
> You are missing the leading/  you should be typing ```
/home/joan/Blender25/blender
```That should work.
                                                                                                   

I suspect we are getting off track a bit.  Please also give me another screen shot of the output of 
```
ls ~/blender25 
```

[IMG]http://inlinethumb45.webshots.com/15020/2670553700056553245S500x500Q85.jpg[/IMG]

Now OpenShot recognizes it! :) Under preferences I typed in "blender25/blender"

I also checked under properties>permission>write (in every box)

---

### Post by mgmiller on 2010-11-05
Excellent news!  I suspect that is working because .openshot is also in your home directory.  The path I gave you, being absolute, rather then relative, should also work.

I hope Tock is following this thread as I suspect he has the same issue you did.

Enjoy OpenShot.  It's an amazing application.

---

### Post by mgmiller on 2010-11-05
> I also checked under properties>permission>write (in every box)The important thing here is that you had "Allow executing file as program" checked.

I would have gotten to that if you still had problems after the path was corrected.

---

### Post by DayLite on 2010-11-05
> **mgmiller said:**
> Excellent news! 
Enjoy OpenShot.  It's an amazing application.

I want to thank you very much for your support and effort to help me :smile:

---

### Post by mgmiller on 2010-11-05
You're very welcome.  That's why we get paid the big bucks around here...LOL

---

### Post by DayLite on 2010-11-05
> **mgmiller said:**
> You're very welcome.  That's why we get paid the big bucks around here...LOL

Money in itself has no value, friendship is priceless.

---

### Post by mgmiller on 2010-11-05
> **DayLite said:**
> Money in itself has no value, friendship is priceless.

How true.  You will find a lot of new friends here in the Ubuntu Forums.  I think it's one of the most helpful, friendliest sites around.

---

### Post by DayLite on 2010-11-05
:popcorn: **Success **

[http://www.youtube.com/watch?v=6HdwpGZCHE8](http://www.youtube.com/watch?v=6HdwpGZCHE8)

---

### Post by tock on 2010-11-08
I think my install is a little different.  I had to use the ppas to install the blender 2.55 because the site did not have the 64 bit version.  I don't see that I have a blender folder under my home folder (except for the .blender folder). This is what I get when running openshot in the terminal:

> pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
ImportError: No module named bpy_types
pyrna_srna_ExternalType: failed to find 'bpy_types' module
Traceback (most recent call last):
  File "/home/bryan/.openshot/blender/6a92df3e-eba9-11df-af44-000854348797/blur.py", line 23, in <module>
    import bpy
ImportError: No module named bpy
No frame was found in the output from Blender
Blender render thread finished



---

### Post by Blutack on 2010-11-10
I believe it's due to the PPA Blender having a broken site-packages path - the python modules are there under /usr/share/blender/2.55/scripts/ but they must be run via Blender's builtin python intepreter (i.e the blender --background -P script.py)
Unfortunately this won't be solved without a Blender update, as modifying the environmental variables of Blender doesn't solve anything.
So all in all, no animated titles on 64bit just yet! (Or at least until the PPA is updated, you build your own 64bit Blender or they put the official 64bit builds back!).

On an unrelated note, the new Blender is absolutely gorgeous!

---

### Post by arron on 2011-02-02
Not sure if this thread is still needed or not, excuse me if its old news.

After much time hitting my head off the keyboard i fixed some errors i was having, and had a lot to do with the versions of openshot and blender, and issues with the two working together.

I posted it here, hope it might help others out there, openshot is so awesome with blender!

[http://ubuntuforums.org/showthread.php?t=1674405&highlight=frame+found+output+blender](http://ubuntuforums.org/showthread.php?t=1674405&highlight=frame+found+output+blender)

---

### Post by raindog7 on 2011-05-14
THANK YOU!!!!!! It's working! =D>:guitar:\\:D/

---

