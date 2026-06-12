---
title: "Removed WINE, now can't use"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-03-05
Hello, I did have WINE installed on my machine a few days ago. Removed it and now can't open some of the folders from the drop-down ; 


                                                    Places.  I get this error : 

                                                    Failed to execute child process "wine" 
                                                          (No such file or directory)



I did get into the home folder and thought I remove everything .  I did a quick scan of the home folder with clam av, and it read all the files which I thought I removed.

  Is there a way to fix this ?   If I deleted the home folder will it rebuild itself ?

It appears the remnants of wine are still in there .


COMPUTIAC

---

### Post by SavageWolf on 2011-03-05
Deleting your home folder will destroy EVERYTHING you own (On the computer anyway).

Deleting ~/.wine should be enough.

---

### Post by COMPUTIAC on 2011-03-05
Hello,  This is the problem, How do I find this and delete it ?   I thought I did but not 100%  yet.

COMPUTIAC

---

### Post by Marlonsm on 2011-03-05
~/.wine is Wine's folder, it's inside your home folder, but hidden by default.
Open the file manager and press Ctrl+h, it will show all hidden folders (the ones starting with "."), delete Wine's and press Ctrl+h again to hide the others.

---

### Post by COMPUTIAC on 2011-03-05
Hello, sorry, where do I find -        file manager ?

COMPUTIAC

---

### Post by maqtanim on 2011-03-05
> **COMPUTIAC said:**
> Hello, sorry, where do I find -        file manager ?

COMPUTIAC
From the top panel go to **Places > Home Folder**. 
Now press **Ctrl+h**. You'll see all the hidden files and folders.
Look for **.wine** (there is really a dot!) and delete that.

---

### Post by grahammechanical on 2011-03-05
You do realize don't you ... but then again perhaps you do not ... when you delete a file it goes into the rubbish bin symbolically speaking. This why when you right click on a file when using the Nautilus file manager you get the option to move to the rubbish bin.

The files that you delete are still on the hard disc until you decide to empty the rubbish bin. Until then they can be found by any program that you use to search for files.

Technically speaking, in Ubuntu we do not delete files but move them to the rubbish bin.

Regards

---

### Post by COMPUTIAC on 2011-03-05
Hello, I have already done this, it changes nothing,  When I click on Places  > Home    I still get the same error !

 The only way to open Home is to click on Computer 1st > then click > Home 

I admit I goofed up things experimenting with WINE , and trying to run different programs on it , Now I just want to put things back as they were .

COMPUTIAC

---

### Post by COMPUTIAC on 2011-03-05
Hello , Yes, I did realize this about the trash bin . As you say when I right click on a file or folder the option to "move to trash"
is one of the choices. 

  I did not understand it was still read as if it was still there.

The problem is ;  after supposedly finding these files , moving them to the trash and emptying the trash ,


         The error , still exists:  

                                              Could not open location 'file:///home/bob'

                                                Failed to execute child process "wine"
                                                       (No such file or directory)


  I don't like to say this anymore but ;  should I do the windows thing and reboot ?

COMPUTIAC

---

### Post by beew on 2011-03-05
> **grahammechanical said:**
> 
Technically speaking, in Ubuntu we do not delete files but move them to the rubbish bin.


Actually you can add the option of permanently delete to the context menu from the file manager, it says "delete" instead of "move to trash" and unlike in Windows "delete" is final (but it will still ask you if you are sure to go ahead). I have that enabled.

@OP
 
Try go to the terminal
```
rm -R .wine


```

---

### Post by COMPUTIAC on 2011-03-05
Hello beew,   This is the read-out of the terminal :

bob@bob-HP-dc5000-uT-DZ216AV:~$ rm -R .wine
rm: cannot remove `.wine': No such file or directory
bob@bob-HP-dc5000-uT-DZ216AV:~$ sudo rm -R .wine
[sudo] password for bob: 
rm: cannot remove `.wine': No such file or directory
bob@bob-HP-dc5000-uT-DZ216AV:~$ 

I still have the error .    How do I enable the delete ?

COMPUTIAC

---

### Post by COMPUTIAC on 2011-03-05
Hello beew ,  I found it .  When I click on places , and find one which still works , click > edit > preferences > Behavior > bottom of window > check >  include a Delete command  that bypasses Trash .

Works great !

      Did not fix my problem.

  COMPUTIAC

---

### Post by beew on 2011-03-05
> **COMPUTIAC said:**
> Hello beew,   This is the read-out of the terminal :

bob@bob-HP-dc5000-uT-DZ216AV:~$ rm -R .wine
rm: cannot remove `.wine': No such file or directory
bob@bob-HP-dc5000-uT-DZ216AV:~$ sudo rm -R .wine
[sudo] password for bob: 
rm: cannot remove `.wine': No such file or directory
bob@bob-HP-dc5000-uT-DZ216AV:~$ 

I still have the error .    How do I enable the delete ?

COMPUTIAC

So .wine has already been deleted. It is a weird problem. I am at a lost. Hope someone more capable comes along to help you out. I am sorry. :(

---

### Post by COMPUTIAC on 2011-03-05
Hello beew ,  Don't be sorry , I have gotten a lot of info. from you which no one else has mentioned .

  Big Plus ,  I now have a   "delete"  choice in my arsenal !

Thank's for your time .

COMPUTIAC

---

### Post by COMPUTIAC on 2011-03-06
Hello ,  I wanted to let everyone know my problem has been "solved" .  I downloaded BleachBit , ran it in regular mode , and all is well at this point .

  I can open anything I click on from the "Places" drop-down and there is no more error showing .

Thank's to all who gave their thoughts on this problem .

COMPUTIAC

---

