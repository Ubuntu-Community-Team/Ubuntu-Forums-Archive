---
title: "path script?"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-09
Ok I tried to search for this one but im at work using my phone and it wont let me use the search forum option, either way my question is that I use adb and sdk programs to push files to my droid x .....I need a script to point the path of my tools folder to get it to work properly ....the tools folder is inside a folder called android in my home directory ....what would the layout of the script be to change the path of this folder ...I use the sdk/tools in terminal if that helps.

---

### Post by gmenfan83 on 2010-12-09
This is what it would look like in windows ...would it be the same for linux?

cd c:android/tools/

---

### Post by m_duck on 2010-12-09
I'm not entirely sure what you are asking? Is it that you have the android tools in ~/android/tools and would like to be able to use adb for example by typing in only ***adb***, instead of having to type the full path?

If that is the case, add something like the following to your ~/.bashrc```
export PATH=$PATH:$HOME/android/tools
```This will add the android tools directory to your $PATH so that you can use the tools within it without typing their full path. You will need to either log out and in again or run the following from a terminal before the change will take effect:```
source ~/.bashrc
```

---

### Post by gmenfan83 on 2010-12-09
> **m_duck said:**
> I'm not entirely sure what you are asking? Is it that you have the android tools in ~/android/tools and would like to be able to use adb for example by typing in only ***adb***, instead of having to type the full path?

If that is the case, add something like the following to your ~/.bashrc```
export PATH=$PATH:$HOME/android/tools
```This will add the android tools directory to your $PATH so that you can use the tools within it without typing their full path. You will need to either log out and in again or run the following from a terminal before the change will take effect:```
source ~/.bashrc
```

That is what I was looking for ....adb is already there and recognized I have that part down ....in order to push / install files you have to place them in the tools folder then open terminal type adb then set the path of what your trying to push/install through tools ....I am sorry if I confused anyone as I am confusing myself but in short I believe your script will work ....thank you

---

### Post by m_duck on 2010-12-09
The file that your pushing can be wherever you like, as long as you know where it is. So for example if for some reason I wanted to push somefile.txt from my Documents folder on my computer to a folder called foo on my phones sdcard, the following should work:```
adb push ~/Documents/somefile.txt /sdcard/foo/
```As long as the sdk tools folder is in your $PATH as outlined above, this should work. If it isn't, you would have to do:```
/home/gmenfan/android/tools/adb push ~/Documents/somefile.txt /sdcard/foo/
```

---

### Post by gmenfan83 on 2010-12-09
Thank you for clearing this up for me ...I have searched and either could not understand the answer or could not find it ...thanks

---

