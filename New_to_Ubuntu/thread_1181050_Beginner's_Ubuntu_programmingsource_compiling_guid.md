---
title: "Beginner's Ubuntu programming/source compiling guide? &amp; various minor questions"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by nunu_ubu on 2009-06-07
Anyone have some recommendations for a beginners/basic level programming/source compiling guide?  Preferbly free, as I'm broke.  I'm very new to Ubuntu, ex Windows XP user - pardon me if my lingo is off. I'm using a Dell Mini 10, with Ubuntu 8.04.  I have read the warning about malicious argument lines, and have read up to Ch 7 of the beginner's guide in the sticky.

My specific problem is, when I'm looking for programs I usually find options such as sources or binary - and the last time I did anything with that was 10 years ago on an old Mac making math games using if-then statements.

So... I download the Hydrogen drum maching sources, extract the files, look thru them for some kind of installation auto exec file or even a guide.  All I find is a guide with command arguments I don't recoginize and try simply copying and pasting into the terminal, and all I get are error messages in return.

All I'm looking for are the basics - the essentials.  I don't want to know how to program my own drum machine from scratch, but I would like to know what arguments mean what, and know how to execute lines so the sources will be installed and I can use programs that exist outside of what the "Add/Remove Apps" tool allows.

Other minor questions - 

There is no Undo command anywhere!  Arg!  The touchpad on my Mini 10 is overly sensitive, and it has a tendency of thinking I want to click when really I just want to move the cursor.  I accidently put a file in the trash because of this and couldn't find it (my can was still saying it was empty until I actually opened it).  Kept looking for an Undo last action, but it wasn't anyplace I'm aware of.  Is there one hidden somewhere?  Anyone have a way of adding one to the OS?

Reviews or thoughts (or links to those) on Ubuntu Studio for use as a music making OS?

I've noticed I can still run some programs I've downloaded without actually installing (or registering, I supose) them in the system - they don't appear in the Apps or the Add/Remove Apps, but I can go to (what Windows calls) the exec file and it appears to run fine. Pros/cons of this?

Dells come with Ubuntu 8.04, and I've noticed 9 is out.  Would it be who of me to upgrade, or stick with the Dell factory build?

Thanks for any help!  Digging the simplicity, accessibility, and the features of Ubuntu over Windows, not to mention Ubuntu's philosophy on free software and community support!

---

### Post by michy99 on 2009-06-07
For the touchpad issue, there are programs which let you control the sensitivity. Try installing tpconfig.```
sudo apt-get install tpconfig
```Or search for it in Synaptic Package Manager and install it from there.

As for compiling from source, the problem you usually run into are other packages that need to be installed first. Often you can tell what you need by the error messages you get. If you post your error messages here I will try to fix you up.

---

### Post by oldos2er on 2009-06-07
Just FYI, Hydrogen's in the repositories:
```
sudo apt-get install hydrogen hydrogen-drumkits
```

---

