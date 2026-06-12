---
title: "Intrepid 8.10 Printer problems"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-03-07
Further to my request for help in getting my printer working ( see below ) I have gone back over recent threads and found this is not an isolated problem , in fact there are several related requests for help .
Is this since a recent update ? If so should I report it ?

---

### Post by johnjohn2 on 2009-03-07
there is nothing hear which states what printer you are using

---

### Post by ivanvajar on 2009-03-07
What printer are you trying to install?

---

### Post by ex-wirecutter on 2009-03-08
Before the recent update I already had my HP deskjet 3822 running perfectly , with the small picture of a printer in the top right hand corner , but now I can't get the cups scheduler to run and it's missing from admin services and when I try to connect to local host , I get connect encrypt failed .

---

### Post by ivanvajar on 2009-03-08
Did you look at:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by ivanvajar on 2009-03-08
Did you look at:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I know for sure that HP DeskJet 3822 is supported by HPLIP => 0.9.5

---

### Post by ex-wirecutter on 2009-03-08
I have just transferred to another computer which also has Intrepid 8.10 and my printer works fine on that , but it hasn't been updated . I feel sure it's something to do with a conflict between cups and cupsys since I updated .

---

### Post by ivanvajar on 2009-03-08
Is your printer shown in System/Administration/Printing?

---

### Post by ex-wirecutter on 2009-03-08
No it isn't , this is the problem , since I updated there no is connection  with the printer , though it is still shown in the /etc/cups folder . I have tried everything I can think of to get cups scheduler to restart but nothing doing . Fortunately as I say I have a spare computer which I can use if I need to print anything , its just that that one is a lot older and slower.

---

### Post by ivanvajar on 2009-03-08
let's see if CUPS is there 

sudo apt-get install cupsys gnome-cups-manager

---

### Post by unutbu on 2009-03-08
What is the output of ```

dpkg --get-selections | grep cups
```
This should list all the cups related packages you have installed.
I'm thinking that maybe if we can figure out the right package to remove and then reinstall, the problem might be fixed.

---

### Post by ex-wirecutter on 2009-03-08
Have tried that and also reinstall from package manager, cups is there alright I can see it in my file system folder , it just refuses to configure . By the way forgot to say " thank you " for all the time you are spending with me on this .

---

### Post by ivanvajar on 2009-03-08
Don't mention it. That is what this forum is all about. Do as ubuntbu said and run dpkg --get-selections | grep cups. Obviously, he's more experienced with this, so, best of luck!

---

### Post by ex-wirecutter on 2009-03-08
Please excuse me for a minute , as I say I have moved over to my spare old computer so I can print out any replies , will have to switch back to the other which I am having problems with so I can post the output .

---

### Post by rafac24 on 2009-03-08
I too had an issue where it didn't want to Print for me and instead froze indefinitely. 
I just created a New Printer and deleted the old one. 

Works now

---

### Post by ex-wirecutter on 2009-03-08
Back now on the newer computer with the problem since updating cups . The message I get from grep is " cups purge " As I read in another thread someone suggested there is a change between cups and cupsys which may be the problem .

---

### Post by ex-wirecutter on 2009-03-08
Have just done a comparison between my two computers and the one that prints says in the print server box " /var/run/cups.sock ", but in the one that doesn't work it says " local host " and thats the one it wont connect to . Any help ?

---

### Post by kansasnoob on 2009-03-08
Well, it looks like that is supported:

[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_3822.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_3822.html)

Read my post #3 here:

[http://ubuntuforums.org/showthread.php?t=1087054](http://ubuntuforums.org/showthread.php?t=1087054)

---

### Post by ex-wirecutter on 2009-03-08
Well I think we have spent enough time on this so I will thank everyone that has made suggestions and just assume the update I did was a bad move and not automaticaly do updates when they pop up .

---

### Post by ivanvajar on 2009-03-09
That is how completely I lost sound once :-)

---

